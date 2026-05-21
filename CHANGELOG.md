# Changelog

All notable changes to this project will be documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). This project uses [Semantic Versioning](https://semver.org/spec/v2.0.0.html) for version numbers, where:

- `MAJOR` — breaking change to the skill interface or directory structure
- `MINOR` — new reference document, new capability, or significant addition
- `PATCH` — corrections, clarifications, updated code examples

---

## [Unreleased]

### Planned
- `generateViewport` reference for the new Next.js viewport export
- Astro version of the App Router SEO reference
- Automated JSON-LD validation in CI

---

## [1.0.0] — 2026-05-21

### Added
- Initial release.
- `skill/SKILL.md` — skill definition with keywords, capabilities, operating principles, default workflow, output formats, guardrails, and reference index.
- `skill/references/keyword-research.md` — SERP-similarity clustering, intent classification, keyword universe expansion, cannibalization detection, prioritization formula.
- `skill/references/on-page-seo.md` — URL, title tag, meta description, heading hierarchy, above-the-fold copy, body copy, semantic coverage, media, links, FAQ block, featured snippet patterns, readability, freshness.
- `skill/references/technical-seo.md` — crawling, robots.txt, crawl budget, indexing, canonical, noindex, sitemap, hreflang, site architecture, pagination, JavaScript rendering, Core Web Vitals (LCP, INP, CLS, TTFB), HTTPS, mobile, international SEO, logs, site migration safety.
- `skill/references/nextjs-seo.md` — `metadataBase`, static `Metadata`, `generateMetadata` with awaited params, `generateStaticParams`, `opengraph-image.tsx` edge runtime, `sitemap.ts` (including sitemap groups for >50k URLs), `robots.ts`, JSON-LD in server components, i18n, performance defaults, common mistakes, validation pipeline.
- `skill/references/schema-markup.md` — `Article` / `BlogPosting`, `FAQPage`, `Product`, `Organization`, `WebSite` with `SearchAction`, `BreadcrumbList`, `HowTo`, `VideoObject`, typed builder pattern, `<JsonLd />` component, combining schemas, validation checklist, common mistakes.
- `skill/references/metadata-guidelines.md` — title tag length and templates, meta description rules and templates, URL slug rules, canonical, Open Graph required and recommended fields, Twitter Cards, OG image design, locale and language, robots metadata, quality scoring rubric.
- `skill/references/internal-linking.md` — hub-and-spoke vs silo, anchor text rules and distribution targets, placement hierarchy, link volume guidance, link equity prioritization, surfacing new pages, breadcrumbs, contextual link components, link equity hygiene, common mistakes.
- `skill/references/blog-writing.md` — brief format, outline template, drafting voice and paragraph rules, three-pass editing system, featured snippet optimization, readability targets, imagery, linking, schema plan, publish checklist, refresh cadence.
- `skill/references/landing-pages.md` — one page one job principle, page structure (hero through footer trust), hero copy patterns, above-the-fold requirements, CTA design, forms, imagery, performance targets, SEO essentials, conversion measurement, A/B testing order, common mistakes.
- `skill/references/eeat.md` — Experience, Expertise, Authoritativeness, Trustworthiness definitions and signals, YMYL handling, author profile structure with `Person` schema, editorial standards, citations, updates and corrections policy, About page, trust elements site-wide, off-site reputation, AI-generated content guidance.

---

*Entries are added in reverse chronological order. The `[Unreleased]` section accumulates changes that have not yet been tagged.*
