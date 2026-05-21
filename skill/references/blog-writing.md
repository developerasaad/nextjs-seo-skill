# Blog content optimization

Blog content earns rankings when it answers the searcher's question better and faster than the competition, with original insight, and from a credible source. This guide covers the full lifecycle: brief, outline, draft, edit, optimize, publish, refresh.

## 1. Brief

A good brief takes 30-60 minutes and saves 4-8 hours of revisions later. Capture:

- **Primary keyword.** One per page.
- **Secondary keywords.** 5-15, all in the same SERP cluster.
- **Search intent.** Informational, commercial, transactional, navigational.
- **SERP analysis.** Top 5 ranking URLs. Note format, word count, headings, missing angles.
- **Audience and stage.** Who is searching, what stage of the funnel.
- **Reader outcome.** What the reader can do after finishing.
- **Business outcome.** What action the page should drive.
- **Author.** Match expertise to topic, especially for YMYL.
- **Sources.** Primary research, expert quotes, internal data, original screenshots.
- **Internal link targets.** 5-10 destinations.
- **Schema plan.** Article, FAQPage, HowTo, BreadcrumbList.
- **Success metric.** Position, sessions, conversions, snippet capture.

## 2. Outline

The outline is the article's skeleton. If the outline is wrong, no editing fixes the draft.

### Required blocks
1. **H1.** Contains the primary keyword. Matches user intent.
2. **TL;DR or Key Takeaways.** 4-6 bullets, scannable, snippet-eligible.
3. **The answer.** 40-60 words right under the H1 for "what is" queries.
4. **H2 sections.** Each covers one secondary keyword or one subtopic.
5. **H3 sections.** Only when an H2 needs decomposition.
6. **Examples.** Concrete, original, ideally with screenshots or code.
7. **FAQ.** 4-8 questions from People Also Ask plus reader-implied questions.
8. **Conclusion or next steps.** One CTA. Internal link to the next step.

### Outline format

```markdown
# [H1: Primary Keyword in a Reader-Centric Phrase]

Intent: [informational]
Audience: [marketers at SaaS companies]
Word count: 1800
Schema: [BlogPosting, FAQPage, BreadcrumbList]
Internal links: [/guides/seo, /blog/keyword-clustering, /tools/serp-preview]

## TL;DR
- [bullet 1]
- [bullet 2]
- [bullet 3]
- [bullet 4]

## What is [primary keyword]?
40-60 word definition.

## Why it matters
Why the reader should care, with a stat or example.

## How to do it
Step-by-step or numbered list.

### Step 1: ...
### Step 2: ...

## Common mistakes
Bullets.

## Tools and templates
Optional, with internal links to your tools.

## FAQ
- Q1
- Q2
- Q3
- Q4

## Sources
Primary citations.
```

## 3. Drafting

### Voice
- Plain language. Replace "utilize" with "use", "leverage" with "use", "in order to" with "to".
- Active voice. Subject does the verb.
- Concrete nouns. "The marketing team" beats "stakeholders".
- Specific verbs. "Cluster" beats "group". "Audit" beats "review".
- Vary sentence length. Mix 8-word punches with 25-word explanations.

### Paragraphs
- 1-3 sentences each. White space is a feature.
- One idea per paragraph.
- Open with the most important sentence; the rest support it.

### Lists
- Use a numbered list for sequences.
- Use a bulleted list for parallel items, three or more.
- Each item starts with a parallel construction (verb, noun, or adjective).
- Avoid listicle inflation: do not split one idea into three bullets to pad length.

### Tables
- Use for any 2x2 or larger comparison.
- Header row in `<th>`.
- Two to four columns; more becomes unreadable on mobile.

### Examples and proof
- Original screenshots beat stock images.
- Code snippets beat prose descriptions of code.
- Internal data beats external citations when available.
- Cite primary sources with descriptive anchors.

## 4. Editing pass

Three-pass system:

