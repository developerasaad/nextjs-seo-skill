# On-page SEO

On-page SEO is everything you control inside a single URL: the HTML, the copy, the media, and the links. This guide covers the elements that move rankings in 2026 and how to get them right on the first pass.

## 1. URL

- Lowercase, hyphenated, ASCII.
- 3-5 meaningful words. Drop articles unless they change meaning.
- Mirror the primary keyword. Avoid keyword stuffing.
- No dates unless freshness is the point and you commit to yearly updates.
- Stable. Once published, do not change. If you must, 301 the old URL to the new one and update internal links.

Good: `/blog/keyword-clustering`
Bad: `/blog/2025/01/the-ultimate-guide-to-keyword-clustering-for-seo`

## 2. Title tag

- 50-60 characters.
- Primary keyword in the first 30 characters where natural.
- One differentiator: number, year, brand, benefit, or audience.
- Distinct per page, no template-only titles.

Templates:
- `[Primary Keyword]: [Benefit] in [Year] | [Brand]`
- `[Number] [Primary Keyword] [Audience] Use in [Year]`
- `[Primary Keyword] vs [Alternative]: [Outcome] for [Audience]`

## 3. Meta description

- 140-160 characters.
- Includes the primary keyword once, naturally.
- Names the audience, the outcome, and a soft CTA.
- Does not duplicate the title.
- Distinct per page.

Template: `[Outcome] with [Primary Keyword]. [Mechanism or proof]. [Soft CTA].`

## 4. Heading hierarchy

- One H1 per page. The H1 contains the primary keyword and matches user intent. The H1 may differ from the title tag if SERP context demands a more clickable title.
- H2 sections cover the main subtopics in the cluster.
- H3 only when an H2 needs decomposition.
- Skip levels never (no H2 then H4).
- Keep headings scannable. A reader should grasp the article from headings alone.

## 5. Above-the-fold copy

The first 100 words decide whether the user stays and whether Google awards a featured snippet.

- Open with the answer to the searcher's question, in 40-60 words.
- State who the page is for in one line.
- Include the primary keyword in the first paragraph, naturally.
- For YMYL topics, name the author and last-updated date.

## 6. Body copy

- Paragraphs of 1-3 sentences.
- Sentences average under 20 words. Mix lengths for rhythm.
- Use bullet and numbered lists for parallel items, three or more.
- Use a table for any 2x2 or larger comparison.
- Use bold sparingly to mark scannable terms, not whole sentences.
- Original examples, screenshots, and data outrank generic prose.

## 7. Semantic coverage

A page about "meta description" should also mention: title tag, SERP, click-through rate, character length, pixel width, mobile preview, snippet rewriting, structured data. Cover the entities Google expects without forcing keywords.

Quick check: paste your draft into a tool that extracts entities and compare against the top three ranking URLs. Add what you are missing if it serves the reader.

## 8. Media

- Every image has descriptive alt text. Alt is for accessibility first, SEO second.
- File names describe the image: `meta-description-pixel-width.png`, not `IMG_4823.png`.
- Use WebP or AVIF. Serve via `next/image` with explicit width and height.
- The LCP image gets `priority`. Nothing else.
- Add `loading="lazy"` to below-the-fold images by default (Next.js does this automatically).
- Videos: host on a CDN, lazy-load the player, provide a transcript.

## 9. Links

### Internal
- Three to ten internal links in body copy for a 1500-word article.
- Anchor text is descriptive and varied. Mix exact match, partial match, and natural phrases.
- Link to the parent pillar and 2-3 sibling spokes.

### External
- Link to primary sources (research, official docs, original studies).
- Open in same tab unless leaving is the explicit user action.
- Use `rel="nofollow"` for paid placements, `rel="sponsored"` for sponsorships, `rel="ugc"` for user-generated content.

## 10. FAQ block

- 4-8 questions matched to People Also Ask and to questions a real reader would ask.
- Each answer is 40-60 words and self-contained.
- Wrap the block in `FAQPage` JSON-LD.
- Place above the conclusion or in a dedicated section near the end.

## 11. Featured snippet optimization

| Snippet type | What to do |
|---|---|
| Paragraph | Place a 40-60 word definition right after the H1 or under the relevant H2. |
| List (ordered) | Use a numbered list with 5-8 short steps. Each `<li>` starts with a verb. |
| List (unordered) | Use bullets for non-sequential items. Keep bullets parallel in structure. |
| Table | Use a real `<table>` with `<th>` headers. Two to four columns. |

## 12. Readability

- Target a Flesch Reading Ease of 60-70 for general audiences, lower for technical.
- Use plain words. Replace "utilize" with "use", "leverage" with "use", "in order to" with "to".
- Define jargon on first use.
- Read the draft out loud. If you stumble, rewrite.

## 13. Freshness

- Update top-performing pages every 6-12 months.
- Change the visible last-updated date only when the change is material.
- Refresh examples, statistics, screenshots, and any year references.
- Re-run internal links after big content updates.

## 14. On-page SEO checklist

- [ ] URL is short, descriptive, lowercase, hyphenated.
- [ ] Title tag is 50-60 chars, unique, primary keyword near the front.
- [ ] Meta description is 140-160 chars, unique, includes primary keyword and CTA.
- [ ] Single H1 contains the primary keyword.
- [ ] Answer in the first 60 words.
- [ ] Headings tell the story without the body.
- [ ] FAQ block with `FAQPage` schema.
- [ ] Internal links: 3-10, descriptive anchors, link to pillar and siblings.
- [ ] External links to primary sources.
- [ ] Images use `next/image`, explicit dimensions, alt text, WebP/AVIF.
- [ ] No render-blocking media above the fold.
- [ ] Last-updated date and author byline visible for editorial pages.
- [ ] Schema validated in Rich Results Test.
- [ ] Page passes Lighthouse SEO audit at 100.
