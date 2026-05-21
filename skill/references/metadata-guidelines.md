# Metadata guidelines

This guide covers titles, meta descriptions, slugs, canonicals, Open Graph, and Twitter Cards. The goal is metadata that earns clicks and renders correctly across every surface (Google, Bing, Twitter, LinkedIn, Slack, iMessage).

## 1. Title tag

### Length
- Target 50-60 characters for desktop.
- Mobile may truncate at ~78 characters; desktop at ~580 pixels.
- Pixel width matters more than character count; capital letters and `W` and `M` consume more pixels.

### Composition
- Primary keyword in the first 30 characters where natural.
- One differentiator: number, year, brand, audience, benefit.
- Brand suffix `| Brand` or ` - Brand` after a separator. Drop the brand for brand-strong queries to save space.

### Templates
- Informational: `[Primary Keyword]: [Promise] in [Year] | [Brand]`
- Listicle: `[Number] [Best/Top] [Primary Keyword] for [Audience] in [Year]`
- Comparison: `[Option A] vs [Option B]: [Outcome] | [Brand]`
- Product: `[Product Name] - [Primary Benefit] | [Brand]`
- Local: `[Service] in [City] | [Brand]`

### Anti-patterns
- Title case capitalization stuffed with keywords.
- Pipes for every word: `SEO | Tools | Reviews | 2026 | Brand`.
- Dates in evergreen titles you will not maintain.
- Identical titles across paginated or filtered URLs.

## 2. Meta description

### Length
- 140-160 characters for desktop.
- 120 for safety on mobile.
- Google rewrites descriptions ~70 percent of the time. Aim for clarity even if Google chooses something else.

### Composition
- Primary keyword once, naturally.
- Name the audience and the outcome.
- Include a soft CTA: "see the template", "compare plans", "get the checklist".
- No clickbait. Match the page.

### Templates
- Informational: `[Outcome] with [Primary Keyword]. [Mechanism or proof]. [Soft CTA].`
- Commercial: `Compare [Primary Keyword] for [Audience]. [Differentiator]. [CTA].`
- Product: `[Product] helps [Audience] [Outcome]. [Proof point]. [CTA].`

### Anti-patterns
- Generic descriptions used across many pages.
- Sentences that end before the primary value is communicated.
- Walls of keywords with no narrative.

## 3. URL slug

- Lowercase, ASCII, hyphens between words.
- 3-5 meaningful words. Drop articles unless required.
- Reflect the primary keyword without stuffing.
- No dates unless the page is dated content (news).
- No category prefixes that duplicate the URL path.
- Stable forever. Once published, do not change. If you must, 301 the old slug.

Good: `/blog/meta-description-template`
Bad: `/blog/2026/01/the-ultimate-meta-description-template-for-seo-in-2026`

## 4. Canonical URL

- Every indexable page declares a canonical.
- Self-referencing canonicals are correct for most pages.
- Use absolute URLs with the production protocol and host.
- Canonical points only to a 200-status page with the same content.
- Faceted, filtered, paginated, and tracking-parameter variants point to the canonical primary URL when their content is duplicate or near-duplicate.

In Next.js: `metadata.alternates.canonical = "/path"` resolves against `metadataBase`.

## 5. Open Graph

OG tags drive Facebook, LinkedIn, Slack, iMessage, Discord, and many embed previews.

Required:
- `og:title` (60-90 chars)
- `og:description` (~150 chars)
- `og:url` (canonical URL)
- `og:image` (1200x630, under 5MB, JPG or PNG)
- `og:type` (`website` for most pages, `article` for blog posts, `product` for product pages)

Recommended additions for articles:
- `og:locale`
- `article:published_time`
- `article:modified_time`
- `article:author`
- `article:section`
- `article:tag`

In Next.js:

```ts
openGraph: {
  type: "article",
  url: "/blog/keyword-research",
  title: "Keyword Research in 2026: A Practical Playbook",
  description: "Move from a seed term to a publishable content map.",
  siteName: "Example",
  locale: "en_US",
  publishedTime: "2026-05-21T08:00:00Z",
  modifiedTime: "2026-05-21T08:00:00Z",
  authors: ["Jane Doe"],
  images: [{ url: "/og/keyword-research.png", width: 1200, height: 630, alt: "Keyword Research" }],
}
```

## 6. Twitter Cards

Twitter (X) reads OG tags as a fallback but prefers explicit `twitter:` tags.

- `twitter:card`: `summary` for short posts, `summary_large_image` for articles and landing pages.
- `twitter:title`: 70 chars.
- `twitter:description`: 200 chars.
- `twitter:image`: 1200x600 minimum, 2:1 ratio for `summary_large_image`.
- `twitter:site` and `twitter:creator`: handles for the brand and author.

In Next.js:

```ts
twitter: {
  card: "summary_large_image",
  site: "@brand",
  creator: "@authorhandle",
  title: "Keyword Research in 2026",
  description: "A practical playbook from seed to publishable map.",
  images: ["/og/keyword-research.png"],
}
```

## 7. OG image design

- 1200x630, safe zone 1100x550 to avoid edge cropping.
- Brand wordmark in a corner.
- Title large enough to read at 600x315 (the small thumbnail size).
- High contrast, brand colors, no clutter.
- Test in:
  - Facebook Sharing Debugger
  - LinkedIn Post Inspector
  - Twitter Card Validator (or post a draft to a private account)
  - Slack and iMessage paste tests

Generate dynamically with Next.js `opengraph-image.tsx` for any catalog content.

## 8. Locale and language

- Set `og:locale` for the primary locale.
- Set `og:locale:alternate` for translations.
- Use `metadata.alternates.languages` for hreflang.
- The `lang` attribute on `<html>` matches the page locale.

## 9. Robots metadata

```ts
robots: {
  index: true,
  follow: true,
  nocache: false,
  googleBot: {
    index: true,
    follow: true,
    "max-snippet": -1,
    "max-image-preview": "large",
    "max-video-preview": -1,
  },
}
```

For private or thin pages: `index: false, follow: true`.

## 10. Title and description quality scoring

Use this rubric for self-review or to guide an editor:

| Criterion | Weight | Pass |
|---|---|---|
| Primary keyword present | 3 | Title and description |
| Length within range | 2 | 50-60 / 140-160 |
| Distinct from siblings | 2 | No template-only |
| Audience named | 1 | Title or description |
| Differentiator | 1 | Year, number, brand, benefit |
| Natural language | 1 | Reads like a sentence |

Score 8+ to ship.

## 11. Common mistakes

- Pulling description from the first paragraph of the page automatically.
- Using `metadataBase` set to localhost in production builds.
- Forgetting OG images on dynamic routes.
- Using PNG screenshots that exceed 5MB.
- Setting `twitter:card` to `summary_large_image` without an image of the right size.
- Inconsistent canonical and `og:url`.
