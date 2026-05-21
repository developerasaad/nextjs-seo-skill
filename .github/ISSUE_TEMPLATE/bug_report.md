---
name: Bug report or inaccuracy
about: Report a code example that does not work, a schema that fails validation, or information that is incorrect
title: "[BUG] "
labels: bug
assignees: ""
---

## What is wrong

Describe the error or inaccuracy. Be specific: what does the current text say, and why is it wrong?

## Location

- File: (e.g., `skill/references/nextjs-seo.md`)
- Section heading: (e.g., `## 3. Dynamic metadata with generateMetadata`)
- Line or paragraph: (approximate is fine)

## Expected behavior

What should the text, code example, or schema say instead?

## Source

If you are citing a documentation source (Next.js docs, schema.org, Google Search Central), link to it here.

## How to reproduce (for code errors)

If the error is in a TypeScript or JavaScript example:

1. Paste the example into a Next.js project.
2. Run `next build` or `tsc --noEmit`.
3. Paste the error output here.

If the error is in a JSON-LD example:

1. Paste the example into the [Rich Results Test](https://search.google.com/test/rich-results) or [Schema Markup Validator](https://validator.schema.org/).
2. Paste the validation error here.

## Additional context

Any other context that helps understand the issue.
