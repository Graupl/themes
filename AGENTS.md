# Project instructions

Accessibility includes the people reading this project's code and documentation. Write so that someone learning the library can follow it, while giving experienced developers the details they need.

## Scope of these instructions

Graupl Themes is a collection of small, standalone CSS themes for Graupl. These instructions cover the stylesheets, previews, and documentation in this repository.

## Follow the contribution guidelines

All agents working on this project must read and follow the [contribution guidelines](.github/CONTRIBUTING.md), [AI contribution policy](.github/AI_CONTRIBUTIONS.md), and [accessibility policy](.github/ACCESSIBILITY.md).

## Use Graupl theme and Unslop

Read and apply the [Graupl theme skill](skills/graupl-theme/SKILL.md) when creating, editing, or reviewing a theme. It defines how to verify the target Graupl CSS, use its custom properties, and check the rendered result.

Always read and apply [the Unslop skill](skills/unslop/SKILL.md) when working on this project. Apply it to documentation, code comments, and explanations to the user. Preserve the author's natural wording and tone when editing existing text.

## Theme structure and accessibility

- Keep each theme in its own directory as `theme.css`. Load it after Graupl. Follow the existing preview structure and use [the default preview](default/index.html) to compare Graupl's unthemed styles.
- Keep theme styling CSS-only and usable with Graupl's documented markup. Preserve its component semantics and behavior. Previews can use Graupl's existing components and documented generators.
- When Graupl's docs load theme copy from this repository, keep each optional `exampleCopy.js` beside its `theme.css`. Export a default object containing only the copy keys the theme overrides. Graupl's docs own the winter defaults, the example markup, and the loader. The catalog supplies sample content for the docs previews.
- Prefer existing Graupl custom properties at the widest scope that gives the intended result. Check the target revision and the computed cascade before narrowing the scope or adding a direct CSS override.
- Use Graupl's existing colour-mode mechanism and verify contrast, keyboard focus, responsive layout, reduced motion, and the other applicable checks in the theme skill. Use [WCAG 2.2](https://www.w3.org/TR/WCAG22/) for accessibility requirements and the [ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/) and [WAI-ARIA](https://www.w3.org/TR/wai-aria/) to verify relevant preview markup and interactions.
- Record the Graupl version or revision checked, how you verified the affected styles and states, and any limits on those checks. Report framework defects in the project that owns the component.

## Approach to changes

- Read the relevant implementation, tests, and documentation before choosing a fix. Follow the project's established patterns instead of introducing a new structure by default.
- When working through an agreed list, finish the current item without folding in unrelated cleanup, refactoring, or documentation work. Carry the user's corrections forward to subsequent items.
- Choose the smallest change that solves the actual problem. A documentation issue can need only a documentation correction, and existing tests can already provide sufficient coverage.
- Keep issue-driven documentation focused on the agreed solution. Read the issue discussion to distinguish the actual request from examples or ideas mentioned along the way. Do not add adjacent patterns just because the same configuration could support them.
- Check compatibility beyond the final result. Preserve focus timing, event propagation, parent synchronization, and other existing side effects unless the requested change requires otherwise.

## Independent verification

- Agents must challenge each other's work. Treat claims, assumptions, and reported checks as unverified until there is evidence. Give concrete findings and be prepared to revise them when the evidence changes.
- For every change, have a separate agent review the full set of changes made for the task against all applicable AGENTS.md instructions. The reviewer must assume the changes do not comply until they verify compliance from the diff, relevant source, and checks. Include changes to AGENTS.md itself.
- Resolve findings and have the reviewer recheck any corrections before finishing. Apply the additional source and coverage checks required for documentation, bug fixes, and tests.

## Attribution

These instructions are adapted from [Graupl's project instructions](https://github.com/Graupl/graupl/blob/1.x/AGENTS.md).
