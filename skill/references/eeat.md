# E-E-A-T guidelines

E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness) is Google's framework for evaluating the credibility of content and the people and organizations behind it. It is not a direct ranking factor; it is the rubric Google's quality raters and ranking systems approximate. Sites that signal E-E-A-T well outperform sites that do not, especially in YMYL (Your Money or Your Life) categories: health, finance, legal, safety, civics, parenting.

## 1. The four pillars

### Experience
The author has personally done the thing they are writing about. First-hand use of a product, lived experience of an event, hands-on application of a method.

Signals:
- "I tested...", "We ran this campaign with...", "After 6 months running...".
- Original screenshots from the author's own account.
- Video showing the author using the product.
- Photos of the author at the event, with the equipment, on the trip.

### Expertise
The author has formal or substantive knowledge of the topic. Credentials, training, or a long track record.

Signals:
- Author bio with relevant degree, certification, or role.
- Author profile linked from every article they write.
- Schema `Person` with `jobTitle`, `worksFor`, `alumniOf`, `sameAs`.
- Linked publications, talks, or open-source contributions.

### Authoritativeness
Other credible sources reference the author or the site as a go-to. Reputation built over time.

Signals:
- Inbound links from authoritative domains.
- Citations of the site in industry publications.
- Mentions on Wikipedia, .edu, and .gov sites.
- Author quoted in the press.

### Trustworthiness
The site is honest, accurate, and safe. Trust is the most important pillar; without it, the others do not matter.

Signals:
- Clear contact information.
- Transparent ownership and authorship.
- Accurate, factual content with citations.
- HTTPS, privacy policy, terms of service.
- Visible last-updated dates and editorial process.

## 2. YMYL content

YMYL topics affect health, finance, safety, or major life decisions. Hold YMYL content to a higher standard:

- Author with verifiable credentials (MD, CPA, JD, RD).
- Reviewer (independent expert) named on the byline.
- Citations from primary sources: peer-reviewed journals, official agencies, regulatory bodies.
- "How we tested", "How we reviewed", "How we sourced" methodology block.
- Disclosures: affiliate relationships, sponsorships, conflicts of interest.

## 3. Author profiles

Every editorial article has an author byline. Every author has a profile page.

### Profile page contents
- Full name, photo, current role.
- Bio: 100-200 words covering relevant experience and expertise.
- Credentials: degrees, certifications, awards.
- Links to social and professional profiles (LinkedIn, X, GitHub, Substack, podcast).
- "Articles by [Author]" feed.
- Optional: contact link, speaking page.

### Person schema

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Jane Doe",
  "url": "https://example.com/authors/jane-doe",
  "image": "https://example.com/authors/jane-doe.jpg",
  "jobTitle": "Senior SEO Strategist",
  "worksFor": { "@type": "Organization", "name": "Example" },
  "alumniOf": "University of Somewhere",
  "sameAs": [
    "https://www.linkedin.com/in/janedoe",
    "https://twitter.com/janedoe",
    "https://github.com/janedoe"
  ]
}
```

Reference the author from each `BlogPosting` via `author`.

## 4. Editorial standards

Publish a public editorial standards page covering:
- Sourcing rules.
- Fact-checking process.
- Review and update cadence.
- Corrections policy.
- Editorial independence (separation from advertising).
- Conflict of interest disclosures.

Link this page from every article footer and from the about page.

## 5. Citations and sources

- Cite primary sources whenever possible: original studies, official documentation, regulatory texts, manufacturer specs.
- Use descriptive anchors: `Google's helpful content guidance` not `here`.
- Avoid citing aggregators or articles that themselves link to the primary source.
- Quote sparingly and accurately.
- Include a "Sources" section at the end of YMYL articles.

## 6. Updates and corrections

- Publish a visible last-updated date when content changes materially.
- Keep a changelog at the bottom of high-stakes articles.
- For corrections: leave the original text struck through or note the correction in a callout, with the date.
- Resubmit updated URLs in Search Console.

## 7. About page

A strong About page is one of the highest-ROI E-E-A-T signals.

Include:
- The story: who founded the site, when, why.
- The team: photos, names, roles, credentials.
- Mission and editorial principles.
- Contact: email, phone, address if applicable.
- Press mentions and awards.
- Organization schema.

## 8. Trust elements site-wide

- Clear navigation to About, Contact, Editorial Standards, Privacy, Terms.
- Visible publisher logo in the header.
- Visible author byline on editorial pages.
- Visible last-updated date on editorial pages.
- HTTPS site-wide.
- No deceptive ads, popups, or interstitials.
- No auto-playing audio or video with sound.

## 9. Reputation signals off-site

- Maintain accurate listings on:
  - Google Business Profile (for local).
  - Industry directories.
  - Wikipedia (if notable; do not edit your own page).
- Earn mentions through:
  - Original research and data.
  - Expert quotes given to journalists (HARO, Qwoted).
  - Conference talks.
  - Open-source contributions.
- Monitor brand mentions and reach out for unlinked mentions.

## 10. Trust hygiene

- Keep the site secure: HTTPS, modern TLS, current dependencies.
- Maintain accurate and current contact info.
- Respond to user reports promptly.
- Honor data deletion requests.
- Display refund and return policies clearly for ecommerce.

## 11. AI-generated content and E-E-A-T

Google does not penalize AI-generated content per se. It does penalize unhelpful, unoriginal, or unverified content regardless of source.

If you use AI assistance:
- Have a human author with topical expertise review and revise.
- Add original experience, examples, and data the AI cannot produce.
- Do not publish AI output verbatim at scale.
- Disclose AI use where readers reasonably expect to know (some publications do).
- Maintain the same fact-checking and sourcing standards as human-written content.

## 12. Common mistakes

- Generic "Editorial team" byline with no real authorship.
- Author photos that are obvious stock or AI-generated.
- Bios that list buzzwords but no verifiable credentials.
- Articles on YMYL topics by anonymous or low-credibility authors.
- "Last updated" timestamps that change without any content change.
- Citations to other content marketing pieces instead of primary sources.
- Hidden ownership and contact info.

## 13. E-E-A-T checklist

- [ ] Visible author byline on every editorial page.
- [ ] Author profile page with credentials, photo, bio, social links.
- [ ] `Person` schema for authors, `Organization` schema for the publisher.
- [ ] Editorial standards page linked site-wide.
- [ ] About page with founder story, team, contact, mission.
- [ ] Last-updated dates accurate and visible.
- [ ] Citations from primary sources.
- [ ] YMYL content reviewed by a credentialed expert.
- [ ] Disclosures for affiliates, sponsorships, conflicts.
- [ ] HTTPS, current TLS, accurate contact info, privacy and terms.
- [ ] Reputation signals (press mentions, awards, listings) maintained.
