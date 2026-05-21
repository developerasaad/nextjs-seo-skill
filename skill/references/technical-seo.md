# Technical SEO

Technical SEO is the foundation that determines whether your content can be discovered, rendered, indexed, and ranked. Get this wrong and on-page work cannot save you.

## 1. Crawling

### robots.txt
- Allow Googlebot, Bingbot, and other reputable crawlers.
- Disallow admin paths, search result pages with thin content, faceted URLs that explode the index, and staging environments.
- Reference the sitemap with an absolute URL.

Example:
```
User-agent: *
Allow: /
Disallow: /admin
Disallow: /api/
Disallow: /*?sort=
Disallow: /*?filter=

Sitemap: https://example.com/sitemap.xml
```

In Next.js App Router, generate this from `app/robots.ts`.

### Crawl budget
- Keep the URL count proportional to the site's authority. A new site does not need 100k pages.
- Remove or noindex thin tag pages, empty search results, and duplicate paginated content.
- Return 404 or 410 for retired URLs. Do not 200 with empty content.
- Avoid infinite spaces: calendars, faceted nav with no `noindex`, session IDs in URLs.

### Server response
- Return 200 for live pages, 301 for permanent moves, 302 for temporary, 404 for missing, 410 for gone, 503 for maintenance.
- Keep TTFB under 600ms. Cache aggressively at the edge.

## 2. Indexing

### Canonical
- Every indexable URL declares its canonical via `<link rel="canonical">`.
- Self-referencing canonicals are correct and required for most pages.
- Use canonicals to consolidate duplicates (tracking parameters, faceted variants, www vs apex).
- Do not point a canonical at a page that returns a different status, redirects, or has a different canonical.

In Next.js, set canonical in `metadata.alternates.canonical`.

### Noindex
- Use `<meta name="robots" content="noindex">` on:
  - Internal search results
  - Thank-you pages
  - User account pages
  - Faceted variants you do not want indexed
- Pair noindex with `follow` so links still pass equity unless you explicitly want a dead end.

### Sitemap
- One sitemap per content type (pages, posts, products, collections) up to 50k URLs each.
- A sitemap index references all sitemaps.
- Include only canonical, indexable, 200-status URLs.
- Update `lastmod` only when the content materially changes.
- Submit in Search Console.

In Next.js, generate from `app/sitemap.ts`. Split via route groups or a sitemap index when over 50k URLs.

### Hreflang
- Use when you serve the same content in multiple languages or regions.
- Each variant lists every other variant plus a self-reference, all with absolute URLs.
- Include `x-default` for the language picker or default region.
- Implement via `metadata.alternates.languages` in the App Router.

## 3. Site architecture

- Flat is better. Every important page should be reachable in 3 clicks from the home page.
- Use breadcrumbs and `BreadcrumbList` schema.
- Group related content under topical hubs (pillar pages).
- Avoid orphan pages. Every page should have at least one internal link in.

## 4. Pagination

- Use `<a href>` links between pages. Do not rely on JavaScript-only pagination.
- Each paginated URL is unique and self-canonical.
- For listing pages, ensure each page has unique title and description with the page number.
- Consider load-more or infinite scroll only with progressive enhancement and proper URLs.

## 5. JavaScript and rendering

- Server-render or static-generate pages that need to rank. Client-only rendering delays indexing and harms rankings.
- In Next.js App Router, default is server components. Use `"use client"` only when needed.
- Critical content (headings, body text, primary CTA, key links) must appear in the initial HTML.
- Avoid hiding content behind tabs or accordions if Google needs to index it. Render it in the DOM, hide with CSS.

## 6. Core Web Vitals

Targets (75th percentile, mobile and desktop):

| Metric | Good | Needs improvement | Poor |
|---|---|---|---|
| LCP | <= 2.5s | 2.5-4.0s | > 4.0s |
| INP | <= 200ms | 200-500ms | > 500ms |
| CLS | <= 0.1 | 0.1-0.25 | > 0.25 |
| TTFB | <= 800ms | 0.8-1.8s | > 1.8s |

