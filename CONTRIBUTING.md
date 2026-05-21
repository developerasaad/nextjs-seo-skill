# Contributing

Thanks for taking the time to contribute. This project is a set of markdown reference documents and a skill definition file, so most contributions are edits to text rather than code. That said, the bar for quality is the same: be accurate, be specific, and match the voice of the existing documents.

## How to contribute

### Reporting a bug or inaccuracy

If a code example is wrong, a schema property is outdated, or a Next.js API reference is incorrect, open an issue using the bug report template.

Include:
- The file and section where the error appears
- What the current text says
- What it should say
- A link to the authoritative source (Next.js docs, schema.org, Google Search Central) if applicable

### Suggesting new content

If you want to add a new reference topic, a prompt example, a schema type, or a supported workflow, open a feature request issue first. Describe what you want to add and why it belongs here. That way we can agree on scope before you write anything.

### Submitting a pull request

1. Fork the repository.
2. Create a branch from `main` with a descriptive name:
   - `fix/breadcrumb-schema-example`
   - `docs/add-howto-schema-section`
   - `feat/recipe-schema`
3. Make your changes.
4. Verify that any code examples you add are syntactically correct. If they are TypeScript, check them with `tsc --noEmit` or copy them into a Next.js playground and confirm they compile.
5. If you are adding a JSON-LD example, run it through the [Rich Results Test](https://search.google.com/test/rich-results) or the [Schema Markup Validator](https://validator.schema.org/).
6. Open a pull request and fill out the template.

## What makes a good contribution

- **Accuracy first.** If you are unsure whether something is correct, say so in the PR description. A qualified "I think this is right, please verify" is more useful than confident misinformation.
- **Source it.** For any claim about Google ranking behavior, Core Web Vitals targets, or schema.org spec, link to the primary source.
- **Match the tone.** The reference documents are written for experienced developers, not beginners. They are direct, avoid marketing language, and explain the why not just the what. Read a few sections before writing.
- **One thing per PR.** A PR that adds a new schema section is much easier to review than one that fixes five typos, adds a new section, and reorganizes the headings.

## What we will not accept

- Content generated verbatim from AI tools without review. AI-assisted drafting is fine; unreviewed AI output is not.
- Vague additions like "you should also think about SEO broadly" with no specific guidance.
- Promotional content for specific tools, services, or platforms.
- Changes that remove nuance from existing guidance (e.g., replacing "it depends on the intent" with a blanket rule that does not hold).
- Code examples that do not compile or schemas that fail validation.

## Style guide

- Use sentence case for headings.
- Prefer short sentences. Mix lengths for readability.
- Use `monospace` for: file names, directory paths, API names, code values, and schema property names.
- Use plain text for bold sparingly — mark the most important term in a section, not every term.
- Tables for comparisons of two or more things with the same set of attributes.
- Numbered lists for sequences. Bullets for parallel, non-sequential items.

## Running local checks

There are no build scripts. Checks are manual:

1. **Markdown** — preview your changes in a markdown viewer. VS Code and GitHub's markdown preview both work.
2. **TypeScript** — if you add TypeScript, paste it into a Next.js project and confirm `next build` passes.
3. **JSON-LD** — paste into the [Rich Results Test](https://search.google.com/test/rich-results).
4. **Links** — check that any URLs you add are live and point to what you intend.

## Code of conduct

This project follows the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to abide by its terms.

## Questions

Open a discussion in the GitHub Discussions tab if you have a question that does not fit an issue or a PR.
