# Next.js App Router SEO

Everything in this guide assumes Next.js 14 or later with the App Router. Pages Router patterns are noted only where migration is relevant.

## 1. metadataBase

Set once in `app/layout.tsx`. This makes every relative `openGraph.images` and `twitter.images` URL resolve correctly.

```ts
// app/layout.tsx
import type { Metadata } from "next";

export const metadata: Metadata = {
  metadataBase: new URL(
    process.env.NEXT_PUBLIC_SITE_URL ?? "https://example.com"
  ),
  title: {
    default: "Brand - Tagline",
    template: "%s | Brand",
  },
  description: "One-sentence description of the site, 140-160 chars.",
  applicationName: "Brand",
  authors: [{ name: "Brand", url: "https://example.com/about" }],
  creator: "Brand",
  publisher: "Brand",
  formatDetection: { email: false, address: false, telephone: false },
};
```

## 2. Static metadata

For pages with stable metadata, export a `Metadata` object directly.

```ts
// app/about/page.tsx
import type { Metadata } from "next";

export const metadata: Metadata = {
  title: "About",
  description: "Who we are, what we ship, and how to reach us.",
  alternates: { canonical: "/about" },
  openGraph: {
    title: "About Brand",
    description: "Who we are, what we ship, and how to reach us.",
    url: "/about",
    type: "website",
  },
};

export default function AboutPage() {
  return /* ... */ null;
}
```

## 3. Dynamic metadata with generateMetadata

For dynamic routes, use `generateMetadata`. Fetch in parallel with the page when possible to avoid duplicate requests; Next.js dedupes `fetch` calls automatically.

```ts
// app/blog/[slug]/page.tsx
import type { Metadata } from "next";
import { notFound } from "next/navigation";
import { getPost } from "@/lib/content/posts";

type Props = { params: Promise<{ slug: string }> };

export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const { slug } = await params;
  const post = await getPost(slug);
  if (!post) return {};

  const url = `/blog/${post.slug}`;
  return {
    title: post.seoTitle ?? post.title,
    description: post.seoDescription ?? post.excerpt,
    alternates: { canonical: url },
    openGraph: {
      title: post.seoTitle ?? post.title,
      description: post.seoDescription ?? post.excerpt,
      url,
      type: "article",
      publishedTime: post.publishedAt,
      modifiedTime: post.updatedAt,
      authors: [post.author.name],
      images: post.heroImage
        ? [{ url: post.heroImage, width: 1200, height: 630, alt: post.title }]
        : undefined,
    },
    twitter: {
      card: "summary_large_image",
      title: post.seoTitle ?? post.title,
      description: post.seoDescription ?? post.excerpt,
      images: post.heroImage ? [post.heroImage] : undefined,
    },
  };
}

export default async function BlogPostPage({ params }: Props) {
  const { slug } = await params;
  const post = await getPost(slug);
  if (!post) notFound();
  return /* render post */ null;
}
```

## 4. generateStaticParams for ISR/SSG

```ts
export async function generateStaticParams() {
  const posts = await getAllPostSlugs();
  return posts.map((slug) => ({ slug }));
}

export const revalidate = 3600; // 1 hour ISR
```

For very large catalogs, return a subset and let the rest render on demand:

```ts
export const dynamicParams = true;
export async function generateStaticParams() {
  const top = await getTopPostSlugs(500);
  return top.map((slug) => ({ slug }));
}
```

## 5. File-based OG and Twitter images

Generate OG images at the edge with `opengraph-image.tsx` and `twitter-image.tsx`. Place per route to override the default.

```tsx
// app/blog/[slug]/opengraph-image.tsx
import { ImageResponse } from "next/og";
import { getPost } from "@/lib/content/posts";

export const runtime = "edge";
export const size = { width: 1200, height: 630 };
export const contentType = "image/png";
export const alt = "Blog post cover image";

export default async function Image({ params }: { params: { slug: string } }) {
  const post = await getPost(params.slug);
  return new ImageResponse(
    (
      <div
        style={{
          width: "100%",
          height: "100%",
          display: "flex",
          flexDirection: "column",
          justifyContent: "space-between",
          padding: 64,
          background: "linear-gradient(135deg, #0f172a, #1e293b)",
          color: "white",
          fontSize: 64,
          fontWeight: 700,
        }}
      >
        <div style={{ fontSize: 28, opacity: 0.8 }}>BRAND</div>
        <div style={{ display: "flex", lineHeight: 1.1 }}>{post?.title ?? "Untitled"}</div>
        <div style={{ fontSize: 28, opacity: 0.8 }}>example.com</div>
      </div>
    ),
    size
  );
}
```

The route now serves `/blog/[slug]/opengraph-image` automatically and Next.js wires it into the OG tags. Do not add a manual `openGraph.images` entry for the same image.

## 6. sitemap.ts

