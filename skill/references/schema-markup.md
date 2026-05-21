# Structured data and JSON-LD

JSON-LD is the recommended format for structured data on the web. It is a separate `<script>` block, decoupled from the rendered HTML, easy to generate from data, and easy to validate.

## 1. Rules of thumb

- One concept per JSON-LD block. Multiple blocks per page are allowed.
- Every required property must be present and accurate. Do not invent data.
- Match the schema to what users actually see on the page.
- Validate with the Rich Results Test before shipping.
- Render in a server component for App Router, never in `next/head`.

## 2. Render pattern in Next.js

```tsx
function JsonLd({ data }: { data: object }) {
  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(data) }}
    />
  );
}
```

Use a typed builder per type so usage is safe and consistent:

```ts
// lib/schema/builders/article.ts
type ArticleInput = {
  url: string;
  title: string;
  description: string;
  image: string;
  datePublished: string;
  dateModified: string;
  authorName: string;
  authorUrl?: string;
  publisherName: string;
  publisherLogo: string;
};

export function buildArticleSchema(i: ArticleInput) {
  return {
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    headline: i.title,
    description: i.description,
    image: i.image,
    datePublished: i.datePublished,
    dateModified: i.dateModified,
    author: { "@type": "Person", name: i.authorName, url: i.authorUrl },
    publisher: {
      "@type": "Organization",
      name: i.publisherName,
      logo: { "@type": "ImageObject", url: i.publisherLogo },
    },
    mainEntityOfPage: { "@type": "WebPage", "@id": i.url },
  } as const;
}
```

## 3. Article and BlogPosting

Use `BlogPosting` for editorial blog content; use `Article` or `NewsArticle` for journalism.

Required: `headline`, `image`, `datePublished`, `author`.

```json
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "Keyword Research in 2026: A Practical Playbook",
  "description": "Move from a seed term to a publishable content map.",
  "image": "https://example.com/og/keyword-research.png",
  "datePublished": "2026-05-21T08:00:00Z",
  "dateModified": "2026-05-21T08:00:00Z",
  "author": {
    "@type": "Person",
    "name": "Jane Doe",
    "url": "https://example.com/authors/jane-doe"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Example",
    "logo": { "@type": "ImageObject", "url": "https://example.com/logo.png" }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://example.com/blog/keyword-research"
  }
}
```

## 4. FAQPage

Use only when the FAQ is visible on the page and the answers are not promotional. Each question must have one answer.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is keyword clustering?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Keyword clustering groups queries that share substantially overlapping SERPs so a single page can target many queries at once."
      }
    },
    {
      "@type": "Question",
      "name": "How long should a meta description be?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Aim for 140 to 160 characters. Include the primary keyword and a soft call to action."
      }
    }
  ]
}
```

## 5. Product

Required: `name`, `image`, `description`, `offers`. For aggregate ratings, both `ratingValue` and `reviewCount` are required.

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Acme Pro Plan",
  "description": "All-in-one SEO platform for growing teams.",
  "image": "https://example.com/products/pro-plan.png",
  "brand": { "@type": "Brand", "name": "Acme" },
  "sku": "ACME-PRO-2026",
  "offers": {
    "@type": "Offer",
    "url": "https://example.com/pricing",
    "priceCurrency": "USD",
    "price": "49.00",
    "priceValidUntil": "2026-12-31",
    "availability": "https://schema.org/InStock",
    "itemCondition": "https://schema.org/NewCondition"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "284"
  }
}
```

## 6. Organization

Place once on the home page or in the root layout's JSON-LD.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "sameAs": [
    "https://twitter.com/example",
    "https://www.linkedin.com/company/example",
    "https://www.youtube.com/@example"
  ],
  "contactPoint": [
    {
      "@type": "ContactPoint",
      "contactType": "customer support",
      "email": "support@example.com",
      "availableLanguage": ["English", "Spanish"]
    }
  ]
}
```

## 7. WebSite with SearchAction

Lets Google show a search box in the SERP for navigational queries.

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Example",
  "url": "https://example.com",
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://example.com/search?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
```

## 8. BreadcrumbList

Add to every page that has a breadcrumb trail. Match the visible breadcrumb exactly.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://example.com/" },
    { "@type": "ListItem", "position": 2, "name": "Blog", "item": "https://example.com/blog" },
    { "@type": "ListItem", "position": 3, "name": "Keyword Research", "item": "https://example.com/blog/keyword-research" }
  ]
}
```

## 9. HowTo

Use only when the page is a literal step-by-step procedure. Each step has a name and text; an image per step is best.

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to set up generateMetadata in Next.js",
  "totalTime": "PT5M",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Open the route",
      "text": "Open the page.tsx file for the route you want to optimize."
    },
    {
      "@type": "HowToStep",
      "name": "Export generateMetadata",
      "text": "Add an async function named generateMetadata that returns a Metadata object."
    },
    {
      "@type": "HowToStep",
      "name": "Set canonical and OG",
      "text": "Set alternates.canonical and openGraph fields with absolute URLs derived from metadataBase."
    }
  ]
}
```

## 10. VideoObject

```json
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "Keyword clustering in 5 minutes",
  "description": "A walkthrough of clustering keywords by SERP overlap.",
  "thumbnailUrl": "https://example.com/video/keyword-clustering.jpg",
  "uploadDate": "2026-05-21",
  "duration": "PT5M30S",
  "contentUrl": "https://cdn.example.com/video/keyword-clustering.mp4",
  "embedUrl": "https://example.com/embed/keyword-clustering"
}
```

## 11. Combining schemas

Wrap multiple top-level objects in an array, or render multiple `<script type="application/ld+json">` blocks. Both are valid; multiple blocks are easier to maintain.

```ts
<>
  <JsonLd data={buildArticleSchema(article)} />
  <JsonLd data={buildBreadcrumbList(crumbs)} />
  <JsonLd data={buildFaqPage(faq)} />
</>
```

## 12. Validation

- Rich Results Test: confirms eligibility for rich results.
- Schema Markup Validator: validates the schema itself, even when Google does not surface a rich result.
- Search Console: enhancement reports for FAQ, Product, Article, Breadcrumb, etc., flag issues at scale.

## 13. Common mistakes

- Marking up content that is not visible to users.
- Including promotional language in `FAQPage` answers.
- Using `Product` schema on category pages instead of `ItemList`.
- Missing `priceValidUntil`, `availability`, or `priceCurrency` on `Offer`.
- Pointing `mainEntityOfPage` at the wrong URL.
- Repeating the same `@id` across different entities.
