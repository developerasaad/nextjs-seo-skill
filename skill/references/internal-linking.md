# Internal linking strategy

Internal links are the cheapest, fastest ranking lever you control. They distribute link equity, signal topical relevance, and keep users moving through the funnel. This guide covers structure, anchor text, placement, and maintenance.

## 1. Site architecture

Two structures dominate:

### Hub-and-spoke (recommended for content sites)
- A pillar page covers a broad topic.
- Spoke pages cover specific subtopics in depth.
- Every spoke links back to the pillar.
- The pillar links to every spoke.
- Spokes link to 2-3 sibling spokes when relevant.

### Silo
- Top-level category page links only within its silo.
- Tighter topical authority but less flexibility.
- Useful for ecommerce: each category is a silo of related products.

Most modern sites combine both: hub-and-spoke for editorial, silo for commerce.

## 2. Anchor text

Anchor text is the most important ranking signal in an internal link. Treat it like ad copy.

### Rules
- Descriptive. The reader should know where the link goes without context.
- Varied. Mix exact-match, partial-match, branded, and natural-language anchors.
- Keyword-aware but not keyword-stuffed. Repeating the same exact-match anchor on every page risks looking manipulative.
- Stable. If you change a page's primary keyword, update its inbound anchor text.

### Distribution targets
For a single destination URL across the site:
- 30-40 percent partial-match (`learn keyword clustering`, `our keyword clustering guide`)
- 20-30 percent exact-match (`keyword clustering`)
- 20-30 percent natural language (`how we cluster keywords by SERP overlap`)
- 10-20 percent branded or generic (`see the guide`, `Brand's playbook`)

### Anti-patterns
- "Click here", "read more", "learn more" as the only anchor.
- Whole-paragraph anchors that hide the link.
- Identical exact-match anchor on every internal link to the same URL.
- Anchor text that contradicts the destination.

## 3. Placement

Where a link sits matters as much as the anchor.

| Location | Equity weight | When to use |
|---|---|---|
| First paragraph body link | High | The most important destination per article |
| Mid-article body link | High | Relevant secondary destination |
| H2 or H3 link | Medium-high | When the section title naturally references another page |
| Sidebar link | Medium | Editorial highlights, related posts |
| Footer link | Low | Site-wide utility links only |
| Nav link | Site-wide | Top-level pages and key conversion paths |

Body links are stronger than nav and footer because they sit in unique content. Use the first body link to point to the most important destination.

## 4. Link volume

Per page guidance:
- Editorial article (1500-3000 words): 5-15 internal body links.
- Pillar page (3000+ words): 15-30 internal body links.
- Product page: 3-8 internal body links to related products, category, and supporting content.
- Landing page: 2-5 internal body links, prioritizing the conversion path.

Too few links wastes equity; too many dilutes it.

## 5. Link prioritization formula

When deciding which existing pages should link to a new page:

```
score = topical_relevance * authority_of_source / link_distance
```

- **Topical relevance**: 1-5, how closely the source content overlaps with the destination's primary keyword.
- **Authority of source**: external links + organic traffic + age.
- **Link distance**: clicks from the home page; lower is better.

Pick the top 5-10 sources and add contextual links from each.

## 6. Surfacing new pages

When a new page goes live:
1. Add a body link from the parent pillar.
2. Add 2-3 sibling links from the strongest related spokes.
3. Add a card to any "related posts" or "related products" component on relevant URLs.
4. Add to the topic hub navigation if one exists.
5. Update the sitemap and request indexing of the source pages so Google re-crawls them.

## 7. Breadcrumbs

- Breadcrumbs give Google a second internal link path and help users orient.
- Match the URL structure: `Home > Blog > SEO > Keyword Research`.
- Render as `<nav aria-label="Breadcrumb">` with `<ol>` and `<li>` items.
- Mark up with `BreadcrumbList` schema.

## 8. Contextual link components

Build components that make linking easy and consistent:

- A `<RelatedReading>` block at the end of articles, fed from a tags-and-cluster lookup.
- A `<CalloutLink>` component for inline references that look like a designed element.
- A `<HubCard>` for pillar-page sections that link to spokes.

Keep these server components in Next.js so the links exist in the initial HTML.

## 9. Link equity hygiene

- Audit quarterly with Screaming Frog or your tool of choice.
- Fix internal redirects: link directly to the final URL.
- Fix internal 404s.
- Remove links to noindex pages from indexable pages.
- Audit orphan pages: any page with zero internal links is invisible to crawlers without a sitemap.

## 10. Outbound external links

- Link to primary sources. It signals expertise and earns reciprocal value.
- Do not over-rotate `nofollow`. Reserve it for paid placements.
- Open external links in the same tab. Returning users can hit the back button.
- Aim for 1-3 high-quality external links per article.

## 11. Common mistakes

- Linking only from the footer. Body links are stronger.
- Same exact-match anchor on every link to the same URL.
- Linking from low-authority pages and skipping high-authority ones.
- Forgetting to update inbound links when a destination URL changes.
- Stuffing related-posts widgets with unrelated content.

## 12. Internal linking checklist

- [ ] Every page belongs to a pillar or is a pillar itself.
- [ ] Every spoke has a body link from its pillar.
- [ ] Every spoke has 2-3 sibling links.
- [ ] Anchor text is descriptive and varied.
- [ ] First body link points to the most important destination.
- [ ] Breadcrumbs present with `BreadcrumbList` schema.
- [ ] No internal redirects or 404s.
- [ ] No orphan indexable pages.
- [ ] Related-posts component populated and accurate.
