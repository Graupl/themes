# Contributing to Graupl Themes

Read these guidelines before contributing code, documentation, bug reports, or feature requests.

## Write for the people who use and maintain this project

Graupl Themes is part of Accessible Ecosystem and helps people who may use the web differently than we do. Contributions should reflect the same care we put into making the web more accessible and friendly for everyone.

Accessibility also includes the people reading our code and documentation. Write plainly so someone just entering the field can follow your work, while giving experienced developers the detail they need to understand and maintain it.

- Use descriptive names, clear steps, and straightforward conditions. Avoid clever shortcuts that make the code harder to understand.
- Follow the project's existing structure and conventions. Introduce shared code when it makes the behavior easier to follow, rather than simply reducing the number of lines.
- Explain decisions and behavior that are not obvious. Keep comments useful, and update affected documentation when behavior changes.
- Keep contributions focused on the problem they address. Avoid unrelated cleanup or refactoring.
- Preserve existing behavior unless the contribution intentionally changes it. Consider keyboard interactions, focus, events, and compatibility.
- Use the relevant accessibility standards and ARIA Authoring Practices Guide patterns when changing accessibility behavior. Check HTML examples and generated markup for validity.
- Test the behavior your contribution affects. Passing automated checks alone does not establish that an interaction is accessible.

By submitting any contribution, you take responsibility for its contents, whether you wrote it yourself or used assistance. Submit work you understand, have reviewed, and can explain.

Read the [project instructions](../AGENTS.md) and [accessibility policy](ACCESSIBILITY.md) before contributing. AI-assisted contributions must also follow the [AI contribution policy](AI_CONTRIBUTIONS.md).

## Where to contribute

We use GitHub to host code, track bugs and feature requests, and review pull requests. Use GitHub issues and pull requests so project discussions and decisions are available to contributors.

## Submit a pull request

All code changes happen through pull requests.

1. Fork the repository and create your branch from `1.x`.
2. Make your changes and update any affected documentation.
3. Verify the affected behavior using the preview checks below.
4. Open your pull request and link any relevant issues. Describe the change, how you verified it, and any remaining limitations.

## Report a bug

Report bugs by [opening a GitHub issue](https://github.com/Graupl/themes/issues/new).

Include the following in your bug report:

- A summary of the problem.
- Steps to reproduce it, with a small code example if possible.
- What you expected to happen.
- What actually happened.
- Any relevant background, such as your browser, package version, and anything you have already tried.

## Set up and check your changes

This repository collects plain CSS themes for Graupl. Read the [Graupl theme skill](../skills/graupl-theme/SKILL.md) for the authoring and review workflow. A theme should work with Graupl's documented markup and JavaScript. Use existing Graupl custom properties wherever they control the styles you want to change.

Serve the repository with a local static file server and open the affected theme's `index.html`. The previews load Graupl from a CDN, so they need network access. Compare with [the default preview](../default/index.html) and verify that removing `theme.css` restores Graupl's styling.

Use the preview to check the affected components in light and dark modes, at narrow and wide widths, and by keyboard. Record the Graupl version or revision, the states you inspected, and any checks you could not run.

## Commit guidelines

Write commit messages using [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/). For example:

```text
fix: cancel pending callbacks when disposing a component
```

The format is:

> \<type>[optional scope]: \<description>
>
> [optional body]
>
> [optional footer(s)]

See the specification for commit types, optional scopes, and how to describe breaking changes.

Commit messages must follow this format before a contribution can be merged.

## References

This document was adapted from the open-source contribution guidelines for [Facebook's Draft](https://github.com/facebook/draft-js/blob/a9316a723f9e918afde44dea68b5f9f39b7d9b00/CONTRIBUTING.md)

## Attribution

This document is based on [Accessible Ecosystem Core](https://github.com/Accessible-Ecosystem/core), adapted from its [corresponding document](https://github.com/Accessible-Ecosystem/core/blob/1.x/.github/CONTRIBUTING.md).