```ts
// app/sitemap.ts
import type { MetadataRoute } from "next";
import { getAllPosts, getAllProducts } from "@/lib/content";

export default async function sitemap(): Promise<MetadataRoute.Sitemap> {
  const base = process.env.NEXT_PUBLIC_SITE_URL ?? "https://example.com";

  const staticRoutes: MetadataRoute.Sitemap = [
    { url: `${base}/`, changeFrequency: "weekly", priority: 1.0 },
    { url: `${base}/about`, changeFrequency: "yearly", priority: 0.5 },
    { url: `${base}/pricing`, changeFrequency: "monthly", priority: 0.8 },
  ];

  const [posts, products] = await Promise.all([getAllPosts(), getAllProducts()]);

  const postRoutes: MetadataRoute.Sitemap = posts.map((p) => ({
    url: `${base}/blog/${p.slug}`,
    lastModified: p.updatedAt,
    changeFrequency: "monthly",
    priority: 0.7,
  }));

  const productRoutes: MetadataRoute.Sitemap = products.map((p) => ({
    url: `${base}/products/${p.slug}`,
    lastModified: p.updatedAt,
    changeFrequency: "weekly",
    priority: 0.8,
  }));

  return [...staticRoutes, ...postRoutes, ...productRoutes];
}
```

For more than 50,000 URLs, split into multiple sitemaps using sitemap groups:

```ts
// app/blog/sitemap.ts
export async function generateSitemaps() {
  return [{ id: 0 }, { id: 1 }, { id: 2 }];
}

export default async function sitemap({ id }: { id: number }) {
  const start = id * 50000;
  const posts = await getPostsRange(start, start + 50000);
  return posts.map((p) => ({ url: `https://example.com/blog/${p.slug}` }));
}
```

## 7. robots.ts

```ts
// app/robots.ts
import type { MetadataRoute } from "next";

export default function robots(): MetadataRoute.Robots {
  const base = process.env.NEXT_PUBLIC_SITE_URL ?? "https://example.com";
  return {
    rules: [
      { userAgent: "*", allow: "/", disallow: ["/admin", "/api/"] },
    ],
    sitemap: `${base}/sitemap.xml`,
    host: base,
  };
}
```

## 8. JSON-LD in App Router

Render JSON-LD in the server component, not via `next/head`.

```tsx
// app/blog/[slug]/page.tsx (excerpt)
export default async function BlogPostPage({ params }: { params: Promise<{ slug: string }> }) {
  const { slug } = await params;
  const post = await getPost(slug);
  if (!post) notFound();

  const jsonLd = {
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    headline: post.title,
    image: post.heroImage,
    datePublished: post.publishedAt,
    dateModified: post.updatedAt,
    author: { "@type": "Person", name: post.author.name, url: post.author.url },
    publisher: {
      "@type": "Organization",
      name: "Brand",
      logo: { "@type": "ImageObject", url: "https://example.com/logo.png" },
    },
    mainEntityOfPage: { "@type": "WebPage", "@id": `https://example.com/blog/${post.slug}` },
  };

  return (
    <article>
      <script
        type="application/ld+json"
        // Use a unique key to allow multiple JSON-LD blocks per page.
        dangerouslySetInnerHTML={{ __json: undefined as never, __html: JSON.stringify(jsonLd) }}
      />
      {/* article content */}
    </article>
  );
}
```

For a typed builder pattern, see `references/schema-markup.md`.

## 9. Internationalization

```ts
// app/[locale]/page.tsx
export async function generateMetadata(
  { params }: { params: Promise<{ locale: string }> }
): Promise<Metadata> {
  const { locale } = await params;
  const t = await loadCopy(locale);

  return {
    title: t.home.title,
    description: t.home.description,
    alternates: {
      canonical: `/${locale}`,
      languages: {
        "en-US": "/en",
        "es-ES": "/es",
        "fr-FR": "/fr",
        "x-default": "/en",
      },
    },
    openGraph: { locale, alternateLocale: ["en_US", "es_ES", "fr_FR"] },
  };
}
```

## 10. Performance defaults

- `next/image` with explicit `width` and `height`. Use `priority` on the LCP image only.
- `next/font` for self-hosted, zero-CLS fonts. Avoid Google Fonts via `<link>`.
- `next/script` with the right strategy:
  - `beforeInteractive` only for critical libs that must run before hydration.
  - `afterInteractive` for analytics that need DOM ready.
  - `lazyOnload` for non-essential widgets.
- Use `fetch` with `next: { revalidate: <seconds> }` to cache server-side data. Set `cache: "force-cache"` for fully static content, `"no-store"` for personalized content.

## 11. Common mistakes

- Setting metadata in a client component. `Metadata` exports must live in server components or layouts.
- Adding `<head>` tags manually. Use `Metadata` and let Next.js render them in the right order.
- Using `priority` on every image. It defeats the purpose and harms LCP elsewhere.
- Forgetting `metadataBase`. OG and Twitter image URLs become invalid relative paths.
- Using `params` synchronously in Next.js 15+. `params` is a `Promise` now; `await` it.
- Putting JSON-LD in `next/head`. Render it inside the server component's JSX.

## 12. Validation pipeline

After every metadata or schema change:

1. `next build` - catches type errors in the `Metadata` shape.
2. View source on the deployed URL - confirm the rendered tags.
3. Rich Results Test - validate JSON-LD.
4. Search Console URL Inspection - confirm Google sees the canonical, OG image, and structured data.
5. Lighthouse SEO audit - target 100.