### LCP (Largest Contentful Paint)
- Identify the LCP element. Usually a hero image, hero heading, or hero video poster.
- Preload it: `<link rel="preload" as="image" href="..." imagesrcset="...">` or use `priority` on `next/image`.
- Serve modern formats (AVIF, WebP) at the right size.
- Inline critical CSS for the hero region.
- Reduce server response time. Cache HTML at the edge.

### INP (Interaction to Next Paint)
- Replace heavy synchronous handlers with event delegation and `requestIdleCallback`.
- Defer non-critical third-party scripts.
- Use `next/script` with `strategy="afterInteractive"` or `"lazyOnload"`.
- Break long tasks (>50ms) with `scheduler.yield()` or `setTimeout(0)`.

### CLS (Cumulative Layout Shift)
- Set explicit width and height on images and embeds.
- Reserve space for ads, banners, cookie notices.
- Use `font-display: optional` or `next/font` to avoid FOIT/FOUT shifts.
- Avoid injecting content above existing content after load.

### TTFB
- Edge caching for static and ISR pages.
- Database indexes on common query paths.
- Avoid cascading waterfalls in server components; parallelize fetches.

## 7. HTTPS and security

- HTTPS site-wide. HTTP redirects to HTTPS with a 301.
- HSTS header with at least one year, `includeSubDomains`, `preload` once verified.
- Mixed content audit: no HTTP assets on HTTPS pages.
- CSP that allows only the origins you actually use.

## 8. Mobile

- Responsive by default.
- Tap targets at least 48 by 48 CSS pixels with adequate spacing.
- Font sizes at least 16px for body.
- No horizontal scroll on common viewports.
- Test in Search Console's URL Inspection on mobile.

## 9. International SEO

- ccTLD, subdomain, or subpath. Pick one strategy per site and stick with it.
- Hreflang on every variant.
- Localize content, currency, and units. Translation alone is not enough.
- Geotarget in Search Console only for ccTLD or subpath setups.

## 10. Logs and monitoring

- Pull access logs at least monthly. Look for:
  - Googlebot fetching 404s, redirects, or noindex pages
  - Pages never crawled
  - Crawl spikes that hit infrastructure
- Monitor Core Web Vitals with `web-vitals` and ship to GA4 or your analytics backend.
- Watch Search Console for: coverage errors, manual actions, security issues, structured data errors.

## 11. Migration safety

When changing URLs, domains, or platforms:

1. Crawl the current site and export all URLs with their status, title, H1, canonical, and last 90 days of clicks.
2. Map old to new 1:1 where possible. Many-to-one only when content is consolidating.
3. Implement 301s before launch. Test with a sample.
4. Keep the old sitemap available for 30 days post-launch.
5. Update internal links to point to new URLs directly. Do not rely on the redirect chain.
6. Submit the new sitemap in Search Console and request indexing of priority URLs.
7. Monitor coverage, clicks, and rankings weekly for 90 days.

## 12. Technical SEO checklist

- [ ] HTTPS with HSTS.
- [ ] `robots.txt` allows crawling, points to sitemap.
- [ ] `sitemap.xml` (or sitemap index) lists only canonical, indexable URLs.
- [ ] Every indexable URL has a self-referencing canonical.
- [ ] Noindex applied to thin and private pages, with `follow`.
- [ ] No infinite crawl spaces.
- [ ] Status codes correct: 200, 301, 404, 410, 503.
- [ ] Server-rendered or static for SEO routes.
- [ ] Core Web Vitals in the green at the 75th percentile.
- [ ] Mobile-friendly per Search Console and PSI.
- [ ] Hreflang correct and bidirectional for international.
- [ ] Structured data validated.
- [ ] Logs and Search Console monitored monthly.
