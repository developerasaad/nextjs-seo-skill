# nextjs-seo-skill

> A structured AI skill for generating SEO-optimized metadata, structured data, and content in Next.js App Router projects.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![GitHub Stars](https://img.shields.io/github/stars/developerasaad/nextjs-seo-skill?style=social)](https://github.com/developerasaad/nextjs-seo-skill)

---

## Repository name suggestions

Five options if you want to fork or adapt this under a different name:

1. **`nextjs-seo-skill`** — short, descriptive, easy to remember *(used here)*
2. **`seo-skill-nextjs-app-router`** — more specific to the App Router context
3. **`ai-seo-assistant-nextjs`** — surfaces the AI-assisted workflow angle
4. **`nextjs-metadata-seo-toolkit`** — emphasizes the metadata generation focus
5. **`nextjs-seo-expert-skill`** — mirrors the internal skill identifier

---

## Short description

An AI skill that helps developers and content teams build SEO-optimized Next.js pages — `generateMetadata`, JSON-LD schemas, Open Graph, Twitter Cards, content outlines, technical SEO, and more.

---

## Why this exists

SEO guidance for Next.js exists in fragments: the App Router metadata docs, the Google structured data reference, Core Web Vitals guides, Stack Overflow answers about canonical URLs, blog posts about `FAQPage` JSON-LD. When you are in the middle of shipping a page, tabbing between five browser windows to get one route right wastes time.

This skill packages that knowledge into a single coherent set of reference documents and wires it into AI-assisted development workflows. Load it and your assistant can generate correct `generateMetadata` exports, validated JSON-LD, keyword clusters, and editorial briefs without needing you to paste documentation into every prompt.

It covers both the engineering side (App Router metadata, schema builders, `sitemap.ts`, `robots.ts`, `opengraph-image.tsx`) and the content side (keyword research, intent analysis, blog outlines, landing page structure, E-E-A-T signals). That combination is usually split across two separate disciplines; this skill keeps them in sync.

---

## Features

### Metadata and technical
- `generateMetadata` patterns for static and dynamic routes
- `metadataBase` setup and resolution for OG images
- Canonical URL generation with `alternates.canonical`
- `robots` metadata with Googlebot-specific directives
- `app/sitemap.ts` generation including sitemap indexes for large catalogs
- `app/robots.ts` generation
- File-based `opengraph-image.tsx` and `twitter-image.tsx` at the edge
- `generateStaticParams` for ISR and SSG of dynamic SEO routes
- Hreflang via `metadata.alternates.languages`
- `next/image` with LCP-correct `priority` usage
- `next/font` for zero-CLS font loading
- `next/script` strategy recommendations

### Structured data (JSON-LD)
- `Article` and `BlogPosting`
- `FAQPage`
- `Product` with `Offer` and `AggregateRating`
- `Organization` with `sameAs` and `contactPoint`
- `WebSite` with `SearchAction` sitelinks searchbox
- `BreadcrumbList`
- `HowTo` with typed steps
- `VideoObject`
- Typed builder pattern for reusable, type-safe schema generation

### Open Graph and Twitter Cards
- `og:title`, `og:description`, `og:url`, `og:image`, `og:type`
- Article-specific OG properties (`publishedTime`, `modifiedTime`, `author`)
- `twitter:card`, `twitter:site`, `twitter:creator`
- Dynamic OG image design guidance
- Platform-specific preview testing checklist

### Keyword research and content strategy
- Keyword expansion from a seed term
- SERP-similarity clustering (not just lexical grouping)
- Search intent classification (informational, commercial, transactional, navigational, local)
- Keyword cannibalization detection and resolution
- Topical map with pillar and spoke structure
- Cluster-to-URL mapping with suggested titles and word counts
- Prioritization scoring formula

### Content creation
- SEO title templates with 3 variants per page
- Meta description templates with 2 variants per page
- URL slug rules
- Content briefs with intent, outline, FAQ, schema plan, internal links
- Long-form article drafting with featured snippet optimization
- Landing page structure with hero, mechanism, social proof, objections, FAQ
- FAQ creation from People Also Ask data
- Readability guidelines (Flesch score targets, sentence length, paragraph length)

### Internal linking
- Hub-and-spoke architecture recommendations
- Anchor text distribution rules
- Link equity prioritization formula
- Breadcrumb structure with `BreadcrumbList` schema
- Orphan page detection guidance
- Post-publish internal link workflow

### Technical SEO
- Crawl budget management
- `robots.txt` rules for common Next.js patterns
- Sitemap best practices including 50k URL limit handling
- Status code decision matrix (200, 301, 302, 404, 410, 503)
- JavaScript rendering implications for SEO
- Pagination best practices
- International SEO with hreflang
- Site migration safety checklist
- Core Web Vitals: LCP, INP, CLS, TTFB targets and fixes
- Monthly log and monitoring workflow

### E-E-A-T and trust
- Author profile structure with `Person` schema
- Editorial standards page guidance
- YMYL content handling
- Citation and sourcing rules
- Correction and update policies
- AI-assisted content guidelines that satisfy quality rater criteria

---

## Directory structure

```
nextjs-seo-skill/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── CHANGELOG.md
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── pull_request_template.md
└── skill/
    ├── SKILL.md                     ← skill definition and behavior
    └── references/
        ├── keyword-research.md      ← clustering, intent, SERP analysis
        ├── on-page-seo.md           ← titles, headings, copy, media, links
        ├── technical-seo.md         ← crawling, indexing, performance
        ├── nextjs-seo.md            ← App Router metadata, sitemap, OG images
        ├── schema-markup.md         ← JSON-LD recipes for every common type
        ├── metadata-guidelines.md   ← title, description, OG, Twitter rules
        ├── internal-linking.md      ← hub-and-spoke, anchor text, link equity
        ├── blog-writing.md          ← outlines, drafting, snippet optimization
        ├── landing-pages.md         ← structure, copy, CTA, conversion
        └── eeat.md                  ← E-E-A-T and trust signals
```

---

## Installation

### Step 1 — Clone or download

```bash
git clone https://github.com/developerasaad/nextjs-seo-skill.git
```

Or download the ZIP from GitHub and unzip it.

### Step 2 — Copy the skill into your project

The skill lives entirely in the `skill/` directory. Copy it into your AI-assisted development environment's skills folder.

For environments that use a `.kiro/skills/` convention:

```bash
cp -r skill/ /path/to/your-project/.kiro/skills/nextjs-seo-expert/
```

Or reference the `skill/` directory directly from wherever your tooling resolves skills.

### Step 3 — Verify the reference files are present

```bash
ls skill/references/
# keyword-research.md  on-page-seo.md  technical-seo.md  nextjs-seo.md
# schema-markup.md  metadata-guidelines.md  internal-linking.md
# blog-writing.md  landing-pages.md  eeat.md
```

No additional dependencies. No npm packages. No build step. Plain markdown.

---

## Usage examples

Once the skill is loaded, your assistant activates on any request that involves SEO, metadata, content, or Next.js page optimization. Here are a few concrete examples.

### Generate a `generateMetadata` function for a blog post route

**Prompt:**
```
Write a generateMetadata function for app/blog/[slug]/page.tsx.
The post has title, description, heroImage, publishedAt, updatedAt, and author fields.
Use my existing metadataBase set in app/layout.tsx.
```

**Output includes:**
- `async function generateMetadata({ params })` with `await params`
- `alternates.canonical`
- `openGraph` with `type: "article"`, `publishedTime`, `modifiedTime`, `authors`, and `images`
- `twitter` card with `summary_large_image`
- A `Metadata` return type that compiles cleanly

---

### Generate JSON-LD for a landing page

**Prompt:**
```
Generate JSON-LD for a SaaS pricing page.
Include Organization, WebSite with SearchAction, and a FAQPage block.
Product name is "Acme Pro", price is $49/month, currency USD, 4.8 rating from 312 reviews.
```

**Output includes:**
- Three `<script type="application/ld+json">` blocks
- Typed builder functions you can drop into `lib/schema/builders/`
- A `<JsonLd />` component for rendering them in a server component

---

### Build a keyword cluster

**Prompt:**
```
I run a SaaS for kids' coloring pages. Seed keyword: "printable coloring pages for kids".
Give me a keyword cluster, intent classification, suggested URLs, target word counts, and internal link map.
```

**Output includes:**
- A YAML-formatted cluster table
- Intent per cluster (informational vs commercial)
- Suggested pillar and spoke URLs
- Cannibalization check flag if any existing URLs are listed

---

### Write a content brief

**Prompt:**
```
Write a content brief for "nextjs metadata seo".
Target audience: mid-level Next.js developers who have used the Pages Router and are migrating to App Router.
Primary conversion: newsletter signup.
```

---

### Audit a page's metadata

**Prompt:**
```
Here is my current metadata for /pricing:
title: "Pricing"
description: "See our plans."
No OG image, no canonical set.
What needs fixing?
```

---

## Example prompts

These prompts work well with the skill loaded. Copy, adapt, and use them directly.

1. `Generate a full generateMetadata export for a Next.js product page at /products/[slug]. Include canonical, OG, and Twitter fields.`
2. `Write a BlogPosting JSON-LD schema for a post titled "How to use generateStaticParams in Next.js 15". Author: Jane Doe. Published today.`
3. `Build a FAQPage schema from these 6 questions: [paste your questions and answers].`
4. `Generate a BreadcrumbList schema for this path: Home > Blog > Next.js SEO > generateMetadata Guide.`
5. `Write a keyword cluster for "nextjs app router seo" with intent classification, suggested URLs, and word counts.`
6. `Write an SEO title and meta description for a page about Core Web Vitals in Next.js. Give me 3 title variants and 2 description variants.`
7. `Generate an app/sitemap.ts file for a Next.js blog with posts fetched from a CMS. Handle up to 50k posts.`
8. `Write an app/robots.ts that blocks /admin, /api, and all paginated facets (/products?page=*).`
9. `Create an opengraph-image.tsx edge function that renders the page title and brand name on a dark gradient.`
10. `Audit this page for E-E-A-T signals: [paste page description]. What is missing?`
11. `Write a content brief for a landing page targeting "best coloring books for toddlers". Primary CTA: add to cart. Include hero copy, FAQ, and internal link targets.`
12. `Detect cannibalization risk: I have /blog/seo-meta-description and /guides/meta-descriptions. Which should I keep?`
13. `Set up hreflang for an English-US, Spanish-ES, and French-FR site using Next.js App Router.`
14. `Write an Organization schema for my company. Name: Acme, website: acme.com, Twitter: @acmehq, LinkedIn: /company/acme, support email: support@acme.com.`
15. `What Core Web Vitals issues would you expect on a Next.js page that uses a custom font via @import in CSS, loads a full Lottie animation above the fold, and has no width/height on its hero image?`
16. `Generate a hub-and-spoke internal link map for a content site about kids' printable activities. Pillar: /printables. Spokes: [list 10].`
17. `Write a 1600-word blog post outline for "how to optimize Next.js pages for Google Search in 2026". Include TL;DR, 6 H2 sections, a FAQ block, and schema plan.`
18. `Propose the minimal Next.js App Router changes to move a Lighthouse SEO score from 82 to 100. I'll share my current metadata and page structure.`

---

## Supported workflows

### Blog publishing
Generate content briefs, outlines, full drafts, author bylines, `BlogPosting` schema, `FAQPage` schema, internal link suggestions, and `generateMetadata` exports — all from a single keyword brief.

### SaaS landing pages
Build hero copy, benefit blocks, FAQ sections, `Product` and `Organization` schemas, Open Graph images, and `generateMetadata` for every pricing or feature page.

### Documentation sites
Generate per-page metadata, breadcrumb trails with `BreadcrumbList` schema, `HowTo` schemas for step-by-step guides, and internal link structure for a multi-section doc site.

### Marketing websites
Cover the full marketing stack: homepage `WebSite` + `Organization` schemas, blog, product pages, use case pages, and landing pages — each with consistent metadata patterns.

### Product and ecommerce pages
Generate `Product` schemas with `Offer`, `AggregateRating`, and `BreadcrumbList`. Handle faceted URLs and canonical decisions for filtered catalog pages.

### Content hubs and topic clusters
Map an entire topical cluster: pillar page, spoke pages, URL structure, internal linking, schema plan, and editorial briefs for each spoke.

### Startup websites
Go from zero to a search-ready Next.js site: `metadataBase`, root layout metadata, homepage schema, sitemap, robots, OG images, and a content roadmap.

---

## Generated outputs

Depending on the request, the skill produces one or more of:

| Output type | Format |
|---|---|
| `generateMetadata` export | TypeScript, App Router compatible |
| `Metadata` object | TypeScript, with all relevant fields populated |
| JSON-LD block | Validated JSON with inline `<script>` tag |
| Schema builder function | TypeScript, typed inputs |
| `opengraph-image.tsx` | Edge runtime, `ImageResponse` |
| `sitemap.ts` | Next.js `MetadataRoute.Sitemap` |
| `robots.ts` | Next.js `MetadataRoute.Robots` |
| Content brief | Markdown, with keyword, intent, outline, FAQ, schema plan |
| Article draft | Markdown, with H1, TL;DR, body, FAQ, sources |
| Landing page copy | Structured markdown sections |
| Keyword cluster | YAML table |
| Internal link map | Markdown table |
| SEO audit | Bulleted findings with recommended fixes |
| Checklist | Per-page or per-workflow verification list |

---

## SEO best practices included

The reference documents in this skill reflect current best practices as of 2026 across several areas:

**Content quality** — Google's helpful content system, E-E-A-T, YMYL handling, originality, and people-first writing. The skill avoids generic AI-output patterns and pushes for specific, verifiable, experience-backed content.

**Keyword strategy** — SERP-similarity clustering rather than lexical grouping, so pages target queries Google actually considers equivalent. Explicit cannibalization detection. Intent-first format selection.

**Technical foundations** — App Router patterns for metadata, sitemap, robots, and OG image generation. Server-side rendering as the default for SEO routes. Canonical URL hygiene. Status code semantics.

**Structured data** — Every schema type includes required and recommended fields. Builder functions enforce correct shapes at the TypeScript level. Validation checkpoints at every step.

**Performance** — Core Web Vitals targets (LCP ≤ 2.5s, INP ≤ 200ms, CLS ≤ 0.1) with specific Next.js implementation patterns for `next/image`, `next/font`, and `next/script`.

---

## Who should use this

- **Next.js developers** who want correct, up-to-date App Router SEO patterns without reading four separate documentation sites.
- **Content teams** at companies shipping marketing sites, blogs, or documentation in Next.js.
- **Technical SEOs** who need to communicate implementation requirements to development teams in code.
- **Founders and indie developers** building their first Next.js site and wanting to get the SEO basics right from the start.
- **Marketing agencies** managing multiple client Next.js projects and wanting a consistent SEO workflow.
- **Developer advocates** and documentation authors who need to produce technically accurate, search-optimized long-form content.

---

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on reporting bugs, proposing changes to the reference documents, and submitting pull requests.

The most useful contributions right now:

- Corrections to any code examples that are outdated or incorrect
- New JSON-LD schema examples for types not yet covered
- Examples from real Next.js projects (with permission)
- Additions to the prompt library

---

## License

[Apache License 2.0](LICENSE)

You are free to use, copy, modify, and distribute this skill in commercial and open-source projects. Attribution is appreciated but not required for most uses. See the LICENSE file for the full terms.

---

## FAQ

**Q: Does this work with the Next.js Pages Router?**
A: The code examples are written for the App Router (`app/` directory, Next.js 13+). Many of the concepts (JSON-LD, OG tags, meta descriptions) apply to any framework, but the TypeScript examples target App Router APIs. Pages Router equivalents are noted where relevant in the reference documents.

**Q: Do I need any paid tools or subscriptions to use this?**
A: No. The skill itself is free and open source. A few reference documents mention tools like Ahrefs, Semrush, or Google Search Console by name in the context of keyword research or validation, but they are optional. The workflows function without them.

**Q: Can I use this with a headless CMS?**
A: Yes. The `generateMetadata` examples fetch data from abstract async functions (e.g., `getPost(slug)`). You wire those functions to your CMS SDK — Contentful, Sanity, Strapi, Payload, or anything else. The skill does not assume a specific data source.

**Q: Is the structured data guaranteed to pass Google's Rich Results Test?**
A: The schemas are written to spec and validated manually against the schema.org definitions. Whether Google awards a rich result depends on additional factors (page quality, content relevance, recency). Always run the Rich Results Test on your specific implementation before treating a schema as production-ready.

**Q: Can I extend the reference documents for my specific niche?**
A: Yes, that is the intended use. Fork the repo, edit the reference files, add your own. The `SKILL.md` points to reference files by relative path; you can add new ones and reference them from the `## Reference index` section.

**Q: Does this handle multilingual and international SEO?**
A: The `technical-seo.md` and `nextjs-seo.md` references cover hreflang, `x-default`, and the Next.js `alternates.languages` pattern. Full localization strategy is beyond the scope of a single skill file but the core implementation patterns are documented.

**Q: What is the difference between this skill and an SEO plugin for a CMS?**
A: A CMS plugin applies SEO rules to content in a GUI. This skill applies SEO knowledge during the development and writing workflow, before content is published. It generates the code you commit, the content you write, and the data structures you ship. It is a development-time tool, not a runtime plugin.

**Q: How do I keep the reference documents up to date?**
A: Watch this repository for updates. Changes to Next.js metadata APIs, Google's structured data guidelines, or Core Web Vitals targets will be reflected in new versions of the reference files. Check `CHANGELOG.md` for what changed between versions.

**Q: Can I use this for non-Next.js projects?**
A: The JSON-LD schemas, keyword research playbook, content writing guides, metadata guidelines, E-E-A-T reference, and landing page guide all apply to any web project. The code examples in `nextjs-seo.md` and parts of `technical-seo.md` are Next.js-specific. Feel free to adapt the concept for Astro, Remix, SvelteKit, or any other framework.

**Q: Will this guarantee higher search rankings?**
A: No. Following these patterns does not guarantee any specific ranking or traffic outcome. Rankings depend on many factors outside this skill's scope — domain authority, competition, link profile, indexing timing, and others. What this skill does is remove the implementation mistakes and content quality issues that commonly prevent pages from ranking. The rest is up to the work.

---

## Roadmap

These are improvements being considered for future versions. None have a committed timeline.

- [ ] Schema builders as a separate TypeScript package on npm
- [ ] Next.js 15 and React 19 pattern updates as they stabilize
- [ ] `generateViewport` reference for the new Next.js viewport export
- [ ] Astro version of the `nextjs-seo.md` reference
- [ ] Remix / React Router v7 version of the `nextjs-seo.md` reference
- [ ] Automated validation CI for JSON-LD examples using a schema.org validator
- [ ] Prompt test suite: a set of reference prompts with expected output shapes
- [ ] Video walkthrough of the keyword-to-published-page workflow
- [ ] Localization: Spanish, Portuguese, and French translations of the reference docs
- [ ] Extended `eeat.md` coverage for medical and financial content verticals

---

## Credits

Written and maintained by [developerasaad](https://github.com/developerasaad).

Reference material draws from publicly available documentation including:
- [Next.js App Router Metadata docs](https://nextjs.org/docs/app/building-your-application/optimizing/metadata)
- [Google Search Central documentation](https://developers.google.com/search)
- [Schema.org specification](https://schema.org)
- [Web Vitals documentation](https://web.dev/vitals/)
- [Google's helpful content guidance](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)

---

## Star history

[![Star History Chart](https://api.star-history.com/svg?repos=developerasaad/nextjs-seo-skill&type=Date)](https://star-history.com/#developerasaad/nextjs-seo-skill&Date)

---
