# Graupl CSS reference

The default and reference previews pin Graupl to [revision c7bff6f](https://github.com/Graupl/graupl/tree/c7bff6f2012a9cf53bae5ccee377a4beb7f6404b). The examples use the compiled CSS from that revision, which reports package version `1.0.0-beta.58`. Check the CSS your preview loads before using these values.

## Base values

The base spacer is `--graupl-spacer`, with a fallback of `1rem`. The derived properties `--graupl-spacer-0` through `--graupl-spacer-10` resolve to the values below when the base spacer keeps its default.

| Suffix | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
| ------ | - | - | - | - | - | - | - | - | - | - | -- |
| Value | `0rem` | `0.125rem` | `0.25rem` | `0.5rem` | `0.75rem` | `1rem` | `1.5rem` | `2rem` | `3rem` | `5rem` | `10rem` |

When the button padding shorthand `--graupl-button-padding` is unset, Graupl checks `--graupl-button-padding-y`, then `--graupl-spacer-3`, then uses half the base spacer for vertical padding. If a theme declares the spacer scale explicitly and changes the base spacer, choose the scale values as part of that change. A change to the base spacer alone will leave the explicit entries in place.

Custom properties inherit their computed values. If a custom property on `:root` references another property, descendants inherit the value that resolved on `:root`. Check the computed result and redeclare the reference where needed. A component-local assignment also takes precedence over an inherited root value. For example, the pinned CSS sets `--graupl-focus-outline-offset` on `.accordion-item .accordion-item-toggle`.

Graupl can consume a property through a fallback chain without declaring it. Define the base properties and the complete spacer scale in the theme so other declarations can reference them. For example, use `--graupl-spacer-5: 1rem` for that entry when keeping Graupl's default scale, and let components reference `var(--graupl-spacer-5)`.

If an alias for `--graupl-spacer-5` resolves on `:root`, changing only `--graupl-spacer` on `.card` leaves the inherited value in place. Set the numbered property at the widest scope that covers the intended elements and check whether an alias also needs to be set there. Keep relative units so the values still respond to the document root's font size. Keep responsive expressions such as `clamp()`, viewport or container calculations, and calculations needed for component behaviour. Check where each retained expression resolves.

## Colour modes

The pinned CSS uses `.light-mode` and `.dark-mode` to set `color-scheme`. Raw shades such as `--graupl-primary--100` define the palette and stay fixed when the mode changes. The `--graupl-theme-active--*` properties map that palette to the active theme and colour mode.

With no mapped override, `var(--graupl-theme-active--primary--100)` uses `--graupl-primary--100` in light mode and `--graupl-primary--900` in dark mode. The pinned default fallbacks are `#e6eeff` and `#001233`, respectively. Use that active property in place of `light-dark(var(--graupl-primary--100), var(--graupl-primary--900))` when the styling should follow the active palette. Keep `light-dark()` for a pair the palette does not map, such as a custom light-mode border colour paired with a shade from a different palette in dark mode.

In the pinned `.default-theme` rule, `--graupl-theme-active--primary--100` checks `--graupl-theme-default--primary--100` before falling back to the raw shades. Set the raw shades when defining the palette. Check the component's fallback chain and verify the computed colour in both modes through the preview controls.

## Typography

The root element's font size uses `--graupl-root-font-size`, with a fallback of `clamp(0.85rem, 0.8rem + 0.5vw, 1.25rem)`. The component size scale uses a separate property, `--graupl-base-font-size`. With its `1rem` fallback, the scale resolves to these values.

| Property | Value |
| --- | --- |
| `--graupl-font-size-xs` | `0.694rem` |
| `--graupl-font-size-sm` | `0.833rem` |
| `--graupl-font-size-base` | `1rem` |
| `--graupl-font-size-lg` | `1.2rem` |
| `--graupl-font-size-xl` | `1.44rem` |
| `--graupl-font-size-2xl` | `1.728rem` |
| `--graupl-font-size-3xl` | `2.074rem` |
| `--graupl-font-size-4xl` | `2.488rem` |
| `--graupl-font-size-5xl` | `2.986rem` |

The weight properties `--graupl-font-weight-light`, `--graupl-font-weight-normal`, and `--graupl-font-weight-bold` fall back to 300, 400, and 700. The root font weight checks `--graupl-root-font-weight` before the normal weight. Button text checks `--graupl-button-font-size` before the base size. Set the base size for a shared change and the button property for a change specific to buttons.

## Focus properties

Graupl's shared focus rule targets `:focus-visible` and `.focus`. It uses `--graupl-focus-outline` for the shorthand. The fallback uses separate width, style, and colour properties and defaults to a dotted outline. The default `--graupl-focus-outline-offset` fallback is the negative outline width. The accordion sets its own offset on `.accordion-item .accordion-item-toggle` using its border widths and the focus width. When a root offset change affects buttons but leaves accordion toggles unchanged, inspect that local declaration and the computed outline before changing the selector.

## Reduced motion

For `.button`, Graupl sets `--graupl-button-transition` in `@media (prefers-reduced-motion: reduce)` using `--graupl-button-transition-reduced-motion`. The normal fallback transitions background, colour, and transform. The reduced-motion fallback keeps background and colour and omits transform. Use the reduced-motion property when adjusting that mode. Check computed transitions in both modes if the theme also sets the normal transition, since selector scope and cascade layers can affect which declaration wins.

## Fieldwork preview and component setup

- Fieldwork loaded its authored CSS after Graupl. It set existing `--graupl-primary`, `--graupl-secondary`, and `--graupl-tertiary` values and numbered shades `--100` through `--900`. It used root properties such as `--graupl-root-background`, `--graupl-root-color`, `--graupl-heading-font-family`, and `--graupl-button-border-radius` after checking the compiled CSS.
- Fieldwork sets `--graupl-root-background` to `var(--graupl-theme-active--secondary--100)` so the page background follows the secondary palette in both modes.
- Fieldwork sets `--graupl-button-border-radius` on `.accordion-item-toggle` to match the item corners. When expanded, it squares the lower corners so the toggle meets its content. Ordinary buttons keep the rounded value declared at the root. Decorative CSS should keep focus visible and controls usable.
- Graupl's component generators initialize existing elements. For example, the beta.58 accordion generator selects `.accordion` by default, uses `@drupal/once`, and creates an Accordion instance. It accepts `options`, `context`, and `selector`. Inspect the target version and component documentation before using them. Use the initialization settings for the preview you are editing.
- The Fieldwork preview loads Accessible Menu separately for its navigation. Check each preview for its navigation dependencies and configuration.
