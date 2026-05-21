# Keyword research and clustering

This guide is the playbook for moving from a seed term to a publishable content map. Follow it whenever the user asks for keyword research, a content plan, a topical map, or a SERP analysis.

## 1. Define the seed and the goal

Before searching, write one sentence: who the page is for, what they want, and what action you want them to take. This becomes the rubric for every later decision.

Capture:
- Seed term(s)
- Target audience and funnel stage (awareness, consideration, decision, retention)
- Primary conversion event (signup, demo, purchase, newsletter, app install)
- Geographic and language scope
- Brand position (challenger, leader, niche specialist)

## 2. Expand the keyword universe

Pull candidates from at least four sources so you do not over-index on one tool:

1. **SERP autocomplete** - Google Suggest, YouTube, Amazon, Reddit, Pinterest.
2. **People Also Ask** and **Related searches** at the bottom of the SERP.
3. **Competitor pages** - top three ranking URLs for the seed, then their internal links.
4. **Tool data** - Ahrefs, Semrush, Moz, Keyword Planner, GSC queries when available. Capture volume, KD, CPC, and parent topic.

Record every candidate in a single table with columns: keyword, volume, KD, intent, SERP type, top-ranking URL, content format, our existing URL (if any).

## 3. Classify search intent

For every keyword, assign one primary intent:

| Intent | SERP signals | Best format |
|---|---|---|
| Informational | "what is", "how to", PAA-heavy, featured snippet, video carousel | Guide, explainer, glossary, video |
| Commercial investigation | "best", "vs", "review", "alternatives", listicles dominate | Listicle, comparison, review |
| Transactional | "buy", "pricing", "coupon", product results, shopping ads | Product page, pricing page |
| Navigational | brand or product name, sitelinks present | Homepage, brand page |
| Local | map pack, "near me" | Location page, GBP |

If the SERP mixes formats, pick the dominant one. If informational and commercial both rank, write a hybrid: long-form guide with a clear product CTA.

## 4. Cluster by SERP similarity

Two keywords belong in the same cluster when at least three of the top ten URLs overlap. Lexical similarity is a hint, not proof. "best running shoes" and "top running shoes" usually share a SERP; "running shoes" and "running shoe size chart" do not.

Process:

1. Pull the top 10 URLs for each candidate.
2. Compute pairwise overlap.
3. Group keywords whose pairwise overlap is at least 30 percent.
4. Pick the highest-volume member as the cluster's primary keyword.
5. The rest become secondary keywords for the same page.

## 5. Map clusters to pages and pillars

For each cluster, decide:

- **Pillar or spoke?** Pillars cover the broad term and link to every spoke. Spokes cover one specific subtopic and link back to the pillar.
- **URL.** Short, descriptive, no dates, no IDs. Examples: `/guides/keyword-research`, `/blog/seo-meta-description-template`.
- **Format and length.** Match what already ranks, then add 20-30 percent more depth or a unique angle (original data, expert quote, interactive tool).
- **Author.** Match expertise to topic. YMYL topics need credentialed authors.

## 6. Detect cannibalization

Before publishing a new page, check Search Console and the live site for any URL that already ranks for the cluster's primary keyword. If one exists:

- If the existing page is strong, expand it instead of creating a new URL.
- If two pages target the same intent, consolidate with a 301 and merge content.
- If intents differ, sharpen each page's primary keyword and update internal links so that anchor text reinforces the split.

## 7. Output template

Return clusters in this exact shape:

```yaml
- cluster: "seo meta description"
  intent: informational
  pillar: "/guides/on-page-seo"
  primary_keyword: "seo meta description"
  secondary_keywords:
    - "meta description length 2026"
    - "meta description examples"
    - "meta description generator"
  monthly_volume: 4400
  difficulty: 38
  serp_features: [featured_snippet, paa, video]
  suggested_url: "/blog/seo-meta-description"
  suggested_title: "SEO Meta Description: Length, Examples, and a 2026 Template"
  format: long_form_guide
  target_word_count: 1800
  internal_links_in: ["/guides/on-page-seo", "/blog/title-tag-template"]
  internal_links_out: ["/blog/title-tag-template", "/tools/serp-preview"]
  schema: [Article, FAQPage, BreadcrumbList]
  success_metric: "rank top 5 for primary keyword within 90 days; 2k organic sessions/mo"
```

## 8. Prioritization

Rank clusters by a simple score: `priority = (intent_fit * traffic_potential) / (difficulty * production_cost)`.

- **Intent fit**: 1-5, how well the keyword aligns with revenue.
- **Traffic potential**: realistic share of monthly volume at position 3-5.
- **Difficulty**: tool KD or your honest assessment.
- **Production cost**: hours to research, write, design, and review.

Ship the top decile first. Re-score quarterly using Search Console data.

## 9. Quick checks before handoff

- [ ] Every cluster has exactly one primary keyword.
- [ ] No two clusters share a primary keyword.
- [ ] Every spoke is mapped to a pillar.
- [ ] Every URL is unique, lowercase, hyphenated, and free of stop-word stuffing.
- [ ] Every cluster has a target intent, format, and success metric.
- [ ] Cannibalization check is logged with a decision (expand, merge, split).