### Pass 1: Structure
- H1 contains the primary keyword.
- Headings narrate the article on their own.
- Each section delivers what its heading promises.
- TL;DR matches the actual content.

### Pass 2: Substance
- Every claim is supported by data, example, or citation.
- Every example is concrete and recent.
- Counterarguments and edge cases are addressed.
- Jargon is defined on first use.

### Pass 3: Polish
- Read every sentence aloud. Rewrite anything that stumbles.
- Cut filler: "It is important to note that", "needless to say", "in this article we will".
- Trim adverbs. "Quickly improve" usually beats "really quickly improve".
- Check transitions. Each paragraph should connect to the next.

## 5. Featured snippet optimization

| Snippet type | Optimization |
|---|---|
| Paragraph | 40-60 word definition under the relevant H2, with the question implicitly in the H2. |
| Ordered list | Numbered list with 5-8 short steps, verb-first. |
| Unordered list | Bullets parallel in structure, 5-10 items. |
| Table | Real `<table>` with 2-4 columns and a header row. |

Mark up FAQ blocks with `FAQPage` schema. Mark up step-by-step guides with `HowTo` schema where the page is genuinely a procedure.

## 6. Readability

- Target Flesch Reading Ease 60-70 for general audiences, 50-60 for technical.
- Average sentence length under 20 words.
- Average paragraph length under 60 words.
- Subheadings every 200-300 words.
- Run the draft through a readability checker, but trust your ear over the score.

## 7. Imagery

- One hero image per article, optimized for the OG card and the LCP.
- Inline images every 300-500 words to break up text.
- Original screenshots, diagrams, charts where possible.
- Alt text describes the image; do not stuff keywords.
- Use `next/image` with explicit dimensions, `priority` only on the hero.

## 8. Linking

Internal:
- Link to the parent pillar in the first 200 words.
- Link to 2-3 sibling spokes in the body.
- Link to the conversion path once, near the end.

External:
- 1-3 primary-source citations.
- Authoritative domains preferred.
- Same-tab unless leaving is the explicit reader goal.

## 9. Schema

Always include:
- `BlogPosting`
- `BreadcrumbList`

When applicable:
- `FAQPage` for the FAQ block.
- `HowTo` for genuine procedures.
- `VideoObject` if the article embeds a primary video.

See `references/schema-markup.md`.

## 10. Publish checklist

- [ ] Title 50-60 chars, primary keyword, differentiator.
- [ ] Description 140-160 chars, soft CTA.
- [ ] Slug short, descriptive, hyphenated.
- [ ] Canonical points to the live URL.
- [ ] OG image 1200x630, OG and Twitter tags set.
- [ ] H1 contains primary keyword.
- [ ] TL;DR present and accurate.
- [ ] FAQ block with `FAQPage` schema.
- [ ] Internal links: pillar, siblings, conversion path.
- [ ] External citations to primary sources.
- [ ] Author byline, last-updated date.
- [ ] Images optimized, alt text set.
- [ ] Lighthouse SEO 100, Core Web Vitals green.
- [ ] Rich Results Test passes.
- [ ] Submit URL in Search Console.

## 11. Refresh cadence

- Top 20 pages: review every 6 months.
- Top 100 pages: review every 12 months.
- Refresh when:
  - Rankings drop two or more positions over a 30-day window.
  - The SERP shifts format (snippet appears, video pack appears).
  - Statistics or screenshots are out of date.
  - A competitor publishes a stronger piece.

When refreshing, update the visible last-updated date only when the change is material. Resubmit the URL in Search Console.

## 12. Common mistakes

- Writing for the keyword instead of the reader.
- Padding word count past the point of usefulness.
- Burying the answer below 500 words of preamble.
- Using AI-tell phrases: "in today's fast-paced world", "delve into", "let's explore".
- Skipping primary sources and original examples.
- Forgetting to add internal links.
- Publishing without schema and OG images.
