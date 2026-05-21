# Security

## Scope

This repository contains markdown documentation and a skill definition. There is no server, no executable code shipped as a library, no npm package, and no data collection.

Security vulnerabilities in the traditional sense do not apply here. However, there are a few scenarios worth calling out.

## Reporting a concern

If you find something in this repository that could cause harm — for example, a code example that introduces a security vulnerability if copied into a production Next.js application — please report it before opening a public issue.

Send a private report via [GitHub's private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing/privately-reporting-a-security-vulnerability) or email the maintainer directly at developer.asaad@gmail.com.

Describe:
- Which file and section contains the problematic code
- What the vulnerability is
- What the impact would be if a developer followed the example as written
- A suggested fix if you have one

## Responsible disclosure

Please give the maintainer a reasonable time (7-14 days) to fix and publish a corrected version before disclosing publicly.

## Code examples and production use

All code examples in this repository are illustrative. They demonstrate patterns and APIs but they do not represent a complete, production-hardened implementation. Before using any code example in a production application:

- Review it against your own security requirements
- Validate that any external inputs are properly sanitized
- Ensure any environment variables or secrets referenced in examples are not committed to source control
- Test thoroughly in a staging environment first

The maintainer makes no warranty about the fitness of any example for any particular use case.

## Third-party links

This repository links to external documentation and tools (Next.js docs, Google Search Central, schema.org, etc.). The maintainer does not control those sites and cannot guarantee their availability or security. If you discover a malicious URL that has been inserted into this repository, report it immediately.

## No data collection

This skill does not collect, transmit, or store any user data. It is a set of text files. Your prompts and your project's code never leave your local environment through this repository.
