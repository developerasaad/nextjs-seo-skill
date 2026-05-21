# Landing page optimization

A landing page exists to convert one audience on one offer. Every decision (copy, layout, imagery, schema) should reduce friction between the visitor's intent and the conversion event.

## 1. Strategy

### One page, one job
- One primary keyword.
- One audience.
- One offer.
- One primary CTA.

If two offers compete, split into two pages.

### Intent classification
Most landing pages target commercial or transactional intent. Determine which:
- **Commercial investigation**: "best", "vs", "review", "alternatives". Lean into comparison and proof.
- **Transactional**: "buy", "pricing", "sign up", "free trial". Lean into immediate conversion.
- **Branded**: "brand + product". Lean into product clarity, not differentiation.

## 2. Page structure

A high-performing landing page follows a predictable rhythm. Variation is fine; skipping sections is not.

1. **Hero**
   - H1: outcome-focused, contains primary keyword.
   - Sub-headline: who it is for, mechanism, proof point.
   - Primary CTA.
   - Secondary CTA (often "see how it works" or "watch demo").
   - Hero image, product shot, or short loop video.
   - Trust strip: customer logos, ratings, or category awards.

2. **Problem**
   - Restate the visitor's pain in their language.
   - One paragraph or 3-5 bullets.

3. **Mechanism**
   - How the product solves the problem.
   - Diagram, screenshot, or 60-second video.
   - Three to five short steps if the product is workflow-based.

4. **Outcomes / Benefits**
   - Three to six benefit blocks.
   - Each block: icon + headline + 1-2 sentences.
   - Each block ties to a measurable outcome.

5. **Social proof**
   - Customer quote with name, role, company, photo.
   - Numeric proof: "500+ teams", "$2M saved", "30 percent lift".
   - Logo grid.
   - Awards, ratings, integrations.

6. **Differentiators**
   - Comparison table vs the obvious alternative or status quo.
   - Two to four rows of meaningful difference.

7. **Objection handling**
   - Address the top 3-5 reasons the visitor would not convert.
   - "Will this integrate with...", "What about pricing", "What if we outgrow it".

8. **FAQ**
   - 5-10 questions.
   - `FAQPage` schema.

9. **Final CTA**
   - Restate the offer.
   - Primary CTA.
   - Optional secondary path (talk to sales, book demo).

10. **Footer trust**
    - Security badges if applicable.
    - Compliance: SOC 2, GDPR, HIPAA where relevant.
    - Privacy and terms links.

## 3. Hero copywriting

### H1 patterns
- Outcome: `[Outcome] for [Audience]`
- Mechanism: `The [category] that [unique mechanism]`
- Comparison: `[Outcome] without [pain]`
- Specific: `[Outcome] in [time]`

Examples:
- `Ship SEO-ready Next.js pages in minutes`
- `The keyword research tool built for content teams`
- `Rank higher without writing more`

### Sub-headline pattern
Combine three elements: who, what, why-better.

`[Who] use [Product] to [outcome] [differentiator].`

Example: `Content teams at 500+ companies use Acme to publish SEO-ready pages 4x faster than their CMS allows.`

### CTA copy
- Verb + outcome: "Start free trial", "Book a demo", "Get the template".
- Avoid generic: "Submit", "Click here", "Learn more".
- Match the next step: if the form has 6 fields, do not say "Sign up in seconds".

## 4. Above the fold

Visible without scrolling on mobile and desktop:
- H1
- Sub-headline
- Primary CTA
- Visual proof (image, video, or hero element)
- One trust signal (logo strip, rating, or review count)

Test on a 1366x768 desktop and a 390x844 mobile viewport.

## 5. CTA design

- Color: contrasts with the surrounding palette. Use the same color for every primary CTA on the page.
- Size: large enough to tap on mobile (at least 48 by 48 CSS pixels), with at least 8px of clear space.
- Placement: above the fold, after each major section, in the final block.
- Repetition: the same CTA copy reduces decision fatigue.
- Motion: subtle hover or focus state. Do not auto-bounce.

## 6. Forms

- Fewer fields convert better. Ask only what you need.
- Smart defaults: detect country, currency, language.
- Validation: inline, friendly, on blur.
- Error states: explain how to fix, not just what is wrong.
- Submit button: verb-first, named action ("Start free trial", not "Submit").

## 7. Imagery and video

- Hero image: original product shot or illustrative scene. Avoid generic stock.
- Looping product video: 6-15 seconds, no sound, autoplay muted, with `playsinline`.
- Captions on any voiceover.
- Use `next/image` with explicit dimensions and `priority` for the hero.

## 8. Performance

Landing pages live or die on Core Web Vitals because users arrive cold and impatient.

- LCP under 2.0s for landing pages (tighter than the 2.5s general target).
- Inline critical CSS for the hero.
- Defer all non-critical JS. Use `next/script` with `lazyOnload` for analytics, chat widgets, and pixels.
- Preload the LCP image.
- Limit third-party scripts. Each one slows INP.
- Self-host fonts via `next/font`.

## 9. SEO essentials for landing pages

- Title and description tuned for click-through, not just length.
- One H1, primary keyword present, outcome-focused.
- Body copy mentions the primary keyword in context, not stuffed.
- FAQ block with `FAQPage` schema.
- `Product` or `Service` schema if applicable.
- Canonical to self.
- OG image with the primary value prop.

## 10. Conversion measurement

Track:
- CTA clicks (per CTA position).
- Form starts vs form submits.
- Scroll depth at 25 / 50 / 75 / 100 percent.
- Time on page.
- Source by channel and campaign.

Set up a single primary conversion event in GA4 and tie it to ad campaigns and search console.

## 11. A/B testing

Before testing, fix the obvious:
- Slow page speed
- Broken or hidden CTAs
- Confusing H1
- Mobile layout issues

Then test in this order:
1. H1 and sub-headline
2. Hero visual
3. Primary CTA copy
4. Social proof placement
5. Form length
6. Pricing presentation

Run each test to statistical significance, not just calendar days.

## 12. Common mistakes

- Two competing CTAs above the fold (signup vs demo) with no visual hierarchy.
- Hero image that looks generic and AI-generated.
- Wall of features instead of outcomes.
- Customer quotes without names, roles, or photos.
- Comparison table biased to the point of caricature; readers detect it instantly.
- Long paragraphs that read like internal documentation.
- No FAQ. Visitors leave with their objections unanswered.

## 13. Landing page checklist

- [ ] One primary keyword, one audience, one offer, one CTA.
- [ ] H1 outcome-focused, contains primary keyword.
- [ ] Sub-headline names audience, mechanism, differentiator.
- [ ] Primary CTA above the fold and repeated through the page.
- [ ] Trust strip near the hero.
- [ ] Mechanism section with diagram or video.
- [ ] 3-6 outcome blocks.
- [ ] Customer quotes with name, role, company, photo.
- [ ] Comparison or differentiator section.
- [ ] FAQ with `FAQPage` schema.
- [ ] Final CTA with low-friction secondary option.
- [ ] LCP under 2.0s, INP under 200ms, CLS under 0.1.
- [ ] OG image with the value prop.
- [ ] Conversion event tracked.
