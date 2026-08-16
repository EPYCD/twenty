# Twenty — Design System Reference

A port sheet for engineers rebuilding Twenty's look outside this repo. Every value below is
transcribed verbatim from a file in this repository and cited as `path:line`. Nothing is
rounded, normalised, or converted.

---

## 0 · Provenance

| | |
|---|---|
| Repository | `twentyhq/twenty` (monorepo, Nx + Yarn 4) |
| Commit | `044fc2d38908f711f5f073c345b656e13b541b8b` |
| Commit date | Sun 16 Aug 2026 10:15:33 +0200 |
| Root package version | `0.2.1` (`package.json:75`) |
| Design-system package | `twenty-ui` `1.0.0-alpha.1` (`packages/twenty-ui/package.json:3`) |

**Styling libraries actually in use** — there are two, and they are split by package:

| Package | Mechanism | Version | Files |
|---|---|---|---|
| `twenty-ui` | SCSS CSS Modules (`*.module.scss`), compiled by Vite | `sass ^1.83.0` (`packages/twenty-ui/package.json:57`) | 129 `.module.scss` |
| `twenty-front` | Linaria (zero-runtime CSS-in-JS) | `@linaria/react ^7.0.1`, `@linaria/core ^7.0.0` (`packages/twenty-front/package.json:48-49`), built by `@wyw-in-js/vite ^1.1.0` (`packages/twenty-front/package.json:186`) | 1180 files importing `styled` |

`twenty-ui` contains **zero** Linaria usages and `twenty-front` contains **zero** `.module.scss`
files. Both reach the same design tokens through plain CSS custom properties, so the two
mechanisms are interchangeable from a token point of view.

Supporting libraries:

| Purpose | Package | Version | Source |
|---|---|---|---|
| Icons | `@tabler/icons-react` | `^3.31.0` | `packages/twenty-ui/package.json:76` |
| Colour primitives | `@radix-ui/colors` | `^3.0.0` | `packages/twenty-ui/package.json:74` |
| Headless primitives | `@base-ui/react` | `^1.5.0` | `packages/twenty-ui/package.json:72` |
| Class composition | `clsx` | `^2.1.1` | `packages/twenty-ui/package.json:77` |
| Animation | `framer-motion` | `^11.18.0` | `packages/twenty-front/package.json` |
| Floating layers | `@floating-ui/react` | used by dropdowns / cell editors | `packages/twenty-front/package.json` |
| Skeletons | `react-loading-skeleton` | imported in `packages/twenty-front/src/index.tsx:13` | |
| Fonts | `@fontsource/inter ^5.2.8`, `@fontsource/dm-mono ^5.2.7` | `packages/twenty-front/package.json:43-44` | |
| React | `^19.2.0` | `packages/twenty-front/package.json:122` | |

### Files read

Theme source of truth (read in full):

- `packages/twenty-ui/src/theme-constants/theme-light.css` (1048 lines)
- `packages/twenty-ui/src/theme-constants/theme-dark.css` (1044 lines)
- `packages/twenty-ui/src/theme-constants/themeCssVariables.ts`
- `packages/twenty-ui/src/theme-constants/ThemeProvider.tsx`
- `packages/twenty-ui/src/theme-constants/useTheme.ts`
- `packages/twenty-ui/src/theme-constants/constants.ts`
- `packages/twenty-ui/src/theme-constants/__tests__/cornerShapeThemeParity.test.ts`
- `packages/twenty-ui/src/theme/index.ts`
- `packages/twenty-ui/src/theme/constants/`: `packages/twenty-ui/src/theme/constants/ThemeCommon.ts`, `packages/twenty-ui/src/theme/constants/ThemeLight.ts`, `packages/twenty-ui/src/theme/constants/ThemeDark.ts`,
  `packages/twenty-ui/src/theme/constants/Animation.ts`, `packages/twenty-ui/src/theme/constants/Icon.ts`, `packages/twenty-ui/src/theme/constants/Modal.ts`, `packages/twenty-ui/src/theme/constants/Text.ts`, `packages/twenty-ui/src/theme/constants/Rgba.ts`, `packages/twenty-ui/src/theme/constants/BorderCommon.ts`,
  `packages/twenty-ui/src/theme/constants/BorderLight.ts`, `packages/twenty-ui/src/theme/constants/BorderDark.ts`, `packages/twenty-ui/src/theme/constants/FontCommon.ts`, `packages/twenty-ui/src/theme/constants/FontLight.ts`, `packages/twenty-ui/src/theme/constants/FontDark.ts`,
  `packages/twenty-ui/src/theme/constants/BoxShadowLight.ts`, `packages/twenty-ui/src/theme/constants/BoxShadowDark.ts`, `packages/twenty-ui/src/theme/constants/BlurLight.ts`, `packages/twenty-ui/src/theme/constants/BlurDark.ts`, `packages/twenty-ui/src/theme/constants/BackgroundLight.ts`,
  `packages/twenty-ui/src/theme/constants/BackgroundDark.ts`, `packages/twenty-ui/src/theme/constants/AccentLight.ts`, `packages/twenty-ui/src/theme/constants/AccentDark.ts`, `packages/twenty-ui/src/theme/constants/GrayScaleLight.ts`,
  `packages/twenty-ui/src/theme/constants/GrayScaleDark.ts`, `packages/twenty-ui/src/theme/constants/GrayScaleLightAlpha.ts`, `packages/twenty-ui/src/theme/constants/GrayScaleDarkAlpha.ts`, `packages/twenty-ui/src/theme/constants/MainColorsLight.ts`,
  `packages/twenty-ui/src/theme/constants/MainColorsDark.ts`, `packages/twenty-ui/src/theme/constants/MainColorNames.ts`, `packages/twenty-ui/src/theme/constants/ColorsLight.ts`, `packages/twenty-ui/src/theme/constants/ColorsDark.ts`,
  `packages/twenty-ui/src/theme/constants/SecondaryColorsLight.ts` (head), `packages/twenty-ui/src/theme/constants/TransparentColorsLight.ts` (head + gray block),
  `packages/twenty-ui/src/theme/constants/CodeLight.ts`, `packages/twenty-ui/src/theme/constants/CodeDark.ts`, `packages/twenty-ui/src/theme/constants/SnackBarLight.ts`, `packages/twenty-ui/src/theme/constants/IllustrationIconLight.ts`,
  `packages/twenty-ui/src/theme/constants/TagLight.ts` (head), `packages/twenty-ui/src/theme/constants/DefaultThemeColorFallback.ts`

Global style entry points:

- `packages/twenty-front/src/index.css`
- `packages/twenty-front/src/index.tsx`
- `packages/twenty-ui/src/styles/base/reset.scss`
- `packages/twenty-ui/src/styles/abstracts/_mixins.scss`
- `packages/twenty-ui/src/styles/abstracts/_functions.scss`
- `packages/twenty-ui/src/styles/abstracts/_breakpoints.scss`
- `packages/twenty-ui/vite.config.ts` (head)

Theme wiring in the app:

- `packages/twenty-front/src/modules/ui/theme/components/BaseThemeProvider.tsx`
- `packages/twenty-front/src/modules/ui/theme/hooks/useColorScheme.ts`
- `packages/twenty-front/src/modules/ui/theme/constants/UiScaleMultipliers.ts`
- `packages/twenty-front/src/modules/ui/theme/constants/MonospaceFontFamily.ts`
- `packages/twenty-front/src/modules/ui/theme/utils/getUiZoom.ts`

Component library (barrels read in full; the listed components read as source):

- Barrels: `accessibility/`, `data-display/`, `feedback/`, `input/`, `layout/`, `navigation/`,
  `surfaces/`, `typography/`, `icon/` `index.ts` under `packages/twenty-ui/src/`
- `packages/twenty-ui/src/input/Button/Button.tsx` + `packages/twenty-ui/src/input/Button/Button.module.scss`, `packages/twenty-ui/src/input/Checkbox/Checkbox.tsx` +
  `.module.scss`, `packages/twenty-ui/src/input/Toggle/Toggle.module.scss`, `packages/twenty-ui/src/input/SegmentedControl/SegmentedControl.tsx`
- `packages/twenty-ui/src/data-display/Tag/Tag.tsx` + `.module.scss`, `packages/twenty-ui/src/data-display/Chip/Chip.tsx` + `.module.scss`,
  `packages/twenty-ui/src/data-display/Status/Status.tsx`, `packages/twenty-ui/src/data-display/Avatar/Avatar.module.scss` +
  `packages/twenty-ui/src/data-display/Avatar/constants/AvatarPropertiesBySize.ts`
- `packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss`
- `packages/twenty-ui/src/surfaces/Card/Card.tsx` + `.module.scss`, `packages/twenty-ui/src/surfaces/Modal/Modal.module.scss`,
  `packages/twenty-ui/src/surfaces/AppTooltip/AppTooltip.tsx` (head)
- `packages/twenty-ui/src/feedback/Callout/Callout.tsx` (head), `packages/twenty-ui/src/feedback/Banner/Banner.tsx` (head),
  `feedback/EmptyPlaceholderStyled/*`, `packages/twenty-ui/src/feedback/AnimatedPlaceholder/AnimatedPlaceholder.tsx`
- `typography/H1Title|H2Title|H3Title|Label|SeparatorLineText|StyledText` `.module.scss`
- `packages/twenty-ui/src/icon/components/Icon.tsx`, `packages/twenty-ui/src/icon/components/TablerIcons.ts`, `packages/twenty-ui/src/icon/types/IconComponent.ts`
- `packages/twenty-ui/src/layout/Section/Section.tsx`, `packages/twenty-ui/src/testing/a11yParameters.ts`

Stories mined for the variant/state matrix: `packages/twenty-ui/src/input/Button/__stories__/Button.stories.tsx` read in
full; the remaining 70 `*.stories.tsx` were surveyed by grepping for `dimensions`, `values` and
`A11Y_DEFER_COLOR_CONTRAST` rather than read line by line — the exported TypeScript union and
enum types carry the same matrix and are cited in §8 instead.

CRM screens (`packages/twenty-front/src/modules/`):

- `object-record/record-table/constants/*` (all 29 files), `packages/twenty-front/src/modules/object-record/record-table/components/RecordTableStyleWrapper.tsx`,
  `packages/twenty-front/src/modules/object-record/record-table/components/HorizontalScrollBoxShadowCSS.ts`, `packages/twenty-front/src/modules/object-record/record-table/components/VerticalScrollBoxShadowCSS.ts`,
  `packages/twenty-front/src/modules/object-record/record-table/record-table-row/components/RecordTableTr.tsx`, `packages/twenty-front/src/modules/object-record/record-table/record-table-row/components/RecordTableRowDiv.tsx`,
  `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellStyleWrapper.tsx`,
  `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx`, `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellDisplayMode.tsx`,
  `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx`, `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellSkeletonLoader.tsx`,
  `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx`,
  `packages/twenty-front/src/modules/object-record/record-table/record-table-header/components/RecordTableHeaderCellContainer.tsx`
- `packages/twenty-front/src/modules/object-record/record-inline-cell/components/RecordInlineCellDisplayMode.tsx`
- `object-record/record-board/constants/*`, `packages/twenty-front/src/modules/object-record/record-board/record-board-card/components/RecordBoardCard.tsx`,
  `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumn.tsx`, `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumnHeader.tsx`
- `packages/twenty-front/src/modules/object-record/components/RecordChip.tsx`
- `side-panel/constants/*`, `packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx`
- `packages/twenty-front/src/modules/command-menu/components/CommandMenuItem.tsx`, `packages/twenty-front/src/modules/command-menu/hooks/useCommandMenuHotKeys.ts`
- `packages/twenty-front/src/modules/ui/layout/overlay/components/OverlayContainer.tsx`,
  `ui/layout/dropdown/constants/*`, `packages/twenty-front/src/modules/ui/layout/dropdown/components/DropdownContent.tsx`,
  `packages/twenty-front/src/modules/ui/layout/dropdown/components/DropdownMenuItemsContainer.tsx`, `packages/twenty-front/src/modules/ui/layout/dropdown/components/internal/DropdownInternalContainer.tsx`
- `packages/twenty-front/src/modules/ui/layout/constants/RootStackingContextZIndices.ts`,
  `ui/layout/resizable-panel/constants/*`, `packages/twenty-front/src/modules/ui/layout/page/constants/PageBarMinHeight.ts`,
  `packages/twenty-front/src/modules/ui/navigation/states/navigationDrawerWidthState.ts`
- `packages/twenty-front/src/modules/ui/input/components/TextInput.tsx`, `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx`
- `packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx`
- `packages/twenty-front/src/modules/activities/components/SkeletonLoader.tsx`, `packages/twenty-front/src/modules/ai/components/internal/AiChatSkeletonLoader.tsx`

Lint rules that encode design constraints:

- `packages/twenty-oxlint-rules/rules/no-hardcoded-colors.ts`
- `packages/twenty-oxlint-rules/rules/sort-css-properties-alphabetically.ts` (head)
- `packages/twenty-oxlint-rules/rules/styled-components-prefixed-with-styled.ts` (head)

### What was sampled rather than read exhaustively

- **The 360 `--t-color-transparent-*` tokens.** Each theme defines 30 alpha families × 12 steps.
  Only the `gray` family and four hex aliases are referenced anywhere outside the token files
  (verified by grep across `twenty-front/src` and `twenty-ui/src`). §2 tables the transparent
  gray ramp in full and names the exact Radix import for the other 29; it does not table all 360.
- **The 30 × 12 solid ramps** are tabled in full in §2.7, generated mechanically from
  `packages/twenty-ui/src/theme-constants/theme-light.css` / `packages/twenty-ui/src/theme-constants/theme-dark.css` rather than hand-transcribed.
- **436 re-exported Tabler icons** (`packages/twenty-ui/src/icon/components/TablerIcons.ts`) were counted, not listed.
- **129 `.module.scss` files and 1180 Linaria files**: the components named above were read;
  the rest were surveyed by grep for `transition:`, `outline`, `focus-visible`, hard-coded hex.

---

## 1 · How styling actually works here

### The token layer is plain CSS custom properties

The single source of truth is two hand-maintained stylesheets:

- `packages/twenty-ui/src/theme-constants/theme-light.css` — 994 declarations under `.light`
- `packages/twenty-ui/src/theme-constants/theme-dark.css` — 994 declarations under `.dark`

Both are imported once, at app boot, alongside the fonts and the reset
(`packages/twenty-front/src/index.tsx:14-17`):

```tsx
import 'twenty-ui/style.css';
import 'twenty-ui/theme-light.css';
import 'twenty-ui/theme-dark.css';
import './index.css';
```

Every token is prefixed `--t-`. The two files are **structurally identical** — same 994 keys, no
key present in one and missing from the other — and 145 of the 994 hold the same value in both
themes. A header comment on each file states they are "mirrored token-for-token from twenty-ui"
and kept in sync by a parity test (`packages/twenty-ui/src/theme-constants/theme-light.css:1-2`); the committed test only pins the
corner-radius invariants (`packages/twenty-ui/src/theme-constants/__tests__/cornerShapeThemeParity.test.ts:49-71`).

The TypeScript objects under `packages/twenty-ui/src/theme/constants/` (`THEME_LIGHT`,
`THEME_DARK`, `GRAY_SCALE_LIGHT`, …) are the *authoring* form — that is where the Radix imports
and the derivations live. They are no longer what components read: the only consumer of
`THEME_LIGHT`/`THEME_DARK` left in the app is the Stripe checkout appearance object
(`packages/twenty-front/src/modules/settings/billing/hooks/useStripeAppearance.ts:4,30`).

### How a component reaches a token

Two accessors, both pointing at the same custom properties.

**1. `themeCssVariables`** — a nested object of literal `var(--t-…)` strings
(`packages/twenty-ui/src/theme-constants/themeCssVariables.ts:1-3`). This is the workhorse: 2355
call sites in `twenty-front` alone. Because the values are inert strings, Linaria can inline them
at build time and stay zero-runtime.

```ts
export const themeCssVariables = {
  icon: { size: { sm: 'var(--t-icon-size-sm)', … } },
  spacing: { '0': 'var(--t-spacing-0)', '1': 'var(--t-spacing-1)', …, '0.5': 'var(--t-spacing-0_5)' },
  …
};
```

**2. `useTheme()`** — returns the same shape with the variables *resolved to values*
(`packages/twenty-ui/src/theme-constants/useTheme.ts:5`). `ThemeProvider` calls
`getComputedStyle(document.documentElement)` once per colour-scheme change, walks the
`themeCssVariables` tree, and replaces every `var(...)` leaf with the computed string, coercing to
`Number` when the string parses as one (`packages/twenty-ui/src/theme-constants/ThemeProvider.tsx:56-92`). That numeric coercion exists
because Tabler icons take numeric props: `theme.icon.size.sm` must be `14`, not `"14"`.

Use `themeCssVariables` inside CSS. Use `useTheme()` only when a number has to cross into JS —
icon `size`/`stroke`, a canvas, a third-party theme object.

**In `twenty-ui`'s SCSS modules there is no accessor at all** — the `var(--t-…)` is written
directly, plus three SCSS helpers from `packages/twenty-ui/src/styles/abstracts/`:

```scss
@mixin focus-ring {                    // _mixins.scss:1-6
  &:focus-visible { outline: 2px solid var(--t-color-blue); outline-offset: 1px; }
}
@mixin hover-capable { @media (hover: hover) { @content; } }   // _mixins.scss:11-15
@function duration($name) {            // _functions.scss:3-5
  @return calc(var(--t-animation-duration-#{$name}) * 1s);
}
```

`duration()` exists because the duration tokens are stored **unitless** (`0.15`, not `150ms`) so
that JS can read them as numbers; every CSS consumer has to multiply by `1s`.

### How dark mode is switched

There is no media query and no `data-theme` attribute. `ThemeProvider` toggles two classes on
`<html>` (`packages/twenty-ui/src/theme-constants/ThemeProvider.tsx:94-100`):

```tsx
const applyColorSchemeClass = (colorScheme: 'light' | 'dark') => {
  const root = document.documentElement;
  root.classList.toggle('dark', colorScheme === 'dark');
  root.classList.toggle('light', colorScheme === 'light');
};
```

The app-level wrapper resolves the user preference — `'System' | 'Light' | 'Dark'`, persisted per
workspace member — into that boolean (`packages/twenty-front/src/modules/ui/theme/components/BaseThemeProvider.tsx:26-38`); `'System'` falls through to
`useSystemColorScheme()`. `useColorScheme()` writes the choice back to the server
(`packages/twenty-front/src/modules/ui/theme/hooks/useColorScheme.ts:40-45`) and exposes the three options with their icons `IconSunMoon`,
`IconMoon`, `IconSun` (`packages/twenty-front/src/modules/ui/theme/hooks/useColorScheme.ts:55-71`).

`ThemeProvider` also supports **scoped** theming: pass `overrides` or `applyToRoot={false}` and it
renders a `display: contents` wrapper carrying the class and the override custom properties, then
recomputes the JS mirror from *that* element instead of `<html>` (`packages/twenty-ui/src/theme-constants/ThemeProvider.tsx:122-196`).

### The spacing helper, and the one that is dead

`THEME_COMMON` still exports a function-style helper (`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:12-14`):

```ts
spacingMultiplicator: 4,
spacing: (...args: number[]) => args.map((m) => `${m * 4}px`).join(' '),
```

**Base unit: 4px.** But `theme.spacing(…)` has **0 call sites** in `twenty-front`. Everything
now goes through the pre-expanded ladder `themeCssVariables.spacing['1'] → var(--t-spacing-1)`,
which the CSS files materialise as `0px … 128px` in 4px steps plus `0.5 → 2px` and `1.5 → 6px`
(`packages/twenty-ui/src/theme-constants/theme-light.css:31-65`). Also of note: `var(--t-spacing-*)` never appears written by hand in
`twenty-front` — always through the accessor.

### Root sizing: 1rem is 13px, and there is a zoom layer

`packages/twenty-front/src/index.css:11-23`:

```css
html {
  font-size: 13px;
  background: var(--t-background-tertiary);
  --t-zoom: var(--t-scale-user, 1);
  zoom: var(--t-zoom);
}
```

Two consequences you must carry across:

1. **Every `rem` in the type scale resolves against 13px, not 16px.** `--t-font-size-md: 1rem`
   is 13px.
2. Interface scale is implemented with CSS `zoom` on the root, not by rescaling tokens.
   `--t-scale-user` is set by `ThemeProvider` from the user preference
   (`packages/twenty-ui/src/theme-constants/ThemeProvider.tsx:158-170`); the four steps are `Smaller 0.9`, `Default 1`, `Large 1.1`,
   `Larger 1.25` (`packages/twenty-front/src/modules/ui/theme/constants/UiScaleMultipliers.ts:7-12`). On phones the root gains a further ×14/13
   (`packages/twenty-front/src/index.css:27-31`). Anything measured in *visual viewport* pixels — pointer deltas, dnd-kit
   drag feedback, `100dvh` — has to be divided back out by `--t-zoom`
   (`packages/twenty-front/src/index.css:46-60`, `packages/twenty-front/src/modules/ui/theme/utils/getUiZoom.ts:4-12`, `packages/twenty-ui/src/theme/constants/Modal.ts:19-20`).

### One real styled component, end to end

`packages/twenty-front/src/modules/ui/layout/overlay/components/OverlayContainer.tsx:1-26` — the
box behind every dropdown, cell editor and floating menu in the product:

```tsx
import { themeCssVariables } from 'twenty-ui/theme-constants';
import { styled } from '@linaria/react';

export const OverlayContainer = styled.div<{
  borderRadius?: 'sm' | 'md';
  hasDangerBorder?: boolean;
}>`
  align-items: center;
  backdrop-filter: ${themeCssVariables.blur.medium};
  background: ${themeCssVariables.background.transparent.primary};
  border: 1px solid
    ${({ hasDangerBorder }) =>
      themeCssVariables.border.color[hasDangerBorder ? 'danger' : 'medium']};
  border-radius: ${({ borderRadius }) =>
    themeCssVariables.border.radius[borderRadius ?? 'md']};
  box-shadow: ${themeCssVariables.boxShadow.strong};
  display: flex;
  overflow: hidden;
  z-index: 30;
`;
```

At build time Linaria emits a static class whose declarations are literally
`backdrop-filter: var(--t-blur-medium); background: var(--t-background-transparent-primary); …`.
The prop-dependent branches become a second custom property set from an inline `style`. Note the
convention on show: declarations are sorted alphabetically (enforced by
`packages/twenty-oxlint-rules/rules/sort-css-properties-alphabetically.ts`), and the variable name
is prefixed `Styled…` — except here, where the rule is explicitly disabled on line 4 because the
component is exported as a public building block.

### Breakpoints

There is exactly one: **768px**.

| Name | Value | Source |
|---|---|---|
| `MOBILE_VIEWPORT` | `768` | `packages/twenty-ui/src/theme-constants/constants.ts:3` |
| `$breakpoints.mobile` | `768px` | `packages/twenty-ui/src/styles/abstracts/_breakpoints.scss:4-6` |

`MOBILE_VIEWPORT` is deliberately a plain number, not a custom property, because "CSS custom
properties don't work in media queries" (`packages/twenty-ui/src/theme-constants/constants.ts:1-2`). SCSS consumers use
`@include respond-to('mobile')` (`packages/twenty-ui/src/styles/abstracts/_breakpoints.scss:8-18`); React consumers use `useIsMobile()`.

### Reset

`packages/twenty-ui/src/styles/base/reset.scss` is 15 lines: `box-sizing: border-box` on
everything, and `button` stripped to `font: inherit; color: inherit; background: none; border:
none; cursor: pointer`. `packages/twenty-front/src/index.css:33-35` then re-fixes
`button { font-size: 13px }` — a hard-coded value, not `var(--t-font-size-md)`.

---

## 2 · Colour

### 2.0 Read this first: the source stores display-p3, not hex

Almost every colour token is written as `color(display-p3 r g b)` or
`color(display-p3 r g b / a)`. A minority — the four transparent semantic aliases, the dark
overlays, all 360 transparent ramp entries, and the dark box shadows — are 8-digit hex or `rgba()`.
The values below are reproduced **exactly as written in the source**; no conversion to hex has
been performed anywhere in this document, because converting would change the colour on wide-gamut
displays. If your target platform cannot express P3, see §11 and §12.

### 2.1 Grayscale — the spine of the whole system

`--t-gray-scale-*`, defined in `packages/twenty-ui/src/theme/constants/GrayScaleLight.ts:1-14` / `packages/twenty-ui/src/theme/constants/GrayScaleDark.ts:1-14`, mirrored to
`packages/twenty-ui/src/theme-constants/theme-light.css:257-268` / `packages/twenty-ui/src/theme-constants/theme-dark.css:253-264`. This is **not** a Radix scale — it is
hand-written neutral grey, and the dark ramp is not a simple inversion (note `gray10` is *darker*
than `gray9` in dark mode).

| Token | Light | Dark |
|---|---|---|
| `--t-gray-scale-gray1` | color(display-p3 1 1 1) | color(display-p3 0.09 0.09 0.09) |
| `--t-gray-scale-gray2` | color(display-p3 0.988 0.988 0.988) | color(display-p3 0.106 0.106 0.106) |
| `--t-gray-scale-gray3` | color(display-p3 0.976 0.976 0.976) | color(display-p3 0.098 0.098 0.098) |
| `--t-gray-scale-gray4` | color(display-p3 0.945 0.945 0.945) | color(display-p3 0.114 0.114 0.114) |
| `--t-gray-scale-gray5` | color(display-p3 0.922 0.922 0.922) | color(display-p3 0.133 0.133 0.133) |
| `--t-gray-scale-gray6` | color(display-p3 0.839 0.839 0.839) | color(display-p3 0.282 0.282 0.282) |
| `--t-gray-scale-gray7` | color(display-p3 0.8 0.8 0.8) | color(display-p3 0.298 0.298 0.298) |
| `--t-gray-scale-gray8` | color(display-p3 0.702 0.702 0.702) | color(display-p3 0.4 0.4 0.4) |
| `--t-gray-scale-gray9` | color(display-p3 0.6 0.6 0.6) | color(display-p3 0.506 0.506 0.506) |
| `--t-gray-scale-gray10` | color(display-p3 0.514 0.514 0.514) | color(display-p3 0.482 0.482 0.482) |
| `--t-gray-scale-gray11` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |
| `--t-gray-scale-gray12` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |

Where each step is used, read off the semantic aliases below:

| Step | Light role | Dark role |
|---|---|---|
| `gray1` | page/card background (`background.primary`), inverted text | app background |
| `gray2` | `background.secondary` (hover on white surfaces) | |
| `gray3` | tag background for the `gray` colour | |
| `gray4` | `background.tertiary` (the body background), `border.color.light` | `background.tertiary`, `border.color.light` |
| `gray5` | `background.quaternary` (pressed), `border.color.medium` | `background.quaternary`, `border.color.medium` |
| `gray6` | `border.color.strong` | `border.color.strong` |
| `gray7` | `font.color.extraLight` | `font.color.extraLight`, the `gray` record colour |
| `gray8` | `font.color.light` | `font.color.light` |
| `gray9` | `font.color.tertiary`, the `gray` record colour | `font.color.tertiary` |
| `gray10` | code text | code text |
| `gray11` | `font.color.secondary`, `background.invertedSecondary` | `font.color.secondary` |
| `gray12` | `font.color.primary`, `background.invertedPrimary` | `font.color.primary` |

### 2.2 Grayscale alpha

`GRAY_SCALE_LIGHT_ALPHA` (`packages/twenty-ui/src/theme/constants/GrayScaleLightAlpha.ts:1-14`) and `GRAY_SCALE_DARK_ALPHA`
(`packages/twenty-ui/src/theme/constants/GrayScaleDarkAlpha.ts:1-14`). These back the hover/press scale and the shadows. In the CSS they
surface as `--t-color-transparent-gray*`:

| Token | Light | Dark |
|---|---|---|
| `--t-color-transparent-gray1` | color(display-p3 0 0 0 / 0.02) | color(display-p3 1 1 1 / 0.031) |
| `--t-color-transparent-gray2` | color(display-p3 0 0 0 / 0.039) | color(display-p3 1 1 1 / 0.059) |
| `--t-color-transparent-gray3` | color(display-p3 0 0 0 / 0.047) | color(display-p3 1 1 1 / 0.047) |
| `--t-color-transparent-gray4` | color(display-p3 0 0 0 / 0.071) | color(display-p3 1 1 1 / 0.071) |
| `--t-color-transparent-gray5` | color(display-p3 0 0 0 / 0.078) | color(display-p3 1 1 1 / 0.102) |
| `--t-color-transparent-gray6` | color(display-p3 0 0 0 / 0.114) | color(display-p3 1 1 1 / 0.114) |
| `--t-color-transparent-gray7` | color(display-p3 0 0 0 / 0.161) | color(display-p3 1 1 1 / 0.141) |
| `--t-color-transparent-gray8` | color(display-p3 0 0 0 / 0.22) | color(display-p3 1 1 1 / 0.22) |
| `--t-color-transparent-gray9` | color(display-p3 0 0 0 / 0.361) | color(display-p3 1 1 1 / 0.427) |
| `--t-color-transparent-gray10` | color(display-p3 0 0 0 / 0.478) | color(display-p3 1 1 1 / 0.478) |
| `--t-color-transparent-gray11` | color(display-p3 0 0 0 / 0.722) | color(display-p3 1 1 1 / 0.565) |
| `--t-color-transparent-gray12` | color(display-p3 0 0 0 / 0.91) | color(display-p3 1 1 1 / 0.91) |

Light is black-over; dark is white-over. Note the alphas are **not** mirrored: light `gray9` is
`0.361`, dark `gray9` is `0.427`; light `gray11` is `0.722`, dark is `0.565`.

### 2.3 Accent — indigo P3

`--t-accent-*`. `accent1…accent12` are Radix `indigoP3` / `indigoDarkP3` verbatim
(`packages/twenty-ui/src/theme/constants/AccentLight.ts:11-22`, `packages/twenty-ui/src/theme/constants/AccentDark.ts:11-22`); the four named aliases point into the *blue*
ramp, which is itself indigo (`packages/twenty-ui/src/theme/constants/AccentLight.ts:5-10`):

- `primary`, `secondary` → `blue5`
- `tertiary` → `blue3`
- `quaternary` → `blue2`
- `accent3570`, `accent4060` → `blue8` (both, identically)

| Token | Light | Dark |
|---|---|---|
| `--t-accent-primary` | color(display-p3 0.831 0.87 1) | color(display-p3 0.163 0.22 0.439) |
| `--t-accent-secondary` | color(display-p3 0.831 0.87 1) | color(display-p3 0.163 0.22 0.439) |
| `--t-accent-tertiary` | color(display-p3 0.933 0.948 0.992) | color(display-p3 0.105 0.141 0.275) |
| `--t-accent-quaternary` | color(display-p3 0.971 0.977 0.998) | color(display-p3 0.081 0.089 0.144) |
| `--t-accent-accent3570` | color(display-p3 0.569 0.639 0.916) | color(display-p3 0.285 0.362 0.674) |
| `--t-accent-accent4060` | color(display-p3 0.569 0.639 0.916) | color(display-p3 0.285 0.362 0.674) |
| `--t-accent-accent1` | color(display-p3 0.992 0.992 0.996) | color(display-p3 0.068 0.074 0.118) |
| `--t-accent-accent2` | color(display-p3 0.971 0.977 0.998) | color(display-p3 0.081 0.089 0.144) |
| `--t-accent-accent3` | color(display-p3 0.933 0.948 0.992) | color(display-p3 0.105 0.141 0.275) |
| `--t-accent-accent4` | color(display-p3 0.885 0.914 1) | color(display-p3 0.129 0.18 0.369) |
| `--t-accent-accent5` | color(display-p3 0.831 0.87 1) | color(display-p3 0.163 0.22 0.439) |
| `--t-accent-accent6` | color(display-p3 0.767 0.814 0.995) | color(display-p3 0.203 0.262 0.5) |
| `--t-accent-accent7` | color(display-p3 0.685 0.74 0.957) | color(display-p3 0.245 0.309 0.575) |
| `--t-accent-accent8` | color(display-p3 0.569 0.639 0.916) | color(display-p3 0.285 0.362 0.674) |
| `--t-accent-accent9` | color(display-p3 0.276 0.384 0.837) | color(display-p3 0.276 0.384 0.837) |
| `--t-accent-accent10` | color(display-p3 0.234 0.343 0.801) | color(display-p3 0.354 0.445 0.866) |
| `--t-accent-accent11` | color(display-p3 0.256 0.354 0.755) | color(display-p3 0.63 0.69 1) |
| `--t-accent-accent12` | color(display-p3 0.133 0.175 0.348) | color(display-p3 0.848 0.881 0.99) |

### 2.4 Semantic layer — background

Aliases defined in `packages/twenty-ui/src/theme/constants/BackgroundLight.ts:7-35` / `packages/twenty-ui/src/theme/constants/BackgroundDark.ts:7-35`.

| Token | Light | Dark |
|---|---|---|
| `--t-background-primary` | color(display-p3 1 1 1) | color(display-p3 0.09 0.09 0.09) |
| `--t-background-secondary` | color(display-p3 0.988 0.988 0.988) | color(display-p3 0.106 0.106 0.106) |
| `--t-background-tertiary` | color(display-p3 0.945 0.945 0.945) | color(display-p3 0.114 0.114 0.114) |
| `--t-background-quaternary` | color(display-p3 0.922 0.922 0.922) | color(display-p3 0.133 0.133 0.133) |
| `--t-background-inverted-primary` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |
| `--t-background-inverted-secondary` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |
| `--t-background-danger` | color(display-p3 0.985 0.925 0.925) | color(display-p3 0.211 0.081 0.099) |
| `--t-background-transparent-primary` | color(display-p3 1 1 1 / 0.5) | color(display-p3 0 0 0 / 0.5) |
| `--t-background-transparent-secondary` | color(display-p3 1 1 1 / 0.4) | color(display-p3 0 0 0 / 0.4) |
| `--t-background-transparent-strong` | color(display-p3 0 0 0 / 0.161) | color(display-p3 1 1 1 / 0.141) |
| `--t-background-transparent-medium` | color(display-p3 0 0 0 / 0.078) | color(display-p3 1 1 1 / 0.102) |
| `--t-background-transparent-light` | color(display-p3 0 0 0 / 0.039) | color(display-p3 1 1 1 / 0.059) |
| `--t-background-transparent-lighter` | color(display-p3 0 0 0 / 0.02) | color(display-p3 1 1 1 / 0.031) |
| `--t-background-transparent-danger` | #f3000d14 | #ff173f2d |
| `--t-background-transparent-blue` | #0047f112 | #3566ff57 |
| `--t-background-transparent-orange` | #ff9c0029 | #ff590039 |
| `--t-background-transparent-success` | #00a43319 | #11ff992d |
| `--t-background-overlay-primary` | color(display-p3 0 0 0 / 0.722) | #000000b8 |
| `--t-background-overlay-secondary` | color(display-p3 0 0 0 / 0.361) | #0000005c |
| `--t-background-overlay-tertiary` | color(display-p3 0 0 0 / 0.071) | #0000005c |
| `--t-background-radial-gradient` | radial-gradient( 50% 62.62% at 50% 0%, color(display-p3 0.6 0.6 0.6) 0%, color(display-p3 0.514 0.514 0.514) 100% ) | radial-gradient( 50% 62.62% at 50% 0%, color(display-p3 0.506 0.506 0.506) 0%, color(display-p3 0.482 0.482 0.482) 100% ) |
| `--t-background-radial-gradient-hover` | radial-gradient( 76.32% 95.59% at 50% 0%, color(display-p3 0.514 0.514 0.514) 0%, color(display-p3 0.4 0.4 0.4) 100% ) | radial-gradient( 76.32% 95.59% at 50% 0%, color(display-p3 0.482 0.482 0.482) 0%, color(display-p3 0.702 0.702 0.702) 100% ) |
| `--t-background-primary-inverted` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |
| `--t-background-primary-inverted-hover` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |

`--t-background-noisy` is omitted from the table: it is a ~9KB base64 PNG data URI
(`packages/twenty-ui/src/theme-constants/theme-light.css:92`, identical in dark), a tiling noise texture.

Intended use:

| Token | Use |
|---|---|
| `background.primary` | cards, table cells, the side panel, dropdown surfaces at rest |
| `background.secondary` | hover on a `primary` surface (table header cell hover) |
| `background.tertiary` | the page/body background, and press state on a `primary` surface |
| `background.quaternary` | press state one level deeper (button `:active`) |
| `background.transparent.lighter/light/medium/strong` | the four-step hover→press ladder for anything sitting on an unknown background |
| `background.transparent.primary/secondary` | frosted overlay fill, paired with `blur` |
| `background.transparent.danger/blue/orange/success` | tinted status fills (snackbars, checkbox accent hover) |
| `background.overlay*` | modal scrims |
| `background.invertedPrimary/Secondary`, `primaryInverted*` | inverted buttons, tooltips |
| `background.danger` | destructive hover fill |

### 2.5 Semantic layer — border

`packages/twenty-ui/src/theme/constants/BorderLight.ts:6-18` / `packages/twenty-ui/src/theme/constants/BorderDark.ts:6-18`.

| Token | Light | Dark |
|---|---|---|
| `--t-border-color-strong` | color(display-p3 0.839 0.839 0.839) | color(display-p3 0.282 0.282 0.282) |
| `--t-border-color-medium` | color(display-p3 0.922 0.922 0.922) | color(display-p3 0.133 0.133 0.133) |
| `--t-border-color-light` | color(display-p3 0.945 0.945 0.945) | color(display-p3 0.114 0.114 0.114) |
| `--t-border-color-secondary-inverted` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |
| `--t-border-color-inverted` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |
| `--t-border-color-danger` | color(display-p3 0.984 0.812 0.811) | color(display-p3 0.348 0.11 0.142) |
| `--t-border-color-blue` | color(display-p3 0.685 0.74 0.957) | color(display-p3 0.245 0.309 0.575) |
| `--t-border-color-transparent-strong` | color(display-p3 0 0 0 / 0.071) | color(display-p3 1 1 1 / 0.071) |

| Token | Use |
|---|---|
| `light` | table cell grid lines, chip dividers — the quietest rule in the product |
| `medium` | the default component border: cards, dropdowns, modals, the side panel edge |
| `strong` | tag outline/border variants, checkbox hover |
| `danger` | invalid input, destructive secondary button |
| `blue` | focused/active affordance edge |
| `inverted` / `secondaryInverted` | checkbox chrome on inverted surfaces |
| `transparentStrong` | defined; see §11 |

### 2.6 Semantic layer — font, shadow, blur, snackbar, code, illustration

**Font colour** (`packages/twenty-ui/src/theme/constants/FontLight.ts:5-16` / `packages/twenty-ui/src/theme/constants/FontDark.ts:5-16`):

| Token | Light | Dark |
|---|---|---|
| `--t-font-color-primary` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |
| `--t-font-color-secondary` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |
| `--t-font-color-tertiary` | color(display-p3 0.6 0.6 0.6) | color(display-p3 0.506 0.506 0.506) |
| `--t-font-color-light` | color(display-p3 0.702 0.702 0.702) | color(display-p3 0.4 0.4 0.4) |
| `--t-font-color-extra-light` | color(display-p3 0.8 0.8 0.8) | color(display-p3 0.298 0.298 0.298) |
| `--t-font-color-inverted` | color(display-p3 1 1 1) | color(display-p3 0.09 0.09 0.09) |
| `--t-font-color-danger` | color(display-p3 0.83 0.329 0.324) | color(display-p3 0.83 0.329 0.324) |

**Box shadow** (`packages/twenty-ui/src/theme/constants/BoxShadowLight.ts:3-9` / `packages/twenty-ui/src/theme/constants/BoxShadowDark.ts:4-19`) — this is the one place where
the two themes **differ in structure, not just value**. Light composes its shadows from
`GRAY_SCALE_LIGHT_ALPHA` (P3 black-alpha) and gives `superHeavy` a distinct three-layer recipe;
dark hard-codes `rgba()` via the `RGBA()` helper (`packages/twenty-ui/src/theme/constants/Rgba.ts:3-18`, file-level
`oxlint-disable twenty/no-hardcoded-colors`) and makes `superHeavy` a *lighter* two-layer shadow
than light's:

| Token | Light | Dark |
|---|---|---|
| `--t-box-shadow-color` | color(display-p3 0 0 0 / 0.039) | rgba(0, 0, 0, 0.6) |
| `--t-box-shadow-light` | 0px 2px 4px 0px color(display-p3 0 0 0 / 0.039), 0px 0px 4px 0px color(display-p3 0 0 0 / 0.078) | 0px 2px 4px 0px rgba(0, 0, 0, 0.04), 0px 0px 4px 0px rgba(0, 0, 0, 0.08) |
| `--t-box-shadow-strong` | 2px 4px 16px 0px color(display-p3 0 0 0 / 0.161), 0px 2px 4px 0px color(display-p3 0 0 0 / 0.078) | 2px 4px 16px 0px rgba(0, 0, 0, 0.16), 0px 2px 4px 0px rgba(0, 0, 0, 0.08) |
| `--t-box-shadow-underline` | 0px 1px 0px 0px color(display-p3 0 0 0 / 0.361) | 0px 1px 0px 0px rgba(0, 0, 0, 0.32) |
| `--t-box-shadow-super-heavy` | 0px 0px 8px 0px color(display-p3 0 0 0 / 0.161), 0px 8px 64px -16px color(display-p3 0 0 0 / 0.478), 0px 24px 56px -16px color(display-p3 0 0 0 / 0.078) | 2px 4px 16px 0px rgba(0, 0, 0, 0.12), 0px 2px 4px 0px rgba(0, 0, 0, 0.04) |

**Blur** (`packages/twenty-ui/src/theme/constants/BlurLight.ts:1-5` / `packages/twenty-ui/src/theme/constants/BlurDark.ts:1-5`) — identical except `contrast(50%)` in light vs
`contrast(100%)` in dark:

| Token | Light | Dark |
|---|---|---|
| `--t-blur-light` | blur(6px) saturate(200%) contrast(50%) brightness(130%) | blur(6px) saturate(200%) contrast(100%) brightness(130%) |
| `--t-blur-medium` | blur(12px) saturate(200%) contrast(50%) brightness(130%) | blur(12px) saturate(200%) contrast(100%) brightness(130%) |
| `--t-blur-strong` | blur(20px) saturate(200%) contrast(50%) brightness(130%) | blur(20px) saturate(200%) contrast(100%) brightness(130%) |

**Snackbar** (`packages/twenty-ui/src/theme/constants/SnackBarLight.ts:5-26`) — each state is a `{ color, backgroundColor }` pair; the
colour comes from the named record colour, the fill from `background.transparent.*`:

| Token | Light | Dark |
|---|---|---|
| `--t-snack-bar-success-color` | color(display-p3 0.297 0.637 0.581) | color(display-p3 0.297 0.637 0.581) |
| `--t-snack-bar-success-background-color` | #00a43319 | #11ff992d |
| `--t-snack-bar-error-color` | color(display-p3 0.83 0.329 0.324) | color(display-p3 0.83 0.329 0.324) |
| `--t-snack-bar-error-background-color` | #f3000d14 | #ff173f2d |
| `--t-snack-bar-warning-color` | color(display-p3 0.9 0.45 0.2) | color(display-p3 0.9 0.45 0.2) |
| `--t-snack-bar-warning-background-color` | #ff9c0029 | #ff590039 |
| `--t-snack-bar-info-color` | color(display-p3 0.276 0.384 0.837) | color(display-p3 0.276 0.384 0.837) |
| `--t-snack-bar-info-background-color` | #0047f112 | #3566ff57 |
| `--t-snack-bar-default-color` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |
| `--t-snack-bar-default-background-color` | color(display-p3 0 0 0 / 0.039) | color(display-p3 1 1 1 / 0.059) |

**Code** (`packages/twenty-ui/src/theme/constants/CodeLight.ts:3-12` / `packages/twenty-ui/src/theme/constants/CodeDark.ts:3-12`) — a five-token syntax palette plus its family:

| Token | Light | Dark |
|---|---|---|
| `--t-code-text-gray` | color(display-p3 0.514 0.514 0.514) | color(display-p3 0.482 0.482 0.482) |
| `--t-code-text-sky` | color(display-p3 0.555 0.845 0.959) | color(display-p3 0.718 0.925 0.991) |
| `--t-code-text-pink` | color(display-p3 0.748 0.27 0.581) | color(display-p3 0.808 0.356 0.645) |
| `--t-code-text-orange` | color(display-p3 0.877 0.597 0.379) | color(display-p3 0.601 0.359 0.201) |
| `--t-code-text-green` | color(display-p3 0.585 0.707 0.378) | color(display-p3 0.365 0.456 0.25) |
| `--t-code-font-family` | DM Mono | DM Mono |

**Illustration icons** (`packages/twenty-ui/src/theme/constants/IllustrationIconLight.ts:4-13`) — two-tone field-type glyphs, a stroke
colour and a fill colour. Note the double dash in the generated variable names:

| Token | Light | Dark |
|---|---|---|
| `--t--illustration-icon-color-blue` | color(display-p3 0.569 0.639 0.916) | color(display-p3 0.354 0.445 0.866) |
| `--t--illustration-icon-color-gray` | color(display-p3 0.6 0.6 0.6) | color(display-p3 0.4 0.4 0.4) |
| `--t--illustration-icon-fill-blue` | color(display-p3 0.831 0.87 1) | color(display-p3 0.848 0.881 0.99) |
| `--t--illustration-icon-fill-gray` | color(display-p3 0.922 0.922 0.922) | color(display-p3 0.133 0.133 0.133) |

### 2.7 The record colour palette

`ThemeColor` is the union of the 25 keys of `MAIN_COLORS_LIGHT`
(`packages/twenty-ui/src/theme/constants/MainColorNames.ts:3-5`); the fallback is `'gray'` (`packages/twenty-ui/src/theme/constants/DefaultThemeColorFallback.ts:3`). Each name
maps to step 9 of a Radix P3 scale, except `gray`, which maps to the hand-written grayscale —
`gray9` in light, `gray7` in dark (`packages/twenty-ui/src/theme/constants/MainColorsLight.ts:34`, `packages/twenty-ui/src/theme/constants/MainColorsDark.ts:34`). Two names are
renamed from their Radix source: **`turquoise` is Radix `teal`** and **`blue` is Radix `indigo`**
(`packages/twenty-ui/src/theme/constants/MainColorsLight.ts:20,23`).

| Token | Light | Dark |
|---|---|---|
| `--t-color-red` | color(display-p3 0.83 0.329 0.324) | color(display-p3 0.83 0.329 0.324) |
| `--t-color-ruby` | color(display-p3 0.83 0.323 0.408) | color(display-p3 0.83 0.323 0.408) |
| `--t-color-crimson` | color(display-p3 0.843 0.298 0.507) | color(display-p3 0.843 0.298 0.507) |
| `--t-color-tomato` | color(display-p3 0.831 0.345 0.231) | color(display-p3 0.831 0.345 0.231) |
| `--t-color-orange` | color(display-p3 0.9 0.45 0.2) | color(display-p3 0.9 0.45 0.2) |
| `--t-color-amber` | color(display-p3 1 0.77 0.26) | color(display-p3 1 0.77 0.26) |
| `--t-color-yellow` | color(display-p3 1 0.92 0.22) | color(display-p3 1 0.92 0.22) |
| `--t-color-lime` | color(display-p3 0.78 0.928 0.466) | color(display-p3 0.78 0.928 0.466) |
| `--t-color-grass` | color(display-p3 0.38 0.647 0.378) | color(display-p3 0.38 0.647 0.378) |
| `--t-color-green` | color(display-p3 0.332 0.634 0.442) | color(display-p3 0.332 0.634 0.442) |
| `--t-color-jade` | color(display-p3 0.319 0.63 0.521) | color(display-p3 0.319 0.63 0.521) |
| `--t-color-mint` | color(display-p3 0.62 0.908 0.834) | color(display-p3 0.62 0.908 0.834) |
| `--t-color-turquoise` | color(display-p3 0.297 0.637 0.581) | color(display-p3 0.297 0.637 0.581) |
| `--t-color-cyan` | color(display-p3 0.282 0.627 0.765) | color(display-p3 0.282 0.627 0.765) |
| `--t-color-sky` | color(display-p3 0.585 0.877 0.983) | color(display-p3 0.585 0.877 0.983) |
| `--t-color-blue` | color(display-p3 0.276 0.384 0.837) | color(display-p3 0.276 0.384 0.837) |
| `--t-color-iris` | color(display-p3 0.357 0.357 0.81) | color(display-p3 0.357 0.357 0.81) |
| `--t-color-violet` | color(display-p3 0.417 0.341 0.784) | color(display-p3 0.417 0.341 0.784) |
| `--t-color-purple` | color(display-p3 0.523 0.318 0.751) | color(display-p3 0.523 0.318 0.751) |
| `--t-color-plum` | color(display-p3 0.624 0.313 0.708) | color(display-p3 0.624 0.313 0.708) |
| `--t-color-pink` | color(display-p3 0.775 0.297 0.61) | color(display-p3 0.775 0.297 0.61) |
| `--t-color-bronze` | color(display-p3 0.611 0.507 0.455) | color(display-p3 0.611 0.507 0.455) |
| `--t-color-gold` | color(display-p3 0.579 0.517 0.41) | color(display-p3 0.579 0.517 0.41) |
| `--t-color-brown` | color(display-p3 0.651 0.505 0.368) | color(display-p3 0.651 0.505 0.368) |
| `--t-color-gray` | color(display-p3 0.6 0.6 0.6) | color(display-p3 0.298 0.298 0.298) |

### 2.8 Full solid ramps

30 families × 12 steps, in both themes. `yellow`…`amber` come from `SECONDARY_COLORS_LIGHT`
(`packages/twenty-ui/src/theme/constants/SecondaryColorsLight.ts`, 394 lines, one Radix P3 import per entry) and its dark twin; `gray`
duplicates the hand-written grayscale. Generated verbatim from `packages/twenty-ui/src/theme-constants/theme-light.css:294-653` and
`packages/twenty-ui/src/theme-constants/theme-dark.css:290-649`.


**yellow**

| Token | Light | Dark |
|---|---|---|
| `--t-color-yellow1` | color(display-p3 0.992 0.992 0.978) | color(display-p3 0.078 0.069 0.047) |
| `--t-color-yellow2` | color(display-p3 0.995 0.99 0.922) | color(display-p3 0.103 0.094 0.063) |
| `--t-color-yellow3` | color(display-p3 0.997 0.982 0.749) | color(display-p3 0.168 0.137 0.039) |
| `--t-color-yellow4` | color(display-p3 0.992 0.953 0.627) | color(display-p3 0.209 0.169 0) |
| `--t-color-yellow5` | color(display-p3 0.984 0.91 0.51) | color(display-p3 0.255 0.209 0) |
| `--t-color-yellow6` | color(display-p3 0.934 0.847 0.474) | color(display-p3 0.31 0.261 0.07) |
| `--t-color-yellow7` | color(display-p3 0.876 0.785 0.46) | color(display-p3 0.389 0.331 0.135) |
| `--t-color-yellow8` | color(display-p3 0.811 0.689 0.313) | color(display-p3 0.497 0.42 0.182) |
| `--t-color-yellow9` | color(display-p3 1 0.92 0.22) | color(display-p3 1 0.92 0.22) |
| `--t-color-yellow10` | color(display-p3 0.977 0.868 0.291) | color(display-p3 1 1 0.456) |
| `--t-color-yellow11` | color(display-p3 0.6 0.44 0) | color(display-p3 0.948 0.885 0.392) |
| `--t-color-yellow12` | color(display-p3 0.271 0.233 0.137) | color(display-p3 0.959 0.934 0.731) |

**green**

| Token | Light | Dark |
|---|---|---|
| `--t-color-green1` | color(display-p3 0.986 0.996 0.989) | color(display-p3 0.062 0.083 0.071) |
| `--t-color-green2` | color(display-p3 0.963 0.983 0.967) | color(display-p3 0.079 0.106 0.09) |
| `--t-color-green3` | color(display-p3 0.913 0.964 0.925) | color(display-p3 0.1 0.173 0.133) |
| `--t-color-green4` | color(display-p3 0.859 0.94 0.879) | color(display-p3 0.115 0.229 0.166) |
| `--t-color-green5` | color(display-p3 0.796 0.907 0.826) | color(display-p3 0.147 0.282 0.206) |
| `--t-color-green6` | color(display-p3 0.718 0.863 0.761) | color(display-p3 0.185 0.338 0.25) |
| `--t-color-green7` | color(display-p3 0.61 0.801 0.675) | color(display-p3 0.227 0.403 0.298) |
| `--t-color-green8` | color(display-p3 0.451 0.715 0.559) | color(display-p3 0.27 0.479 0.351) |
| `--t-color-green9` | color(display-p3 0.332 0.634 0.442) | color(display-p3 0.332 0.634 0.442) |
| `--t-color-green10` | color(display-p3 0.308 0.595 0.417) | color(display-p3 0.357 0.682 0.474) |
| `--t-color-green11` | color(display-p3 0.19 0.5 0.32) | color(display-p3 0.434 0.828 0.573) |
| `--t-color-green12` | color(display-p3 0.132 0.228 0.18) | color(display-p3 0.747 0.938 0.807) |

**turquoise**

| Token | Light | Dark |
|---|---|---|
| `--t-color-turquoise1` | color(display-p3 0.983 0.996 0.992) | color(display-p3 0.059 0.083 0.079) |
| `--t-color-turquoise2` | color(display-p3 0.958 0.983 0.976) | color(display-p3 0.075 0.11 0.107) |
| `--t-color-turquoise3` | color(display-p3 0.895 0.971 0.952) | color(display-p3 0.087 0.175 0.165) |
| `--t-color-turquoise4` | color(display-p3 0.831 0.949 0.92) | color(display-p3 0.087 0.227 0.214) |
| `--t-color-turquoise5` | color(display-p3 0.761 0.914 0.878) | color(display-p3 0.12 0.277 0.261) |
| `--t-color-turquoise6` | color(display-p3 0.682 0.864 0.825) | color(display-p3 0.162 0.335 0.314) |
| `--t-color-turquoise7` | color(display-p3 0.581 0.798 0.756) | color(display-p3 0.205 0.406 0.379) |
| `--t-color-turquoise8` | color(display-p3 0.433 0.716 0.671) | color(display-p3 0.245 0.489 0.453) |
| `--t-color-turquoise9` | color(display-p3 0.297 0.637 0.581) | color(display-p3 0.297 0.637 0.581) |
| `--t-color-turquoise10` | color(display-p3 0.275 0.599 0.542) | color(display-p3 0.319 0.69 0.62) |
| `--t-color-turquoise11` | color(display-p3 0.08 0.5 0.43) | color(display-p3 0.388 0.835 0.719) |
| `--t-color-turquoise12` | color(display-p3 0.11 0.235 0.219) | color(display-p3 0.734 0.934 0.87) |

**sky**

| Token | Light | Dark |
|---|---|---|
| `--t-color-sky1` | color(display-p3 0.98 0.995 0.999) | color(display-p3 0.056 0.078 0.116) |
| `--t-color-sky2` | color(display-p3 0.953 0.98 0.99) | color(display-p3 0.075 0.101 0.149) |
| `--t-color-sky3` | color(display-p3 0.899 0.963 0.989) | color(display-p3 0.089 0.154 0.244) |
| `--t-color-sky4` | color(display-p3 0.842 0.937 0.977) | color(display-p3 0.106 0.207 0.323) |
| `--t-color-sky5` | color(display-p3 0.777 0.9 0.954) | color(display-p3 0.135 0.261 0.394) |
| `--t-color-sky6` | color(display-p3 0.701 0.851 0.921) | color(display-p3 0.17 0.322 0.469) |
| `--t-color-sky7` | color(display-p3 0.604 0.785 0.879) | color(display-p3 0.205 0.394 0.557) |
| `--t-color-sky8` | color(display-p3 0.457 0.696 0.829) | color(display-p3 0.232 0.48 0.665) |
| `--t-color-sky9` | color(display-p3 0.585 0.877 0.983) | color(display-p3 0.585 0.877 0.983) |
| `--t-color-sky10` | color(display-p3 0.555 0.845 0.959) | color(display-p3 0.718 0.925 0.991) |
| `--t-color-sky11` | color(display-p3 0.193 0.448 0.605) | color(display-p3 0.536 0.772 0.924) |
| `--t-color-sky12` | color(display-p3 0.145 0.241 0.329) | color(display-p3 0.799 0.947 0.993) |

**blue**

| Token | Light | Dark |
|---|---|---|
| `--t-color-blue1` | color(display-p3 0.992 0.992 0.996) | color(display-p3 0.068 0.074 0.118) |
| `--t-color-blue2` | color(display-p3 0.971 0.977 0.998) | color(display-p3 0.081 0.089 0.144) |
| `--t-color-blue3` | color(display-p3 0.933 0.948 0.992) | color(display-p3 0.105 0.141 0.275) |
| `--t-color-blue4` | color(display-p3 0.885 0.914 1) | color(display-p3 0.129 0.18 0.369) |
| `--t-color-blue5` | color(display-p3 0.831 0.87 1) | color(display-p3 0.163 0.22 0.439) |
| `--t-color-blue6` | color(display-p3 0.767 0.814 0.995) | color(display-p3 0.203 0.262 0.5) |
| `--t-color-blue7` | color(display-p3 0.685 0.74 0.957) | color(display-p3 0.245 0.309 0.575) |
| `--t-color-blue8` | color(display-p3 0.569 0.639 0.916) | color(display-p3 0.285 0.362 0.674) |
| `--t-color-blue9` | color(display-p3 0.276 0.384 0.837) | color(display-p3 0.276 0.384 0.837) |
| `--t-color-blue10` | color(display-p3 0.234 0.343 0.801) | color(display-p3 0.354 0.445 0.866) |
| `--t-color-blue11` | color(display-p3 0.256 0.354 0.755) | color(display-p3 0.63 0.69 1) |
| `--t-color-blue12` | color(display-p3 0.133 0.175 0.348) | color(display-p3 0.848 0.881 0.99) |

**purple**

| Token | Light | Dark |
|---|---|---|
| `--t-color-purple1` | color(display-p3 0.995 0.988 0.996) | color(display-p3 0.09 0.068 0.103) |
| `--t-color-purple2` | color(display-p3 0.983 0.971 0.993) | color(display-p3 0.113 0.082 0.134) |
| `--t-color-purple3` | color(display-p3 0.963 0.931 0.989) | color(display-p3 0.175 0.112 0.224) |
| `--t-color-purple4` | color(display-p3 0.937 0.888 0.981) | color(display-p3 0.224 0.137 0.297) |
| `--t-color-purple5` | color(display-p3 0.904 0.837 0.966) | color(display-p3 0.264 0.167 0.349) |
| `--t-color-purple6` | color(display-p3 0.86 0.774 0.942) | color(display-p3 0.311 0.208 0.406) |
| `--t-color-purple7` | color(display-p3 0.799 0.69 0.91) | color(display-p3 0.381 0.266 0.496) |
| `--t-color-purple8` | color(display-p3 0.719 0.583 0.874) | color(display-p3 0.49 0.349 0.649) |
| `--t-color-purple9` | color(display-p3 0.523 0.318 0.751) | color(display-p3 0.523 0.318 0.751) |
| `--t-color-purple10` | color(display-p3 0.483 0.289 0.7) | color(display-p3 0.57 0.373 0.791) |
| `--t-color-purple11` | color(display-p3 0.473 0.281 0.687) | color(display-p3 0.8 0.62 1) |
| `--t-color-purple12` | color(display-p3 0.234 0.132 0.363) | color(display-p3 0.913 0.854 0.971) |

**pink**

| Token | Light | Dark |
|---|---|---|
| `--t-color-pink1` | color(display-p3 0.998 0.989 0.996) | color(display-p3 0.093 0.068 0.089) |
| `--t-color-pink2` | color(display-p3 0.992 0.97 0.985) | color(display-p3 0.121 0.073 0.11) |
| `--t-color-pink3` | color(display-p3 0.981 0.917 0.96) | color(display-p3 0.198 0.098 0.179) |
| `--t-color-pink4` | color(display-p3 0.963 0.867 0.932) | color(display-p3 0.271 0.095 0.231) |
| `--t-color-pink5` | color(display-p3 0.939 0.815 0.899) | color(display-p3 0.32 0.127 0.273) |
| `--t-color-pink6` | color(display-p3 0.907 0.756 0.859) | color(display-p3 0.382 0.177 0.326) |
| `--t-color-pink7` | color(display-p3 0.869 0.683 0.81) | color(display-p3 0.477 0.238 0.405) |
| `--t-color-pink8` | color(display-p3 0.825 0.59 0.751) | color(display-p3 0.612 0.304 0.51) |
| `--t-color-pink9` | color(display-p3 0.775 0.297 0.61) | color(display-p3 0.775 0.297 0.61) |
| `--t-color-pink10` | color(display-p3 0.748 0.27 0.581) | color(display-p3 0.808 0.356 0.645) |
| `--t-color-pink11` | color(display-p3 0.698 0.219 0.528) | color(display-p3 1 0.535 0.78) |
| `--t-color-pink12` | color(display-p3 0.363 0.101 0.279) | color(display-p3 0.964 0.826 0.912) |

**red**

| Token | Light | Dark |
|---|---|---|
| `--t-color-red1` | color(display-p3 0.998 0.989 0.988) | color(display-p3 0.093 0.068 0.067) |
| `--t-color-red2` | color(display-p3 0.995 0.971 0.971) | color(display-p3 0.118 0.077 0.079) |
| `--t-color-red3` | color(display-p3 0.985 0.925 0.925) | color(display-p3 0.211 0.081 0.099) |
| `--t-color-red4` | color(display-p3 0.999 0.866 0.866) | color(display-p3 0.287 0.079 0.113) |
| `--t-color-red5` | color(display-p3 0.984 0.812 0.811) | color(display-p3 0.348 0.11 0.142) |
| `--t-color-red6` | color(display-p3 0.955 0.751 0.749) | color(display-p3 0.414 0.16 0.183) |
| `--t-color-red7` | color(display-p3 0.915 0.675 0.672) | color(display-p3 0.508 0.224 0.236) |
| `--t-color-red8` | color(display-p3 0.872 0.575 0.572) | color(display-p3 0.659 0.298 0.297) |
| `--t-color-red9` | color(display-p3 0.83 0.329 0.324) | color(display-p3 0.83 0.329 0.324) |
| `--t-color-red10` | color(display-p3 0.798 0.294 0.285) | color(display-p3 0.861 0.403 0.387) |
| `--t-color-red11` | color(display-p3 0.744 0.234 0.222) | color(display-p3 1 0.57 0.55) |
| `--t-color-red12` | color(display-p3 0.36 0.115 0.143) | color(display-p3 0.971 0.826 0.852) |

**orange**

| Token | Light | Dark |
|---|---|---|
| `--t-color-orange1` | color(display-p3 0.995 0.988 0.985) | color(display-p3 0.088 0.07 0.057) |
| `--t-color-orange2` | color(display-p3 0.994 0.968 0.934) | color(display-p3 0.113 0.089 0.061) |
| `--t-color-orange3` | color(display-p3 0.989 0.938 0.85) | color(display-p3 0.189 0.12 0.056) |
| `--t-color-orange4` | color(display-p3 1 0.874 0.687) | color(display-p3 0.262 0.132 0) |
| `--t-color-orange5` | color(display-p3 1 0.821 0.583) | color(display-p3 0.315 0.168 0.016) |
| `--t-color-orange6` | color(display-p3 0.975 0.767 0.545) | color(display-p3 0.376 0.219 0.088) |
| `--t-color-orange7` | color(display-p3 0.919 0.693 0.486) | color(display-p3 0.465 0.283 0.147) |
| `--t-color-orange8` | color(display-p3 0.877 0.597 0.379) | color(display-p3 0.601 0.359 0.201) |
| `--t-color-orange9` | color(display-p3 0.9 0.45 0.2) | color(display-p3 0.9 0.45 0.2) |
| `--t-color-orange10` | color(display-p3 0.87 0.409 0.164) | color(display-p3 0.98 0.51 0.23) |
| `--t-color-orange11` | color(display-p3 0.76 0.34 0) | color(display-p3 1 0.63 0.38) |
| `--t-color-orange12` | color(display-p3 0.323 0.185 0.127) | color(display-p3 0.98 0.883 0.775) |

**gray**

| Token | Light | Dark |
|---|---|---|
| `--t-color-gray1` | color(display-p3 1 1 1) | color(display-p3 0.09 0.09 0.09) |
| `--t-color-gray2` | color(display-p3 0.988 0.988 0.988) | color(display-p3 0.106 0.106 0.106) |
| `--t-color-gray3` | color(display-p3 0.976 0.976 0.976) | color(display-p3 0.098 0.098 0.098) |
| `--t-color-gray4` | color(display-p3 0.945 0.945 0.945) | color(display-p3 0.114 0.114 0.114) |
| `--t-color-gray5` | color(display-p3 0.922 0.922 0.922) | color(display-p3 0.133 0.133 0.133) |
| `--t-color-gray6` | color(display-p3 0.839 0.839 0.839) | color(display-p3 0.282 0.282 0.282) |
| `--t-color-gray7` | color(display-p3 0.8 0.8 0.8) | color(display-p3 0.298 0.298 0.298) |
| `--t-color-gray8` | color(display-p3 0.702 0.702 0.702) | color(display-p3 0.4 0.4 0.4) |
| `--t-color-gray9` | color(display-p3 0.6 0.6 0.6) | color(display-p3 0.506 0.506 0.506) |
| `--t-color-gray10` | color(display-p3 0.514 0.514 0.514) | color(display-p3 0.482 0.482 0.482) |
| `--t-color-gray11` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |
| `--t-color-gray12` | color(display-p3 0.2 0.2 0.2) | color(display-p3 0.922 0.922 0.922) |

**mauve**

| Token | Light | Dark |
|---|---|---|
| `--t-color-mauve1` | color(display-p3 0.991 0.988 0.992) | color(display-p3 0.07 0.067 0.074) |
| `--t-color-mauve2` | color(display-p3 0.98 0.976 0.984) | color(display-p3 0.101 0.098 0.105) |
| `--t-color-mauve3` | color(display-p3 0.946 0.938 0.952) | color(display-p3 0.138 0.134 0.144) |
| `--t-color-mauve4` | color(display-p3 0.915 0.906 0.925) | color(display-p3 0.167 0.161 0.175) |
| `--t-color-mauve5` | color(display-p3 0.886 0.876 0.901) | color(display-p3 0.196 0.189 0.206) |
| `--t-color-mauve6` | color(display-p3 0.856 0.846 0.875) | color(display-p3 0.232 0.225 0.245) |
| `--t-color-mauve7` | color(display-p3 0.814 0.804 0.84) | color(display-p3 0.286 0.277 0.302) |
| `--t-color-mauve8` | color(display-p3 0.735 0.728 0.777) | color(display-p3 0.383 0.373 0.408) |
| `--t-color-mauve9` | color(display-p3 0.555 0.549 0.596) | color(display-p3 0.434 0.428 0.467) |
| `--t-color-mauve10` | color(display-p3 0.514 0.508 0.552) | color(display-p3 0.487 0.48 0.519) |
| `--t-color-mauve11` | color(display-p3 0.395 0.388 0.424) | color(display-p3 0.707 0.7 0.735) |
| `--t-color-mauve12` | color(display-p3 0.128 0.122 0.147) | color(display-p3 0.933 0.933 0.94) |

**slate**

| Token | Light | Dark |
|---|---|---|
| `--t-color-slate1` | color(display-p3 0.988 0.988 0.992) | color(display-p3 0.067 0.067 0.074) |
| `--t-color-slate2` | color(display-p3 0.976 0.976 0.984) | color(display-p3 0.095 0.098 0.105) |
| `--t-color-slate3` | color(display-p3 0.94 0.941 0.953) | color(display-p3 0.13 0.135 0.145) |
| `--t-color-slate4` | color(display-p3 0.908 0.909 0.925) | color(display-p3 0.156 0.163 0.176) |
| `--t-color-slate5` | color(display-p3 0.88 0.881 0.901) | color(display-p3 0.183 0.191 0.206) |
| `--t-color-slate6` | color(display-p3 0.85 0.852 0.876) | color(display-p3 0.215 0.226 0.244) |
| `--t-color-slate7` | color(display-p3 0.805 0.808 0.838) | color(display-p3 0.265 0.28 0.302) |
| `--t-color-slate8` | color(display-p3 0.727 0.733 0.773) | color(display-p3 0.357 0.381 0.409) |
| `--t-color-slate9` | color(display-p3 0.547 0.553 0.592) | color(display-p3 0.415 0.431 0.463) |
| `--t-color-slate10` | color(display-p3 0.503 0.512 0.549) | color(display-p3 0.469 0.483 0.514) |
| `--t-color-slate11` | color(display-p3 0.379 0.392 0.421) | color(display-p3 0.692 0.704 0.728) |
| `--t-color-slate12` | color(display-p3 0.113 0.125 0.14) | color(display-p3 0.93 0.933 0.94) |

**sage**

| Token | Light | Dark |
|---|---|---|
| `--t-color-sage1` | color(display-p3 0.986 0.992 0.988) | color(display-p3 0.064 0.07 0.067) |
| `--t-color-sage2` | color(display-p3 0.97 0.977 0.974) | color(display-p3 0.092 0.098 0.094) |
| `--t-color-sage3` | color(display-p3 0.935 0.944 0.94) | color(display-p3 0.128 0.135 0.131) |
| `--t-color-sage4` | color(display-p3 0.904 0.913 0.909) | color(display-p3 0.155 0.164 0.159) |
| `--t-color-sage5` | color(display-p3 0.875 0.885 0.88) | color(display-p3 0.183 0.193 0.188) |
| `--t-color-sage6` | color(display-p3 0.844 0.854 0.849) | color(display-p3 0.218 0.23 0.224) |
| `--t-color-sage7` | color(display-p3 0.8 0.811 0.806) | color(display-p3 0.269 0.285 0.277) |
| `--t-color-sage8` | color(display-p3 0.725 0.738 0.732) | color(display-p3 0.362 0.382 0.373) |
| `--t-color-sage9` | color(display-p3 0.531 0.556 0.546) | color(display-p3 0.398 0.438 0.421) |
| `--t-color-sage10` | color(display-p3 0.492 0.515 0.506) | color(display-p3 0.453 0.49 0.474) |
| `--t-color-sage11` | color(display-p3 0.377 0.395 0.389) | color(display-p3 0.685 0.709 0.697) |
| `--t-color-sage12` | color(display-p3 0.107 0.129 0.118) | color(display-p3 0.927 0.933 0.93) |

**olive**

| Token | Light | Dark |
|---|---|---|
| `--t-color-olive1` | color(display-p3 0.989 0.992 0.989) | color(display-p3 0.067 0.07 0.063) |
| `--t-color-olive2` | color(display-p3 0.974 0.98 0.973) | color(display-p3 0.095 0.098 0.091) |
| `--t-color-olive3` | color(display-p3 0.939 0.945 0.937) | color(display-p3 0.131 0.135 0.126) |
| `--t-color-olive4` | color(display-p3 0.907 0.914 0.905) | color(display-p3 0.158 0.163 0.153) |
| `--t-color-olive5` | color(display-p3 0.878 0.885 0.875) | color(display-p3 0.186 0.192 0.18) |
| `--t-color-olive6` | color(display-p3 0.846 0.855 0.843) | color(display-p3 0.221 0.229 0.215) |
| `--t-color-olive7` | color(display-p3 0.803 0.812 0.8) | color(display-p3 0.273 0.284 0.266) |
| `--t-color-olive8` | color(display-p3 0.727 0.738 0.723) | color(display-p3 0.365 0.382 0.359) |
| `--t-color-olive9` | color(display-p3 0.541 0.556 0.532) | color(display-p3 0.414 0.438 0.404) |
| `--t-color-olive10` | color(display-p3 0.5 0.515 0.491) | color(display-p3 0.467 0.49 0.458) |
| `--t-color-olive11` | color(display-p3 0.38 0.395 0.374) | color(display-p3 0.69 0.709 0.682) |
| `--t-color-olive12` | color(display-p3 0.117 0.129 0.111) | color(display-p3 0.927 0.933 0.926) |

**sand**

| Token | Light | Dark |
|---|---|---|
| `--t-color-sand1` | color(display-p3 0.992 0.992 0.989) | color(display-p3 0.067 0.067 0.063) |
| `--t-color-sand2` | color(display-p3 0.977 0.977 0.973) | color(display-p3 0.098 0.098 0.094) |
| `--t-color-sand3` | color(display-p3 0.943 0.942 0.936) | color(display-p3 0.135 0.135 0.129) |
| `--t-color-sand4` | color(display-p3 0.913 0.912 0.903) | color(display-p3 0.164 0.163 0.156) |
| `--t-color-sand5` | color(display-p3 0.885 0.883 0.873) | color(display-p3 0.193 0.192 0.183) |
| `--t-color-sand6` | color(display-p3 0.854 0.852 0.839) | color(display-p3 0.23 0.229 0.217) |
| `--t-color-sand7` | color(display-p3 0.813 0.81 0.794) | color(display-p3 0.285 0.282 0.267) |
| `--t-color-sand8` | color(display-p3 0.738 0.734 0.713) | color(display-p3 0.384 0.378 0.357) |
| `--t-color-sand9` | color(display-p3 0.553 0.553 0.528) | color(display-p3 0.434 0.428 0.403) |
| `--t-color-sand10` | color(display-p3 0.511 0.511 0.488) | color(display-p3 0.487 0.481 0.456) |
| `--t-color-sand11` | color(display-p3 0.388 0.388 0.37) | color(display-p3 0.707 0.703 0.68) |
| `--t-color-sand12` | color(display-p3 0.129 0.126 0.111) | color(display-p3 0.933 0.933 0.926) |

**tomato**

| Token | Light | Dark |
|---|---|---|
| `--t-color-tomato1` | color(display-p3 0.998 0.989 0.988) | color(display-p3 0.09 0.068 0.067) |
| `--t-color-tomato2` | color(display-p3 0.994 0.974 0.969) | color(display-p3 0.115 0.084 0.076) |
| `--t-color-tomato3` | color(display-p3 0.985 0.924 0.909) | color(display-p3 0.205 0.097 0.083) |
| `--t-color-tomato4` | color(display-p3 0.996 0.868 0.835) | color(display-p3 0.282 0.099 0.077) |
| `--t-color-tomato5` | color(display-p3 0.98 0.812 0.77) | color(display-p3 0.339 0.129 0.101) |
| `--t-color-tomato6` | color(display-p3 0.953 0.75 0.698) | color(display-p3 0.398 0.179 0.141) |
| `--t-color-tomato7` | color(display-p3 0.917 0.673 0.611) | color(display-p3 0.487 0.245 0.194) |
| `--t-color-tomato8` | color(display-p3 0.875 0.575 0.502) | color(display-p3 0.629 0.322 0.248) |
| `--t-color-tomato9` | color(display-p3 0.831 0.345 0.231) | color(display-p3 0.831 0.345 0.231) |
| `--t-color-tomato10` | color(display-p3 0.802 0.313 0.2) | color(display-p3 0.862 0.415 0.298) |
| `--t-color-tomato11` | color(display-p3 0.755 0.259 0.152) | color(display-p3 1 0.585 0.455) |
| `--t-color-tomato12` | color(display-p3 0.335 0.165 0.132) | color(display-p3 0.959 0.833 0.802) |

**ruby**

| Token | Light | Dark |
|---|---|---|
| `--t-color-ruby1` | color(display-p3 0.998 0.989 0.992) | color(display-p3 0.093 0.068 0.074) |
| `--t-color-ruby2` | color(display-p3 0.995 0.971 0.974) | color(display-p3 0.113 0.083 0.089) |
| `--t-color-ruby3` | color(display-p3 0.983 0.92 0.928) | color(display-p3 0.208 0.088 0.117) |
| `--t-color-ruby4` | color(display-p3 0.987 0.869 0.885) | color(display-p3 0.279 0.092 0.147) |
| `--t-color-ruby5` | color(display-p3 0.968 0.817 0.839) | color(display-p3 0.337 0.12 0.18) |
| `--t-color-ruby6` | color(display-p3 0.937 0.758 0.786) | color(display-p3 0.401 0.166 0.223) |
| `--t-color-ruby7` | color(display-p3 0.897 0.685 0.721) | color(display-p3 0.495 0.224 0.281) |
| `--t-color-ruby8` | color(display-p3 0.851 0.588 0.639) | color(display-p3 0.652 0.295 0.359) |
| `--t-color-ruby9` | color(display-p3 0.83 0.323 0.408) | color(display-p3 0.83 0.323 0.408) |
| `--t-color-ruby10` | color(display-p3 0.795 0.286 0.375) | color(display-p3 0.857 0.392 0.455) |
| `--t-color-ruby11` | color(display-p3 0.728 0.211 0.311) | color(display-p3 1 0.57 0.59) |
| `--t-color-ruby12` | color(display-p3 0.36 0.115 0.171) | color(display-p3 0.968 0.83 0.88) |

**crimson**

| Token | Light | Dark |
|---|---|---|
| `--t-color-crimson1` | color(display-p3 0.998 0.989 0.992) | color(display-p3 0.093 0.068 0.078) |
| `--t-color-crimson2` | color(display-p3 0.991 0.969 0.976) | color(display-p3 0.117 0.078 0.095) |
| `--t-color-crimson3` | color(display-p3 0.987 0.917 0.941) | color(display-p3 0.203 0.091 0.143) |
| `--t-color-crimson4` | color(display-p3 0.975 0.866 0.904) | color(display-p3 0.277 0.087 0.182) |
| `--t-color-crimson5` | color(display-p3 0.953 0.813 0.864) | color(display-p3 0.332 0.115 0.22) |
| `--t-color-crimson6` | color(display-p3 0.921 0.755 0.817) | color(display-p3 0.394 0.162 0.268) |
| `--t-color-crimson7` | color(display-p3 0.88 0.683 0.761) | color(display-p3 0.489 0.222 0.336) |
| `--t-color-crimson8` | color(display-p3 0.834 0.592 0.694) | color(display-p3 0.638 0.289 0.429) |
| `--t-color-crimson9` | color(display-p3 0.843 0.298 0.507) | color(display-p3 0.843 0.298 0.507) |
| `--t-color-crimson10` | color(display-p3 0.807 0.266 0.468) | color(display-p3 0.864 0.364 0.539) |
| `--t-color-crimson11` | color(display-p3 0.731 0.195 0.388) | color(display-p3 1 0.56 0.66) |
| `--t-color-crimson12` | color(display-p3 0.352 0.111 0.221) | color(display-p3 0.966 0.834 0.906) |

**plum**

| Token | Light | Dark |
|---|---|---|
| `--t-color-plum1` | color(display-p3 0.995 0.988 0.999) | color(display-p3 0.09 0.068 0.092) |
| `--t-color-plum2` | color(display-p3 0.988 0.971 0.99) | color(display-p3 0.118 0.077 0.121) |
| `--t-color-plum3` | color(display-p3 0.973 0.923 0.98) | color(display-p3 0.192 0.105 0.202) |
| `--t-color-plum4` | color(display-p3 0.953 0.875 0.966) | color(display-p3 0.25 0.121 0.271) |
| `--t-color-plum5` | color(display-p3 0.926 0.825 0.945) | color(display-p3 0.293 0.152 0.319) |
| `--t-color-plum6` | color(display-p3 0.89 0.765 0.916) | color(display-p3 0.343 0.198 0.372) |
| `--t-color-plum7` | color(display-p3 0.84 0.686 0.877) | color(display-p3 0.424 0.262 0.461) |
| `--t-color-plum8` | color(display-p3 0.775 0.58 0.832) | color(display-p3 0.54 0.341 0.595) |
| `--t-color-plum9` | color(display-p3 0.624 0.313 0.708) | color(display-p3 0.624 0.313 0.708) |
| `--t-color-plum10` | color(display-p3 0.587 0.29 0.667) | color(display-p3 0.666 0.365 0.748) |
| `--t-color-plum11` | color(display-p3 0.543 0.263 0.619) | color(display-p3 0.86 0.602 0.933) |
| `--t-color-plum12` | color(display-p3 0.299 0.114 0.352) | color(display-p3 0.936 0.836 0.949) |

**violet**

| Token | Light | Dark |
|---|---|---|
| `--t-color-violet1` | color(display-p3 0.991 0.988 0.995) | color(display-p3 0.077 0.071 0.118) |
| `--t-color-violet2` | color(display-p3 0.978 0.974 0.998) | color(display-p3 0.101 0.084 0.141) |
| `--t-color-violet3` | color(display-p3 0.953 0.943 0.993) | color(display-p3 0.154 0.123 0.256) |
| `--t-color-violet4` | color(display-p3 0.916 0.897 1) | color(display-p3 0.191 0.148 0.345) |
| `--t-color-violet5` | color(display-p3 0.876 0.851 1) | color(display-p3 0.226 0.182 0.396) |
| `--t-color-violet6` | color(display-p3 0.825 0.793 0.981) | color(display-p3 0.269 0.223 0.449) |
| `--t-color-violet7` | color(display-p3 0.752 0.712 0.943) | color(display-p3 0.326 0.277 0.53) |
| `--t-color-violet8` | color(display-p3 0.654 0.602 0.902) | color(display-p3 0.399 0.346 0.656) |
| `--t-color-violet9` | color(display-p3 0.417 0.341 0.784) | color(display-p3 0.417 0.341 0.784) |
| `--t-color-violet10` | color(display-p3 0.381 0.306 0.741) | color(display-p3 0.477 0.402 0.823) |
| `--t-color-violet11` | color(display-p3 0.383 0.317 0.702) | color(display-p3 0.72 0.65 1) |
| `--t-color-violet12` | color(display-p3 0.179 0.15 0.359) | color(display-p3 0.883 0.867 0.986) |

**iris**

| Token | Light | Dark |
|---|---|---|
| `--t-color-iris1` | color(display-p3 0.992 0.992 0.999) | color(display-p3 0.075 0.075 0.114) |
| `--t-color-iris2` | color(display-p3 0.972 0.973 0.998) | color(display-p3 0.089 0.086 0.14) |
| `--t-color-iris3` | color(display-p3 0.943 0.945 0.992) | color(display-p3 0.128 0.134 0.272) |
| `--t-color-iris4` | color(display-p3 0.902 0.906 1) | color(display-p3 0.153 0.165 0.382) |
| `--t-color-iris5` | color(display-p3 0.857 0.861 1) | color(display-p3 0.192 0.201 0.44) |
| `--t-color-iris6` | color(display-p3 0.799 0.805 0.987) | color(display-p3 0.239 0.241 0.491) |
| `--t-color-iris7` | color(display-p3 0.721 0.727 0.955) | color(display-p3 0.291 0.289 0.565) |
| `--t-color-iris8` | color(display-p3 0.61 0.619 0.918) | color(display-p3 0.35 0.345 0.673) |
| `--t-color-iris9` | color(display-p3 0.357 0.357 0.81) | color(display-p3 0.357 0.357 0.81) |
| `--t-color-iris10` | color(display-p3 0.318 0.318 0.774) | color(display-p3 0.428 0.416 0.843) |
| `--t-color-iris11` | color(display-p3 0.337 0.326 0.748) | color(display-p3 0.685 0.662 1) |
| `--t-color-iris12` | color(display-p3 0.154 0.161 0.371) | color(display-p3 0.878 0.875 0.986) |

**cyan**

| Token | Light | Dark |
|---|---|---|
| `--t-color-cyan1` | color(display-p3 0.982 0.992 0.996) | color(display-p3 0.053 0.085 0.098) |
| `--t-color-cyan2` | color(display-p3 0.955 0.981 0.984) | color(display-p3 0.072 0.105 0.122) |
| `--t-color-cyan3` | color(display-p3 0.888 0.965 0.975) | color(display-p3 0.073 0.168 0.209) |
| `--t-color-cyan4` | color(display-p3 0.821 0.941 0.959) | color(display-p3 0.063 0.216 0.277) |
| `--t-color-cyan5` | color(display-p3 0.751 0.907 0.935) | color(display-p3 0.091 0.267 0.336) |
| `--t-color-cyan6` | color(display-p3 0.671 0.862 0.9) | color(display-p3 0.137 0.324 0.4) |
| `--t-color-cyan7` | color(display-p3 0.564 0.8 0.854) | color(display-p3 0.186 0.398 0.484) |
| `--t-color-cyan8` | color(display-p3 0.388 0.715 0.798) | color(display-p3 0.23 0.496 0.6) |
| `--t-color-cyan9` | color(display-p3 0.282 0.627 0.765) | color(display-p3 0.282 0.627 0.765) |
| `--t-color-cyan10` | color(display-p3 0.264 0.583 0.71) | color(display-p3 0.331 0.675 0.801) |
| `--t-color-cyan11` | color(display-p3 0.08 0.48 0.63) | color(display-p3 0.446 0.79 0.887) |
| `--t-color-cyan12` | color(display-p3 0.108 0.232 0.277) | color(display-p3 0.757 0.919 0.962) |

**jade**

| Token | Light | Dark |
|---|---|---|
| `--t-color-jade1` | color(display-p3 0.986 0.996 0.992) | color(display-p3 0.059 0.083 0.071) |
| `--t-color-jade2` | color(display-p3 0.962 0.983 0.969) | color(display-p3 0.078 0.11 0.094) |
| `--t-color-jade3` | color(display-p3 0.912 0.965 0.932) | color(display-p3 0.091 0.176 0.138) |
| `--t-color-jade4` | color(display-p3 0.858 0.941 0.893) | color(display-p3 0.102 0.228 0.177) |
| `--t-color-jade5` | color(display-p3 0.795 0.909 0.847) | color(display-p3 0.133 0.279 0.221) |
| `--t-color-jade6` | color(display-p3 0.715 0.864 0.791) | color(display-p3 0.174 0.334 0.273) |
| `--t-color-jade7` | color(display-p3 0.603 0.802 0.718) | color(display-p3 0.219 0.402 0.335) |
| `--t-color-jade8` | color(display-p3 0.44 0.72 0.629) | color(display-p3 0.263 0.488 0.411) |
| `--t-color-jade9` | color(display-p3 0.319 0.63 0.521) | color(display-p3 0.319 0.63 0.521) |
| `--t-color-jade10` | color(display-p3 0.299 0.592 0.488) | color(display-p3 0.338 0.68 0.555) |
| `--t-color-jade11` | color(display-p3 0.15 0.5 0.37) | color(display-p3 0.4 0.835 0.656) |
| `--t-color-jade12` | color(display-p3 0.142 0.229 0.194) | color(display-p3 0.734 0.934 0.838) |

**grass**

| Token | Light | Dark |
|---|---|---|
| `--t-color-grass1` | color(display-p3 0.986 0.996 0.985) | color(display-p3 0.062 0.083 0.067) |
| `--t-color-grass2` | color(display-p3 0.966 0.983 0.964) | color(display-p3 0.083 0.103 0.085) |
| `--t-color-grass3` | color(display-p3 0.923 0.965 0.917) | color(display-p3 0.118 0.163 0.122) |
| `--t-color-grass4` | color(display-p3 0.872 0.94 0.865) | color(display-p3 0.142 0.225 0.15) |
| `--t-color-grass5` | color(display-p3 0.811 0.908 0.802) | color(display-p3 0.178 0.279 0.186) |
| `--t-color-grass6` | color(display-p3 0.733 0.864 0.724) | color(display-p3 0.217 0.337 0.224) |
| `--t-color-grass7` | color(display-p3 0.628 0.803 0.622) | color(display-p3 0.258 0.4 0.264) |
| `--t-color-grass8` | color(display-p3 0.477 0.72 0.482) | color(display-p3 0.302 0.47 0.305) |
| `--t-color-grass9` | color(display-p3 0.38 0.647 0.378) | color(display-p3 0.38 0.647 0.378) |
| `--t-color-grass10` | color(display-p3 0.344 0.598 0.342) | color(display-p3 0.426 0.694 0.426) |
| `--t-color-grass11` | color(display-p3 0.263 0.488 0.261) | color(display-p3 0.535 0.807 0.542) |
| `--t-color-grass12` | color(display-p3 0.151 0.233 0.153) | color(display-p3 0.797 0.936 0.776) |

**mint**

| Token | Light | Dark |
|---|---|---|
| `--t-color-mint1` | color(display-p3 0.98 0.995 0.992) | color(display-p3 0.059 0.082 0.081) |
| `--t-color-mint2` | color(display-p3 0.957 0.985 0.977) | color(display-p3 0.068 0.104 0.105) |
| `--t-color-mint3` | color(display-p3 0.888 0.972 0.95) | color(display-p3 0.077 0.17 0.168) |
| `--t-color-mint4` | color(display-p3 0.819 0.951 0.916) | color(display-p3 0.068 0.224 0.22) |
| `--t-color-mint5` | color(display-p3 0.747 0.918 0.873) | color(display-p3 0.104 0.275 0.264) |
| `--t-color-mint6` | color(display-p3 0.668 0.87 0.818) | color(display-p3 0.154 0.332 0.313) |
| `--t-color-mint7` | color(display-p3 0.567 0.805 0.744) | color(display-p3 0.207 0.403 0.373) |
| `--t-color-mint8` | color(display-p3 0.42 0.724 0.649) | color(display-p3 0.258 0.49 0.441) |
| `--t-color-mint9` | color(display-p3 0.62 0.908 0.834) | color(display-p3 0.62 0.908 0.834) |
| `--t-color-mint10` | color(display-p3 0.585 0.871 0.797) | color(display-p3 0.725 0.954 0.898) |
| `--t-color-mint11` | color(display-p3 0.203 0.463 0.397) | color(display-p3 0.482 0.825 0.733) |
| `--t-color-mint12` | color(display-p3 0.136 0.259 0.236) | color(display-p3 0.807 0.955 0.887) |

**lime**

| Token | Light | Dark |
|---|---|---|
| `--t-color-lime1` | color(display-p3 0.989 0.992 0.981) | color(display-p3 0.067 0.073 0.048) |
| `--t-color-lime2` | color(display-p3 0.975 0.98 0.954) | color(display-p3 0.086 0.1 0.067) |
| `--t-color-lime3` | color(display-p3 0.939 0.965 0.851) | color(display-p3 0.13 0.16 0.099) |
| `--t-color-lime4` | color(display-p3 0.896 0.94 0.76) | color(display-p3 0.172 0.214 0.126) |
| `--t-color-lime5` | color(display-p3 0.843 0.903 0.678) | color(display-p3 0.213 0.266 0.153) |
| `--t-color-lime6` | color(display-p3 0.778 0.852 0.599) | color(display-p3 0.257 0.321 0.182) |
| `--t-color-lime7` | color(display-p3 0.694 0.784 0.508) | color(display-p3 0.307 0.383 0.215) |
| `--t-color-lime8` | color(display-p3 0.585 0.707 0.378) | color(display-p3 0.365 0.456 0.25) |
| `--t-color-lime9` | color(display-p3 0.78 0.928 0.466) | color(display-p3 0.78 0.928 0.466) |
| `--t-color-lime10` | color(display-p3 0.734 0.896 0.397) | color(display-p3 0.865 0.995 0.519) |
| `--t-color-lime11` | color(display-p3 0.386 0.482 0.227) | color(display-p3 0.771 0.893 0.485) |
| `--t-color-lime12` | color(display-p3 0.222 0.25 0.128) | color(display-p3 0.905 0.966 0.753) |

**bronze**

| Token | Light | Dark |
|---|---|---|
| `--t-color-bronze1` | color(display-p3 0.991 0.988 0.988) | color(display-p3 0.076 0.067 0.063) |
| `--t-color-bronze2` | color(display-p3 0.989 0.97 0.961) | color(display-p3 0.106 0.097 0.093) |
| `--t-color-bronze3` | color(display-p3 0.958 0.932 0.919) | color(display-p3 0.147 0.132 0.125) |
| `--t-color-bronze4` | color(display-p3 0.929 0.894 0.877) | color(display-p3 0.185 0.166 0.156) |
| `--t-color-bronze5` | color(display-p3 0.898 0.853 0.832) | color(display-p3 0.227 0.202 0.19) |
| `--t-color-bronze6` | color(display-p3 0.861 0.805 0.778) | color(display-p3 0.278 0.246 0.23) |
| `--t-color-bronze7` | color(display-p3 0.812 0.739 0.706) | color(display-p3 0.343 0.302 0.281) |
| `--t-color-bronze8` | color(display-p3 0.741 0.647 0.606) | color(display-p3 0.426 0.374 0.347) |
| `--t-color-bronze9` | color(display-p3 0.611 0.507 0.455) | color(display-p3 0.611 0.507 0.455) |
| `--t-color-bronze10` | color(display-p3 0.563 0.461 0.414) | color(display-p3 0.66 0.556 0.504) |
| `--t-color-bronze11` | color(display-p3 0.471 0.373 0.336) | color(display-p3 0.81 0.707 0.655) |
| `--t-color-bronze12` | color(display-p3 0.251 0.191 0.172) | color(display-p3 0.921 0.88 0.854) |

**gold**

| Token | Light | Dark |
|---|---|---|
| `--t-color-gold1` | color(display-p3 0.992 0.992 0.989) | color(display-p3 0.071 0.071 0.067) |
| `--t-color-gold2` | color(display-p3 0.98 0.976 0.953) | color(display-p3 0.104 0.101 0.09) |
| `--t-color-gold3` | color(display-p3 0.947 0.94 0.909) | color(display-p3 0.141 0.136 0.122) |
| `--t-color-gold4` | color(display-p3 0.914 0.904 0.865) | color(display-p3 0.177 0.17 0.152) |
| `--t-color-gold5` | color(display-p3 0.88 0.865 0.816) | color(display-p3 0.217 0.207 0.185) |
| `--t-color-gold6` | color(display-p3 0.84 0.818 0.756) | color(display-p3 0.265 0.252 0.225) |
| `--t-color-gold7` | color(display-p3 0.788 0.753 0.677) | color(display-p3 0.327 0.31 0.277) |
| `--t-color-gold8` | color(display-p3 0.715 0.66 0.565) | color(display-p3 0.407 0.384 0.342) |
| `--t-color-gold9` | color(display-p3 0.579 0.517 0.41) | color(display-p3 0.579 0.517 0.41) |
| `--t-color-gold10` | color(display-p3 0.538 0.479 0.38) | color(display-p3 0.628 0.566 0.463) |
| `--t-color-gold11` | color(display-p3 0.433 0.386 0.305) | color(display-p3 0.784 0.728 0.635) |
| `--t-color-gold12` | color(display-p3 0.227 0.209 0.173) | color(display-p3 0.906 0.887 0.855) |

**brown**

| Token | Light | Dark |
|---|---|---|
| `--t-color-brown1` | color(display-p3 0.995 0.992 0.989) | color(display-p3 0.071 0.067 0.059) |
| `--t-color-brown2` | color(display-p3 0.987 0.976 0.964) | color(display-p3 0.107 0.095 0.087) |
| `--t-color-brown3` | color(display-p3 0.959 0.936 0.909) | color(display-p3 0.151 0.13 0.115) |
| `--t-color-brown4` | color(display-p3 0.934 0.897 0.855) | color(display-p3 0.191 0.161 0.138) |
| `--t-color-brown5` | color(display-p3 0.909 0.856 0.798) | color(display-p3 0.235 0.194 0.162) |
| `--t-color-brown6` | color(display-p3 0.88 0.808 0.73) | color(display-p3 0.291 0.237 0.192) |
| `--t-color-brown7` | color(display-p3 0.841 0.742 0.639) | color(display-p3 0.365 0.295 0.232) |
| `--t-color-brown8` | color(display-p3 0.782 0.647 0.514) | color(display-p3 0.469 0.377 0.287) |
| `--t-color-brown9` | color(display-p3 0.651 0.505 0.368) | color(display-p3 0.651 0.505 0.368) |
| `--t-color-brown10` | color(display-p3 0.601 0.465 0.344) | color(display-p3 0.697 0.557 0.423) |
| `--t-color-brown11` | color(display-p3 0.485 0.374 0.288) | color(display-p3 0.835 0.715 0.597) |
| `--t-color-brown12` | color(display-p3 0.236 0.202 0.183) | color(display-p3 0.938 0.885 0.802) |

**amber**

| Token | Light | Dark |
|---|---|---|
| `--t-color-amber1` | color(display-p3 0.995 0.992 0.985) | color(display-p3 0.082 0.07 0.05) |
| `--t-color-amber2` | color(display-p3 0.994 0.986 0.921) | color(display-p3 0.111 0.094 0.064) |
| `--t-color-amber3` | color(display-p3 0.994 0.969 0.782) | color(display-p3 0.178 0.128 0.049) |
| `--t-color-amber4` | color(display-p3 0.989 0.937 0.65) | color(display-p3 0.239 0.156 0) |
| `--t-color-amber5` | color(display-p3 0.97 0.902 0.527) | color(display-p3 0.29 0.193 0) |
| `--t-color-amber6` | color(display-p3 0.936 0.844 0.506) | color(display-p3 0.344 0.245 0.076) |
| `--t-color-amber7` | color(display-p3 0.89 0.762 0.443) | color(display-p3 0.422 0.314 0.141) |
| `--t-color-amber8` | color(display-p3 0.85 0.65 0.3) | color(display-p3 0.535 0.399 0.189) |
| `--t-color-amber9` | color(display-p3 1 0.77 0.26) | color(display-p3 1 0.77 0.26) |
| `--t-color-amber10` | color(display-p3 0.959 0.741 0.274) | color(display-p3 1 0.87 0.15) |
| `--t-color-amber11` | color(display-p3 0.64 0.4 0) | color(display-p3 1 0.8 0.29) |
| `--t-color-amber12` | color(display-p3 0.294 0.208 0.145) | color(display-p3 0.984 0.909 0.726) |

### 2.9 Tag colours

The most product-specific part of the palette: every `ThemeColor` plus `mauve/slate/sage/olive/
sand` gets a text/background pair, always step 11 over step 3 of its family
(`TagLight.ts:4-…`). 30 pairs.

**Tag text:**

| Token | Light | Dark |
|---|---|---|
| `--t-tag-text-gray` | color(display-p3 0.4 0.4 0.4) | color(display-p3 0.702 0.702 0.702) |
| `--t-tag-text-mauve` | color(display-p3 0.395 0.388 0.424) | color(display-p3 0.707 0.7 0.735) |
| `--t-tag-text-slate` | color(display-p3 0.379 0.392 0.421) | color(display-p3 0.692 0.704 0.728) |
| `--t-tag-text-sage` | color(display-p3 0.377 0.395 0.389) | color(display-p3 0.685 0.709 0.697) |
| `--t-tag-text-olive` | color(display-p3 0.38 0.395 0.374) | color(display-p3 0.69 0.709 0.682) |
| `--t-tag-text-sand` | color(display-p3 0.388 0.388 0.37) | color(display-p3 0.707 0.703 0.68) |
| `--t-tag-text-tomato` | color(display-p3 0.755 0.259 0.152) | color(display-p3 1 0.585 0.455) |
| `--t-tag-text-red` | color(display-p3 0.744 0.234 0.222) | color(display-p3 1 0.57 0.55) |
| `--t-tag-text-ruby` | color(display-p3 0.728 0.211 0.311) | color(display-p3 1 0.57 0.59) |
| `--t-tag-text-crimson` | color(display-p3 0.731 0.195 0.388) | color(display-p3 1 0.56 0.66) |
| `--t-tag-text-pink` | color(display-p3 0.698 0.219 0.528) | color(display-p3 1 0.535 0.78) |
| `--t-tag-text-plum` | color(display-p3 0.543 0.263 0.619) | color(display-p3 0.86 0.602 0.933) |
| `--t-tag-text-purple` | color(display-p3 0.473 0.281 0.687) | color(display-p3 0.8 0.62 1) |
| `--t-tag-text-violet` | color(display-p3 0.383 0.317 0.702) | color(display-p3 0.72 0.65 1) |
| `--t-tag-text-iris` | color(display-p3 0.337 0.326 0.748) | color(display-p3 0.685 0.662 1) |
| `--t-tag-text-cyan` | color(display-p3 0.08 0.48 0.63) | color(display-p3 0.446 0.79 0.887) |
| `--t-tag-text-turquoise` | color(display-p3 0.08 0.5 0.43) | color(display-p3 0.388 0.835 0.719) |
| `--t-tag-text-sky` | color(display-p3 0.193 0.448 0.605) | color(display-p3 0.536 0.772 0.924) |
| `--t-tag-text-blue` | color(display-p3 0.256 0.354 0.755) | color(display-p3 0.63 0.69 1) |
| `--t-tag-text-jade` | color(display-p3 0.15 0.5 0.37) | color(display-p3 0.4 0.835 0.656) |
| `--t-tag-text-green` | color(display-p3 0.19 0.5 0.32) | color(display-p3 0.434 0.828 0.573) |
| `--t-tag-text-grass` | color(display-p3 0.263 0.488 0.261) | color(display-p3 0.535 0.807 0.542) |
| `--t-tag-text-mint` | color(display-p3 0.203 0.463 0.397) | color(display-p3 0.482 0.825 0.733) |
| `--t-tag-text-lime` | color(display-p3 0.386 0.482 0.227) | color(display-p3 0.771 0.893 0.485) |
| `--t-tag-text-bronze` | color(display-p3 0.471 0.373 0.336) | color(display-p3 0.81 0.707 0.655) |
| `--t-tag-text-gold` | color(display-p3 0.433 0.386 0.305) | color(display-p3 0.784 0.728 0.635) |
| `--t-tag-text-brown` | color(display-p3 0.485 0.374 0.288) | color(display-p3 0.835 0.715 0.597) |
| `--t-tag-text-orange` | color(display-p3 0.76 0.34 0) | color(display-p3 1 0.63 0.38) |
| `--t-tag-text-amber` | color(display-p3 0.64 0.4 0) | color(display-p3 1 0.8 0.29) |
| `--t-tag-text-yellow` | color(display-p3 0.6 0.44 0) | color(display-p3 0.948 0.885 0.392) |

**Tag background:**

| Token | Light | Dark |
|---|---|---|
| `--t-tag-background-gray` | color(display-p3 0.976 0.976 0.976) | color(display-p3 0.098 0.098 0.098) |
| `--t-tag-background-mauve` | color(display-p3 0.946 0.938 0.952) | color(display-p3 0.138 0.134 0.144) |
| `--t-tag-background-slate` | color(display-p3 0.94 0.941 0.953) | color(display-p3 0.13 0.135 0.145) |
| `--t-tag-background-sage` | color(display-p3 0.935 0.944 0.94) | color(display-p3 0.128 0.135 0.131) |
| `--t-tag-background-olive` | color(display-p3 0.939 0.945 0.937) | color(display-p3 0.131 0.135 0.126) |
| `--t-tag-background-sand` | color(display-p3 0.943 0.942 0.936) | color(display-p3 0.135 0.135 0.129) |
| `--t-tag-background-tomato` | color(display-p3 0.985 0.924 0.909) | color(display-p3 0.205 0.097 0.083) |
| `--t-tag-background-red` | color(display-p3 0.985 0.925 0.925) | color(display-p3 0.211 0.081 0.099) |
| `--t-tag-background-ruby` | color(display-p3 0.983 0.92 0.928) | color(display-p3 0.208 0.088 0.117) |
| `--t-tag-background-crimson` | color(display-p3 0.987 0.917 0.941) | color(display-p3 0.203 0.091 0.143) |
| `--t-tag-background-pink` | color(display-p3 0.981 0.917 0.96) | color(display-p3 0.198 0.098 0.179) |
| `--t-tag-background-plum` | color(display-p3 0.973 0.923 0.98) | color(display-p3 0.192 0.105 0.202) |
| `--t-tag-background-purple` | color(display-p3 0.963 0.931 0.989) | color(display-p3 0.175 0.112 0.224) |
| `--t-tag-background-violet` | color(display-p3 0.953 0.943 0.993) | color(display-p3 0.154 0.123 0.256) |
| `--t-tag-background-iris` | color(display-p3 0.943 0.945 0.992) | color(display-p3 0.128 0.134 0.272) |
| `--t-tag-background-cyan` | color(display-p3 0.888 0.965 0.975) | color(display-p3 0.073 0.168 0.209) |
| `--t-tag-background-turquoise` | color(display-p3 0.895 0.971 0.952) | color(display-p3 0.087 0.175 0.165) |
| `--t-tag-background-sky` | color(display-p3 0.899 0.963 0.989) | color(display-p3 0.089 0.154 0.244) |
| `--t-tag-background-blue` | color(display-p3 0.933 0.948 0.992) | color(display-p3 0.105 0.141 0.275) |
| `--t-tag-background-jade` | color(display-p3 0.912 0.965 0.932) | color(display-p3 0.091 0.176 0.138) |
| `--t-tag-background-green` | color(display-p3 0.913 0.964 0.925) | color(display-p3 0.1 0.173 0.133) |
| `--t-tag-background-grass` | color(display-p3 0.923 0.965 0.917) | color(display-p3 0.118 0.163 0.122) |
| `--t-tag-background-mint` | color(display-p3 0.888 0.972 0.95) | color(display-p3 0.077 0.17 0.168) |
| `--t-tag-background-lime` | color(display-p3 0.939 0.965 0.851) | color(display-p3 0.13 0.16 0.099) |
| `--t-tag-background-bronze` | color(display-p3 0.958 0.932 0.919) | color(display-p3 0.147 0.132 0.125) |
| `--t-tag-background-gold` | color(display-p3 0.947 0.94 0.909) | color(display-p3 0.141 0.136 0.122) |
| `--t-tag-background-brown` | color(display-p3 0.959 0.936 0.909) | color(display-p3 0.151 0.13 0.115) |
| `--t-tag-background-orange` | color(display-p3 0.989 0.938 0.85) | color(display-p3 0.189 0.12 0.056) |
| `--t-tag-background-amber` | color(display-p3 0.994 0.969 0.782) | color(display-p3 0.178 0.128 0.049) |
| `--t-tag-background-yellow` | color(display-p3 0.997 0.982 0.749) | color(display-p3 0.168 0.137 0.039) |

### 2.10 Structural differences between light and dark

The two themes are token-for-token identical in **shape**: 994 keys each, no key in one and absent
from the other. Where they genuinely diverge:

1. **Shadows** — different composition and a different `superHeavy` recipe (see §2.6). Light uses
   P3 alpha, dark uses `rgba()`.
2. **Overlays** — light `background.overlay*` derive from the transparent gray ramp; dark
   hard-codes `#000000b8` / `#0000005c`, and `overlaySecondary` and `overlayTertiary` are the
   *same value* in dark but different in light (`packages/twenty-ui/src/theme/constants/BackgroundDark.ts:28-30` vs
   `packages/twenty-ui/src/theme/constants/BackgroundLight.ts:28-30`).
3. **Transparent tints** — light aliases `blue3/orange3/green3`, dark aliases `blue4/orange4/green4`
   (`packages/twenty-ui/src/theme/constants/BackgroundLight.ts:24-26` vs `packages/twenty-ui/src/theme/constants/BackgroundDark.ts:24-26`).
4. **The `gray` record colour** — `gray9` light, `gray7` dark.
5. **Frosted surfaces** — `background.transparent.primary/secondary` is white-alpha in light
   (Radix `whiteP3A`) and black-alpha in dark (`blackP3A`), so the same overlay reads as a
   lightening scrim in light and a darkening one in dark.
6. **`--t-buttons-secondary-text-color`** is `color(display-p3 0.63 0.69 1)` in **both** themes,
   because `packages/twenty-ui/src/theme/constants/ThemeCommon.ts:25` pins it to `ACCENT_DARK.accent11` unconditionally — the dark accent
   leaks into the light theme by design.

---

## 3 · Typography

### Families

| Role | Value | Source |
|---|---|---|
| UI | `Inter, sans-serif` | `packages/twenty-ui/src/theme/constants/FontCommon.ts:16` → `--t-font-family` (`packages/twenty-ui/src/theme-constants/theme-light.css:175`) |
| Body element | `'Inter', sans-serif` | `packages/twenty-front/src/index.css:3` |
| Code / syntax | `DM Mono` — **no fallback declared** | `packages/twenty-ui/src/theme/constants/CodeLight.ts:11` → `--t-code-font-family` (`packages/twenty-ui/src/theme-constants/theme-light.css:252`) |
| Monospace (app-side) | `'SF Mono', 'Monaco', 'Inconsolata', 'Roboto Mono', monospace` | `packages/twenty-front/src/modules/ui/theme/constants/MonospaceFontFamily.ts:1` |

Weights loaded from `@fontsource` at boot (`packages/twenty-front/src/index.tsx:7-12`): DM Mono
400 and 500; Inter 400, 500, 600 and 700.

### Scale

Written in `rem` in the source (`packages/twenty-ui/src/theme/constants/FontCommon.ts:2-10`). Against the 13px root
(`packages/twenty-front/src/index.css:12`) the computed pixel values are as shown — **the px column is arithmetic, not a
value present in the source**.

| Token | CSS variable | Source value | Computes to (13px root) |
|---|---|---|---|
| `font.size.xxs` | `--t-font-size-xxs` | `0.625rem` | 8.125px |
| `font.size.xs` | `--t-font-size-xs` | `0.85rem` | 11.05px |
| `font.size.sm` | `--t-font-size-sm` | `0.92rem` | 11.96px |
| `font.size.md` | `--t-font-size-md` | `1rem` | 13px |
| `font.size.lg` | `--t-font-size-lg` | `1.23rem` | 15.99px |
| `font.size.xl` | `--t-font-size-xl` | `1.54rem` | 20.02px |
| `font.size.xxl` | `--t-font-size-xxl` | `1.85rem` | 24.05px |

`md` (13px) is the workhorse — it is the size of buttons, tags, chips, table cells and menu item
labels. `sm` is used for menu-item containers and secondary descriptions.

### Weights

| Token | Value | Source |
|---|---|---|
| `font.weight.regular` | `400` | `packages/twenty-ui/src/theme/constants/FontCommon.ts:12` |
| `font.weight.medium` | `500` | `packages/twenty-ui/src/theme/constants/FontCommon.ts:13` |
| `font.weight.semiBold` | `600` | `packages/twenty-ui/src/theme/constants/FontCommon.ts:14` |

Inter 700 is loaded but there is no `bold` token; the SCSS/Linaria layer never asks for 700.
`packages/twenty-ui/src/input/Button/Button.module.scss:44` writes `font-weight: 500` as a literal rather than through the token.

### Line height and letter spacing

| Token | Value | Source |
|---|---|---|
| `text.lineHeight.md` | `1.1` | `packages/twenty-ui/src/theme/constants/Text.ts:3` → `--t-text-line-height-md` |
| `text.lineHeight.lg` | `1.5` | `packages/twenty-ui/src/theme/constants/Text.ts:4` → `--t-text-line-height-lg` |

**There is no letter-spacing token anywhere in the theme.** No `letterSpacing`, `tracking` or
`letter-spacing` key exists in any of the 994 tokens.

### Named text styles

These are the only pre-composed type styles in the library.

| Component | Size | Weight | Colour | Line height | Other | Source |
|---|---|---|---|---|---|---|
| `H1Title` | `--t-font-size-lg` | semi-bold | `primary` \| `secondary` \| `tertiary` (prop) | `--t-text-line-height-md` | `margin-bottom: 16px` | `packages/twenty-ui/src/typography/H1Title/H1Title.module.scss:1-19` |
| `H2Title` title | `--t-font-size-md` | semi-bold | `font.color.primary` | — | container `margin-bottom: 16px` | `packages/twenty-ui/src/typography/H2Title/H2Title.module.scss:13-18` |
| `H2Title` description | `--t-font-size-md` | regular | `font.color.tertiary` | `--t-text-line-height-lg` | `margin-top: 8px` | `packages/twenty-ui/src/typography/H2Title/H2Title.module.scss:20-27` |
| `H3Title` title | `--t-font-size-lg` | semi-bold | `font.color.primary` | — | | `packages/twenty-ui/src/typography/H3Title/H3Title.module.scss:6-11` |
| `H3Title` description | `--t-font-size-md` | regular | `font.color.tertiary` | — | `margin-top: 8px` | `packages/twenty-ui/src/typography/H3Title/H3Title.module.scss:13-19` |
| `Label` default | **`11px` literal** | semi-bold | `font.color.light` | — | | `packages/twenty-ui/src/typography/Label/Label.module.scss:1-8` |
| `Label` small | **`9px` literal** | semi-bold | `font.color.light` | — | | `packages/twenty-ui/src/typography/Label/Label.module.scss:10-12` |
| `SeparatorLineText` | `--t-font-size-md` | semi-bold | `font.color.extraLight` | — | 1px rules either side, 16px gap | `packages/twenty-ui/src/typography/SeparatorLineText/SeparatorLineText.module.scss:1-24` |
| `StyledText` content | `--t-font-size-sm` | regular | inherited | — | `nowrap`, `overflow: hidden` | `packages/twenty-ui/src/typography/StyledText/StyledText.module.scss:1-9` |

The heading ladder does not descend: `H1Title` and `H3Title` are both `lg` (15.99px) while
`H2Title` is `md` (13px), so H2 renders *smaller* than H3. That is what the source says. See §11.

`Label`'s 11px and 9px are the only type sizes in the library that bypass the scale entirely.

---

## 4 · Space and size

### 4.1 The spacing scale

Base unit **4px**, exposed as `--t-spacing-multiplicator: 4` (`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:12`). The ladder is
pre-expanded in the CSS from `0` to `32` in whole steps, plus two half-steps
(`packages/twenty-ui/src/theme-constants/theme-light.css:31-65`; values identical in dark).

| Accessor | CSS variable | Value |
|---|---|---|
| `spacing['0']` | `--t-spacing-0` | `0px` |
| `spacing['0.5']` | `--t-spacing-0_5` | `2px` |
| `spacing['1']` | `--t-spacing-1` | `4px` |
| `spacing['1.5']` | `--t-spacing-1_5` | `6px` |
| `spacing['2']` | `--t-spacing-2` | `8px` |
| `spacing['3']` | `--t-spacing-3` | `12px` |
| `spacing['4']` | `--t-spacing-4` | `16px` |
| `spacing['5']` | `--t-spacing-5` | `20px` |
| `spacing['6']` | `--t-spacing-6` | `24px` |
| `spacing['7']` | `--t-spacing-7` | `28px` |
| `spacing['8']` | `--t-spacing-8` | `32px` |
| `spacing['9']` … `spacing['32']` | `--t-spacing-9` … `--t-spacing-32` | `36px` … `128px`, +4px per step |

Full ladder, verbatim:

| Token | Light | Dark |
|---|---|---|
| `--t-spacing-0` | 0px | 0px |
| `--t-spacing-1` | 4px | 4px |
| `--t-spacing-2` | 8px | 8px |
| `--t-spacing-3` | 12px | 12px |
| `--t-spacing-4` | 16px | 16px |
| `--t-spacing-5` | 20px | 20px |
| `--t-spacing-6` | 24px | 24px |
| `--t-spacing-7` | 28px | 28px |
| `--t-spacing-8` | 32px | 32px |
| `--t-spacing-9` | 36px | 36px |
| `--t-spacing-10` | 40px | 40px |
| `--t-spacing-11` | 44px | 44px |
| `--t-spacing-12` | 48px | 48px |
| `--t-spacing-13` | 52px | 52px |
| `--t-spacing-14` | 56px | 56px |
| `--t-spacing-15` | 60px | 60px |
| `--t-spacing-16` | 64px | 64px |
| `--t-spacing-17` | 68px | 68px |
| `--t-spacing-18` | 72px | 72px |
| `--t-spacing-19` | 76px | 76px |
| `--t-spacing-20` | 80px | 80px |
| `--t-spacing-21` | 84px | 84px |
| `--t-spacing-22` | 88px | 88px |
| `--t-spacing-23` | 92px | 92px |
| `--t-spacing-24` | 96px | 96px |
| `--t-spacing-25` | 100px | 100px |
| `--t-spacing-26` | 104px | 104px |
| `--t-spacing-27` | 108px | 108px |
| `--t-spacing-28` | 112px | 112px |
| `--t-spacing-29` | 116px | 116px |
| `--t-spacing-30` | 120px | 120px |
| `--t-spacing-31` | 124px | 124px |
| `--t-spacing-32` | 128px | 128px |
| `--t-spacing-0_5` | 2px | 2px |
| `--t-spacing-1_5` | 6px | 6px |

Note the dot notation on the accessor (`spacing['0.5']`) versus the underscore in the variable
name (`--t-spacing-0_5`) — a `.` is not legal in a custom-property identifier
(`packages/twenty-ui/src/theme-constants/themeCssVariables.ts:92-93`).

One more spacing-adjacent token: `--t-between-siblings-gap: 2px` (`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:15`), the gap
used between adjacent items in tight vertical lists. 10 call sites.

### 4.2 Control heights

Almost everything is a multiple of 4 landing on **32px** (the master row height) or **24px**.

| Control | Size | Height | Source |
|---|---|---|---|
| Button | `small` | `24px` | `packages/twenty-ui/src/input/Button/Button.module.scss:72-74` |
| Button | `medium` (default) | `32px` | `packages/twenty-ui/src/input/Button/Button.module.scss:76-78` |
| TextInput | `xs` | `20px` | `packages/twenty-front/src/modules/ui/input/components/TextInput.tsx:416-418` |
| TextInput | `sm` | `24px` | `packages/twenty-front/src/modules/ui/input/components/TextInput.tsx:419-421` |
| TextInput | `md` | `28px` | `packages/twenty-front/src/modules/ui/input/components/TextInput.tsx:422-424` |
| TextInput | `lg` | `32px` | `packages/twenty-front/src/modules/ui/input/components/TextInput.tsx:425-427` |
| Record table row / cell | — | `32px` | `packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableRowHeight.ts:1`; `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx:23` |
| Record table header cell | — | `32px` (`height` and `max-height`) | `packages/twenty-front/src/modules/object-record/record-table/record-table-header/components/RecordTableHeaderCellContainer.tsx:22-24` |
| MenuItem | — | `32px` total: `content-box` height `calc(32px - 2 × 8px)` + 8px vertical padding | `packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:5,16-18` |
| Tag | — | `var(--t-spacing-5)` = `20px`, `box-sizing: content-box` | `packages/twenty-ui/src/data-display/Tag/Tag.module.scss:2,12` |
| Chip | `large` | `var(--t-spacing-4)` = `16px` content + 4px padding | `packages/twenty-ui/src/data-display/Chip/Chip.module.scss:28-30` |
| Chip | `small` (default) | `var(--t-spacing-3)` = `12px` content + 4px padding | `packages/twenty-ui/src/data-display/Chip/Chip.module.scss:32-34` |
| Toggle | `small` | `24 × 16`, knob `12 × 12` | `packages/twenty-ui/src/input/Toggle/Toggle.module.scss:28-29,49-51` |
| Toggle | `medium` | `32 × 20`, knob `16 × 16` | `packages/twenty-ui/src/input/Toggle/Toggle.module.scss:33-34,55-57` |
| Checkbox | `small` (default) | box `12px`, icon `14px`, hit area `12 + 2×5 = 22px` | `packages/twenty-ui/src/input/Checkbox/Checkbox.module.scss:2-3,32-33,69` |
| Checkbox | `large` | box `18px`, icon `20px`, border `1.43px`, hit area `18 + 2×6 = 30px` | `packages/twenty-ui/src/input/Checkbox/Checkbox.module.scss:37-39,73` |
| Sort/filter chip | — | `24px`, delete button `20 × 20` | `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx:47,68,73` |
| Page bar | min | `32px` | `packages/twenty-front/src/modules/ui/layout/page/constants/PageBarMinHeight.ts:1` |
| Tab list | — | `themeCssVariables.spacing[10]` = `40px` | `packages/twenty-front/src/modules/ui/layout/tab-list/constants/TabListHeight.ts:3` |
| Side panel top bar | desktop | `48px` | `packages/twenty-front/src/modules/side-panel/constants/SidePanelTopBarHeight.ts:1` |
| Side panel top bar | mobile | `52px` | `packages/twenty-front/src/modules/side-panel/constants/SidePanelTopBarHeightMobile.ts:1` |

### 4.3 Icon sizes and strokes

`packages/twenty-ui/src/theme/constants/Icon.ts:1-13`, mirrored to `packages/twenty-ui/src/theme-constants/theme-light.css:5-11`. Stored as **unitless numbers**, because they
are passed as React props to Tabler icons, not written into CSS.

| Token | Value |
|---|---|
| `icon.size.sm` | `14` |
| `icon.size.md` | `16` |
| `icon.size.lg` | `20` |
| `icon.size.xl` | `24` |
| `icon.stroke.sm` | `1.6` |
| `icon.stroke.md` | `2` |
| `icon.stroke.lg` | `2.5` |

A parallel, duplicated set lives under `text.*` (`packages/twenty-ui/src/theme/constants/Text.ts:7-12`) with the same numbers under
different names: `iconSizeSmall 14`, `iconSizeMedium 16`, `iconStrikeLight 1.6`,
`iconStrikeMedium 2`, `iconStrikeBold 2.5`. See §11.

### 4.4 Avatar sizes

`packages/twenty-ui/src/data-display/Avatar/constants/AvatarPropertiesBySize.ts:1-22`, duplicated as classes in
`packages/twenty-ui/src/data-display/Avatar/Avatar.module.scss:35-62`. Square by default (radius `xs`), `50%` when `type="rounded"`.

| Size | Width = height | Font size |
|---|---|---|
| `xs` | `12px` | `8px` |
| `sm` | `14px` | `10px` |
| `md` | `16px` | `12px` |
| `lg` | `24px` | `13px` |
| `xl` | `40px` | `16px` |

### 4.5 Panel, drawer and container widths

| Thing | Value | Source |
|---|---|---|
| Navigation drawer | min `180`, max `350`, **default `220`** | `packages/twenty-front/src/modules/ui/layout/resizable-panel/constants/NavigationDrawerConstraints.ts:3-7` |
| Navigation drawer, collapsed | `40px` | `packages/twenty-front/src/modules/ui/layout/resizable-panel/constants/NavigationDrawerCollapsedWidth.ts:1` |
| Navigation drawer, live width | CSS var `--navigation-drawer-width`, persisted to localStorage | `packages/twenty-front/src/modules/ui/navigation/states/navigationDrawerWidthState.ts:4-10` |
| Side panel | min `320`, max `600`, **default `400`** | `packages/twenty-front/src/modules/side-panel/constants/SidePanelConstraints.ts:3-7` |
| Side panel, live width | CSS var `--side-panel-width`, persisted to localStorage | `packages/twenty-front/src/modules/side-panel/states/sidePanelWidthState.ts:4-10` |
| `theme.sidePanelWidth` | `500px` — a *different* number, used only by the command-menu open/close animation variants | `packages/twenty-ui/src/theme/constants/ThemeCommon.ts:21`; `packages/twenty-front/src/modules/side-panel/constants/SidePanelAnimationVariants.ts:3-25` |
| Resize edge hit area | `8px`; drag threshold `5px` | `packages/twenty-front/src/modules/ui/layout/resizable-panel/constants/ResizeEdgeWidthPx.ts:1`, `packages/twenty-front/src/modules/ui/layout/resizable-panel/constants/ResizeDragThresholdPx.ts:1` |
| Settings content | `max-width: 760px`, centred | `packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx:11,34` |
| Dropdown, default | `200px` | `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownWidth.ts:1` |
| Dropdown, named widths | `Narrow 160`, `Medium 200`, `Large 240`, `ExtraLarge 320` | `packages/twenty-front/src/modules/ui/layout/dropdown/constants/GenericDropdownContentWidth.ts:1-6` |
| Dropdown items container | `max-height: 168px` | `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownMenuItemsContainerMaxHeight.ts:1` |
| Dropdown resize floor | `140 × 200` | `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownResizeMinWidth.ts:1`, `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownResizeMinHeight.ts:1` |
| Dropdown offset from anchor | `8px` on Y | `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownOffsetY.ts:1` |
| Dropdown viewport padding | `32` desktop / `64` mobile bottom, `32` horizontal | `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownBoundaryBottomPaddingDesktop.ts:1`, `…Mobile.ts:1`, `packages/twenty-front/src/modules/ui/layout/dropdown/constants/DropdownBoundaryHorizontalPadding.ts:1` |
| Icon picker dropdown | `176px` | `packages/twenty-front/src/modules/ui/input/components/constants/IconPickerDropdownContentWidth.ts:1` |
| Modal `sm` / `md` / `lg` / `xl` | `300px` / `400px` / `53%` / `1200 × 800px` | `packages/twenty-ui/src/theme/constants/Modal.ts:5-17` |
| Modal `fullscreen` | `calc(100dvw / var(--t-zoom, 1))` × `calc(100dvh / var(--t-zoom, 1))` | `packages/twenty-ui/src/theme/constants/Modal.ts:18-21` |
| Modal max height | `calc(90dvh / var(--t-zoom, 1))` | `packages/twenty-ui/src/surfaces/Modal/Modal.module.scss:13` |

### 4.6 Record table column widths

| Column | Width | Source |
|---|---|---|
| Drag handle | `12px` | `packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableColumnDragAndDropWidth.ts:1` |
| Checkbox | `28px` | `packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableColumnCheckboxWidth.ts:1` |
| Any field column, minimum | `104px` | `packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableColumnMinWidth.ts:1` |
| Label-identifier column on mobile | `38px` | `packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableLabelIdentifierColumnWidthOnMobile.ts:1` |
| "Add column" button column | `32px` | `packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableColumnAddColumnButtonWidth.ts:1` |
| Field edit button | `28px` | `packages/twenty-front/src/modules/ui/field/display/constants/FieldEditButtonWidth.ts:1` |

Per-column widths are written as inline custom properties `--record-table-column-field-<i>` on the
table root, one per visible field, up to `MAX_COLUMNS = 100`
(`packages/twenty-front/src/modules/object-record/record-table/components/RecordTableStyleWrapper.tsx:27-37,48-53`).

Separately, the theme carries a *stale* table block (`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:16-20`) —
`horizontalCellMargin: '8px'`, `checkboxColumnWidth: '32px'`, `horizontalCellPadding: '8px'` —
with **0 call sites**, and its checkbox width disagrees with the real `28`. See §11.

### 4.7 Record board (kanban) sizes

| Thing | Value | Source |
|---|---|---|
| Column width | `200` | `packages/twenty-front/src/modules/object-record/record-board/constants/RecordBoardColumnWidth.ts:1` |
| Column min / max | `150` / `400` | `packages/twenty-front/src/modules/object-record/record-board/constants/RecordBoardColumnMinWidth.ts:1`, `packages/twenty-front/src/modules/object-record/record-board/constants/RecordBoardColumnMaxWidth.ts:1` |
| Column padding + border allowance | `17` | `packages/twenty-front/src/modules/object-record/record-board/constants/RecordBoardColumnPaddingAndBorderWidth.ts:1` |
| Column padding | `spacing[2]` = `8px`, `padding-top: 0` | `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumn.tsx:32-33` |
| Card gap | `padding-bottom: spacing[2]` = `8px` | `packages/twenty-front/src/modules/object-record/record-board/record-board-card/components/RecordBoardCard.tsx:50` |

### 4.8 Skeleton heights

`packages/twenty-front/src/modules/activities/components/SkeletonLoader.tsx:29-42`:

| Group | Key | Value |
|---|---|---|
| `standard` | `xs` / `s` / `m` / `l` / `xl` | `13` / `16` / `24` / `32` / `40` |
| `columns` | `s` / `m` / `xxl` | `84` / `120` / `542` |

### 4.9 Z-index

Three separate registries, deliberately not merged.

**Root stacking context** (`packages/twenty-front/src/modules/ui/layout/constants/RootStackingContextZIndices.ts:14-26`) — the file
carries a long comment explaining that these are the only components allowed to create a stacking
context on the document root, and that they were determined by inspection:

| Name | Value |
|---|---|
| `SidePanel` | `21` |
| `SidePanelButton` | `22` |
| `MobileNavigationBar` | `23` |
| `DropdownPortalBelowModal` | `38` |
| `RootModalBackDrop` | `39` |
| `RootModal` | `40` |
| `DropdownPortalAboveModal` | `50` |
| `Dialog` | `9999` |
| `WelcomeOverlay` | `10000` |
| `NotFound` | `10001` |
| `SnackBar` | `10002` |

**Record table** (`packages/twenty-front/src/modules/object-record/record-table/constants/TableZIndex.ts:1-24`) — a local scale, all small:

| Path | Value |
|---|---|
| `base` | `1` |
| `cell.default` | `3` |
| `hoverPortal` | `4` |
| `cell.sticky` | `8` · `groupSection.normalCell` `8` · `footer.default` `8` |
| `groupSection.stickyCell` | `9` · `rowDropLine` `9` · `footer.stickyColumn` `9` |
| `headerRow` / `headerColumns.headerColumnsNormal` | `10` |
| `headerColumns.headerColumnsSticky` | `14` |
| `cell.editMode` / `columnGrip` | `30` |

**Theme** — `--t-last-layer-z-index: 2147483647` (`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:23`), the 32-bit signed max,
for anything that must beat everything including third-party widgets. 4 call sites.

`OverlayContainer` hard-codes `z-index: 30` (`packages/twenty-front/src/modules/ui/layout/overlay/components/OverlayContainer.tsx:25`), outside all three
registries.

---

## 5 · Shape and depth

### 5.1 Radius

Base scale, `packages/twenty-ui/src/theme/constants/BorderCommon.ts:1-13` → `packages/twenty-ui/src/theme-constants/theme-light.css:136-145` (identical in dark):

| Token | Value | Used on |
|---|---|---|
| `border.radius.xs` | `2px` | square avatars (`packages/twenty-ui/src/data-display/Avatar/Avatar.module.scss:7`) |
| `border.radius.sm` | `4px` | cell edit-mode overlay, the rounded right edge of an active table row, sort/filter chip delete hover |
| `border.radius.smRound` | `4px` | **tags and chips** — same value as `sm`, but explicitly excluded from the squircle doubling |
| `border.radius.md` | `8px` | the default: buttons, cards, dropdowns, modals, inline-cell hover |
| `border.radius.mdRound` | `8px` | round-locked twin of `md`; checkbox container |
| `border.radius.lg` | `16px` | |
| `border.radius.xl` | `20px` | |
| `border.radius.xxl` | `40px` | |
| `border.radius.pill` | `999px` | toggles, scrollbar thumbs |
| `border.radius.rounded` | `100%` | circular checkbox shape |

### 5.2 Squircles

Under `@supports (corner-shape: squircle)` — Chromium 139+ — six radius tokens are **doubled** and
a zero-specificity rule opts the whole document in (`packages/twenty-ui/src/theme-constants/theme-light.css:1016-1048`):

| Token | Base | Squircle |
|---|---|---|
| `--t-border-radius-xs` | `2px` | `4px` |
| `--t-border-radius-sm` | `4px` | `8px` |
| `--t-border-radius-md` | `8px` | `16px` |
| `--t-border-radius-lg` | `16px` | `32px` |
| `--t-border-radius-xl` | `20px` | `40px` |
| `--t-border-radius-xxl` | `40px` | `80px` |

```css
@supports (corner-shape: squircle) {
  .light { --t-border-radius-md: 16px; /* … */ }
  /* Zero specificity on purpose: any component rule can override it. */
  *, *::before, *::after { corner-shape: var(--t-corner-shape, squircle); }
}
```

The rules stated in the source comment (`packages/twenty-ui/src/theme-constants/theme-light.css:1016-1031`) and pinned by
`packages/twenty-ui/src/theme-constants/__tests__/cornerShapeThemeParity.test.ts:56-71`:

- `pill`, `rounded` and the two `*-round` tokens are **never** doubled. They belong to elements
  that keep `corner-shape: round` — circles, capsules, checkboxes, chips, tags — and must look
  identical in both modes. `packages/twenty-ui/src/data-display/Tag/Tag.module.scss:5-6` and `packages/twenty-ui/src/data-display/Chip/Chip.module.scss:20-21` each pair
  `border-radius: var(--t-border-radius-sm-round)` with an explicit `corner-shape: round`.
- Opt a subtree out with `--t-corner-shape: round`, or a single element with `corner-shape: round`.
- Nested radii must stay concentric in **both** modes, derived as parent-radius minus inset:
  `calc(var(--t-border-radius-md) - var(--t-spacing-1))` — the token doubles under squircle, the
  inset does not, which is exactly what concentricity needs. `packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:11`
  is the live example.

If your target does not support `corner-shape`, use the base scale; the whole block is
progressive enhancement.

### 5.3 Border widths and colours

There is **one border width in the system: `1px`.** No border-width token exists. The exceptions,
all literal:

- `1.43px` — the large checkbox and the tertiary checkbox variant (`packages/twenty-ui/src/input/Checkbox/Checkbox.module.scss:28,39`)
- `0 0 0 3px` — the focus glow, expressed as a `box-shadow` spread, not a border
  (`packages/twenty-ui/src/input/Button/Button.module.scss:176,217,295,337`)
- `2px` — the `:focus-visible` outline (`packages/twenty-ui/src/styles/abstracts/_mixins.scss:3`)

Colours: see §2.5. The practical hierarchy is `border.color.light` for grid lines,
`border.color.medium` for component chrome, `border.color.strong` for emphasis.

### 5.4 Shadows

Four elevation tokens plus a raw colour. Values are in §2.6; here is what each is for:

| Token | Composition (light) | Used on |
|---|---|---|
| `boxShadow.color` | `color(display-p3 0 0 0 / 0.039)` | raw ink for hand-rolled shadows — the record table's scroll shadows |
| `boxShadow.light` | two layers, `0 2 4` + `0 0 4` | the least-used tier |
| `boxShadow.strong` | `2 4 16` + `0 2 4` | **the default floating elevation**: every `OverlayContainer`, every `Modal` |
| `boxShadow.underline` | `0 1 0 0` at 0.361 alpha | a 1px hairline under an element, used as an underline you can colour |
| `boxShadow.superHeavy` | three layers, `0 0 8` + `0 8 64 -16` + `0 24 56 -16` | modals with `overlay="dark"` |

Elevation is *always* paired with a border: `OverlayContainer` and `Card` both carry
`1px solid border.color.medium` alongside their shadow. Nothing in the library floats on a shadow
alone.

Two hand-built shadows deserve mention because they are the table's scroll affordance rather than
an elevation: `packages/twenty-front/src/modules/object-record/record-table/components/HorizontalScrollBoxShadowCSS.ts:4-21` and `packages/twenty-front/src/modules/object-record/record-table/components/VerticalScrollBoxShadowCSS.ts:4-20`
attach a 4px `::after` / `::before` strip clipped with `clip-path: inset(...)` and gated on a
`visibility` custom property that JS flips when the container scrolls.

### 5.5 Blur

Three tokens, each a full filter chain rather than a radius (`packages/twenty-ui/src/theme/constants/BlurLight.ts:1-5`):

| Token | Light | Dark |
|---|---|---|
| `blur.light` | `blur(6px) saturate(200%) contrast(50%) brightness(130%)` | `blur(6px) saturate(200%) contrast(100%) brightness(130%)` |
| `blur.medium` | `blur(12px) saturate(200%) contrast(50%) brightness(130%)` | `blur(12px) saturate(200%) contrast(100%) brightness(130%)` |
| `blur.strong` | `blur(20px) saturate(200%) contrast(50%) brightness(130%)` | `blur(20px) saturate(200%) contrast(100%) brightness(130%)` |

`blur.medium` + `background.transparent.primary` is the frosted-glass recipe behind every
floating surface (`packages/twenty-front/src/modules/ui/layout/overlay/components/OverlayContainer.tsx:10-12`).

---

## 6 · Motion

### 6.1 Durations

`packages/twenty-ui/src/theme/constants/Animation.ts:1-8`. Stored **unitless** so JS can read them as numbers; CSS must multiply.

| Token | Value | In seconds | Typical use |
|---|---|---|---|
| `animation.duration.instant` | `0.075` | 75ms | opacity swaps on hover (menu-item hover buttons, grip swap) |
| `animation.duration.fast` | `0.15` | 150ms | transform/colour transitions, board header actions, placeholder fade-in |
| `animation.duration.normal` | `0.3` | 300ms | panel open/close, modal fade, expand/collapse |
| `animation.duration.slow` | `1.5` | 1500ms | long ambient loops |

Two ways to consume:

```scss
transition: opacity duration(instant) ease;                          // SCSS, packages/twenty-ui/src/styles/abstracts/_functions.scss:1-5
```
```ts
transition: `width calc(${themeCssVariables.animation.duration.normal} * 1s)`  // Linaria
```

### 6.2 Easings

**There is no easing token.** Every transition writes its curve inline. The distribution across
`twenty-ui`'s SCSS:

| Curve | Occurrences |
|---|---|
| `ease` | dominant — the default for background, transform, opacity |
| `ease-out` | modal fade-out, some transforms |
| `ease-in-out` | expandable containers, board header |
| `linear` | one case: progress bar width |

### 6.3 The one canonical transition

Ten separate SCSS files write, byte for byte:

```scss
transition: background 0.1s ease;
```

with a literal `0.1s` that is **not** one of the four duration tokens. It is also frozen into the
theme as `--t-clickable-element-background-transition: background 0.1s ease`
(`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:22`) — which has **0 call sites**. So the convention exists twice: once as a dead
token, once as a copy-pasted literal in `packages/twenty-ui/src/input/Button/Button.module.scss:49`,
`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:23` and eight others.

### 6.4 What animates

- **Background colour on hover and press** — the single most common animation in the product,
  always 100ms, always `ease`.
- **Opacity of hover-revealed controls** — menu-item trailing buttons and the drag-grip icon swap
  fade at `duration(instant)` (75ms) (`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:104,113-123`).
- **Panel width** — the side panel animates `width` over `duration(normal)`
  (`packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx:31-37`), and drops to `transition: none` while the user is actively
  dragging the resize handle.
- **Modal opacity** — Base UI's `data-starting-style` / `data-ending-style` drive a
  `duration(normal) ease-out` fade (`packages/twenty-ui/src/surfaces/Modal/Modal.module.scss:14-22`).
- **Empty placeholders** — a `duration(fast)` opacity fade-in keyframe
  (`packages/twenty-ui/src/feedback/EmptyPlaceholderStyled/EmptyPlaceholderStyled.module.scss:10-21`).
- **Toggle knob, expandable containers, progress bars, circular loaders.**

### 6.5 What deliberately does not animate

- **Disabled and hover-suppressed menu items** explicitly set `transition: none`
  (`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:46,50`) so that a state you cannot act on never eases in.
- **Table cells.** `RecordTableCellBaseContainer` and `RecordTableCellStyleWrapper` declare no
  transition at all; selection, focus and hover repaint instantly. At 32px rows and hundreds of
  visible cells, that is the difference between crisp and soupy.
- **The side panel while resizing** (see above).
- **Drag feedback.** `[data-dnd-dragging='true']` is positioned by dnd-kit from measured pixels
  and is explicitly counter-zoomed rather than transitioned (`packages/twenty-front/src/index.css:46-60`).

### 6.6 Reduced motion

Honoured, but not systematically. `useReducedMotion()` from framer-motion gates the side panel's
shrink-from-full-width animation (`packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx:22,90-96`), and the welcome overlay
carries four `@media (prefers-reduced-motion: reduce)` blocks. There is **no global**
reduced-motion reset — the 100ms background transitions and the menu-item fades run regardless.

---

## 7 · Icons

### Library

`@tabler/icons-react ^3.31.0` (`packages/twenty-ui/package.json:76`). 436 Tabler icons are
re-exported through a single curated barrel, `packages/twenty-ui/src/icon/components/TablerIcons.ts`,
which opens with `/* oxlint-disable no-restricted-imports */` — importing from `@tabler/icons-react`
directly is banned everywhere else; you go through the barrel. A handful are aliased on the way
through (`IconNumber123 as Icon123`, `packages/twenty-ui/src/icon/components/TablerIcons.ts:3`).

Alongside those, `twenty-ui` ships ~30 hand-drawn SVG components in the same namespace
(`packages/twenty-ui/src/icon/index.ts:12-32`): brand marks (`IconGmail`, `IconGoogle`, `IconMicrosoft`,
`IconBrandAnthropic`, `IconModelClaude`, …), relation glyphs (`IconRelationManyToOne`), and 21
two-tone `IllustrationIcon*` components used as field-type badges.

### The icon contract

Every icon — Tabler or hand-drawn — satisfies one type
(`packages/twenty-ui/src/icon/types/IconComponent.ts:3-12`):

```ts
export type IconComponentProps = {
  className?: string;
  style?: CSSProperties;
  size?: number | string;
  stroke?: number | string;
  color?: string;
  'aria-hidden'?: boolean;
};
export type IconComponent = FunctionComponent<IconComponentProps>;
```

`IconComponent` is what components accept as an `Icon` / `LeftIcon` prop. There is also a
name-resolving wrapper `<Icon name="…" />` backed by `useIcons()`
(`packages/twenty-ui/src/icon/components/Icon.tsx:8-31`) for icons chosen at runtime from metadata.

### Defaults

| Property | Default | Source |
|---|---|---|
| Size | **`16`** (`icon.size.md`) — the general default | `packages/twenty-ui/src/theme/constants/Icon.ts:4` |
| Size inside a tag, chip or filter chip | **`14`** (`icon.size.sm`) | `packages/twenty-ui/src/data-display/Tag/Tag.tsx:58`, `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx:153,175` |
| Size in a text input adornment | `16` (`icon.size.md`) | `packages/twenty-front/src/modules/ui/input/components/TextInput.tsx:397` |
| Stroke | **`2`** (`icon.stroke.md`) | `packages/twenty-ui/src/theme/constants/Icon.ts:10` |
| Stroke inside a tag or chip | `1.6` (`icon.stroke.sm`) | `packages/twenty-ui/src/data-display/Tag/Tag.tsx:59`, `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx:175` |

Sizes and strokes are passed as **numbers via React props**, never via CSS — that is why the
tokens are unitless and why `useTheme()` coerces them:

```tsx
<Icon size={theme.icon.size.sm} stroke={theme.icon.stroke.sm} aria-hidden />
```

### Colour rules

Icons almost never take a `color` prop. They inherit `currentColor` from the element they sit in,
which is why `Tag`, `Chip` and `MenuItem` set `color` on the container and the icon simply
follows. Where an override is needed, it is done through the parent's `color`, not the icon:
`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx:38-41` recolours descendant `svg` on read-only hover;
`packages/twenty-ui/src/input/Checkbox/Checkbox.module.scss:143` sets `stroke: var(--t-font-color-inverted)` on the checkmark path.

Two-tone illustration icons are the exception: they read the dedicated
`--t--illustration-icon-color-*` / `--t--illustration-icon-fill-*` pair (§2.6).

### Icon + text pairing

Always flexbox with a token gap, never margin:

| Context | Gap | Source |
|---|---|---|
| Button | `var(--t-spacing-1)` = `4px` | `packages/twenty-ui/src/input/Button/Button.module.scss:45` |
| Tag | `var(--t-spacing-1)` = `4px` | `packages/twenty-ui/src/data-display/Tag/Tag.module.scss:17` |
| Chip | `var(--t-spacing-1)` = `4px` | `packages/twenty-ui/src/data-display/Chip/Chip.module.scss:12` |
| MenuItem (item level and within left/right content) | `var(--t-spacing-2)` = `8px` | `packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:15,152,165` |
| Sort/filter chip | `column-gap: spacing[1]` = `4px` | `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx:39` |

The icon is always `flex-shrink: 0` so text truncates and the glyph does not
(`packages/twenty-ui/src/data-display/Chip/Chip.module.scss:23-25`, `packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:157-159,168-170`), and decorative icons
carry `aria-hidden` (`packages/twenty-ui/src/data-display/Tag/Tag.tsx:60`).

---

## 8 · Component inventory

Everything exported from `twenty-ui`'s public entry points. "States" lists states the component
styles explicitly; every clickable primitive additionally inherits `:focus-visible` from the
`focus-ring` mixin where noted in §11.

### 8.1 `twenty-ui/input`

| Name | What it is for | Variants | Sizes | States | Notable props |
|---|---|---|---|---|---|
| `Button` | The primary action control | `primary` \| `secondary` \| `tertiary` × accent `default` \| `blue` \| `danger` \| `green`, plus `inverted` | `small` (24px) \| `medium` (32px) | default, hover, active, focus, disabled, loading, `soon` | `position` `standalone`\|`left`\|`middle`\|`right`, `Icon`, `hotkeys`, `to`, `fullWidth`, `justify` (`packages/twenty-ui/src/input/Button/Button.tsx:16-44`) |
| `IconButton` | Icon-only Button | same three variants, accent `default` \| `blue` \| `danger` | `small` \| `medium` | same as Button | `position`, `Icon`, `to` (`packages/twenty-ui/src/input/IconButton/IconButton.tsx:9-12`) |
| `LightButton` | Chromeless text button | accent `secondary` \| `tertiary` | — | hover, active, focus, disabled | `Icon`, `title` (`packages/twenty-ui/src/input/LightButton/LightButton.tsx:9`) |
| `LightIconButton` | Chromeless icon button | accent `secondary` \| `tertiary` | `small` \| `medium` | hover, active, focus, disabled | (`packages/twenty-ui/src/input/LightIconButton/LightIconButton.tsx:9-10`) |
| `MainButton` | Full-width auth/onboarding CTA | `primary` \| `secondary` | — | hover, disabled, `soon` | `fullWidth`, `width`, `Icon` (`packages/twenty-ui/src/input/MainButton/MainButton.tsx:9`) |
| `FloatingButton` | Button on a floating surface | — | `small` \| `medium` | hover, active, focus, disabled | `position` (`packages/twenty-ui/src/input/FloatingButton/FloatingButton.tsx:9-10`) |
| `FloatingIconButton` | Icon-only floating button | — | `small` \| `medium` | as above | `position` (`packages/twenty-ui/src/input/FloatingIconButton/FloatingIconButton.tsx:9-10`) |
| `RoundedIconButton` | Circular icon button | — | `small` \| `medium` | hover, disabled | (`packages/twenty-ui/src/input/RoundedIconButton/RoundedIconButton.tsx:9`) |
| `AnimatedButton` / `AnimatedLightIconButton` | Button whose label/width animates in | — | — | as their base | |
| `InsideButton` | Button nested inside an input | — | — | hover, disabled | `Icon`, `ariaLabel` |
| `ButtonGroup`, `IconButtonGroup`, `LightIconButtonGroup`, `FloatingButtonGroup`, `FloatingIconButtonGroup` | Join buttons into a segmented bar by rewriting each child's `position` | — | inherits child size | — | `iconButtons` / `children` |
| `Checkbox` | Boolean input; base-ui `Checkbox` primitive | `primary` \| `secondary` \| `tertiary`; shape `squared` \| `rounded`; accent `blue` \| `orange` | `small` (12px box) \| `large` (18px box) | checked, indeterminate, hover, disabled | `hoverable`, `onCheckedChange` (`packages/twenty-ui/src/input/Checkbox/Checkbox.tsx:9-45`) |
| `Radio` | Single-choice input | — | `RadioSize` enum | checked, disabled | `labelPosition` (`LabelPosition` enum) |
| `RadioGroup` | Layout wrapper for `Radio` | — | — | — | |
| `Toggle` | Switch | — | `small` (24×16) \| `medium` (32×20) | on, off, disabled | `onChange`, colour override via `--toggle-on-color` |
| `AdvancedSettingsToggle` | Toggle preset for the "advanced settings" reveal | — | — | on/off | |
| `SegmentedControl` | Mutually-exclusive inline choice | item width `content` \| `equal` | — | selected, disabled | `role` `group`\|`tablist`, `ariaLabel`, options may be icon-only with a required `ariaLabel` (`packages/twenty-ui/src/input/SegmentedControl/SegmentedControl.tsx:11-54`) |
| `TabButton` / `TabContent` / `StyledTabContainer` | Tab strip | — | — | active, disabled | `LeftIcon`, `RightIcon`, `logo`, `to` |
| `Slider` | Range input | colour `SliderColor` | — | — | `min`/`max`/`step`/`value` |
| `SearchInput` | Search field with optional filter dropdown slot | — | — | focus, disabled | `filterDropdown` render prop |
| `CardPicker` | Selectable card wrapper (used by settings pickers) | — | — | checked | `handleChange` |
| `ColorPickerButton`, `ThemeColorPickerMenu` | Pick a `ThemeColor` | — | — | selected | |
| `ColorSchemeCard`, `ColorSchemePicker` | Light/dark/system preview cards | — | — | selected | |
| `CodeEditor`, `CoreEditorHeader` | Monaco wrapper + its header | — | — | — | `getBaseCodeEditorTheme()`, `BASE_CODE_EDITOR_THEME_ID` |
| `IconListViewGrip` | The 6-dot drag grip glyph | — | — | — | |

### 8.2 `twenty-ui/data-display`

| Name | What it is for | Variants | Sizes | States | Notable props |
|---|---|---|---|---|---|
| `Tag` | A coloured label — the product's signature atom | `solid` \| `outline` (dashed 1px) \| `border` (solid 1px); weight `regular` \| `medium` | fixed 20px | interactive (renders `<button>`) when `onClick` given | `color: ThemeColor \| 'transparent'`, `Icon`, `preventShrink`, `preventPadding` (`packages/twenty-ui/src/data-display/Tag/Tag.tsx:10-24`) |
| `Chip` | An inline reference to a record | `Highlighted` \| `Regular` \| `Transparent` \| `Rounded` \| `Static`; accent `TextPrimary` \| `TextSecondary` | `Large` (16px) \| `Small` (12px) | hover, active, disabled, clickable | `leftComponent`, `rightComponent`, `rightComponentDivider`, `maxWidth`, `isBold`, `emptyLabel` (`packages/twenty-ui/src/data-display/Chip/Chip.tsx:10-46`) |
| `LinkChip` | `Chip` wrapped in a router link | inherits `Chip` | inherits | inherits | `to`, `target`, `triggerEvent` |
| `Status` | A pill for a select-field value; `<h3>` element | weight `regular` \| `medium` | — | loader visible | `color: ThemeColor`, `isLoaderVisible` (`packages/twenty-ui/src/data-display/Status/Status.tsx:12-19`) |
| `Avatar` | Person/workspace image or initial | type `rounded` \| `squared` \| `icon` | `xs` 12 · `sm` 14 · `md` 16 · `lg` 24 · `xl` 40 | clickable (4px transparent ring on hover) | `avatarUrl`, `placeholder`, `placeholderColorSeed` |
| `AvatarGroup` | Overlapped stack of avatars | overlap `left` \| `right` | inherits | — | `maxVisible` (default 4), `overflowAvatar`, `overlapOffset` |
| `AvatarOrIcon` | Avatar, falling back to an icon tile | — | inherits | — | `isIconInverted`, `IconColor`, `IconBackgroundColor` |
| `Checkmark` | 14px check on a filled square | — | — | — | |
| `AnimatedCheckmark` | Draw-on check | — | — | — | `duration`, `color` |
| `ColorSample` | Colour swatch for pickers | `circle` \| `default` \| `pipeline` | — | — | `colorName: ThemeColor` |
| `Pill` | Small static label with optional 12px icon | — | — | — | `label`, `Icon` |
| `NotificationCounter` | Unread badge | `primary` \| `secondary` | — | — | `count` |
| `TintedIconTile` / `StyledTintedIconTileContainer` | Icon on a tinted square, coloured from a `ThemeColor` | — | `size`, `stroke` props | — | `getIconTileColorShades()` |
| `CommandBlock` | Terminal-style copyable command list | — | — | — | `commands: string[]`, `button` |

### 8.3 `twenty-ui/navigation`

| Name | What it is for | Variants | Sizes | States | Notable props |
|---|---|---|---|---|---|
| `MenuItem` | The single row that every menu, dropdown and command list is built from | accent `default` \| `danger` \| `placeholder` | fixed 32px | hover, focused, key-selected, disabled, hover-background-disabled, sub-menu open | `LeftIcon`/`LeftComponent`, `RightIcon`/`RightComponent`, `contextualText` + `contextualTextPosition`, `iconButtons`, `isIconDisplayedOnHoverOnly`, `hotKeys`, `hasSubMenu` (`packages/twenty-ui/src/navigation/MenuItem/MenuItem.tsx:46-72`) |
| `MenuItemSelect` | `MenuItem` + trailing check | inherits | inherits | `selected` | |
| `MenuItemMultiSelect` | `MenuItem` + leading checkbox | inherits | inherits | `selected`, `indeterminate` | |
| `MenuItemSelectAvatar` / `MenuItemMultiSelectAvatar` | …with an avatar | inherits | inherits | inherits | |
| `MenuItemSelectTag` / `MenuItemMultiSelectTag` | …with a `Tag` | inherits | inherits | inherits | |
| `MenuItemSelectColor` | …with a `ColorSample` | inherits | inherits | inherits | `DEFAULT_COLOR_LABELS` |
| `MenuItemToggle` | …with a `Toggle` | inherits | inherits | on/off | |
| `MenuItemNavigate` | …with a trailing chevron | inherits | inherits | inherits | |
| `MenuItemDraggable` | …with a drag grip that swaps in on hover | grip `always` \| `onHover` \| `never` | inherits | dragging | |
| `MenuItemHotKeys` | …with a keyboard-shortcut cluster | inherits | inherits | inherits | `hotKeys: string[]` |
| `MenuItemAvatar`, `MenuItemSuggestion` | Avatar-first and suggestion rows | inherits | inherits | inherits | |
| `MenuPicker` | Icon button that opens a menu, with tooltip | — | — | selected, disabled | `tooltipContent`, `tooltipDelay`, `tooltipOffset`, `showLabel` |
| `NavigationBar` / `NavigationBarItem` | Mobile bottom tab bar | — | — | active, hidden | `items: {name,label,Icon,onClick}[]` |
| `RoundedLink` | Pill-shaped external link | — | — | hover | `href`, `label` |
| `SocialLink` | `RoundedLink` that derives its label from the URL | `LinkType` | — | — | `SOCIAL_LINK_PROVIDERS` |
| `ClickToActionLink`, `ContactLink` | mailto/tel style links | — | — | hover | |
| `RawLink`, `UndecoratedLink` | Unstyled/undecorated router links | — | — | — | |
| `GithubVersionLink` | Version badge linking to a release | — | — | — | |

### 8.4 `twenty-ui/surfaces`

| Name | What it is for | Variants | Sizes | States | Notable props |
|---|---|---|---|---|---|
| `Modal` (+ `ModalHeader`, `ModalContent`, `ModalFooter`, `ModalBackdrop`) | Dialog. Base UI under the hood; fades via `data-starting-style` | overlay `light` \| `dark` \| `transparent`; padding `none` \| `small` \| `medium` \| `large` | `small` 300 · `medium` 400 · `large` 53% · `extraLarge` 1200×800 · `fullscreen` | open/closed, mobile | `isInContainer`, `container`, `smallBorderRadius`, `narrowWidth`, `autoHeight`, `modalZIndex`, `backdropZIndex` (`packages/twenty-ui/src/surfaces/Modal/types/ModalProps.ts:1-18`) |
| `Card` (+ `CardHeader`, `CardContent`, `CardFooter`) | Bordered container | `rounded` | — | — | `fullWidth`, `backgroundColor` (writes `--card-background-color`) |
| `AppTooltip` | Tooltip; Base UI `Tooltip` | position `Top`\|`Left`\|`Right`\|`Bottom`; 12 `PlacesType` placements | — | open/closed | delay `noDelay` 0 · `shortDelay` 300ms · `mediumDelay` 500ms · `longDelay` 1000ms (`packages/twenty-ui/src/surfaces/AppTooltip/AppTooltip.tsx:10-21`) |
| `OverflowingTextWithTooltip` | Truncate with ellipsis, reveal full text in a tooltip only when clipped | — | `large` \| `small` | overflowing / not | `displayedMaxRows`, `isTooltipMultiline`, `alwaysShowTooltip` |

### 8.5 `twenty-ui/feedback`

| Name | What it is for | Variants | Sizes | States | Notable props |
|---|---|---|---|---|---|
| `Banner` | Full-width notice bar | `primary` \| `secondary` × colour `blue` \| `danger` | — | — | |
| `InlineBanner` | Inline notice with an action | colour `blue` \| `danger` | — | — | `button`, `LeftIcon` |
| `Callout` | Boxed inline message | `info` \| `warning` \| `error` \| `neutral` \| `success` | — | dismissed | `Icon`, dismissible |
| `Info` | Compact one-line notice with a button | accent `blue` \| `danger` | — | — | `buttonTitle`, `to` |
| `SidePanelInformationBanner` | Side-panel-specific banner | — | — | — | |
| `ProgressBar` | Determinate bar, can run as a countdown | — | — | — | `value`, `barColor`, `backgroundColor`, `countdownDurationInMs`, `isCountdownPaused` |
| `CircularProgressBar` | Ring progress | — | `size`, `barWidth` | — | |
| `Loader` | Spinner tinted by `ThemeColor` | — | — | — | `color` |
| `AnimatedPlaceholder` | Two-layer parallax illustration for empty/error states, 2px offset, theme-aware asset set | one per `AnimatedPlaceholderType` | — | — | `type` (`packages/twenty-ui/src/feedback/AnimatedPlaceholder/AnimatedPlaceholder.tsx:12-23`) |
| `AnimatedPlaceholderEmptyContainer` / `…EmptyTextContainer` / `…EmptyTitle` / `…EmptySubTitle` | The four-part empty-state layout | — | — | — | `width` |
| `AnimatedPlaceholderError*` (same four) | The error-state layout | — | — | — | |

### 8.6 `twenty-ui/layout`, `typography`, `accessibility`

| Name | What it is for | Variants | States | Notable props |
|---|---|---|---|---|
| `Section` | Vertical block with alignment/colour presets | alignment `Left`\|`Center`; font colour `Primary`\|`Secondary`\|`Tertiary` | — | `fullWidth` |
| `HorizontalSeparator` | 1px rule, optionally with centred text | — | visible/hidden | `text`, `noMargin`, `color` |
| `AnimatedExpandableContainer` | Height/width reveal | dimension, `AnimationMode`, `AnimationDurations` | expanded/collapsed | `containAnimation` |
| `AnimatedEaseIn`, `AnimatedEaseInOut`, `AnimatedContainer`, `AnimatedRotate`, `AnimatedIconCrossfade`, `AnimatedCircleLoading` | Motion wrappers | — | — | |
| `AutogrowWrapper` | Sizes an input to its content | — | — | |
| `ResizeHandle` + `useResizeHandle` | Drag-to-resize edge | — | dragging | |
| `H1Title` | Page title | font colour `Primary`\|`Secondary`\|`Tertiary` | — | |
| `H2Title` | Section title + description | — | — | `description` |
| `H3Title` | Sub-section title + description | — | — | `description` |
| `Label` | Uppercase-ish meta label | `default` (11px) \| `small` (9px) | — | |
| `SeparatorLineText` | "or"-style divider with rules | — | — | |
| `LinkifiedText` | Auto-links URLs in a text run | — | — | |
| `StyledText` / `StyledTextContent` / `StyledTextWrapper` | Truncating text primitives | — | — | |
| `VisibilityHidden` / `VisibilityHiddenInput` | Screen-reader-only content | — | — | `VISIBILITY_HIDDEN` const |
| `JsonTree` (`twenty-ui/json-visualizer`) | Collapsible JSON viewer | — | expanded nodes | |

---

### 8.7 Full anatomy of the five components that carry the product's identity

#### (1) Record table cell — the densest surface in the product

The table is not a `<table>`. It is nested `div`s with `display: flex` rows and per-column widths
driven by custom properties, so that resizing a column is a single style write rather than a React
re-render.

```
div.table-row                      RecordTableRowDiv        flex row, relative
└── div.table-cell.<width-class>   RecordTableCellStyleWrapper
    └── div                        RecordTableCellBaseContainer   height 32px, flex, user-select:none
        ├── (display) RecordTableCellDisplayContainer → the field's display component
        └── (edit)    RecordTableCellEditMode
                      └── OverlayContainer (floating-ui, placement bottom-start)
                          └── the field's input component
```

The cell wrapper owns background, borders and text colour — nothing else does
(`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellStyleWrapper.tsx:6-28,49-55`):

```tsx
export const StyledCell = styled.div<{ … }>`
  background: ${({ backgroundColor, isDragging }) =>
    isDragging ? 'transparent' : backgroundColor};
  border-bottom: 1px solid
    ${({ borderColor, hasBottomBorder, isDragging }) =>
      hasBottomBorder && !isDragging ? borderColor : 'transparent'};
  border-right: ${({ borderColor, hasRightBorder }) =>
    hasRightBorder ? `1px solid ${borderColor}` : 'none'};
  color: ${({ fontColor }) => fontColor};
  padding: 0;
  text-align: left;
`;
// …
const tdBackgroundColor = isSelected ? theme.accent.quaternary : theme.background.primary;
const borderColor = theme.border.color.light;
const fontColor = theme.font.color.primary;
```

| Part | Token |
|---|---|
| Cell background, at rest | `background.primary` |
| Cell background, row selected | `accent.quaternary` |
| Grid lines (bottom + right) | `border.color.light` |
| Text | `font.color.primary` |
| Row / cell height | `32px` (`packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableRowHeight.ts:1`; `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx:23`) |
| Horizontal padding | `0` on the cell; input-only fields get `padding-left: 8px` from their edit container (`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:32-39`) |
| Read-only hover | outline `1px solid font.color.tertiary`, background `background.secondary`, text `font.color.secondary`, `img { opacity: 0.64 }` (`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx:28-47`) |
| Header cell | background `background.primary`, hover `background.secondary`, active `background.tertiary`, text `font.color.tertiary`, borders `border.color.light` (`packages/twenty-front/src/modules/object-record/record-table/record-table-header/components/RecordTableHeaderCellContainer.tsx:11-45`) |

Row focus and row active are drawn by the *row*, not the cell, so the highlight can wrap the whole
run of cells with one rounded right edge (`packages/twenty-front/src/modules/object-record/record-table/record-table-row/components/RecordTableRowDiv.tsx:17-41`):

```tsx
&[data-focused='true'], &[data-active='true'] {
  div.table-cell, div.table-cell-0-0 {
    &:not(:first-of-type) {
      background-color: ${themeCssVariables.accent.quaternary};
      border-bottom: 1px solid ${themeCssVariables.border.color.medium};
      border-color: ${themeCssVariables.border.color.medium};
    }
    &:nth-of-type(2) { border-left: 1px solid …medium; margin-left: -1px; div { margin-left: -1px; } }
    &:last-of-type  { border-radius: 0 ${…radius.sm} ${…radius.sm} 0; border-right: 1px solid …medium; }
  }
}
```

The negative `margin-left: -1px` is how the added left border avoids shifting the grid by a pixel.

#### (2) `Tag` — the coloured label

The whole component is a background/text pair chosen from the tag palette, injected as two custom
properties so the SCSS module stays static (`packages/twenty-ui/src/data-display/Tag/Tag.tsx:39-49,76-79`):

```tsx
const tagBackground = color === 'transparent'
  ? 'transparent'
  : (themeCssVariables.tag.background[color] ?? themeCssVariables.tag.background.gray);
const tagText = color === 'transparent'
  ? themeCssVariables.font.color.secondary
  : (themeCssVariables.tag.text[color] ?? themeCssVariables.font.color.secondary);
const sharedStyle = { '--tag-background': tagBackground, '--tag-text': tagText };
```

```
span.tag  (or button.tag.interactive when onClick is given)
├── div.iconContainer  → <Icon size={14} stroke={1.6} aria-hidden />
└── span.content       → <OverflowingTextWithTooltip text={text} />
    (or span.nonShrinkableText when preventShrink)
```

`packages/twenty-ui/src/data-display/Tag/Tag.module.scss:1-21`:

| Property | Value |
|---|---|
| `box-sizing` | `content-box` |
| `height` | `var(--t-spacing-5)` = 20px |
| `padding` | `0 var(--t-spacing-2)` = 0 8px |
| `gap` | `var(--t-spacing-1)` = 4px |
| `border-radius` | `var(--t-border-radius-sm-round)` = 4px, with `corner-shape: round` |
| `font-size` | `var(--t-font-size-md)` = 13px |
| `font-weight` | `var(--t-font-weight-regular)` (`medium` with `weight="medium"`) |
| `overflow` | `hidden` |
| `outline` variant | `border: 1px dashed var(--t-border-color-strong)` |
| `border` variant | `border: 1px solid var(--t-border-color-strong)` |

The unknown-colour fallback (`?? tag.background.gray`) is what makes it safe to feed a Tag a
user-authored select option whose colour was deleted.

#### (3) `Chip` — how a record is referenced inline

The chip is the record. Wherever a company, person or custom record appears inside another
record's field, it is a `Chip` with an `Avatar` in `leftComponent`.

```
a | button | div  .chip.<size>.<accent>[.<background>][.cursor*]
├── leftComponent         → usually <Avatar size="md" />
├── label (or <OverflowingTextWithTooltip/>)
├── div.rightComponentDivider   (1px left border, border.color.light) — optional
└── rightComponent
```

`packages/twenty-ui/src/data-display/Chip/Chip.module.scss:1-115`:

| Part | Token |
|---|---|
| Height, `Large` / `Small` | `var(--t-spacing-4)` = 16px / `var(--t-spacing-3)` = 12px, `content-box` |
| Padding | `var(--t-spacing-1)` on all four sides, via `--chip-vertical-padding` / `--chip-horizontal-padding` |
| Gap | `var(--t-spacing-1)` = 4px |
| Radius | `var(--t-border-radius-sm-round)` = 4px + `corner-shape: round` |
| Text, `TextPrimary` / `TextSecondary` | `font.color.primary` / `font.color.secondary` |
| Text, disabled | `font.color.light` (wins over accent) |
| Empty label | `font.color.tertiary` |
| `Regular` interactive | hover `background.transparent.light`, active `background.transparent.medium` |
| `Highlighted` | rest `background.transparent.light`, hover `…medium`, active `…strong` |
| `Static` | `background.transparent.light` at rest, hover and active — a chip that looks interactive but is not |
| Divider | `border-left: 1px solid var(--t-border-color-light)` |

All hover rules are wrapped in `@include hover-capable` — `@media (hover: hover)` — so a tap on
a touch device does not leave the chip stuck in its hover fill
(`packages/twenty-ui/src/data-display/Chip/Chip.module.scss:64,89`, mixin at `packages/twenty-ui/src/styles/abstracts/_mixins.scss:8-15`).

The app-level wrapper `RecordChip` binds this to CRM semantics: it resolves the record's
label/avatar via `useRecordChipData`, and chooses between opening the record in the side panel or
navigating, based on the user's `OpenRecordIn` preference
(`packages/twenty-front/src/modules/object-record/components/RecordChip.tsx:36-58`). Only two of the five chip variants are exposed
to it: `Highlighted` and `Transparent` (`packages/twenty-front/src/modules/object-record/components/RecordChip.tsx:25`).

#### (4) `MenuItem` — the atom every menu is made of

Dropdowns, the command menu, filter pickers, the navigation drawer and the record-action menus are
all stacks of this one 32px row.

```
div.hoverableMenuItemBase
  data-accent | data-key-selected | data-focused | data-disabled
  data-hover-background-disabled | data-icon-displayed-on-hover-only | data-cursor
├── div.menuItemLeftContent    (flex, gap 8px, min-width 0)
│   ├── icon container | LeftComponent
│   ├── div.menuItemLabel      (13px, regular, nowrap, overflow hidden)
│   └── div.menuItemContextualText  (font.color.light, padding-left 4px)
└── div.menuItemRightContent   (flex, gap 8px)
    ├── .hoverable-buttons     (opacity 0 → 1 on hover, 75ms)
    ├── RightIcon | RightComponent | hotkeys
    └── .subMenuIcon           (rotates 0deg → 90deg over duration(normal))
```

`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:3-25`:

```scss
@mixin menu-item-base {
  --horizontal-padding: var(--t-spacing-1);   // 4px
  --vertical-padding: var(--t-spacing-2);     // 8px
  box-sizing: content-box;
  border-radius: calc(var(--t-border-radius-md) - var(--t-spacing-1));  // concentric with the dropdown
  font-size: var(--t-font-size-sm);           // 11.96px
  gap: var(--t-spacing-2);                    // 8px
  height: calc(32px - 2 * var(--vertical-padding));
  justify-content: space-between;
  padding: var(--vertical-padding) var(--horizontal-padding);
  width: calc(100% - 2 * var(--horizontal-padding));
  background: transparent;
  transition: background 0.1s ease;
  color: var(--t-font-color-secondary);
}
```

The state matrix is expressed entirely as data attributes in cascade order, which the source
comment explicitly documents as replicating the precedence of the deleted Linaria ternaries
(`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:27-73`):

| Selector | Effect |
|---|---|
| base | text `font.color.secondary`, background transparent |
| `[data-key-selected]`, `[data-focused]` | background `background.transparent.light` — keyboard selection looks identical to hover |
| `[data-accent='danger']` | text `font.color.danger` |
| `[data-accent='placeholder']` | text `font.color.tertiary` |
| `[data-hover-background-disabled]` | `transition: none` |
| `[data-disabled]` | text `font.color.tertiary`, `transition: none` |
| `:hover` | background `background.transparent.light` |
| `[data-hover-background-disabled]:hover` | background transparent |
| `[data-accent='danger']:hover` | background `background.transparent.danger` |
| `[data-disabled]:hover` | background transparent |
| `[data-disabled][data-key-selected]:hover` | background `background.transparent.light` — a disabled row still shows where the keyboard cursor is |

Note the font size: `sm`, not `md`. The *label inside it* is `md`
(`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:14` vs `:128`).

#### (5) `Button` — where the accent semantics are defined

The largest single body of design decisions in the repo. React sets six data attributes and one
inline custom property; every visual decision is made in SCSS
(`packages/twenty-ui/src/input/Button/Button.tsx:91-117`):

```tsx
<ButtonComponent                       // 'button', or react-router Link when `to` is set
  className={clsx(styles.button, styles[size], fullWidth && styles.fullWidth, className)}
  data-variant={variant} data-accent={accent} data-position={position}
  data-inverted={inverted || undefined} data-disabled={isDisabled || undefined}
  data-focus={isFocused || undefined}
  style={{ '--btn-justify': justify }}
>
  {(isLoading || Icon) && <ButtonIcon Icon={Icon} isLoading={!!isLoading} />}
  {isDefined(title) && <ButtonText hasIcon={!!Icon} title={title} isLoading={isLoading} />}
  {hotkeys && !isMobile && <ButtonHotkeys … />}
  {soon && <ButtonSoon />}
</ButtonComponent>
```

Every rule in the matrix assigns only custom properties; the actual declarations live once on the
flat `.button` class. The source comment states why: so that `styled(Button)` overrides in
`twenty-front` keep beating them at (0,1,0) specificity, exactly as the single legacy Linaria class
did (`packages/twenty-ui/src/input/Button/Button.module.scss:7-15`).

```scss
.button {                                        // Button.module.scss:27-70
  background: var(--btn-bg, transparent);
  border-color: var(--btn-border-color, transparent);
  border-radius: var(--btn-radius, var(--t-border-radius-md));
  border-width: var(--btn-border-width, 1px 1px 1px 1px);
  box-shadow: var(--btn-box-shadow, none);
  color: var(--btn-color, var(--t-font-color-secondary));
  font-family: var(--t-font-family);
  font-size: var(--t-font-size-md);
  font-weight: 500;
  gap: var(--t-spacing-1);
  padding: 0 var(--t-spacing-2) 0 var(--t-spacing-2);
  transition: background 0.1s ease;
  white-space: nowrap;
  &:hover  { background: var(--btn-hover-bg, transparent); }
  &:active { background: var(--btn-active-bg, transparent); }
  &:focus  { outline: none; }
  @include focus-ring;
  &[data-disabled] { cursor: not-allowed; }
}
```

`variant="primary"`, not inverted (`packages/twenty-ui/src/input/Button/Button.module.scss:110-159`):

| Accent | Background | Hover | Active | Text | Disabled bg | Disabled text | Focus border | Focus glow |
|---|---|---|---|---|---|---|---|---|
| `default` | `background.transparent.lighter` | `background.tertiary` | `background.quaternary` | `font.color.secondary` | `background.transparent.lighter` | `font.color.extraLight` | `color.blue` | `0 0 0 3px accent.tertiary` |
| `blue` | `color.blue` | `color.blue10` | `color.blue12` | literal `color(display-p3 1 1 1)` | `accent.accent4060` | white | `color.blue` | `0 0 0 3px accent.tertiary` |
| `danger` | `color.red` | `color.red8` | `color.red10` | `background.primary` | `color.red` | `background.primary` | `color.red` | `0 0 0 3px color.red3` |
| `green` | `color.green9` | `color.green10` | `color.green12` | literal white | `color.green3` | `color.green9` | `color.green9` | `0 0 0 3px color.green3` |

`variant="secondary"` / `"tertiary"`, not inverted (`packages/twenty-ui/src/input/Button/Button.module.scss:231-315`) — background
stays transparent for both; they differ only in the resting border, which `secondary` has and
`tertiary` does not:

| Accent | Secondary border | Text | Hover | Active | Disabled text |
|---|---|---|---|---|---|
| `default` | `background.transparent.medium` | `font.color.secondary` | `background.transparent.light` | `background.transparent.light` | `font.color.extraLight` |
| `blue` | `accent.primary` | `color.blue` | `accent.tertiary` | `accent.secondary` | `accent.accent4060` |
| `danger` | `border.color.danger` | `font.color.danger` | `background.danger` | `background.danger` | `color.red5` |
| `green` | `color.green9` | `color.green9` | `color.green3` | `color.green4` | `color.green3` |

`inverted` collapses the matrix: `primary` becomes `background.primary` with a
`background.transparent.light` border and only the *text* colour varies by accent;
`secondary`/`tertiary` become `font.color.inverted` text with transparent-light/medium hover and
press (`packages/twenty-ui/src/input/Button/Button.module.scss:196-224,317-349`).

`position` reshapes only radius and collapses inner borders (`packages/twenty-ui/src/input/Button/Button.module.scss:91-104`):

| `data-position` | `--btn-radius` | `--btn-border-width` |
|---|---|---|
| `standalone` (default) | `var(--t-border-radius-md)` | `1px 1px 1px 1px` |
| `left` | `md 0 0 md` | `1px 0 1px 1px` |
| `middle` | `0px` | `1px 0 1px 0` |
| `right` | `0 md md 0` | `1px 1px 1px 0` |

One documented asymmetry, preserved deliberately: with `variant="primary" accent="default"` the
focus border is dropped when the button is disabled, while `blue`, `danger` and `green` keep
theirs. It is encoded as a `focus-needs-enabled` flag in the SCSS map
(`packages/twenty-ui/src/input/Button/Button.module.scss:107-116,188-190`).

---

## 9 · The CRM patterns

### 9.1 The record table

**Structure.** Not a `<table>`. `div.table-row` (flex row) → `div.table-cell.<width-class>` →
content. Column widths are custom properties written on the table root, one per visible field, so
a resize is a single style mutation instead of a React render
(`packages/twenty-front/src/modules/object-record/record-table/components/RecordTableStyleWrapper.tsx:27-64`):

```ts
style[`--record-table-column-field-${i}`] = `${visibleRecordFields[i].size}px`;
style['--record-table-drag-drop-width'] = isDragColumnHidden ? '0px' : '12px';
style['--record-table-checkbox-width']  = isCheckboxColumnHidden ? '0px' : '28px';
```

`MAX_COLUMNS = 100` static width rules are generated at module load
(`packages/twenty-front/src/modules/object-record/record-table/components/RecordTableStyleWrapper.tsx:27-37`); hiding a column sets its width variable to `0px` rather
than unmounting it.

**Density.** Row height `32px`, and it is the same value for the header row, the body cell and its
inner container (`packages/twenty-front/src/modules/object-record/record-table/constants/RecordTableRowHeight.ts:1`, `packages/twenty-front/src/modules/object-record/record-table/record-table-header/components/RecordTableHeaderCellContainer.tsx:22-24`,
`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx:23`). Cells have `padding: 0`; the field display components
supply their own inset. Minimum column width `104px`. There is no comfortable/compact density
switch on the table — the board has an `isCompact` view flag, the table does not.

**Tokens.**

| Part | Token |
|---|---|
| Cell background | `background.primary` |
| Selected row cell | `accent.quaternary` |
| Grid lines | `border.color.light` (1px) |
| Focused/active row border | `border.color.medium` (1px) |
| Header text | `font.color.tertiary` |
| Header hover / press | `background.secondary` / `background.tertiary` |
| Body text | `font.color.primary` |

**Sticky parts.** Three left columns pin, in this order, each offset by the accumulated widths of
the ones before it (`packages/twenty-front/src/modules/object-record/record-table/components/RecordTableStyleWrapper.tsx:84-141`):

1. the drag handle (`left: 0`, z-index 14 header / 8 body)
2. the checkbox (`left: var(--record-table-drag-drop-width)`)
3. the **label-identifier column** — column 0, the record's name — at
   `left: calc(var(--record-table-drag-drop-width) + var(--record-table-checkbox-width))`

The header row is sticky at the top. Both sticky edges get a generated shadow, not a border:
`packages/twenty-front/src/modules/object-record/record-table/components/HorizontalScrollBoxShadowCSS.ts:4-21` attaches a 4px `::after` with
`clip-path: inset(0px -4px 0px 0px)` so the shadow only bleeds sideways, and its `visibility` is
gated on a custom property that JS toggles when the container scrolls off zero
(`packages/twenty-front/src/modules/object-record/record-table/utils/updateRecordTableCSSVariable.ts:5-10`). The vertical equivalent does the same for the header.

**Selection.** Row selection is a Jotai atom family keyed by record id
(`isRowSelectedComponentFamilyState`), read by `RecordTableTr` and pushed into a row context
(`packages/twenty-front/src/modules/object-record/record-table/record-table-row/components/RecordTableTr.tsx:29-65`). Row *focus* and row *active* are separate
atoms again, and only `data-active` / `data-focused` reach the DOM
(`packages/twenty-front/src/modules/object-record/record-table/record-table-row/components/RecordTableTr.tsx:71-76`) — the highlight is then painted by CSS from the row down
(`packages/twenty-front/src/modules/object-record/record-table/record-table-row/components/RecordTableRowDiv.tsx:17-41`), with a rounded `sm` right edge on the last cell.

**Keyboard.** All bindings go through `useHotkeysOnFocusedElement`, scoped to a focus id, so the
same key means different things depending on whether a row or a cell holds focus.

| Scope | Key | Action | Source |
|---|---|---|---|
| Cell | `↑ ↓ ← →` | move cell focus | `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/hooks/useRecordTableCellFocusHotkeys.ts:16,25,34,43` |
| Cell | `Enter` | open the cell editor (or toggle, for input-only fields) | `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:37-47,87-92` |
| Cell | any printable key | open the editor **and seed it with that character** | `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:49-70,102-110` |
| Cell | `Backspace` / `Delete` | clear the field, if clearable | `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:31-35,80-85` |
| Cell | `Escape` | drop back to row focus | `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:75-77,94-99` |
| Cell / Row / Table | `⌘A` / `Ctrl A` | select all rows | `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:119`, `packages/twenty-front/src/modules/object-record/record-table/record-table-row/hooks/useRecordTableRowHotkeys.ts:143`, `packages/twenty-front/src/modules/object-record/record-table/components/RecordTableWithWrappers.tsx:44` |
| Row | `x` | toggle row selection | `packages/twenty-front/src/modules/object-record/record-table/record-table-row/hooks/useRecordTableRowHotkeys.ts:101-106` |
| Row | `Shift X` | range-select | `packages/twenty-front/src/modules/object-record/record-table/record-table-row/hooks/useRecordTableRowHotkeys.ts:108-113` |
| Row | `⌘Enter` / `Ctrl Enter` | open the record in the side panel | `packages/twenty-front/src/modules/object-record/record-table/record-table-row/hooks/useRecordTableRowHotkeys.ts:115-120` |
| Row | `Enter` | enter the row (move focus into cells) | `packages/twenty-front/src/modules/object-record/record-table/record-table-row/hooks/useRecordTableRowHotkeys.ts:122-127` |
| Row | `Escape` | unfocus, and clear the selection if any | `packages/twenty-front/src/modules/object-record/record-table/record-table-row/hooks/useRecordTableRowHotkeys.ts:94-98,129-134` |

The type-to-edit behaviour is worth copying: `handleAnyKey` filters out non-text-writing keys and
modifier combos, then calls `openTableCell(keyboardEvent.key)` — the editor opens *already
containing* what you typed (`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:49-70`).

### 9.2 Inline editing — read to edit and back

Two distinct implementations, one for the table and one for the record detail panel.

**In the table.** A cell has a display container and an edit container; only one is mounted.

*Read → edit* is triggered by click (`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellDisplayMode.tsx:26-31`, gated on
`!isFieldInputOnly && !isReadOnly`), by `Enter`, or by typing. On open,
`RecordTableCellEditMode` mounts an `OverlayContainer` positioned by floating-ui with
`placement: 'bottom-start'` and a deliberately negative offset
(`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:76-88`):

```tsx
const { refs, floatingStyles } = useFloating({
  placement: 'bottom-start',
  middleware: [flip(), offset({ mainAxis: -33, crossAxis: -3 }), setFieldInputLayoutDirectionMiddleware],
  whileElementsMounted: autoUpdate,
});
```

`mainAxis: -33` pulls the popover back up so that it sits **on top of** the 32px row rather than
below it — the editor visually replaces the cell instead of appearing next to it. `crossAxis: -3`
compensates for the border and padding so the text does not jump horizontally. The custom
middleware records whether floating-ui flipped upward, exposing it as a `layoutDirection` state so
the field input can render its own dropdown the right way up.

The editor container is `position: absolute; width: calc(100% + 2px)` — the extra 2px covers the
cell's 1px borders on both sides (`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:22-30`). Invalid input swaps the
overlay border to `border.color.danger` via `hasDangerBorder`
(`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:111-116`). Fields marked "input only" (checkbox, rating) skip the
overlay entirely and edit in place inside an 8px-padded container
(`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:32-39,102-110`).

*Edit → read* is `Escape` (back to row focus), or the side panel opening
(`useListenToSidePanelOpening(() => onCloseTableCell())`, `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellHotkeysEffect.tsx:79`).

**In the record detail panel.** `RecordInlineCellDisplayMode` is a smaller affordance
(`packages/twenty-front/src/modules/object-record/record-inline-cell/components/RecordInlineCellDisplayMode.tsx:15-41`):

| State | Style |
|---|---|
| Rest | transparent, `border-radius: md`, `min-height: 16px`, `padding: 0 4px` |
| Hover, editable | `background.transparent.light`, `cursor: pointer` |
| Hover, read-only | `outline: 1px solid border.color.medium`, no fill, `cursor: default` |
| Empty | `font.color.light`, fixed `height: 20px` (`packages/twenty-front/src/modules/object-record/record-inline-cell/components/RecordInlineCellDisplayMode.tsx:57-62`) |

So the two surfaces mark "you can edit this" differently: the table uses an outline for
*read-only* hover and no treatment for editable hover; the inline cell uses a fill for editable
hover and an outline for read-only.

### 9.3 The record board (kanban)

Present. Columns are flex children with per-column width driven by a custom property.

| Part | Value | Source |
|---|---|---|
| Column background | `background.primary` | `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumn.tsx:21` |
| Column padding | `spacing[2]` = 8px, `padding-top: 0` | `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumn.tsx:32-33` |
| Column width | default `200`, min `150`, max `400`, live value from a CSS var | `packages/twenty-front/src/modules/object-record/record-board/constants/RecordBoardColumnWidth.ts:1`, `…MinWidth.ts:1`, `…MaxWidth.ts:1`, `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumn.tsx:24-30` |
| Column separator | `border-left: 1px solid border.color.light`, applied only when `columnIndex > 0` via `data-has-left-border` | `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumnHeader.tsx:103-105,198` |
| Header background | `background.primary` (sticky over scrolling cards) | `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumnHeader.tsx:74` |
| Header actions | fade + max-width transition over `duration(fast)`, revealed to `spacing[14]` = 56px | `packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumnHeader.tsx:57-67` |
| Card gap | `padding-bottom: spacing[2]` = 8px on each card wrapper | `packages/twenty-front/src/modules/object-record/record-board/record-board-card/components/RecordBoardCard.tsx:49-52` |
| Multi-drag primary card | `transform: scale(1.02); z-index: 10` | `packages/twenty-front/src/modules/object-record/record-board/record-board-card/components/RecordBoardCard.tsx:42-47` |

The column header uses a `Tag` for the group value, so a kanban column title and a table cell
value for the same select field render identically (`packages/twenty-front/src/modules/object-record/record-board/record-board-column/components/RecordBoardColumnHeader.tsx:108`).
Compact mode is a per-view flag (`currentView.isCompact`) read by the card
(`packages/twenty-front/src/modules/object-record/record-board/record-board-card/components/RecordBoardCard.tsx:78`).

### 9.4 The command menu (⌘K)

Not a centred palette. In this codebase the command menu **is a page inside the right side panel**
— `CommandMenuSidePanelPages`, rendered by `SidePanelRouter`. Opening it opens the panel.

Global bindings (`packages/twenty-front/src/modules/command-menu/hooks/useCommandMenuHotKeys.ts:22-54`):

| Key | Action |
|---|---|
| `⌘K` / `Ctrl K` | close the keyboard-shortcut menu, then toggle the side panel menu |
| `/` | open the records-search page in the side panel |
| `@` | open the Ask-AI page, resetting the navigation stack |
| `Escape` | `handleSidePanelEscape()`, scoped to the side panel focus id |

`/` and `@` are registered with `containsModifier: false` and `ignoreModifiers: true` — bare
single-character global hotkeys, which only works because the hotkey layer is focus-scoped.

Rows are `MenuItem`s (`packages/twenty-front/src/modules/command-menu/components/CommandMenuItem.tsx:54-60`), so the command menu
inherits the whole state matrix from §8.7(4) — including the rule that keyboard selection
(`data-key-selected`) and mouse hover paint the same `background.transparent.light`. A `to` prop
with no explicit `Icon` auto-substitutes `IconArrowUpRight`
(`packages/twenty-front/src/modules/command-menu/components/CommandMenuItem.tsx:45-47`). Result count is capped by `packages/twenty-front/src/modules/command-menu/constants/MaxSearchResults.ts`.

The open/close motion is a framer-motion variant set (`packages/twenty-front/src/modules/side-panel/constants/SidePanelAnimationVariants.ts:3-25`) with
three states — `closed` (`x: '100%'`), `normal` (`x: '0%'`, width `theme.sidePanelWidth` = 500px),
`fullScreen` (100% × 100%).

### 9.5 The right drawer / side panel

`packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx`. It is a resizable, persisted, in-flow `<aside>`,
not an overlay: the main content shrinks to make room.

```tsx
const StyledSidePanelWrapper = styled.div<{ isOpen; isResizing }>`
  flex-shrink: 0;
  overflow: hidden;
  transition: ${({ isResizing }) =>
    isResizing ? 'none' : `width calc(${themeCssVariables.animation.duration.normal} * 1s)`};
  width: ${({ isOpen }) => (isOpen ? `var(--side-panel-width)` : '0px')};
`;
const StyledSidePanel = styled.aside`
  background: ${themeCssVariables.background.primary};
  border-left: 1px solid ${themeCssVariables.border.color.medium};
  display: flex; flex-direction: column; height: 100%;
  overflow: hidden; position: relative;
  width: var(--side-panel-width);
`;
```

| Property | Value | Source |
|---|---|---|
| Width | min `320`, max `600`, default `400`, persisted to localStorage | `packages/twenty-front/src/modules/side-panel/constants/SidePanelConstraints.ts:3-7`, `packages/twenty-front/src/modules/side-panel/states/sidePanelWidthState.ts:6-10` |
| Live width channel | `--side-panel-width` on the panel element | `packages/twenty-front/src/modules/side-panel/states/sidePanelWidthState.ts:4` |
| Surface | `background.primary`, `border-left: 1px solid border.color.medium` — **no shadow** | `packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx:53-56` |
| Open/close | `width` transition over `duration(normal)` = 300ms; `transition: none` while dragging the handle | `packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx:31-37` |
| Full-width → normal | a dedicated `sidePanelShrinkFromFullWidth` keyframe, skipped under `useReducedMotion()` | `packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx:39-50,90-96` |
| Top bar | `48px` desktop, `52px` mobile | `packages/twenty-front/src/modules/side-panel/constants/SidePanelTopBarHeight.ts:1`, `packages/twenty-front/src/modules/side-panel/constants/SidePanelTopBarHeightMobile.ts:1` |
| List padding | `2` | `packages/twenty-front/src/modules/side-panel/constants/SidePanelListPadding.ts:1` |
| Stacking | `RootStackingContextZIndices.SidePanel = 21`, its toggle button `22` | `packages/twenty-front/src/modules/ui/layout/constants/RootStackingContextZIndices.ts:16-17` |
| Modals inside it | a `pointer-events: none`, `z-index: 1` absolute container so panel-scoped modals stack locally | `packages/twenty-front/src/modules/side-panel/components/SidePanelForDesktop.tsx:65-73` |

The panel is a router: `SidePanelRouter` / `SidePanelSubPageRouter` swap pages
(record detail, command menu, Ask AI, search, filters) inside the same chrome, with a navigation
history and a back button (`packages/twenty-front/src/modules/side-panel/components/SidePanelBackButton.tsx`). That is why ⌘K and "open record" land in
the same box.

### 9.6 Chips, tags, and inline record references

Three distinct atoms, and picking the wrong one is the most common way to look off-brand:

| Atom | Use | Shape | Colour source |
|---|---|---|---|
| `Tag` | a **value** of a select/multi-select field | 20px, radius `sm-round`, `corner-shape: round` | `tag.background[color]` over `tag.text[color]` — step 3 under step 11 |
| `Status` | a **select value rendered as a status**, with a leading 4px dot and a pill radius | 20px, radius `pill` | same tag pair; the dot is `background-color: var(--status-text-color)` (`packages/twenty-ui/src/data-display/Status/Status.module.scss:20-29`) |
| `Chip` / `RecordChip` | a **reference to another record** | 12 or 16px content, radius `sm-round` | neutral: `font.color.primary`/`secondary` on `background.transparent.*`; the colour comes from the avatar, not the chip |

The rule that falls out: **coloured chrome means a field value; neutral chrome with an avatar
means a record.** A record reference is never tinted by category colour.

`RecordChip` composes `AvatarOrIcon` into `Chip.leftComponent`, and routes the click through
`useResolveOpenRecordIn` so the same chip opens a side panel or navigates depending on user
preference (`packages/twenty-front/src/modules/object-record/components/RecordChip.tsx:36-58`). It exposes only `Highlighted` and
`Transparent` (`packages/twenty-front/src/modules/object-record/components/RecordChip.tsx:25`). `LinkChip` is the router-link variant, with
`LINK_CHIP_CLICK_OUTSIDE_ID` so click-outside handlers can whitelist it
(`packages/twenty-ui/src/data-display/index.ts:25`).

Truncation is uniform: `Tag`, `Chip` and `Status` all delegate to `OverflowingTextWithTooltip`,
which shows the tooltip **only when the text is actually clipped**.

### 9.7 Filters and sort

Applied filters and sorts render as the same component, `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx`,
differing only in the font weight of the value (`medium` for a sort, `regular` for a filter,
lines 93-99).

```
div (StyledChip)                     24px tall, accent-tinted
├── div StyledIcon        → <Icon size={14} />
├── div StyledKeyLabelContainer
│   ├── div StyledLabelKey        (weight medium)   "Stage"
│   ├── span StyledFilterValue    (weight regular)  "is Customer"
│   ├── span StyledSubFieldSeparator  "·" at opacity 0.6, padding 0 4px
│   └── span StyledSubFieldValue
└── button StyledDelete   20 × 20   → <IconX size={14} stroke={1.6} />
```

| Property | `default` | `danger` |
|---|---|---|
| Background | `accent.quaternary` | `background.danger` |
| Border | `1px solid accent.tertiary` | `1px solid border.color.danger` |
| Text | `color.blue` | `color.red` |
| Delete hover fill | `accent.secondary` | `color.red5` |
| Height / radius / padding | `24px` / `border.radius.smRound` + `corner-shape: round` / `2px`, `4px` on the left | same |
| Font | `font.size.sm`, `font.weight.medium` | same |

This is the only place in the product where a **blue-tinted** container means "a filter is
active". Removing a filter is a nested `<button>` inside a clickable chip, with
`e.stopPropagation()` on its handler (`packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx:144-147`).

Filter *editing* happens in a dropdown built from `MenuItem`s
(`object-record/object-filter-dropdown/components/`), one component per field type
(`…TextInput`, `…DateInput`, `…RecordSelect`, `…BooleanSelect`, `…CountrySelect`, …), all
rendered inside the standard `OverlayContainer`.

### 9.8 Empty states, loading states, skeletons

**Empty states** are a fixed four-part composition
(`packages/twenty-ui/src/feedback/EmptyPlaceholderStyled/EmptyPlaceholderStyled.module.scss`):

```
AnimatedPlaceholderEmptyContainer     centred column, gap 24px, fades in over duration(fast)
├── AnimatedPlaceholder type="…"      two-layer parallax illustration
└── AnimatedPlaceholderEmptyTextContainer   gap 8px
    ├── AnimatedPlaceholderEmptyTitle       font-size lg, semi-bold, font.color.primary
    └── AnimatedPlaceholderEmptySubTitle    font-size sm, regular, font.color.tertiary,
                                            line-height 1.5, max-height 2.8em, width 50%
```

The subtitle is clamped to `max-height: 2.8em` and `width: 50%` — two lines, half the container —
which is what keeps every empty state in the product the same silhouette
(`packages/twenty-ui/src/feedback/EmptyPlaceholderStyled/EmptyPlaceholderStyled.module.scss:39-47`). `AnimatedPlaceholderError*` is the identical
structure with an error illustration set.

The illustration itself is a parallax pair: a static background image and a moving foreground that
tracks the pointer by ±2px via `--parallax-x` / `--parallax-y`
(`packages/twenty-ui/src/feedback/AnimatedPlaceholder/AnimatedPlaceholder.tsx:12,32-49`), with separate light and dark asset constants
(`BACKGROUND` / `DARK_BACKGROUND`, `MOVING_IMAGE` / `DARK_MOVING_IMAGE`).

**Skeletons** use `react-loading-skeleton`, always with the same three-value theme:

```tsx
<SkeletonTheme
  baseColor={theme.background.tertiary}
  highlightColor={theme.background.transparent.lighter}
  borderRadius={4}
>
```

(`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellSkeletonLoader.tsx:16-20`, `packages/twenty-front/src/modules/ai/components/internal/AiChatSkeletonLoader.tsx:65-69`,
`packages/twenty-front/src/modules/activities/components/SkeletonLoader.tsx:47-51` — the last raises `borderRadius` to `80` for its
pill-shaped column bars.) Heights come from `SKELETON_LOADER_HEIGHT_SIZES`
(`packages/twenty-front/src/modules/activities/components/SkeletonLoader.tsx:29-42`, §4.8). A table cell skeleton is `standard.s` = 16px inside
`padding: 6px 8px 0` (`packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellSkeletonLoader.tsx:7-11`).

**Inline loading** is `Loader` (a spinner tinted by `ThemeColor`), `CircularProgressBar`, or —
inside `Button` — the `isLoading` prop, which swaps the icon slot and shrinks the wrapper's
`max-width` by `spacing[8]` to make room (`packages/twenty-ui/src/input/Button/Button.module.scss:23-25`, `packages/twenty-ui/src/input/Button/Button.tsx:118-123`).

### 9.9 The settings area

Settings uses the same tokens and the same components; what differs is the **page frame**.

| Property | App pages | Settings |
|---|---|---|
| Content width | fills the viewport between the drawer and the side panel | `max-width: 760px`, `margin: 0 auto` (`packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx:11,33-34`) |
| Padding | per-page | `24px 32px 32px`, then `padding-bottom: 32 → 80px` (`packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx:36-38`) |
| Section rhythm | per-page | `gap: spacing[8]` = 32px between blocks (`packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx:32`) |
| Density | 32px rows, 0-padding cells | `Card` + `H2Title`/`H3Title` + `Section`, 16px-scale rhythm |
| Scroll | virtualised table | `ScrollWrapper` with per-path scroll restoration keyed on the matched settings route (`packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx:16-22,61-63`) |

So: same palette, same type scale, same controls — a measured column instead of a dense grid. The
`760px` is a literal in the component file, not a token.

---

## 10 · The rules worth stealing

1. **Every colour comes from the theme; hard-coded colours are a lint error.**
   `twenty/no-hardcoded-colors` fails any string literal or template literal matching
   `/(?:rgba?\()|(?:#[0-9a-fA-F]{3,6})\b/`
   (`packages/twenty-oxlint-rules/rules/no-hardcoded-colors.ts:21`). Eleven files opt out, each
   with an explicit `oxlint-disable` — and every one of them is a boundary to something outside the
   theme (Stripe, Monaco, BlockNote, the `RGBA()` helper itself).
2. **Tokens are CSS custom properties, always. The JS mirror is a convenience, not the source.**
   Anything that needs a token in CSS writes `var(--t-…)`; only values that must cross into
   JavaScript as numbers go through `useTheme()`.
3. **Numbers that cross into JS are stored unitless.** Icon sizes, strokes and animation durations
   are `14`, `2`, `0.15`; the unit is added at the point of use (`duration()` in SCSS,
   `calc(… * 1s)` in Linaria). Do this and one token serves both React props and CSS.
4. **32px is the unit of density.** Table row, table cell, header cell, menu item, medium button
   and the page bar are all 32. 24 is the "compact" tier (small button, filter chip). 20 is the
   inline tier (tag, status, empty-field row).
5. **Borders define structure; shadows only lift.** Grid lines, cards, panels and dropdowns all
   get a 1px border. A shadow is added *on top of* a border when something floats
   (`OverlayContainer`, `Modal`), never instead of it. Nothing in the library floats on shadow
   alone.
6. **One border width: 1px.** There is no border-width token because there is nothing to choose.
   Emphasis is expressed by moving between `border.color.light` → `medium` → `strong`, not by
   thickening.
7. **Hover is a transparent overlay, not a colour.** The ladder is
   `transparent.lighter → light → medium → strong`, applied on top of whatever surface you are on,
   so one hover rule works on white, on grey, and inverted. `background.secondary`/`tertiary` are
   used for hover only where the surface underneath is known to be `primary`.
8. **Hover paint is gated on `@media (hover: hover)`.** The `hover-capable` mixin exists because
   "a tap leaves `:hover` applied until the next tap lands elsewhere"
   (`packages/twenty-ui/src/styles/abstracts/_mixins.scss:8-10`). Anything that paints on hover is wrapped.
9. **Hover and keyboard selection look identical.** `[data-key-selected]`, `[data-focused]` and
   `:hover` all resolve to `background.transparent.light` on a menu item
   (`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:31-34,53-55`). Moving the arrow keys through a list looks
   exactly like moving the mouse.
10. **State is expressed as data attributes, styled in CSS; React only decides booleans.**
    `data-variant`, `data-accent`, `data-position`, `data-inverted`, `data-disabled`, `data-focus`
    on `Button`; `data-accent`, `data-key-selected`, `data-focused`, `data-disabled` on
    `MenuItem`. No style objects are computed in render.
11. **Variant matrices assign custom properties only; declarations live once on the base class.**
    That keeps every matrix rule at low specificity so downstream `styled(Button)` overrides still
    win (`packages/twenty-ui/src/input/Button/Button.module.scss:7-15`).
12. **Destructive is `danger`, and it is a full accent, not a colour swap.** `accent="danger"`
    reaches border, text, fill, hover fill and focus glow together
    (`packages/twenty-ui/src/input/Button/Button.module.scss:135-146,252-261`); `MenuItem` gets `font.color.danger` text and a
    `background.transparent.danger` hover (`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:36-38,61-63`). Never
    just paint the label red.
13. **Colour is only decorative in one place: the record colour palette.** The 25 `ThemeColor`
    names exist for user-chosen select options, tags, statuses and avatar placeholders. Everything
    structural draws from grey + the single indigo accent + red/green/orange for status. Blue
    means "selected / filtered / focused", never "primary brand".
14. **A record reference is neutral; a field value is tinted.** See §9.6.
15. **Truncate with a tooltip that only appears when clipped.** `OverflowingTextWithTooltip` is
    used by `Tag`, `Chip` and `Status`, so the behaviour is identical everywhere.
16. **Concentric radii are computed, never guessed.** A child inset by `n` inside a parent with
    radius `r` uses `calc(r - n)` — `calc(var(--t-border-radius-md) - var(--t-spacing-1))` on the
    menu item inside its 8px-radius dropdown (`packages/twenty-ui/src/navigation/MenuItem/parts/StyledMenuItemBase.module.scss:10-11`). Under
    squircles the parent token doubles and the inset does not, which is exactly what keeps them
    concentric (`packages/twenty-ui/src/theme-constants/theme-light.css:1027-1031`).
17. **Pills, circles and chips never become squircles.** `pill`, `rounded`, `sm-round` and
    `md-round` are excluded from the squircle doubling and pin `corner-shape: round` at the call
    site (`packages/twenty-ui/src/data-display/Tag/Tag.module.scss:5-6`, `packages/twenty-ui/src/data-display/Chip/Chip.module.scss:20-21`, `packages/twenty-ui/src/data-display/Status/Status.module.scss:4-5`).
18. **Dense surfaces do not animate.** Table cells have no `transition` at all; menu items drop
    theirs when disabled. The one transition that is everywhere — `background 0.1s ease` — is
    short enough to feel like a repaint.
19. **Declarations are alphabetically sorted, and styled components are named `Styled*`.** Both
    are lint-enforced (`packages/twenty-oxlint-rules/rules/sort-css-properties-alphabetically.ts`,
    `packages/twenty-oxlint-rules/rules/styled-components-prefixed-with-styled.ts`). The payoff is that any two styled blocks in the
    codebase diff cleanly.
20. **Overlay chrome is one recipe, reused.** `blur.medium` backdrop-filter +
    `background.transparent.primary` + `1px border.color.medium` + `boxShadow.strong` +
    `border.radius.md`. Dropdowns, cell editors and floating menus are all literally the same
    `OverlayContainer`, which is why they read as one system.
21. **Z-index is a registry, not a number you pick.** Three enums — root stacking context, table,
    and the theme's `lastLayerZIndex` — with a comment explaining that they were derived by
    inspecting the DOM and must stay in one place
    (`packages/twenty-front/src/modules/ui/layout/constants/RootStackingContextZIndices.ts:1-13`).
22. **Interface scale is `zoom` on `<html>`, not a token rescale.** One property multiplies every
    used length; the tokens never change (`packages/twenty-front/src/index.css:14-23`). Viewport units and pointer maths are
    the only things that need the divisor.

---

## 11 · Where it strains

**Dead tokens.** Grepping every consumer outside the token files themselves:

| Token | Call sites |
|---|---|
| `theme.table.checkboxColumnWidth` (`32px`) | 0 — and it **disagrees** with the real `RECORD_TABLE_COLUMN_CHECKBOX_WIDTH = 28` |
| `theme.table.horizontalCellMargin` / `horizontalCellPadding` (`8px`) | 0 |
| `theme.clickableElementBackgroundTransition` (`background 0.1s ease`) | 0 — while ten SCSS files write the identical string as a literal |
| `theme.buttons.secondaryTextColor` | 0 |
| `border.color.transparentStrong` | 0 |
| `accent.accent3570` | 0 (`accent4060` has 1) |
| `modal.size.lg` (`53%`) | 0 |
| 356 of the 360 `--t-color-transparent-*` tokens | 0 |

`accent3570` and `accent4060` are also *the same value* (`blue8`) in both themes despite their
names implying different opacity targets (`packages/twenty-ui/src/theme/constants/AccentLight.ts:9-10`).

**Two components solving the same problem differently.**

- **Icon size/stroke exists twice.** `theme.icon.{size,stroke}` and `theme.text.{iconSizeSmall,
  iconSizeMedium, iconStrikeLight, iconStrikeMedium, iconStrikeBold}` hold the same five numbers
  under two naming schemes (`packages/twenty-ui/src/theme/constants/Icon.ts:1-13` vs `packages/twenty-ui/src/theme/constants/Text.ts:7-12`) — and "strike" is a typo for
  "stroke" that has been mirrored into the CSS as `--t-text-icon-strike-*`.
- **Two hover conventions for "editable".** The table marks *read-only* hover with an outline and
  leaves editable hover unstyled; the inline cell marks *editable* hover with a fill and read-only
  with an outline (§9.2). Same product, opposite signal.
- **Two theme APIs.** `THEME_LIGHT`/`THEME_DARK` (JS objects, with `spacing()` as a function) and
  `themeCssVariables` (`var()` strings, with `spacing` as an object). The first is effectively
  dead — one consumer, in the Stripe integration — but it is still exported from the package's
  public `theme` entry point, so a newcomer can pick the wrong one and get a `theme.spacing is not
  a function` error at runtime.
- **Two side-panel widths.** `theme.sidePanelWidth = 500px` drives the command-menu animation
  variants while `SIDE_PANEL_CONSTRAINTS.default = 400` drives the actual panel. They are never
  reconciled.

**Hard-coded values that bypass the theme.**

- `packages/twenty-front/src/index.css:34` — `button { font-size: 13px }` instead of
  `var(--t-font-size-md)`.
- `packages/twenty-ui/src/input/Button/Button.module.scss:44` — `font-weight: 500` instead of `var(--t-font-weight-medium)`.
- `packages/twenty-ui/src/input/Button/Button.module.scss:5` — `$gray-scale-light-gray1: color(display-p3 1 1 1)` copied into SCSS as
  a literal, with a comment explaining that it is theme-invariant so it does not need the variable.
  Used for blue and green button text in **both** themes, so a blue button's label is pure white in
  dark mode by design.
- `packages/twenty-ui/src/input/Checkbox/Checkbox.module.scss:28,39` — `1.43px` border widths.
- `packages/twenty-ui/src/typography/Label/Label.module.scss:7,11` — `11px` and `9px`, the only type sizes off the scale.
- `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellBaseContainer.tsx:23`, `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:37`,
  `packages/twenty-front/src/modules/object-record/record-inline-cell/components/RecordInlineCellDisplayMode.tsx:31-32,50-51,61`, `packages/twenty-front/src/modules/views/components/SortOrFilterChip.tsx:47,68,73`,
  `packages/twenty-ui/src/data-display/Avatar/Avatar.module.scss:35-62`, `packages/twenty-front/src/modules/object-record/record-table/record-table-cell/components/RecordTableCellEditMode.tsx:81-82` — pixel literals for heights,
  paddings and floating offsets.
- `packages/twenty-front/src/modules/settings/components/SettingsPageContainer.tsx:11` — `SETTINGS_CONTENT_MAX_WIDTH = 760` is a
  module-local constant, not a token, so nothing else can align to it.
- `packages/twenty-front/src/modules/ui/layout/overlay/components/OverlayContainer.tsx:25` — `z-index: 30`, outside all three z-index registries.

**Naming and structure oddities, recorded as-is.**

- `--t--illustration-icon-color-blue` and its three siblings have a **double dash** after the `t`
  prefix (`packages/twenty-ui/src/theme-constants/theme-light.css:253-256`), an artefact of the generator's key-flattening.
- `packages/twenty-ui/src/data-display/Tag/Tag.module.scss:20` declares `min-width: none`, which is not a valid `min-width` value. The
  comment says it is "kept for byte-equivalence with the deprecated Linaria styles where the
  declaration was equally inert" — a deliberately preserved no-op.
- `theme.name` is a token (`--t-name: light` / `dark`) whose value is a word, not a style.
- Heading sizes do not descend: `H1Title` and `H3Title` are both `lg`, `H2Title` is `md`, so an
  H2 renders smaller than an H3 (§3).
- `--t-last-layer-z-index: 2147483647` — the 32-bit signed maximum. Anything that needs to beat it
  has nowhere to go.

**Accessibility gaps.**

- **Colour contrast is systematically deferred.** 45 of the 71 `*.stories.tsx` files pass
  `A11Y_DEFER_COLOR_CONTRAST`, which sets `test: 'error'` but disables the axe `color-contrast`
  rule outright (`packages/twenty-ui/src/testing/a11yParameters.ts:3-6`). Every `Tag`, `Chip`,
  `Status`, `MenuItem`, `Banner` and `Info` story is in that list. Assume the tag palette
  (step 11 text on step 3 background) has not been verified against WCAG AA, and re-check it
  before shipping.
- **The focus ring covers 11 components.** `@include focus-ring` — the only
  `:focus-visible` treatment in `twenty-ui` — appears in exactly 11 SCSS modules, all of them
  buttons plus `NavigationBarItem`. `Tag`'s interactive `<button>` form, `Chip`, `Toggle`,
  `SegmentedControl`, `TabButton` and every `MenuItem` have **no** `:focus-visible` style. Menu
  items do get `data-focused`, but that is application state, not browser focus.
- **`outline: none` outnumbers `:focus-visible` in the app.** 30 occurrences of `outline: none`
  against 7 of `focus-visible` across `twenty-front`.
- **Hit targets below 24px.** `Chip` at `ChipSize.Small` is a 12px content box with 4px padding
  (20px total); the sort/filter chip's delete button is 20 × 20; the small `Checkbox` is 22px
  including its padding; the `xs` avatar is 12px. All are under the WCAG 2.2 AA 24 × 24 minimum.
- **No global `prefers-reduced-motion` reset.** Reduced motion is honoured in exactly two places
  (the side panel's shrink animation and the welcome overlay). The ubiquitous 100ms background
  transitions and the 75ms opacity fades run regardless.
- **`Status` renders as `<h3>`** (`packages/twenty-ui/src/data-display/Status/Status.tsx:32`) — a heading element used for
  a data value, which pollutes the document outline. Its click affordance is a `tabIndex={0}` div
  with a keydown handler rather than a button.
- **`Tag`'s icon is `aria-hidden`, which is right; `Status`'s dot is a `::before`, also right.**
  But `Loader` inside `Status` has no live-region announcement.

**Copy of the theme is committed to `dist`.** `packages/twenty-ui/dist/theme-light.css` and
`packages/twenty-ui/src/theme-constants/theme-dark.css` are checked in, and the parity test asserts the source and dist copies stay in
sync (`packages/twenty-ui/src/theme-constants/__tests__/cornerShapeThemeParity.test.ts:13`). Editing the source without rebuilding fails
CI rather than silently drifting — worth knowing before you patch a token.

---

## 12 · Port sheet

### 12.1 What ports cleanly, and what does not

The good news: **the tokens are already CSS custom properties.** There is no runtime theme object
to unwind for colour, spacing, radius, type or shadow — you can copy `packages/twenty-ui/src/theme-constants/theme-light.css` and
`packages/twenty-ui/src/theme-constants/theme-dark.css` almost verbatim and be done. What needs work is the five things that are not
plain values.

| Thing | In Twenty | What you must do in Tailwind v4 |
|---|---|---|
| **`theme.spacing(a, b, c)`** | A JS function returning a space-joined px string (`packages/twenty-ui/src/theme/constants/ThemeCommon.ts:12-14`) | Nothing — it has **0 call sites**. The live API is the pre-expanded ladder `--t-spacing-0 … --t-spacing-32`, which maps 1:1 to `--spacing-*`. |
| **Unitless durations** (`0.15`) | Multiplied at use: `calc(var(--t-animation-duration-fast) * 1s)` | Tailwind's `--duration-*` expects a time. Either store `150ms` and lose the JS-readable number, or keep both. The block below stores `150ms`. **This is the one lossy conversion**: nothing downstream can read the duration as a number any more. |
| **Unitless icon size / stroke** (`14`, `1.6`) | Read as numbers through `useTheme()` and passed as React props | Tailwind has no home for these. Keep them as raw `--t-icon-*` custom properties and read them with `getComputedStyle` (or just hard-code 14/16/20/24 and 1.6/2/2.5 in your icon wrapper). **Lossy**: you lose the single source of truth unless you keep the raw vars. |
| **`display-p3` colours** | Every colour token | Tailwind v4 emits whatever you give it; `color(display-p3 …)` passes through fine in modern browsers. But there is **no sRGB fallback anywhere in Twenty** — if you need one you must generate it, and generating it means picking a conversion. This document does not do that. |
| **`corner-shape: squircle`** | `@supports` block doubling six radius tokens (`packages/twenty-ui/src/theme-constants/theme-light.css:1032-1048`) | Keep the `@supports` block verbatim *after* your `@theme`. Tailwind will not know about it, which is fine: it only rewrites the values of the same custom properties. |
| **Root `zoom` / `--t-zoom`** | `html { zoom: var(--t-zoom) }` scales every used length | No Tailwind equivalent, and nothing needs one: it operates below the token layer. Copy `packages/twenty-front/src/index.css:11-31` as-is if you want interface scaling. |
| **`1rem = 13px`** | `html { font-size: 13px }` (`packages/twenty-front/src/index.css:12`) | **You must set this**, or the whole type scale shifts by 23%. Either set `html { font-size: 13px }` and keep the rem values, or convert the scale to px. The block below keeps rem and assumes you set the root. |
| **`ThemeType` numeric coercion** | `ThemeProvider` walks the accessor tree and `Number()`s every leaf that parses (`packages/twenty-ui/src/theme-constants/ThemeProvider.tsx:56-92`) | Drop it. Read the two or three numeric vars you need directly. |

### 12.2 Token → CSS custom property map

The source variable name *is* the custom property; the third column is the idiomatic Tailwind v4
name for the `@theme` block below. Rows marked "keep as-is" are semantic aliases that Tailwind has
no namespace for — declare them as plain custom properties in `:root` / `.dark` and reference them
with `var()` or arbitrary values (`bg-[var(--t-background-primary)]`), or add
`@theme inline { --color-surface: var(--t-background-primary); }` to give them a utility class.

The 348 `--t-color-transparent-<non-gray>` rows are omitted — see §0 and §13. Everything else
from §2–§6 is here.

| Accessor (`themeCssVariables.…`) | Source CSS variable | Suggested Tailwind v4 name |
|---|---|---|
| `icon.size.sm` | `--t-icon-size-sm` | `--t-icon-size-sm`  (semantic; keep as-is) |
| `icon.size.md` | `--t-icon-size-md` | `--t-icon-size-md`  (semantic; keep as-is) |
| `icon.size.lg` | `--t-icon-size-lg` | `--t-icon-size-lg`  (semantic; keep as-is) |
| `icon.size.xl` | `--t-icon-size-xl` | `--t-icon-size-xl`  (semantic; keep as-is) |
| `icon.stroke.sm` | `--t-icon-stroke-sm` | `--t-icon-stroke-sm`  (semantic; keep as-is) |
| `icon.stroke.md` | `--t-icon-stroke-md` | `--t-icon-stroke-md`  (semantic; keep as-is) |
| `icon.stroke.lg` | `--t-icon-stroke-lg` | `--t-icon-stroke-lg`  (semantic; keep as-is) |
| `modal.size.sm.width` | `--t-modal-size-sm-width` | `--t-modal-size-sm-width`  (semantic; keep as-is) |
| `modal.size.md.width` | `--t-modal-size-md-width` | `--t-modal-size-md-width`  (semantic; keep as-is) |
| `modal.size.lg.width` | `--t-modal-size-lg-width` | `--t-modal-size-lg-width`  (semantic; keep as-is) |
| `modal.size.xl.width` | `--t-modal-size-xl-width` | `--t-modal-size-xl-width`  (semantic; keep as-is) |
| `modal.size.xl.height` | `--t-modal-size-xl-height` | `--t-modal-size-xl-height`  (semantic; keep as-is) |
| `modal.size.fullscreen.width` | `--t-modal-size-fullscreen-width` | `--t-modal-size-fullscreen-width`  (semantic; keep as-is) |
| `modal.size.fullscreen.height` | `--t-modal-size-fullscreen-height` | `--t-modal-size-fullscreen-height`  (semantic; keep as-is) |
| `text.lineHeight.lg` | `--t-text-line-height-lg` | `--leading-lg` |
| `text.lineHeight.md` | `--t-text-line-height-md` | `--leading-md` |
| `text.iconSizeMedium` | `--t-text-icon-size-medium` | `--t-text-icon-size-medium`  (semantic; keep as-is) |
| `text.iconSizeSmall` | `--t-text-icon-size-small` | `--t-text-icon-size-small`  (semantic; keep as-is) |
| `text.iconStrikeLight` | `--t-text-icon-strike-light` | `--t-text-icon-strike-light`  (semantic; keep as-is) |
| `text.iconStrikeMedium` | `--t-text-icon-strike-medium` | `--t-text-icon-strike-medium`  (semantic; keep as-is) |
| `text.iconStrikeBold` | `--t-text-icon-strike-bold` | `--t-text-icon-strike-bold`  (semantic; keep as-is) |
| `animation.duration.instant` | `--t-animation-duration-instant` | `--duration-instant` |
| `animation.duration.fast` | `--t-animation-duration-fast` | `--duration-fast` |
| `animation.duration.normal` | `--t-animation-duration-normal` | `--duration-normal` |
| `animation.duration.slow` | `--t-animation-duration-slow` | `--duration-slow` |
| `spacingMultiplicator` | `--t-spacing-multiplicator` | `--spacing-multiplicator` |
| `spacing.0` | `--t-spacing-0` | `--spacing-0` |
| `spacing.1` | `--t-spacing-1` | `--spacing-1` |
| `spacing.2` | `--t-spacing-2` | `--spacing-2` |
| `spacing.3` | `--t-spacing-3` | `--spacing-3` |
| `spacing.4` | `--t-spacing-4` | `--spacing-4` |
| `spacing.5` | `--t-spacing-5` | `--spacing-5` |
| `spacing.6` | `--t-spacing-6` | `--spacing-6` |
| `spacing.7` | `--t-spacing-7` | `--spacing-7` |
| `spacing.8` | `--t-spacing-8` | `--spacing-8` |
| `spacing.9` | `--t-spacing-9` | `--spacing-9` |
| `spacing.10` | `--t-spacing-10` | `--spacing-10` |
| `spacing.11` | `--t-spacing-11` | `--spacing-11` |
| `spacing.12` | `--t-spacing-12` | `--spacing-12` |
| `spacing.13` | `--t-spacing-13` | `--spacing-13` |
| `spacing.14` | `--t-spacing-14` | `--spacing-14` |
| `spacing.15` | `--t-spacing-15` | `--spacing-15` |
| `spacing.16` | `--t-spacing-16` | `--spacing-16` |
| `spacing.17` | `--t-spacing-17` | `--spacing-17` |
| `spacing.18` | `--t-spacing-18` | `--spacing-18` |
| `spacing.19` | `--t-spacing-19` | `--spacing-19` |
| `spacing.20` | `--t-spacing-20` | `--spacing-20` |
| `spacing.21` | `--t-spacing-21` | `--spacing-21` |
| `spacing.22` | `--t-spacing-22` | `--spacing-22` |
| `spacing.23` | `--t-spacing-23` | `--spacing-23` |
| `spacing.24` | `--t-spacing-24` | `--spacing-24` |
| `spacing.25` | `--t-spacing-25` | `--spacing-25` |
| `spacing.26` | `--t-spacing-26` | `--spacing-26` |
| `spacing.27` | `--t-spacing-27` | `--spacing-27` |
| `spacing.28` | `--t-spacing-28` | `--spacing-28` |
| `spacing.29` | `--t-spacing-29` | `--spacing-29` |
| `spacing.30` | `--t-spacing-30` | `--spacing-30` |
| `spacing.31` | `--t-spacing-31` | `--spacing-31` |
| `spacing.32` | `--t-spacing-32` | `--spacing-32` |
| `spacing.0.5` | `--t-spacing-0_5` | `--spacing-0.5` |
| `spacing.1.5` | `--t-spacing-1_5` | `--spacing-1.5` |
| `betweenSiblingsGap` | `--t-between-siblings-gap` | `--t-between-siblings-gap`  (semantic; keep as-is) |
| `table.horizontalCellMargin` | `--t-table-horizontal-cell-margin` | `--t-table-horizontal-cell-margin`  (semantic; keep as-is) |
| `table.checkboxColumnWidth` | `--t-table-checkbox-column-width` | `--t-table-checkbox-column-width`  (semantic; keep as-is) |
| `table.horizontalCellPadding` | `--t-table-horizontal-cell-padding` | `--t-table-horizontal-cell-padding`  (semantic; keep as-is) |
| `sidePanelWidth` | `--t-side-panel-width` | `--t-side-panel-width`  (semantic; keep as-is) |
| `lastLayerZIndex` | `--t-last-layer-z-index` | `--t-last-layer-z-index`  (semantic; keep as-is) |
| `buttons.secondaryTextColor` | `--t-buttons-secondary-text-color` | `--t-buttons-secondary-text-color`  (semantic; keep as-is) |
| `accent.primary` | `--t-accent-primary` | `--t-accent-primary`  (semantic; keep as-is) |
| `accent.secondary` | `--t-accent-secondary` | `--t-accent-secondary`  (semantic; keep as-is) |
| `accent.tertiary` | `--t-accent-tertiary` | `--t-accent-tertiary`  (semantic; keep as-is) |
| `accent.quaternary` | `--t-accent-quaternary` | `--t-accent-quaternary`  (semantic; keep as-is) |
| `accent.accent3570` | `--t-accent-accent3570` | `--color-accent3570` |
| `accent.accent4060` | `--t-accent-accent4060` | `--color-accent4060` |
| `accent.accent1` | `--t-accent-accent1` | `--color-accent1` |
| `accent.accent2` | `--t-accent-accent2` | `--color-accent2` |
| `accent.accent3` | `--t-accent-accent3` | `--color-accent3` |
| `accent.accent4` | `--t-accent-accent4` | `--color-accent4` |
| `accent.accent5` | `--t-accent-accent5` | `--color-accent5` |
| `accent.accent6` | `--t-accent-accent6` | `--color-accent6` |
| `accent.accent7` | `--t-accent-accent7` | `--color-accent7` |
| `accent.accent8` | `--t-accent-accent8` | `--color-accent8` |
| `accent.accent9` | `--t-accent-accent9` | `--color-accent9` |
| `accent.accent10` | `--t-accent-accent10` | `--color-accent10` |
| `accent.accent11` | `--t-accent-accent11` | `--color-accent11` |
| `accent.accent12` | `--t-accent-accent12` | `--color-accent12` |
| `background.noisy` | `--t-background-noisy` | `--t-background-noisy`  (semantic; keep as-is) |
| `background.primary` | `--t-background-primary` | `--t-background-primary`  (semantic; keep as-is) |
| `background.secondary` | `--t-background-secondary` | `--t-background-secondary`  (semantic; keep as-is) |
| `background.tertiary` | `--t-background-tertiary` | `--t-background-tertiary`  (semantic; keep as-is) |
| `background.quaternary` | `--t-background-quaternary` | `--t-background-quaternary`  (semantic; keep as-is) |
| `background.invertedPrimary` | `--t-background-inverted-primary` | `--t-background-inverted-primary`  (semantic; keep as-is) |
| `background.invertedSecondary` | `--t-background-inverted-secondary` | `--t-background-inverted-secondary`  (semantic; keep as-is) |
| `background.danger` | `--t-background-danger` | `--t-background-danger`  (semantic; keep as-is) |
| `background.transparent.primary` | `--t-background-transparent-primary` | `--t-background-transparent-primary`  (semantic; keep as-is) |
| `background.transparent.secondary` | `--t-background-transparent-secondary` | `--t-background-transparent-secondary`  (semantic; keep as-is) |
| `background.transparent.strong` | `--t-background-transparent-strong` | `--t-background-transparent-strong`  (semantic; keep as-is) |
| `background.transparent.medium` | `--t-background-transparent-medium` | `--t-background-transparent-medium`  (semantic; keep as-is) |
| `background.transparent.light` | `--t-background-transparent-light` | `--t-background-transparent-light`  (semantic; keep as-is) |
| `background.transparent.lighter` | `--t-background-transparent-lighter` | `--t-background-transparent-lighter`  (semantic; keep as-is) |
| `background.transparent.danger` | `--t-background-transparent-danger` | `--t-background-transparent-danger`  (semantic; keep as-is) |
| `background.transparent.blue` | `--t-background-transparent-blue` | `--t-background-transparent-blue`  (semantic; keep as-is) |
| `background.transparent.orange` | `--t-background-transparent-orange` | `--t-background-transparent-orange`  (semantic; keep as-is) |
| `background.transparent.success` | `--t-background-transparent-success` | `--t-background-transparent-success`  (semantic; keep as-is) |
| `background.overlayPrimary` | `--t-background-overlay-primary` | `--t-background-overlay-primary`  (semantic; keep as-is) |
| `background.overlaySecondary` | `--t-background-overlay-secondary` | `--t-background-overlay-secondary`  (semantic; keep as-is) |
| `background.overlayTertiary` | `--t-background-overlay-tertiary` | `--t-background-overlay-tertiary`  (semantic; keep as-is) |
| `background.radialGradient` | `--t-background-radial-gradient` | `--t-background-radial-gradient`  (semantic; keep as-is) |
| `background.radialGradientHover` | `--t-background-radial-gradient-hover` | `--t-background-radial-gradient-hover`  (semantic; keep as-is) |
| `background.primaryInverted` | `--t-background-primary-inverted` | `--t-background-primary-inverted`  (semantic; keep as-is) |
| `background.primaryInvertedHover` | `--t-background-primary-inverted-hover` | `--t-background-primary-inverted-hover`  (semantic; keep as-is) |
| `blur.light` | `--t-blur-light` | `--t-blur-light`  (semantic; keep as-is) |
| `blur.medium` | `--t-blur-medium` | `--t-blur-medium`  (semantic; keep as-is) |
| `blur.strong` | `--t-blur-strong` | `--t-blur-strong`  (semantic; keep as-is) |
| `border.color.strong` | `--t-border-color-strong` | `--t-border-color-strong`  (semantic; keep as-is) |
| `border.color.medium` | `--t-border-color-medium` | `--t-border-color-medium`  (semantic; keep as-is) |
| `border.color.light` | `--t-border-color-light` | `--t-border-color-light`  (semantic; keep as-is) |
| `border.color.secondaryInverted` | `--t-border-color-secondary-inverted` | `--t-border-color-secondary-inverted`  (semantic; keep as-is) |
| `border.color.inverted` | `--t-border-color-inverted` | `--t-border-color-inverted`  (semantic; keep as-is) |
| `border.color.danger` | `--t-border-color-danger` | `--t-border-color-danger`  (semantic; keep as-is) |
| `border.color.blue` | `--t-border-color-blue` | `--t-border-color-blue`  (semantic; keep as-is) |
| `border.color.transparentStrong` | `--t-border-color-transparent-strong` | `--t-border-color-transparent-strong`  (semantic; keep as-is) |
| `border.radius.xs` | `--t-border-radius-xs` | `--radius-xs` |
| `border.radius.sm` | `--t-border-radius-sm` | `--radius-sm` |
| `border.radius.md` | `--t-border-radius-md` | `--radius-md` |
| `border.radius.smRound` | `--t-border-radius-sm-round` | `--radius-sm-round` |
| `border.radius.mdRound` | `--t-border-radius-md-round` | `--radius-md-round` |
| `border.radius.lg` | `--t-border-radius-lg` | `--radius-lg` |
| `border.radius.xl` | `--t-border-radius-xl` | `--radius-xl` |
| `border.radius.xxl` | `--t-border-radius-xxl` | `--radius-xxl` |
| `border.radius.pill` | `--t-border-radius-pill` | `--radius-pill` |
| `border.radius.rounded` | `--t-border-radius-rounded` | `--radius-rounded` |
| `boxShadow.color` | `--t-box-shadow-color` | `--t-box-shadow-color`  (semantic; keep as-is) |
| `boxShadow.light` | `--t-box-shadow-light` | `--shadow-light` |
| `boxShadow.strong` | `--t-box-shadow-strong` | `--shadow-strong` |
| `boxShadow.underline` | `--t-box-shadow-underline` | `--shadow-underline` |
| `boxShadow.superHeavy` | `--t-box-shadow-super-heavy` | `--shadow-super-heavy` |
| `font.color.primary` | `--t-font-color-primary` | `--t-font-color-primary`  (semantic; keep as-is) |
| `font.color.secondary` | `--t-font-color-secondary` | `--t-font-color-secondary`  (semantic; keep as-is) |
| `font.color.tertiary` | `--t-font-color-tertiary` | `--t-font-color-tertiary`  (semantic; keep as-is) |
| `font.color.light` | `--t-font-color-light` | `--t-font-color-light`  (semantic; keep as-is) |
| `font.color.extraLight` | `--t-font-color-extra-light` | `--t-font-color-extra-light`  (semantic; keep as-is) |
| `font.color.inverted` | `--t-font-color-inverted` | `--t-font-color-inverted`  (semantic; keep as-is) |
| `font.color.danger` | `--t-font-color-danger` | `--t-font-color-danger`  (semantic; keep as-is) |
| `font.size.xxs` | `--t-font-size-xxs` | `--text-xxs` |
| `font.size.xs` | `--t-font-size-xs` | `--text-xs` |
| `font.size.sm` | `--t-font-size-sm` | `--text-sm` |
| `font.size.md` | `--t-font-size-md` | `--text-md` |
| `font.size.lg` | `--t-font-size-lg` | `--text-lg` |
| `font.size.xl` | `--t-font-size-xl` | `--text-xl` |
| `font.size.xxl` | `--t-font-size-xxl` | `--text-xxl` |
| `font.weight.regular` | `--t-font-weight-regular` | `--font-weight-regular` |
| `font.weight.medium` | `--t-font-weight-medium` | `--font-weight-medium` |
| `font.weight.semiBold` | `--t-font-weight-semi-bold` | `--font-weight-semi-bold` |
| `font.family` | `--t-font-family` | `--font-sans` |
| `name` | `--t-name` | `--t-name`  (semantic; keep as-is) |
| `snackBar.success.color` | `--t-snack-bar-success-color` | `--t-snack-bar-success-color`  (semantic; keep as-is) |
| `snackBar.success.backgroundColor` | `--t-snack-bar-success-background-color` | `--t-snack-bar-success-background-color`  (semantic; keep as-is) |
| `snackBar.error.color` | `--t-snack-bar-error-color` | `--t-snack-bar-error-color`  (semantic; keep as-is) |
| `snackBar.error.backgroundColor` | `--t-snack-bar-error-background-color` | `--t-snack-bar-error-background-color`  (semantic; keep as-is) |
| `snackBar.warning.color` | `--t-snack-bar-warning-color` | `--t-snack-bar-warning-color`  (semantic; keep as-is) |
| `snackBar.warning.backgroundColor` | `--t-snack-bar-warning-background-color` | `--t-snack-bar-warning-background-color`  (semantic; keep as-is) |
| `snackBar.info.color` | `--t-snack-bar-info-color` | `--t-snack-bar-info-color`  (semantic; keep as-is) |
| `snackBar.info.backgroundColor` | `--t-snack-bar-info-background-color` | `--t-snack-bar-info-background-color`  (semantic; keep as-is) |
| `snackBar.default.color` | `--t-snack-bar-default-color` | `--t-snack-bar-default-color`  (semantic; keep as-is) |
| `snackBar.default.backgroundColor` | `--t-snack-bar-default-background-color` | `--t-snack-bar-default-background-color`  (semantic; keep as-is) |
| `tag.text.gray` | `--t-tag-text-gray` | `--t-tag-text-gray`  (semantic; keep as-is) |
| `tag.text.mauve` | `--t-tag-text-mauve` | `--t-tag-text-mauve`  (semantic; keep as-is) |
| `tag.text.slate` | `--t-tag-text-slate` | `--t-tag-text-slate`  (semantic; keep as-is) |
| `tag.text.sage` | `--t-tag-text-sage` | `--t-tag-text-sage`  (semantic; keep as-is) |
| `tag.text.olive` | `--t-tag-text-olive` | `--t-tag-text-olive`  (semantic; keep as-is) |
| `tag.text.sand` | `--t-tag-text-sand` | `--t-tag-text-sand`  (semantic; keep as-is) |
| `tag.text.tomato` | `--t-tag-text-tomato` | `--t-tag-text-tomato`  (semantic; keep as-is) |
| `tag.text.red` | `--t-tag-text-red` | `--t-tag-text-red`  (semantic; keep as-is) |
| `tag.text.ruby` | `--t-tag-text-ruby` | `--t-tag-text-ruby`  (semantic; keep as-is) |
| `tag.text.crimson` | `--t-tag-text-crimson` | `--t-tag-text-crimson`  (semantic; keep as-is) |
| `tag.text.pink` | `--t-tag-text-pink` | `--t-tag-text-pink`  (semantic; keep as-is) |
| `tag.text.plum` | `--t-tag-text-plum` | `--t-tag-text-plum`  (semantic; keep as-is) |
| `tag.text.purple` | `--t-tag-text-purple` | `--t-tag-text-purple`  (semantic; keep as-is) |
| `tag.text.violet` | `--t-tag-text-violet` | `--t-tag-text-violet`  (semantic; keep as-is) |
| `tag.text.iris` | `--t-tag-text-iris` | `--t-tag-text-iris`  (semantic; keep as-is) |
| `tag.text.cyan` | `--t-tag-text-cyan` | `--t-tag-text-cyan`  (semantic; keep as-is) |
| `tag.text.turquoise` | `--t-tag-text-turquoise` | `--t-tag-text-turquoise`  (semantic; keep as-is) |
| `tag.text.sky` | `--t-tag-text-sky` | `--t-tag-text-sky`  (semantic; keep as-is) |
| `tag.text.blue` | `--t-tag-text-blue` | `--t-tag-text-blue`  (semantic; keep as-is) |
| `tag.text.jade` | `--t-tag-text-jade` | `--t-tag-text-jade`  (semantic; keep as-is) |
| `tag.text.green` | `--t-tag-text-green` | `--t-tag-text-green`  (semantic; keep as-is) |
| `tag.text.grass` | `--t-tag-text-grass` | `--t-tag-text-grass`  (semantic; keep as-is) |
| `tag.text.mint` | `--t-tag-text-mint` | `--t-tag-text-mint`  (semantic; keep as-is) |
| `tag.text.lime` | `--t-tag-text-lime` | `--t-tag-text-lime`  (semantic; keep as-is) |
| `tag.text.bronze` | `--t-tag-text-bronze` | `--t-tag-text-bronze`  (semantic; keep as-is) |
| `tag.text.gold` | `--t-tag-text-gold` | `--t-tag-text-gold`  (semantic; keep as-is) |
| `tag.text.brown` | `--t-tag-text-brown` | `--t-tag-text-brown`  (semantic; keep as-is) |
| `tag.text.orange` | `--t-tag-text-orange` | `--t-tag-text-orange`  (semantic; keep as-is) |
| `tag.text.amber` | `--t-tag-text-amber` | `--t-tag-text-amber`  (semantic; keep as-is) |
| `tag.text.yellow` | `--t-tag-text-yellow` | `--t-tag-text-yellow`  (semantic; keep as-is) |
| `tag.background.gray` | `--t-tag-background-gray` | `--t-tag-background-gray`  (semantic; keep as-is) |
| `tag.background.mauve` | `--t-tag-background-mauve` | `--t-tag-background-mauve`  (semantic; keep as-is) |
| `tag.background.slate` | `--t-tag-background-slate` | `--t-tag-background-slate`  (semantic; keep as-is) |
| `tag.background.sage` | `--t-tag-background-sage` | `--t-tag-background-sage`  (semantic; keep as-is) |
| `tag.background.olive` | `--t-tag-background-olive` | `--t-tag-background-olive`  (semantic; keep as-is) |
| `tag.background.sand` | `--t-tag-background-sand` | `--t-tag-background-sand`  (semantic; keep as-is) |
| `tag.background.tomato` | `--t-tag-background-tomato` | `--t-tag-background-tomato`  (semantic; keep as-is) |
| `tag.background.red` | `--t-tag-background-red` | `--t-tag-background-red`  (semantic; keep as-is) |
| `tag.background.ruby` | `--t-tag-background-ruby` | `--t-tag-background-ruby`  (semantic; keep as-is) |
| `tag.background.crimson` | `--t-tag-background-crimson` | `--t-tag-background-crimson`  (semantic; keep as-is) |
| `tag.background.pink` | `--t-tag-background-pink` | `--t-tag-background-pink`  (semantic; keep as-is) |
| `tag.background.plum` | `--t-tag-background-plum` | `--t-tag-background-plum`  (semantic; keep as-is) |
| `tag.background.purple` | `--t-tag-background-purple` | `--t-tag-background-purple`  (semantic; keep as-is) |
| `tag.background.violet` | `--t-tag-background-violet` | `--t-tag-background-violet`  (semantic; keep as-is) |
| `tag.background.iris` | `--t-tag-background-iris` | `--t-tag-background-iris`  (semantic; keep as-is) |
| `tag.background.cyan` | `--t-tag-background-cyan` | `--t-tag-background-cyan`  (semantic; keep as-is) |
| `tag.background.turquoise` | `--t-tag-background-turquoise` | `--t-tag-background-turquoise`  (semantic; keep as-is) |
| `tag.background.sky` | `--t-tag-background-sky` | `--t-tag-background-sky`  (semantic; keep as-is) |
| `tag.background.blue` | `--t-tag-background-blue` | `--t-tag-background-blue`  (semantic; keep as-is) |
| `tag.background.jade` | `--t-tag-background-jade` | `--t-tag-background-jade`  (semantic; keep as-is) |
| `tag.background.green` | `--t-tag-background-green` | `--t-tag-background-green`  (semantic; keep as-is) |
| `tag.background.grass` | `--t-tag-background-grass` | `--t-tag-background-grass`  (semantic; keep as-is) |
| `tag.background.mint` | `--t-tag-background-mint` | `--t-tag-background-mint`  (semantic; keep as-is) |
| `tag.background.lime` | `--t-tag-background-lime` | `--t-tag-background-lime`  (semantic; keep as-is) |
| `tag.background.bronze` | `--t-tag-background-bronze` | `--t-tag-background-bronze`  (semantic; keep as-is) |
| `tag.background.gold` | `--t-tag-background-gold` | `--t-tag-background-gold`  (semantic; keep as-is) |
| `tag.background.brown` | `--t-tag-background-brown` | `--t-tag-background-brown`  (semantic; keep as-is) |
| `tag.background.orange` | `--t-tag-background-orange` | `--t-tag-background-orange`  (semantic; keep as-is) |
| `tag.background.amber` | `--t-tag-background-amber` | `--t-tag-background-amber`  (semantic; keep as-is) |
| `tag.background.yellow` | `--t-tag-background-yellow` | `--t-tag-background-yellow`  (semantic; keep as-is) |
| `code.text.gray` | `--t-code-text-gray` | `--t-code-text-gray`  (semantic; keep as-is) |
| `code.text.sky` | `--t-code-text-sky` | `--t-code-text-sky`  (semantic; keep as-is) |
| `code.text.pink` | `--t-code-text-pink` | `--t-code-text-pink`  (semantic; keep as-is) |
| `code.text.orange` | `--t-code-text-orange` | `--t-code-text-orange`  (semantic; keep as-is) |
| `code.text.green` | `--t-code-text-green` | `--t-code-text-green`  (semantic; keep as-is) |
| `code.font.family` | `--t-code-font-family` | `--font-mono` |
| `IllustrationIcon.color.blue` | `--t--illustration-icon-color-blue` | `--t--illustration-icon-color-blue`  (semantic; keep as-is) |
| `IllustrationIcon.color.gray` | `--t--illustration-icon-color-gray` | `--t--illustration-icon-color-gray`  (semantic; keep as-is) |
| `IllustrationIcon.fill.blue` | `--t--illustration-icon-fill-blue` | `--t--illustration-icon-fill-blue`  (semantic; keep as-is) |
| `IllustrationIcon.fill.gray` | `--t--illustration-icon-fill-gray` | `--t--illustration-icon-fill-gray`  (semantic; keep as-is) |
| `grayScale.gray1` | `--t-gray-scale-gray1` | `--color-gray1` |
| `grayScale.gray2` | `--t-gray-scale-gray2` | `--color-gray2` |
| `grayScale.gray3` | `--t-gray-scale-gray3` | `--color-gray3` |
| `grayScale.gray4` | `--t-gray-scale-gray4` | `--color-gray4` |
| `grayScale.gray5` | `--t-gray-scale-gray5` | `--color-gray5` |
| `grayScale.gray6` | `--t-gray-scale-gray6` | `--color-gray6` |
| `grayScale.gray7` | `--t-gray-scale-gray7` | `--color-gray7` |
| `grayScale.gray8` | `--t-gray-scale-gray8` | `--color-gray8` |
| `grayScale.gray9` | `--t-gray-scale-gray9` | `--color-gray9` |
| `grayScale.gray10` | `--t-gray-scale-gray10` | `--color-gray10` |
| `grayScale.gray11` | `--t-gray-scale-gray11` | `--color-gray11` |
| `grayScale.gray12` | `--t-gray-scale-gray12` | `--color-gray12` |
| `color.red` | `--t-color-red` | `--color-red-base` |
| `color.ruby` | `--t-color-ruby` | `--color-ruby-base` |
| `color.crimson` | `--t-color-crimson` | `--color-crimson-base` |
| `color.tomato` | `--t-color-tomato` | `--color-tomato-base` |
| `color.orange` | `--t-color-orange` | `--color-orange-base` |
| `color.amber` | `--t-color-amber` | `--color-amber-base` |
| `color.yellow` | `--t-color-yellow` | `--color-yellow-base` |
| `color.lime` | `--t-color-lime` | `--color-lime-base` |
| `color.grass` | `--t-color-grass` | `--color-grass-base` |
| `color.green` | `--t-color-green` | `--color-green-base` |
| `color.jade` | `--t-color-jade` | `--color-jade-base` |
| `color.mint` | `--t-color-mint` | `--color-mint-base` |
| `color.turquoise` | `--t-color-turquoise` | `--color-turquoise-base` |
| `color.cyan` | `--t-color-cyan` | `--color-cyan-base` |
| `color.sky` | `--t-color-sky` | `--color-sky-base` |
| `color.blue` | `--t-color-blue` | `--color-blue-base` |
| `color.iris` | `--t-color-iris` | `--color-iris-base` |
| `color.violet` | `--t-color-violet` | `--color-violet-base` |
| `color.purple` | `--t-color-purple` | `--color-purple-base` |
| `color.plum` | `--t-color-plum` | `--color-plum-base` |
| `color.pink` | `--t-color-pink` | `--color-pink-base` |
| `color.bronze` | `--t-color-bronze` | `--color-bronze-base` |
| `color.gold` | `--t-color-gold` | `--color-gold-base` |
| `color.brown` | `--t-color-brown` | `--color-brown-base` |
| `color.gray` | `--t-color-gray` | `--color-gray-base` |
| `color.yellow1` | `--t-color-yellow1` | `--color-yellow1` |
| `color.yellow2` | `--t-color-yellow2` | `--color-yellow2` |
| `color.yellow3` | `--t-color-yellow3` | `--color-yellow3` |
| `color.yellow4` | `--t-color-yellow4` | `--color-yellow4` |
| `color.yellow5` | `--t-color-yellow5` | `--color-yellow5` |
| `color.yellow6` | `--t-color-yellow6` | `--color-yellow6` |
| `color.yellow7` | `--t-color-yellow7` | `--color-yellow7` |
| `color.yellow8` | `--t-color-yellow8` | `--color-yellow8` |
| `color.yellow9` | `--t-color-yellow9` | `--color-yellow9` |
| `color.yellow10` | `--t-color-yellow10` | `--color-yellow10` |
| `color.yellow11` | `--t-color-yellow11` | `--color-yellow11` |
| `color.yellow12` | `--t-color-yellow12` | `--color-yellow12` |
| `color.green1` | `--t-color-green1` | `--color-green1` |
| `color.green2` | `--t-color-green2` | `--color-green2` |
| `color.green3` | `--t-color-green3` | `--color-green3` |
| `color.green4` | `--t-color-green4` | `--color-green4` |
| `color.green5` | `--t-color-green5` | `--color-green5` |
| `color.green6` | `--t-color-green6` | `--color-green6` |
| `color.green7` | `--t-color-green7` | `--color-green7` |
| `color.green8` | `--t-color-green8` | `--color-green8` |
| `color.green9` | `--t-color-green9` | `--color-green9` |
| `color.green10` | `--t-color-green10` | `--color-green10` |
| `color.green11` | `--t-color-green11` | `--color-green11` |
| `color.green12` | `--t-color-green12` | `--color-green12` |
| `color.turquoise1` | `--t-color-turquoise1` | `--color-turquoise1` |
| `color.turquoise2` | `--t-color-turquoise2` | `--color-turquoise2` |
| `color.turquoise3` | `--t-color-turquoise3` | `--color-turquoise3` |
| `color.turquoise4` | `--t-color-turquoise4` | `--color-turquoise4` |
| `color.turquoise5` | `--t-color-turquoise5` | `--color-turquoise5` |
| `color.turquoise6` | `--t-color-turquoise6` | `--color-turquoise6` |
| `color.turquoise7` | `--t-color-turquoise7` | `--color-turquoise7` |
| `color.turquoise8` | `--t-color-turquoise8` | `--color-turquoise8` |
| `color.turquoise9` | `--t-color-turquoise9` | `--color-turquoise9` |
| `color.turquoise10` | `--t-color-turquoise10` | `--color-turquoise10` |
| `color.turquoise11` | `--t-color-turquoise11` | `--color-turquoise11` |
| `color.turquoise12` | `--t-color-turquoise12` | `--color-turquoise12` |
| `color.sky1` | `--t-color-sky1` | `--color-sky1` |
| `color.sky2` | `--t-color-sky2` | `--color-sky2` |
| `color.sky3` | `--t-color-sky3` | `--color-sky3` |
| `color.sky4` | `--t-color-sky4` | `--color-sky4` |
| `color.sky5` | `--t-color-sky5` | `--color-sky5` |
| `color.sky6` | `--t-color-sky6` | `--color-sky6` |
| `color.sky7` | `--t-color-sky7` | `--color-sky7` |
| `color.sky8` | `--t-color-sky8` | `--color-sky8` |
| `color.sky9` | `--t-color-sky9` | `--color-sky9` |
| `color.sky10` | `--t-color-sky10` | `--color-sky10` |
| `color.sky11` | `--t-color-sky11` | `--color-sky11` |
| `color.sky12` | `--t-color-sky12` | `--color-sky12` |
| `color.blue1` | `--t-color-blue1` | `--color-blue1` |
| `color.blue2` | `--t-color-blue2` | `--color-blue2` |
| `color.blue3` | `--t-color-blue3` | `--color-blue3` |
| `color.blue4` | `--t-color-blue4` | `--color-blue4` |
| `color.blue5` | `--t-color-blue5` | `--color-blue5` |
| `color.blue6` | `--t-color-blue6` | `--color-blue6` |
| `color.blue7` | `--t-color-blue7` | `--color-blue7` |
| `color.blue8` | `--t-color-blue8` | `--color-blue8` |
| `color.blue9` | `--t-color-blue9` | `--color-blue9` |
| `color.blue10` | `--t-color-blue10` | `--color-blue10` |
| `color.blue11` | `--t-color-blue11` | `--color-blue11` |
| `color.blue12` | `--t-color-blue12` | `--color-blue12` |
| `color.purple1` | `--t-color-purple1` | `--color-purple1` |
| `color.purple2` | `--t-color-purple2` | `--color-purple2` |
| `color.purple3` | `--t-color-purple3` | `--color-purple3` |
| `color.purple4` | `--t-color-purple4` | `--color-purple4` |
| `color.purple5` | `--t-color-purple5` | `--color-purple5` |
| `color.purple6` | `--t-color-purple6` | `--color-purple6` |
| `color.purple7` | `--t-color-purple7` | `--color-purple7` |
| `color.purple8` | `--t-color-purple8` | `--color-purple8` |
| `color.purple9` | `--t-color-purple9` | `--color-purple9` |
| `color.purple10` | `--t-color-purple10` | `--color-purple10` |
| `color.purple11` | `--t-color-purple11` | `--color-purple11` |
| `color.purple12` | `--t-color-purple12` | `--color-purple12` |
| `color.pink1` | `--t-color-pink1` | `--color-pink1` |
| `color.pink2` | `--t-color-pink2` | `--color-pink2` |
| `color.pink3` | `--t-color-pink3` | `--color-pink3` |
| `color.pink4` | `--t-color-pink4` | `--color-pink4` |
| `color.pink5` | `--t-color-pink5` | `--color-pink5` |
| `color.pink6` | `--t-color-pink6` | `--color-pink6` |
| `color.pink7` | `--t-color-pink7` | `--color-pink7` |
| `color.pink8` | `--t-color-pink8` | `--color-pink8` |
| `color.pink9` | `--t-color-pink9` | `--color-pink9` |
| `color.pink10` | `--t-color-pink10` | `--color-pink10` |
| `color.pink11` | `--t-color-pink11` | `--color-pink11` |
| `color.pink12` | `--t-color-pink12` | `--color-pink12` |
| `color.red1` | `--t-color-red1` | `--color-red1` |
| `color.red2` | `--t-color-red2` | `--color-red2` |
| `color.red3` | `--t-color-red3` | `--color-red3` |
| `color.red4` | `--t-color-red4` | `--color-red4` |
| `color.red5` | `--t-color-red5` | `--color-red5` |
| `color.red6` | `--t-color-red6` | `--color-red6` |
| `color.red7` | `--t-color-red7` | `--color-red7` |
| `color.red8` | `--t-color-red8` | `--color-red8` |
| `color.red9` | `--t-color-red9` | `--color-red9` |
| `color.red10` | `--t-color-red10` | `--color-red10` |
| `color.red11` | `--t-color-red11` | `--color-red11` |
| `color.red12` | `--t-color-red12` | `--color-red12` |
| `color.orange1` | `--t-color-orange1` | `--color-orange1` |
| `color.orange2` | `--t-color-orange2` | `--color-orange2` |
| `color.orange3` | `--t-color-orange3` | `--color-orange3` |
| `color.orange4` | `--t-color-orange4` | `--color-orange4` |
| `color.orange5` | `--t-color-orange5` | `--color-orange5` |
| `color.orange6` | `--t-color-orange6` | `--color-orange6` |
| `color.orange7` | `--t-color-orange7` | `--color-orange7` |
| `color.orange8` | `--t-color-orange8` | `--color-orange8` |
| `color.orange9` | `--t-color-orange9` | `--color-orange9` |
| `color.orange10` | `--t-color-orange10` | `--color-orange10` |
| `color.orange11` | `--t-color-orange11` | `--color-orange11` |
| `color.orange12` | `--t-color-orange12` | `--color-orange12` |
| `color.gray1` | `--t-color-gray1` | `--color-gray1` |
| `color.gray2` | `--t-color-gray2` | `--color-gray2` |
| `color.gray3` | `--t-color-gray3` | `--color-gray3` |
| `color.gray4` | `--t-color-gray4` | `--color-gray4` |
| `color.gray5` | `--t-color-gray5` | `--color-gray5` |
| `color.gray6` | `--t-color-gray6` | `--color-gray6` |
| `color.gray7` | `--t-color-gray7` | `--color-gray7` |
| `color.gray8` | `--t-color-gray8` | `--color-gray8` |
| `color.gray9` | `--t-color-gray9` | `--color-gray9` |
| `color.gray10` | `--t-color-gray10` | `--color-gray10` |
| `color.gray11` | `--t-color-gray11` | `--color-gray11` |
| `color.gray12` | `--t-color-gray12` | `--color-gray12` |
| `color.mauve1` | `--t-color-mauve1` | `--color-mauve1` |
| `color.mauve2` | `--t-color-mauve2` | `--color-mauve2` |
| `color.mauve3` | `--t-color-mauve3` | `--color-mauve3` |
| `color.mauve4` | `--t-color-mauve4` | `--color-mauve4` |
| `color.mauve5` | `--t-color-mauve5` | `--color-mauve5` |
| `color.mauve6` | `--t-color-mauve6` | `--color-mauve6` |
| `color.mauve7` | `--t-color-mauve7` | `--color-mauve7` |
| `color.mauve8` | `--t-color-mauve8` | `--color-mauve8` |
| `color.mauve9` | `--t-color-mauve9` | `--color-mauve9` |
| `color.mauve10` | `--t-color-mauve10` | `--color-mauve10` |
| `color.mauve11` | `--t-color-mauve11` | `--color-mauve11` |
| `color.mauve12` | `--t-color-mauve12` | `--color-mauve12` |
| `color.slate1` | `--t-color-slate1` | `--color-slate1` |
| `color.slate2` | `--t-color-slate2` | `--color-slate2` |
| `color.slate3` | `--t-color-slate3` | `--color-slate3` |
| `color.slate4` | `--t-color-slate4` | `--color-slate4` |
| `color.slate5` | `--t-color-slate5` | `--color-slate5` |
| `color.slate6` | `--t-color-slate6` | `--color-slate6` |
| `color.slate7` | `--t-color-slate7` | `--color-slate7` |
| `color.slate8` | `--t-color-slate8` | `--color-slate8` |
| `color.slate9` | `--t-color-slate9` | `--color-slate9` |
| `color.slate10` | `--t-color-slate10` | `--color-slate10` |
| `color.slate11` | `--t-color-slate11` | `--color-slate11` |
| `color.slate12` | `--t-color-slate12` | `--color-slate12` |
| `color.sage1` | `--t-color-sage1` | `--color-sage1` |
| `color.sage2` | `--t-color-sage2` | `--color-sage2` |
| `color.sage3` | `--t-color-sage3` | `--color-sage3` |
| `color.sage4` | `--t-color-sage4` | `--color-sage4` |
| `color.sage5` | `--t-color-sage5` | `--color-sage5` |
| `color.sage6` | `--t-color-sage6` | `--color-sage6` |
| `color.sage7` | `--t-color-sage7` | `--color-sage7` |
| `color.sage8` | `--t-color-sage8` | `--color-sage8` |
| `color.sage9` | `--t-color-sage9` | `--color-sage9` |
| `color.sage10` | `--t-color-sage10` | `--color-sage10` |
| `color.sage11` | `--t-color-sage11` | `--color-sage11` |
| `color.sage12` | `--t-color-sage12` | `--color-sage12` |
| `color.olive1` | `--t-color-olive1` | `--color-olive1` |
| `color.olive2` | `--t-color-olive2` | `--color-olive2` |
| `color.olive3` | `--t-color-olive3` | `--color-olive3` |
| `color.olive4` | `--t-color-olive4` | `--color-olive4` |
| `color.olive5` | `--t-color-olive5` | `--color-olive5` |
| `color.olive6` | `--t-color-olive6` | `--color-olive6` |
| `color.olive7` | `--t-color-olive7` | `--color-olive7` |
| `color.olive8` | `--t-color-olive8` | `--color-olive8` |
| `color.olive9` | `--t-color-olive9` | `--color-olive9` |
| `color.olive10` | `--t-color-olive10` | `--color-olive10` |
| `color.olive11` | `--t-color-olive11` | `--color-olive11` |
| `color.olive12` | `--t-color-olive12` | `--color-olive12` |
| `color.sand1` | `--t-color-sand1` | `--color-sand1` |
| `color.sand2` | `--t-color-sand2` | `--color-sand2` |
| `color.sand3` | `--t-color-sand3` | `--color-sand3` |
| `color.sand4` | `--t-color-sand4` | `--color-sand4` |
| `color.sand5` | `--t-color-sand5` | `--color-sand5` |
| `color.sand6` | `--t-color-sand6` | `--color-sand6` |
| `color.sand7` | `--t-color-sand7` | `--color-sand7` |
| `color.sand8` | `--t-color-sand8` | `--color-sand8` |
| `color.sand9` | `--t-color-sand9` | `--color-sand9` |
| `color.sand10` | `--t-color-sand10` | `--color-sand10` |
| `color.sand11` | `--t-color-sand11` | `--color-sand11` |
| `color.sand12` | `--t-color-sand12` | `--color-sand12` |
| `color.tomato1` | `--t-color-tomato1` | `--color-tomato1` |
| `color.tomato2` | `--t-color-tomato2` | `--color-tomato2` |
| `color.tomato3` | `--t-color-tomato3` | `--color-tomato3` |
| `color.tomato4` | `--t-color-tomato4` | `--color-tomato4` |
| `color.tomato5` | `--t-color-tomato5` | `--color-tomato5` |
| `color.tomato6` | `--t-color-tomato6` | `--color-tomato6` |
| `color.tomato7` | `--t-color-tomato7` | `--color-tomato7` |
| `color.tomato8` | `--t-color-tomato8` | `--color-tomato8` |
| `color.tomato9` | `--t-color-tomato9` | `--color-tomato9` |
| `color.tomato10` | `--t-color-tomato10` | `--color-tomato10` |
| `color.tomato11` | `--t-color-tomato11` | `--color-tomato11` |
| `color.tomato12` | `--t-color-tomato12` | `--color-tomato12` |
| `color.ruby1` | `--t-color-ruby1` | `--color-ruby1` |
| `color.ruby2` | `--t-color-ruby2` | `--color-ruby2` |
| `color.ruby3` | `--t-color-ruby3` | `--color-ruby3` |
| `color.ruby4` | `--t-color-ruby4` | `--color-ruby4` |
| `color.ruby5` | `--t-color-ruby5` | `--color-ruby5` |
| `color.ruby6` | `--t-color-ruby6` | `--color-ruby6` |
| `color.ruby7` | `--t-color-ruby7` | `--color-ruby7` |
| `color.ruby8` | `--t-color-ruby8` | `--color-ruby8` |
| `color.ruby9` | `--t-color-ruby9` | `--color-ruby9` |
| `color.ruby10` | `--t-color-ruby10` | `--color-ruby10` |
| `color.ruby11` | `--t-color-ruby11` | `--color-ruby11` |
| `color.ruby12` | `--t-color-ruby12` | `--color-ruby12` |
| `color.crimson1` | `--t-color-crimson1` | `--color-crimson1` |
| `color.crimson2` | `--t-color-crimson2` | `--color-crimson2` |
| `color.crimson3` | `--t-color-crimson3` | `--color-crimson3` |
| `color.crimson4` | `--t-color-crimson4` | `--color-crimson4` |
| `color.crimson5` | `--t-color-crimson5` | `--color-crimson5` |
| `color.crimson6` | `--t-color-crimson6` | `--color-crimson6` |
| `color.crimson7` | `--t-color-crimson7` | `--color-crimson7` |
| `color.crimson8` | `--t-color-crimson8` | `--color-crimson8` |
| `color.crimson9` | `--t-color-crimson9` | `--color-crimson9` |
| `color.crimson10` | `--t-color-crimson10` | `--color-crimson10` |
| `color.crimson11` | `--t-color-crimson11` | `--color-crimson11` |
| `color.crimson12` | `--t-color-crimson12` | `--color-crimson12` |
| `color.plum1` | `--t-color-plum1` | `--color-plum1` |
| `color.plum2` | `--t-color-plum2` | `--color-plum2` |
| `color.plum3` | `--t-color-plum3` | `--color-plum3` |
| `color.plum4` | `--t-color-plum4` | `--color-plum4` |
| `color.plum5` | `--t-color-plum5` | `--color-plum5` |
| `color.plum6` | `--t-color-plum6` | `--color-plum6` |
| `color.plum7` | `--t-color-plum7` | `--color-plum7` |
| `color.plum8` | `--t-color-plum8` | `--color-plum8` |
| `color.plum9` | `--t-color-plum9` | `--color-plum9` |
| `color.plum10` | `--t-color-plum10` | `--color-plum10` |
| `color.plum11` | `--t-color-plum11` | `--color-plum11` |
| `color.plum12` | `--t-color-plum12` | `--color-plum12` |
| `color.violet1` | `--t-color-violet1` | `--color-violet1` |
| `color.violet2` | `--t-color-violet2` | `--color-violet2` |
| `color.violet3` | `--t-color-violet3` | `--color-violet3` |
| `color.violet4` | `--t-color-violet4` | `--color-violet4` |
| `color.violet5` | `--t-color-violet5` | `--color-violet5` |
| `color.violet6` | `--t-color-violet6` | `--color-violet6` |
| `color.violet7` | `--t-color-violet7` | `--color-violet7` |
| `color.violet8` | `--t-color-violet8` | `--color-violet8` |
| `color.violet9` | `--t-color-violet9` | `--color-violet9` |
| `color.violet10` | `--t-color-violet10` | `--color-violet10` |
| `color.violet11` | `--t-color-violet11` | `--color-violet11` |
| `color.violet12` | `--t-color-violet12` | `--color-violet12` |
| `color.iris1` | `--t-color-iris1` | `--color-iris1` |
| `color.iris2` | `--t-color-iris2` | `--color-iris2` |
| `color.iris3` | `--t-color-iris3` | `--color-iris3` |
| `color.iris4` | `--t-color-iris4` | `--color-iris4` |
| `color.iris5` | `--t-color-iris5` | `--color-iris5` |
| `color.iris6` | `--t-color-iris6` | `--color-iris6` |
| `color.iris7` | `--t-color-iris7` | `--color-iris7` |
| `color.iris8` | `--t-color-iris8` | `--color-iris8` |
| `color.iris9` | `--t-color-iris9` | `--color-iris9` |
| `color.iris10` | `--t-color-iris10` | `--color-iris10` |
| `color.iris11` | `--t-color-iris11` | `--color-iris11` |
| `color.iris12` | `--t-color-iris12` | `--color-iris12` |
| `color.cyan1` | `--t-color-cyan1` | `--color-cyan1` |
| `color.cyan2` | `--t-color-cyan2` | `--color-cyan2` |
| `color.cyan3` | `--t-color-cyan3` | `--color-cyan3` |
| `color.cyan4` | `--t-color-cyan4` | `--color-cyan4` |
| `color.cyan5` | `--t-color-cyan5` | `--color-cyan5` |
| `color.cyan6` | `--t-color-cyan6` | `--color-cyan6` |
| `color.cyan7` | `--t-color-cyan7` | `--color-cyan7` |
| `color.cyan8` | `--t-color-cyan8` | `--color-cyan8` |
| `color.cyan9` | `--t-color-cyan9` | `--color-cyan9` |
| `color.cyan10` | `--t-color-cyan10` | `--color-cyan10` |
| `color.cyan11` | `--t-color-cyan11` | `--color-cyan11` |
| `color.cyan12` | `--t-color-cyan12` | `--color-cyan12` |
| `color.jade1` | `--t-color-jade1` | `--color-jade1` |
| `color.jade2` | `--t-color-jade2` | `--color-jade2` |
| `color.jade3` | `--t-color-jade3` | `--color-jade3` |
| `color.jade4` | `--t-color-jade4` | `--color-jade4` |
| `color.jade5` | `--t-color-jade5` | `--color-jade5` |
| `color.jade6` | `--t-color-jade6` | `--color-jade6` |
| `color.jade7` | `--t-color-jade7` | `--color-jade7` |
| `color.jade8` | `--t-color-jade8` | `--color-jade8` |
| `color.jade9` | `--t-color-jade9` | `--color-jade9` |
| `color.jade10` | `--t-color-jade10` | `--color-jade10` |
| `color.jade11` | `--t-color-jade11` | `--color-jade11` |
| `color.jade12` | `--t-color-jade12` | `--color-jade12` |
| `color.grass1` | `--t-color-grass1` | `--color-grass1` |
| `color.grass2` | `--t-color-grass2` | `--color-grass2` |
| `color.grass3` | `--t-color-grass3` | `--color-grass3` |
| `color.grass4` | `--t-color-grass4` | `--color-grass4` |
| `color.grass5` | `--t-color-grass5` | `--color-grass5` |
| `color.grass6` | `--t-color-grass6` | `--color-grass6` |
| `color.grass7` | `--t-color-grass7` | `--color-grass7` |
| `color.grass8` | `--t-color-grass8` | `--color-grass8` |
| `color.grass9` | `--t-color-grass9` | `--color-grass9` |
| `color.grass10` | `--t-color-grass10` | `--color-grass10` |
| `color.grass11` | `--t-color-grass11` | `--color-grass11` |
| `color.grass12` | `--t-color-grass12` | `--color-grass12` |
| `color.mint1` | `--t-color-mint1` | `--color-mint1` |
| `color.mint2` | `--t-color-mint2` | `--color-mint2` |
| `color.mint3` | `--t-color-mint3` | `--color-mint3` |
| `color.mint4` | `--t-color-mint4` | `--color-mint4` |
| `color.mint5` | `--t-color-mint5` | `--color-mint5` |
| `color.mint6` | `--t-color-mint6` | `--color-mint6` |
| `color.mint7` | `--t-color-mint7` | `--color-mint7` |
| `color.mint8` | `--t-color-mint8` | `--color-mint8` |
| `color.mint9` | `--t-color-mint9` | `--color-mint9` |
| `color.mint10` | `--t-color-mint10` | `--color-mint10` |
| `color.mint11` | `--t-color-mint11` | `--color-mint11` |
| `color.mint12` | `--t-color-mint12` | `--color-mint12` |
| `color.lime1` | `--t-color-lime1` | `--color-lime1` |
| `color.lime2` | `--t-color-lime2` | `--color-lime2` |
| `color.lime3` | `--t-color-lime3` | `--color-lime3` |
| `color.lime4` | `--t-color-lime4` | `--color-lime4` |
| `color.lime5` | `--t-color-lime5` | `--color-lime5` |
| `color.lime6` | `--t-color-lime6` | `--color-lime6` |
| `color.lime7` | `--t-color-lime7` | `--color-lime7` |
| `color.lime8` | `--t-color-lime8` | `--color-lime8` |
| `color.lime9` | `--t-color-lime9` | `--color-lime9` |
| `color.lime10` | `--t-color-lime10` | `--color-lime10` |
| `color.lime11` | `--t-color-lime11` | `--color-lime11` |
| `color.lime12` | `--t-color-lime12` | `--color-lime12` |
| `color.bronze1` | `--t-color-bronze1` | `--color-bronze1` |
| `color.bronze2` | `--t-color-bronze2` | `--color-bronze2` |
| `color.bronze3` | `--t-color-bronze3` | `--color-bronze3` |
| `color.bronze4` | `--t-color-bronze4` | `--color-bronze4` |
| `color.bronze5` | `--t-color-bronze5` | `--color-bronze5` |
| `color.bronze6` | `--t-color-bronze6` | `--color-bronze6` |
| `color.bronze7` | `--t-color-bronze7` | `--color-bronze7` |
| `color.bronze8` | `--t-color-bronze8` | `--color-bronze8` |
| `color.bronze9` | `--t-color-bronze9` | `--color-bronze9` |
| `color.bronze10` | `--t-color-bronze10` | `--color-bronze10` |
| `color.bronze11` | `--t-color-bronze11` | `--color-bronze11` |
| `color.bronze12` | `--t-color-bronze12` | `--color-bronze12` |
| `color.gold1` | `--t-color-gold1` | `--color-gold1` |
| `color.gold2` | `--t-color-gold2` | `--color-gold2` |
| `color.gold3` | `--t-color-gold3` | `--color-gold3` |
| `color.gold4` | `--t-color-gold4` | `--color-gold4` |
| `color.gold5` | `--t-color-gold5` | `--color-gold5` |
| `color.gold6` | `--t-color-gold6` | `--color-gold6` |
| `color.gold7` | `--t-color-gold7` | `--color-gold7` |
| `color.gold8` | `--t-color-gold8` | `--color-gold8` |
| `color.gold9` | `--t-color-gold9` | `--color-gold9` |
| `color.gold10` | `--t-color-gold10` | `--color-gold10` |
| `color.gold11` | `--t-color-gold11` | `--color-gold11` |
| `color.gold12` | `--t-color-gold12` | `--color-gold12` |
| `color.brown1` | `--t-color-brown1` | `--color-brown1` |
| `color.brown2` | `--t-color-brown2` | `--color-brown2` |
| `color.brown3` | `--t-color-brown3` | `--color-brown3` |
| `color.brown4` | `--t-color-brown4` | `--color-brown4` |
| `color.brown5` | `--t-color-brown5` | `--color-brown5` |
| `color.brown6` | `--t-color-brown6` | `--color-brown6` |
| `color.brown7` | `--t-color-brown7` | `--color-brown7` |
| `color.brown8` | `--t-color-brown8` | `--color-brown8` |
| `color.brown9` | `--t-color-brown9` | `--color-brown9` |
| `color.brown10` | `--t-color-brown10` | `--color-brown10` |
| `color.brown11` | `--t-color-brown11` | `--color-brown11` |
| `color.brown12` | `--t-color-brown12` | `--color-brown12` |
| `color.amber1` | `--t-color-amber1` | `--color-amber1` |
| `color.amber2` | `--t-color-amber2` | `--color-amber2` |
| `color.amber3` | `--t-color-amber3` | `--color-amber3` |
| `color.amber4` | `--t-color-amber4` | `--color-amber4` |
| `color.amber5` | `--t-color-amber5` | `--color-amber5` |
| `color.amber6` | `--t-color-amber6` | `--color-amber6` |
| `color.amber7` | `--t-color-amber7` | `--color-amber7` |
| `color.amber8` | `--t-color-amber8` | `--color-amber8` |
| `color.amber9` | `--t-color-amber9` | `--color-amber9` |
| `color.amber10` | `--t-color-amber10` | `--color-amber10` |
| `color.amber11` | `--t-color-amber11` | `--color-amber11` |
| `color.amber12` | `--t-color-amber12` | `--color-amber12` |
| `color.transparent.gray1` | `--t-color-transparent-gray1` | `--color-transparent-gray1` |
| `color.transparent.gray2` | `--t-color-transparent-gray2` | `--color-transparent-gray2` |
| `color.transparent.gray3` | `--t-color-transparent-gray3` | `--color-transparent-gray3` |
| `color.transparent.gray4` | `--t-color-transparent-gray4` | `--color-transparent-gray4` |
| `color.transparent.gray5` | `--t-color-transparent-gray5` | `--color-transparent-gray5` |
| `color.transparent.gray6` | `--t-color-transparent-gray6` | `--color-transparent-gray6` |
| `color.transparent.gray7` | `--t-color-transparent-gray7` | `--color-transparent-gray7` |
| `color.transparent.gray8` | `--t-color-transparent-gray8` | `--color-transparent-gray8` |
| `color.transparent.gray9` | `--t-color-transparent-gray9` | `--color-transparent-gray9` |
| `color.transparent.gray10` | `--t-color-transparent-gray10` | `--color-transparent-gray10` |
| `color.transparent.gray11` | `--t-color-transparent-gray11` | `--color-transparent-gray11` |
| `color.transparent.gray12` | `--t-color-transparent-gray12` | `--color-transparent-gray12` |

### 12.3 Ready-to-paste Tailwind v4 theme

Three blocks, in this order. Set `html { font-size: 13px }` first or the type scale is wrong.

**Block 1 — the static scale and the full palette.** Colours are the light-theme values; the
semantic aliases are handled in block 2.

Two notes on the spacing entries. The fractional names carry an escaped dot
(`--spacing-0\.5`) because that is what makes Tailwind emit a `p-0.5` utility. And because
Twenty's ladder is exactly `n × 4px` with no exceptions, you can delete all 35 `--spacing-*` lines
and write `--spacing: 4px;` instead — Tailwind v4 then generates the whole scale dynamically,
including values above 32 that Twenty's ladder stops at. The explicit list is kept below so the
port is a literal transcription of `packages/twenty-ui/src/theme-constants/theme-light.css:31-65`; the one-liner is the better long-term
form. The port-map table in §12.2 writes these names unescaped for readability.

```css
@theme {
  /* ---- families ---- */
  --font-sans: Inter, sans-serif;
  --font-mono: 'DM Mono', 'SF Mono', 'Monaco', 'Inconsolata', 'Roboto Mono', monospace;

  /* ---- type scale (1rem === 13px, see §3) ---- */
  --text-xxs: 0.625rem;
  --text-xs: 0.85rem;
  --text-sm: 0.92rem;
  --text-md: 1rem;
  --text-lg: 1.23rem;
  --text-xl: 1.54rem;
  --text-xxl: 1.85rem;
  --leading-md: 1.1;
  --leading-lg: 1.5;
  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semi-bold: 600;

  /* ---- spacing (4px base) ---- */
  --spacing-0: 0px;
  --spacing-1: 4px;
  --spacing-2: 8px;
  --spacing-3: 12px;
  --spacing-4: 16px;
  --spacing-5: 20px;
  --spacing-6: 24px;
  --spacing-7: 28px;
  --spacing-8: 32px;
  --spacing-9: 36px;
  --spacing-10: 40px;
  --spacing-11: 44px;
  --spacing-12: 48px;
  --spacing-13: 52px;
  --spacing-14: 56px;
  --spacing-15: 60px;
  --spacing-16: 64px;
  --spacing-17: 68px;
  --spacing-18: 72px;
  --spacing-19: 76px;
  --spacing-20: 80px;
  --spacing-21: 84px;
  --spacing-22: 88px;
  --spacing-23: 92px;
  --spacing-24: 96px;
  --spacing-25: 100px;
  --spacing-26: 104px;
  --spacing-27: 108px;
  --spacing-28: 112px;
  --spacing-29: 116px;
  --spacing-30: 120px;
  --spacing-31: 124px;
  --spacing-32: 128px;
  --spacing-0\.5: 2px;
  --spacing-1\.5: 6px;

  /* ---- radii (base scale; see §5 for the squircle doubling) ---- */
  --radius-xs: 2px;
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-xl: 20px;
  --radius-xxl: 40px;
  --radius-pill: 999px;
  --radius-rounded: 100%;
  --radius-sm-round: 4px;
  --radius-md-round: 8px;

  /* ---- durations ---- */
  --duration-instant: 75ms;
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 1500ms;

  /* ---- grayscale ---- */
  --color-gray1: color(display-p3 1 1 1);
  --color-gray2: color(display-p3 0.988 0.988 0.988);
  --color-gray3: color(display-p3 0.976 0.976 0.976);
  --color-gray4: color(display-p3 0.945 0.945 0.945);
  --color-gray5: color(display-p3 0.922 0.922 0.922);
  --color-gray6: color(display-p3 0.839 0.839 0.839);
  --color-gray7: color(display-p3 0.8 0.8 0.8);
  --color-gray8: color(display-p3 0.702 0.702 0.702);
  --color-gray9: color(display-p3 0.6 0.6 0.6);
  --color-gray10: color(display-p3 0.514 0.514 0.514);
  --color-gray11: color(display-p3 0.4 0.4 0.4);
  --color-gray12: color(display-p3 0.2 0.2 0.2);

  /* ---- accent (indigo P3) ---- */
  --color-accent3570: color(display-p3 0.569 0.639 0.916);
  --color-accent4060: color(display-p3 0.569 0.639 0.916);
  --color-accent1: color(display-p3 0.992 0.992 0.996);
  --color-accent2: color(display-p3 0.971 0.977 0.998);
  --color-accent3: color(display-p3 0.933 0.948 0.992);
  --color-accent4: color(display-p3 0.885 0.914 1);
  --color-accent5: color(display-p3 0.831 0.87 1);
  --color-accent6: color(display-p3 0.767 0.814 0.995);
  --color-accent7: color(display-p3 0.685 0.74 0.957);
  --color-accent8: color(display-p3 0.569 0.639 0.916);
  --color-accent9: color(display-p3 0.276 0.384 0.837);
  --color-accent10: color(display-p3 0.234 0.343 0.801);
  --color-accent11: color(display-p3 0.256 0.354 0.755);
  --color-accent12: color(display-p3 0.133 0.175 0.348);

  /* ---- full solid ramps, 30 families x 12 ---- */
  --color-yellow1: color(display-p3 0.992 0.992 0.978);
  --color-yellow2: color(display-p3 0.995 0.99 0.922);
  --color-yellow3: color(display-p3 0.997 0.982 0.749);
  --color-yellow4: color(display-p3 0.992 0.953 0.627);
  --color-yellow5: color(display-p3 0.984 0.91 0.51);
  --color-yellow6: color(display-p3 0.934 0.847 0.474);
  --color-yellow7: color(display-p3 0.876 0.785 0.46);
  --color-yellow8: color(display-p3 0.811 0.689 0.313);
  --color-yellow9: color(display-p3 1 0.92 0.22);
  --color-yellow10: color(display-p3 0.977 0.868 0.291);
  --color-yellow11: color(display-p3 0.6 0.44 0);
  --color-yellow12: color(display-p3 0.271 0.233 0.137);
  --color-green1: color(display-p3 0.986 0.996 0.989);
  --color-green2: color(display-p3 0.963 0.983 0.967);
  --color-green3: color(display-p3 0.913 0.964 0.925);
  --color-green4: color(display-p3 0.859 0.94 0.879);
  --color-green5: color(display-p3 0.796 0.907 0.826);
  --color-green6: color(display-p3 0.718 0.863 0.761);
  --color-green7: color(display-p3 0.61 0.801 0.675);
  --color-green8: color(display-p3 0.451 0.715 0.559);
  --color-green9: color(display-p3 0.332 0.634 0.442);
  --color-green10: color(display-p3 0.308 0.595 0.417);
  --color-green11: color(display-p3 0.19 0.5 0.32);
  --color-green12: color(display-p3 0.132 0.228 0.18);
  --color-turquoise1: color(display-p3 0.983 0.996 0.992);
  --color-turquoise2: color(display-p3 0.958 0.983 0.976);
  --color-turquoise3: color(display-p3 0.895 0.971 0.952);
  --color-turquoise4: color(display-p3 0.831 0.949 0.92);
  --color-turquoise5: color(display-p3 0.761 0.914 0.878);
  --color-turquoise6: color(display-p3 0.682 0.864 0.825);
  --color-turquoise7: color(display-p3 0.581 0.798 0.756);
  --color-turquoise8: color(display-p3 0.433 0.716 0.671);
  --color-turquoise9: color(display-p3 0.297 0.637 0.581);
  --color-turquoise10: color(display-p3 0.275 0.599 0.542);
  --color-turquoise11: color(display-p3 0.08 0.5 0.43);
  --color-turquoise12: color(display-p3 0.11 0.235 0.219);
  --color-sky1: color(display-p3 0.98 0.995 0.999);
  --color-sky2: color(display-p3 0.953 0.98 0.99);
  --color-sky3: color(display-p3 0.899 0.963 0.989);
  --color-sky4: color(display-p3 0.842 0.937 0.977);
  --color-sky5: color(display-p3 0.777 0.9 0.954);
  --color-sky6: color(display-p3 0.701 0.851 0.921);
  --color-sky7: color(display-p3 0.604 0.785 0.879);
  --color-sky8: color(display-p3 0.457 0.696 0.829);
  --color-sky9: color(display-p3 0.585 0.877 0.983);
  --color-sky10: color(display-p3 0.555 0.845 0.959);
  --color-sky11: color(display-p3 0.193 0.448 0.605);
  --color-sky12: color(display-p3 0.145 0.241 0.329);
  --color-blue1: color(display-p3 0.992 0.992 0.996);
  --color-blue2: color(display-p3 0.971 0.977 0.998);
  --color-blue3: color(display-p3 0.933 0.948 0.992);
  --color-blue4: color(display-p3 0.885 0.914 1);
  --color-blue5: color(display-p3 0.831 0.87 1);
  --color-blue6: color(display-p3 0.767 0.814 0.995);
  --color-blue7: color(display-p3 0.685 0.74 0.957);
  --color-blue8: color(display-p3 0.569 0.639 0.916);
  --color-blue9: color(display-p3 0.276 0.384 0.837);
  --color-blue10: color(display-p3 0.234 0.343 0.801);
  --color-blue11: color(display-p3 0.256 0.354 0.755);
  --color-blue12: color(display-p3 0.133 0.175 0.348);
  --color-purple1: color(display-p3 0.995 0.988 0.996);
  --color-purple2: color(display-p3 0.983 0.971 0.993);
  --color-purple3: color(display-p3 0.963 0.931 0.989);
  --color-purple4: color(display-p3 0.937 0.888 0.981);
  --color-purple5: color(display-p3 0.904 0.837 0.966);
  --color-purple6: color(display-p3 0.86 0.774 0.942);
  --color-purple7: color(display-p3 0.799 0.69 0.91);
  --color-purple8: color(display-p3 0.719 0.583 0.874);
  --color-purple9: color(display-p3 0.523 0.318 0.751);
  --color-purple10: color(display-p3 0.483 0.289 0.7);
  --color-purple11: color(display-p3 0.473 0.281 0.687);
  --color-purple12: color(display-p3 0.234 0.132 0.363);
  --color-pink1: color(display-p3 0.998 0.989 0.996);
  --color-pink2: color(display-p3 0.992 0.97 0.985);
  --color-pink3: color(display-p3 0.981 0.917 0.96);
  --color-pink4: color(display-p3 0.963 0.867 0.932);
  --color-pink5: color(display-p3 0.939 0.815 0.899);
  --color-pink6: color(display-p3 0.907 0.756 0.859);
  --color-pink7: color(display-p3 0.869 0.683 0.81);
  --color-pink8: color(display-p3 0.825 0.59 0.751);
  --color-pink9: color(display-p3 0.775 0.297 0.61);
  --color-pink10: color(display-p3 0.748 0.27 0.581);
  --color-pink11: color(display-p3 0.698 0.219 0.528);
  --color-pink12: color(display-p3 0.363 0.101 0.279);
  --color-red1: color(display-p3 0.998 0.989 0.988);
  --color-red2: color(display-p3 0.995 0.971 0.971);
  --color-red3: color(display-p3 0.985 0.925 0.925);
  --color-red4: color(display-p3 0.999 0.866 0.866);
  --color-red5: color(display-p3 0.984 0.812 0.811);
  --color-red6: color(display-p3 0.955 0.751 0.749);
  --color-red7: color(display-p3 0.915 0.675 0.672);
  --color-red8: color(display-p3 0.872 0.575 0.572);
  --color-red9: color(display-p3 0.83 0.329 0.324);
  --color-red10: color(display-p3 0.798 0.294 0.285);
  --color-red11: color(display-p3 0.744 0.234 0.222);
  --color-red12: color(display-p3 0.36 0.115 0.143);
  --color-orange1: color(display-p3 0.995 0.988 0.985);
  --color-orange2: color(display-p3 0.994 0.968 0.934);
  --color-orange3: color(display-p3 0.989 0.938 0.85);
  --color-orange4: color(display-p3 1 0.874 0.687);
  --color-orange5: color(display-p3 1 0.821 0.583);
  --color-orange6: color(display-p3 0.975 0.767 0.545);
  --color-orange7: color(display-p3 0.919 0.693 0.486);
  --color-orange8: color(display-p3 0.877 0.597 0.379);
  --color-orange9: color(display-p3 0.9 0.45 0.2);
  --color-orange10: color(display-p3 0.87 0.409 0.164);
  --color-orange11: color(display-p3 0.76 0.34 0);
  --color-orange12: color(display-p3 0.323 0.185 0.127);
  --color-gray1: color(display-p3 1 1 1);
  --color-gray2: color(display-p3 0.988 0.988 0.988);
  --color-gray3: color(display-p3 0.976 0.976 0.976);
  --color-gray4: color(display-p3 0.945 0.945 0.945);
  --color-gray5: color(display-p3 0.922 0.922 0.922);
  --color-gray6: color(display-p3 0.839 0.839 0.839);
  --color-gray7: color(display-p3 0.8 0.8 0.8);
  --color-gray8: color(display-p3 0.702 0.702 0.702);
  --color-gray9: color(display-p3 0.6 0.6 0.6);
  --color-gray10: color(display-p3 0.514 0.514 0.514);
  --color-gray11: color(display-p3 0.4 0.4 0.4);
  --color-gray12: color(display-p3 0.2 0.2 0.2);
  --color-mauve1: color(display-p3 0.991 0.988 0.992);
  --color-mauve2: color(display-p3 0.98 0.976 0.984);
  --color-mauve3: color(display-p3 0.946 0.938 0.952);
  --color-mauve4: color(display-p3 0.915 0.906 0.925);
  --color-mauve5: color(display-p3 0.886 0.876 0.901);
  --color-mauve6: color(display-p3 0.856 0.846 0.875);
  --color-mauve7: color(display-p3 0.814 0.804 0.84);
  --color-mauve8: color(display-p3 0.735 0.728 0.777);
  --color-mauve9: color(display-p3 0.555 0.549 0.596);
  --color-mauve10: color(display-p3 0.514 0.508 0.552);
  --color-mauve11: color(display-p3 0.395 0.388 0.424);
  --color-mauve12: color(display-p3 0.128 0.122 0.147);
  --color-slate1: color(display-p3 0.988 0.988 0.992);
  --color-slate2: color(display-p3 0.976 0.976 0.984);
  --color-slate3: color(display-p3 0.94 0.941 0.953);
  --color-slate4: color(display-p3 0.908 0.909 0.925);
  --color-slate5: color(display-p3 0.88 0.881 0.901);
  --color-slate6: color(display-p3 0.85 0.852 0.876);
  --color-slate7: color(display-p3 0.805 0.808 0.838);
  --color-slate8: color(display-p3 0.727 0.733 0.773);
  --color-slate9: color(display-p3 0.547 0.553 0.592);
  --color-slate10: color(display-p3 0.503 0.512 0.549);
  --color-slate11: color(display-p3 0.379 0.392 0.421);
  --color-slate12: color(display-p3 0.113 0.125 0.14);
  --color-sage1: color(display-p3 0.986 0.992 0.988);
  --color-sage2: color(display-p3 0.97 0.977 0.974);
  --color-sage3: color(display-p3 0.935 0.944 0.94);
  --color-sage4: color(display-p3 0.904 0.913 0.909);
  --color-sage5: color(display-p3 0.875 0.885 0.88);
  --color-sage6: color(display-p3 0.844 0.854 0.849);
  --color-sage7: color(display-p3 0.8 0.811 0.806);
  --color-sage8: color(display-p3 0.725 0.738 0.732);
  --color-sage9: color(display-p3 0.531 0.556 0.546);
  --color-sage10: color(display-p3 0.492 0.515 0.506);
  --color-sage11: color(display-p3 0.377 0.395 0.389);
  --color-sage12: color(display-p3 0.107 0.129 0.118);
  --color-olive1: color(display-p3 0.989 0.992 0.989);
  --color-olive2: color(display-p3 0.974 0.98 0.973);
  --color-olive3: color(display-p3 0.939 0.945 0.937);
  --color-olive4: color(display-p3 0.907 0.914 0.905);
  --color-olive5: color(display-p3 0.878 0.885 0.875);
  --color-olive6: color(display-p3 0.846 0.855 0.843);
  --color-olive7: color(display-p3 0.803 0.812 0.8);
  --color-olive8: color(display-p3 0.727 0.738 0.723);
  --color-olive9: color(display-p3 0.541 0.556 0.532);
  --color-olive10: color(display-p3 0.5 0.515 0.491);
  --color-olive11: color(display-p3 0.38 0.395 0.374);
  --color-olive12: color(display-p3 0.117 0.129 0.111);
  --color-sand1: color(display-p3 0.992 0.992 0.989);
  --color-sand2: color(display-p3 0.977 0.977 0.973);
  --color-sand3: color(display-p3 0.943 0.942 0.936);
  --color-sand4: color(display-p3 0.913 0.912 0.903);
  --color-sand5: color(display-p3 0.885 0.883 0.873);
  --color-sand6: color(display-p3 0.854 0.852 0.839);
  --color-sand7: color(display-p3 0.813 0.81 0.794);
  --color-sand8: color(display-p3 0.738 0.734 0.713);
  --color-sand9: color(display-p3 0.553 0.553 0.528);
  --color-sand10: color(display-p3 0.511 0.511 0.488);
  --color-sand11: color(display-p3 0.388 0.388 0.37);
  --color-sand12: color(display-p3 0.129 0.126 0.111);
  --color-tomato1: color(display-p3 0.998 0.989 0.988);
  --color-tomato2: color(display-p3 0.994 0.974 0.969);
  --color-tomato3: color(display-p3 0.985 0.924 0.909);
  --color-tomato4: color(display-p3 0.996 0.868 0.835);
  --color-tomato5: color(display-p3 0.98 0.812 0.77);
  --color-tomato6: color(display-p3 0.953 0.75 0.698);
  --color-tomato7: color(display-p3 0.917 0.673 0.611);
  --color-tomato8: color(display-p3 0.875 0.575 0.502);
  --color-tomato9: color(display-p3 0.831 0.345 0.231);
  --color-tomato10: color(display-p3 0.802 0.313 0.2);
  --color-tomato11: color(display-p3 0.755 0.259 0.152);
  --color-tomato12: color(display-p3 0.335 0.165 0.132);
  --color-ruby1: color(display-p3 0.998 0.989 0.992);
  --color-ruby2: color(display-p3 0.995 0.971 0.974);
  --color-ruby3: color(display-p3 0.983 0.92 0.928);
  --color-ruby4: color(display-p3 0.987 0.869 0.885);
  --color-ruby5: color(display-p3 0.968 0.817 0.839);
  --color-ruby6: color(display-p3 0.937 0.758 0.786);
  --color-ruby7: color(display-p3 0.897 0.685 0.721);
  --color-ruby8: color(display-p3 0.851 0.588 0.639);
  --color-ruby9: color(display-p3 0.83 0.323 0.408);
  --color-ruby10: color(display-p3 0.795 0.286 0.375);
  --color-ruby11: color(display-p3 0.728 0.211 0.311);
  --color-ruby12: color(display-p3 0.36 0.115 0.171);
  --color-crimson1: color(display-p3 0.998 0.989 0.992);
  --color-crimson2: color(display-p3 0.991 0.969 0.976);
  --color-crimson3: color(display-p3 0.987 0.917 0.941);
  --color-crimson4: color(display-p3 0.975 0.866 0.904);
  --color-crimson5: color(display-p3 0.953 0.813 0.864);
  --color-crimson6: color(display-p3 0.921 0.755 0.817);
  --color-crimson7: color(display-p3 0.88 0.683 0.761);
  --color-crimson8: color(display-p3 0.834 0.592 0.694);
  --color-crimson9: color(display-p3 0.843 0.298 0.507);
  --color-crimson10: color(display-p3 0.807 0.266 0.468);
  --color-crimson11: color(display-p3 0.731 0.195 0.388);
  --color-crimson12: color(display-p3 0.352 0.111 0.221);
  --color-plum1: color(display-p3 0.995 0.988 0.999);
  --color-plum2: color(display-p3 0.988 0.971 0.99);
  --color-plum3: color(display-p3 0.973 0.923 0.98);
  --color-plum4: color(display-p3 0.953 0.875 0.966);
  --color-plum5: color(display-p3 0.926 0.825 0.945);
  --color-plum6: color(display-p3 0.89 0.765 0.916);
  --color-plum7: color(display-p3 0.84 0.686 0.877);
  --color-plum8: color(display-p3 0.775 0.58 0.832);
  --color-plum9: color(display-p3 0.624 0.313 0.708);
  --color-plum10: color(display-p3 0.587 0.29 0.667);
  --color-plum11: color(display-p3 0.543 0.263 0.619);
  --color-plum12: color(display-p3 0.299 0.114 0.352);
  --color-violet1: color(display-p3 0.991 0.988 0.995);
  --color-violet2: color(display-p3 0.978 0.974 0.998);
  --color-violet3: color(display-p3 0.953 0.943 0.993);
  --color-violet4: color(display-p3 0.916 0.897 1);
  --color-violet5: color(display-p3 0.876 0.851 1);
  --color-violet6: color(display-p3 0.825 0.793 0.981);
  --color-violet7: color(display-p3 0.752 0.712 0.943);
  --color-violet8: color(display-p3 0.654 0.602 0.902);
  --color-violet9: color(display-p3 0.417 0.341 0.784);
  --color-violet10: color(display-p3 0.381 0.306 0.741);
  --color-violet11: color(display-p3 0.383 0.317 0.702);
  --color-violet12: color(display-p3 0.179 0.15 0.359);
  --color-iris1: color(display-p3 0.992 0.992 0.999);
  --color-iris2: color(display-p3 0.972 0.973 0.998);
  --color-iris3: color(display-p3 0.943 0.945 0.992);
  --color-iris4: color(display-p3 0.902 0.906 1);
  --color-iris5: color(display-p3 0.857 0.861 1);
  --color-iris6: color(display-p3 0.799 0.805 0.987);
  --color-iris7: color(display-p3 0.721 0.727 0.955);
  --color-iris8: color(display-p3 0.61 0.619 0.918);
  --color-iris9: color(display-p3 0.357 0.357 0.81);
  --color-iris10: color(display-p3 0.318 0.318 0.774);
  --color-iris11: color(display-p3 0.337 0.326 0.748);
  --color-iris12: color(display-p3 0.154 0.161 0.371);
  --color-cyan1: color(display-p3 0.982 0.992 0.996);
  --color-cyan2: color(display-p3 0.955 0.981 0.984);
  --color-cyan3: color(display-p3 0.888 0.965 0.975);
  --color-cyan4: color(display-p3 0.821 0.941 0.959);
  --color-cyan5: color(display-p3 0.751 0.907 0.935);
  --color-cyan6: color(display-p3 0.671 0.862 0.9);
  --color-cyan7: color(display-p3 0.564 0.8 0.854);
  --color-cyan8: color(display-p3 0.388 0.715 0.798);
  --color-cyan9: color(display-p3 0.282 0.627 0.765);
  --color-cyan10: color(display-p3 0.264 0.583 0.71);
  --color-cyan11: color(display-p3 0.08 0.48 0.63);
  --color-cyan12: color(display-p3 0.108 0.232 0.277);
  --color-jade1: color(display-p3 0.986 0.996 0.992);
  --color-jade2: color(display-p3 0.962 0.983 0.969);
  --color-jade3: color(display-p3 0.912 0.965 0.932);
  --color-jade4: color(display-p3 0.858 0.941 0.893);
  --color-jade5: color(display-p3 0.795 0.909 0.847);
  --color-jade6: color(display-p3 0.715 0.864 0.791);
  --color-jade7: color(display-p3 0.603 0.802 0.718);
  --color-jade8: color(display-p3 0.44 0.72 0.629);
  --color-jade9: color(display-p3 0.319 0.63 0.521);
  --color-jade10: color(display-p3 0.299 0.592 0.488);
  --color-jade11: color(display-p3 0.15 0.5 0.37);
  --color-jade12: color(display-p3 0.142 0.229 0.194);
  --color-grass1: color(display-p3 0.986 0.996 0.985);
  --color-grass2: color(display-p3 0.966 0.983 0.964);
  --color-grass3: color(display-p3 0.923 0.965 0.917);
  --color-grass4: color(display-p3 0.872 0.94 0.865);
  --color-grass5: color(display-p3 0.811 0.908 0.802);
  --color-grass6: color(display-p3 0.733 0.864 0.724);
  --color-grass7: color(display-p3 0.628 0.803 0.622);
  --color-grass8: color(display-p3 0.477 0.72 0.482);
  --color-grass9: color(display-p3 0.38 0.647 0.378);
  --color-grass10: color(display-p3 0.344 0.598 0.342);
  --color-grass11: color(display-p3 0.263 0.488 0.261);
  --color-grass12: color(display-p3 0.151 0.233 0.153);
  --color-mint1: color(display-p3 0.98 0.995 0.992);
  --color-mint2: color(display-p3 0.957 0.985 0.977);
  --color-mint3: color(display-p3 0.888 0.972 0.95);
  --color-mint4: color(display-p3 0.819 0.951 0.916);
  --color-mint5: color(display-p3 0.747 0.918 0.873);
  --color-mint6: color(display-p3 0.668 0.87 0.818);
  --color-mint7: color(display-p3 0.567 0.805 0.744);
  --color-mint8: color(display-p3 0.42 0.724 0.649);
  --color-mint9: color(display-p3 0.62 0.908 0.834);
  --color-mint10: color(display-p3 0.585 0.871 0.797);
  --color-mint11: color(display-p3 0.203 0.463 0.397);
  --color-mint12: color(display-p3 0.136 0.259 0.236);
  --color-lime1: color(display-p3 0.989 0.992 0.981);
  --color-lime2: color(display-p3 0.975 0.98 0.954);
  --color-lime3: color(display-p3 0.939 0.965 0.851);
  --color-lime4: color(display-p3 0.896 0.94 0.76);
  --color-lime5: color(display-p3 0.843 0.903 0.678);
  --color-lime6: color(display-p3 0.778 0.852 0.599);
  --color-lime7: color(display-p3 0.694 0.784 0.508);
  --color-lime8: color(display-p3 0.585 0.707 0.378);
  --color-lime9: color(display-p3 0.78 0.928 0.466);
  --color-lime10: color(display-p3 0.734 0.896 0.397);
  --color-lime11: color(display-p3 0.386 0.482 0.227);
  --color-lime12: color(display-p3 0.222 0.25 0.128);
  --color-bronze1: color(display-p3 0.991 0.988 0.988);
  --color-bronze2: color(display-p3 0.989 0.97 0.961);
  --color-bronze3: color(display-p3 0.958 0.932 0.919);
  --color-bronze4: color(display-p3 0.929 0.894 0.877);
  --color-bronze5: color(display-p3 0.898 0.853 0.832);
  --color-bronze6: color(display-p3 0.861 0.805 0.778);
  --color-bronze7: color(display-p3 0.812 0.739 0.706);
  --color-bronze8: color(display-p3 0.741 0.647 0.606);
  --color-bronze9: color(display-p3 0.611 0.507 0.455);
  --color-bronze10: color(display-p3 0.563 0.461 0.414);
  --color-bronze11: color(display-p3 0.471 0.373 0.336);
  --color-bronze12: color(display-p3 0.251 0.191 0.172);
  --color-gold1: color(display-p3 0.992 0.992 0.989);
  --color-gold2: color(display-p3 0.98 0.976 0.953);
  --color-gold3: color(display-p3 0.947 0.94 0.909);
  --color-gold4: color(display-p3 0.914 0.904 0.865);
  --color-gold5: color(display-p3 0.88 0.865 0.816);
  --color-gold6: color(display-p3 0.84 0.818 0.756);
  --color-gold7: color(display-p3 0.788 0.753 0.677);
  --color-gold8: color(display-p3 0.715 0.66 0.565);
  --color-gold9: color(display-p3 0.579 0.517 0.41);
  --color-gold10: color(display-p3 0.538 0.479 0.38);
  --color-gold11: color(display-p3 0.433 0.386 0.305);
  --color-gold12: color(display-p3 0.227 0.209 0.173);
  --color-brown1: color(display-p3 0.995 0.992 0.989);
  --color-brown2: color(display-p3 0.987 0.976 0.964);
  --color-brown3: color(display-p3 0.959 0.936 0.909);
  --color-brown4: color(display-p3 0.934 0.897 0.855);
  --color-brown5: color(display-p3 0.909 0.856 0.798);
  --color-brown6: color(display-p3 0.88 0.808 0.73);
  --color-brown7: color(display-p3 0.841 0.742 0.639);
  --color-brown8: color(display-p3 0.782 0.647 0.514);
  --color-brown9: color(display-p3 0.651 0.505 0.368);
  --color-brown10: color(display-p3 0.601 0.465 0.344);
  --color-brown11: color(display-p3 0.485 0.374 0.288);
  --color-brown12: color(display-p3 0.236 0.202 0.183);
  --color-amber1: color(display-p3 0.995 0.992 0.985);
  --color-amber2: color(display-p3 0.994 0.986 0.921);
  --color-amber3: color(display-p3 0.994 0.969 0.782);
  --color-amber4: color(display-p3 0.989 0.937 0.65);
  --color-amber5: color(display-p3 0.97 0.902 0.527);
  --color-amber6: color(display-p3 0.936 0.844 0.506);
  --color-amber7: color(display-p3 0.89 0.762 0.443);
  --color-amber8: color(display-p3 0.85 0.65 0.3);
  --color-amber9: color(display-p3 1 0.77 0.26);
  --color-amber10: color(display-p3 0.959 0.741 0.274);
  --color-amber11: color(display-p3 0.64 0.4 0);
  --color-amber12: color(display-p3 0.294 0.208 0.145);

  /* ---- 25 named record colours (ThemeColor union) ---- */
  --color-red-base: color(display-p3 0.83 0.329 0.324);
  --color-ruby-base: color(display-p3 0.83 0.323 0.408);
  --color-crimson-base: color(display-p3 0.843 0.298 0.507);
  --color-tomato-base: color(display-p3 0.831 0.345 0.231);
  --color-orange-base: color(display-p3 0.9 0.45 0.2);
  --color-amber-base: color(display-p3 1 0.77 0.26);
  --color-yellow-base: color(display-p3 1 0.92 0.22);
  --color-lime-base: color(display-p3 0.78 0.928 0.466);
  --color-grass-base: color(display-p3 0.38 0.647 0.378);
  --color-green-base: color(display-p3 0.332 0.634 0.442);
  --color-jade-base: color(display-p3 0.319 0.63 0.521);
  --color-mint-base: color(display-p3 0.62 0.908 0.834);
  --color-turquoise-base: color(display-p3 0.297 0.637 0.581);
  --color-cyan-base: color(display-p3 0.282 0.627 0.765);
  --color-sky-base: color(display-p3 0.585 0.877 0.983);
  --color-blue-base: color(display-p3 0.276 0.384 0.837);
  --color-iris-base: color(display-p3 0.357 0.357 0.81);
  --color-violet-base: color(display-p3 0.417 0.341 0.784);
  --color-purple-base: color(display-p3 0.523 0.318 0.751);
  --color-plum-base: color(display-p3 0.624 0.313 0.708);
  --color-pink-base: color(display-p3 0.775 0.297 0.61);
  --color-bronze-base: color(display-p3 0.611 0.507 0.455);
  --color-gold-base: color(display-p3 0.579 0.517 0.41);
  --color-brown-base: color(display-p3 0.651 0.505 0.368);
  --color-gray-base: color(display-p3 0.6 0.6 0.6);

  /* ---- transparent gray ramp (the app's hover/press scale) ---- */
  --color-transparent-gray1: color(display-p3 0 0 0 / 0.02);
  --color-transparent-gray2: color(display-p3 0 0 0 / 0.039);
  --color-transparent-gray3: color(display-p3 0 0 0 / 0.047);
  --color-transparent-gray4: color(display-p3 0 0 0 / 0.071);
  --color-transparent-gray5: color(display-p3 0 0 0 / 0.078);
  --color-transparent-gray6: color(display-p3 0 0 0 / 0.114);
  --color-transparent-gray7: color(display-p3 0 0 0 / 0.161);
  --color-transparent-gray8: color(display-p3 0 0 0 / 0.22);
  --color-transparent-gray9: color(display-p3 0 0 0 / 0.361);
  --color-transparent-gray10: color(display-p3 0 0 0 / 0.478);
  --color-transparent-gray11: color(display-p3 0 0 0 / 0.722);
  --color-transparent-gray12: color(display-p3 0 0 0 / 0.91);

  /* ---- shadows ---- */
  --shadow-light: 0px 2px 4px 0px color(display-p3 0 0 0 / 0.039), 0px 0px 4px 0px color(display-p3 0 0 0 / 0.078);
  --shadow-strong: 2px 4px 16px 0px color(display-p3 0 0 0 / 0.161), 0px 2px 4px 0px color(display-p3 0 0 0 / 0.078);
  --shadow-underline: 0px 1px 0px 0px color(display-p3 0 0 0 / 0.361);
  --shadow-super-heavy: 0px 0px 8px 0px color(display-p3 0 0 0 / 0.161), 0px 8px 64px -16px color(display-p3 0 0 0 / 0.478), 0px 24px 56px -16px color(display-p3 0 0 0 / 0.078);
}
```

**Block 2 — the semantic layer, light and dark.** Tailwind's `@theme` has no notion of a colour
scheme, so the aliases live as ordinary custom properties. Put this *after* block 1. Add
`@custom-variant dark (&:where(.dark, .dark *));` if you want a `dark:` variant driven by the same
class Twenty uses.

```css
:root, .light {
  --t-background-primary: color(display-p3 1 1 1);
  --t-background-secondary: color(display-p3 0.988 0.988 0.988);
  --t-background-tertiary: color(display-p3 0.945 0.945 0.945);
  --t-background-quaternary: color(display-p3 0.922 0.922 0.922);
  --t-background-inverted-primary: color(display-p3 0.2 0.2 0.2);
  --t-background-inverted-secondary: color(display-p3 0.4 0.4 0.4);
  --t-background-danger: color(display-p3 0.985 0.925 0.925);
  --t-background-transparent-primary: color(display-p3 1 1 1 / 0.5);
  --t-background-transparent-secondary: color(display-p3 1 1 1 / 0.4);
  --t-background-transparent-strong: color(display-p3 0 0 0 / 0.161);
  --t-background-transparent-medium: color(display-p3 0 0 0 / 0.078);
  --t-background-transparent-light: color(display-p3 0 0 0 / 0.039);
  --t-background-transparent-lighter: color(display-p3 0 0 0 / 0.02);
  --t-background-transparent-danger: #f3000d14;
  --t-background-transparent-blue: #0047f112;
  --t-background-transparent-orange: #ff9c0029;
  --t-background-transparent-success: #00a43319;
  --t-background-overlay-primary: color(display-p3 0 0 0 / 0.722);
  --t-background-overlay-secondary: color(display-p3 0 0 0 / 0.361);
  --t-background-overlay-tertiary: color(display-p3 0 0 0 / 0.071);
  --t-background-radial-gradient: radial-gradient( 50% 62.62% at 50% 0%, color(display-p3 0.6 0.6 0.6) 0%, color(display-p3 0.514 0.514 0.514) 100% );
  --t-background-radial-gradient-hover: radial-gradient( 76.32% 95.59% at 50% 0%, color(display-p3 0.514 0.514 0.514) 0%, color(display-p3 0.4 0.4 0.4) 100% );
  --t-background-primary-inverted: color(display-p3 0.2 0.2 0.2);
  --t-background-primary-inverted-hover: color(display-p3 0.4 0.4 0.4);
  --t-border-color-strong: color(display-p3 0.839 0.839 0.839);
  --t-border-color-medium: color(display-p3 0.922 0.922 0.922);
  --t-border-color-light: color(display-p3 0.945 0.945 0.945);
  --t-border-color-secondary-inverted: color(display-p3 0.4 0.4 0.4);
  --t-border-color-inverted: color(display-p3 0.2 0.2 0.2);
  --t-border-color-danger: color(display-p3 0.984 0.812 0.811);
  --t-border-color-blue: color(display-p3 0.685 0.74 0.957);
  --t-border-color-transparent-strong: color(display-p3 0 0 0 / 0.071);
  --t-font-color-primary: color(display-p3 0.2 0.2 0.2);
  --t-font-color-secondary: color(display-p3 0.4 0.4 0.4);
  --t-font-color-tertiary: color(display-p3 0.6 0.6 0.6);
  --t-font-color-light: color(display-p3 0.702 0.702 0.702);
  --t-font-color-extra-light: color(display-p3 0.8 0.8 0.8);
  --t-font-color-inverted: color(display-p3 1 1 1);
  --t-font-color-danger: color(display-p3 0.83 0.329 0.324);
  --t-box-shadow-color: color(display-p3 0 0 0 / 0.039);
  --t-box-shadow-light: 0px 2px 4px 0px color(display-p3 0 0 0 / 0.039), 0px 0px 4px 0px color(display-p3 0 0 0 / 0.078);
  --t-box-shadow-strong: 2px 4px 16px 0px color(display-p3 0 0 0 / 0.161), 0px 2px 4px 0px color(display-p3 0 0 0 / 0.078);
  --t-box-shadow-underline: 0px 1px 0px 0px color(display-p3 0 0 0 / 0.361);
  --t-box-shadow-super-heavy: 0px 0px 8px 0px color(display-p3 0 0 0 / 0.161), 0px 8px 64px -16px color(display-p3 0 0 0 / 0.478), 0px 24px 56px -16px color(display-p3 0 0 0 / 0.078);
  --t-blur-light: blur(6px) saturate(200%) contrast(50%) brightness(130%);
  --t-blur-medium: blur(12px) saturate(200%) contrast(50%) brightness(130%);
  --t-blur-strong: blur(20px) saturate(200%) contrast(50%) brightness(130%);
  --t-snack-bar-success-color: color(display-p3 0.297 0.637 0.581);
  --t-snack-bar-success-background-color: #00a43319;
  --t-snack-bar-error-color: color(display-p3 0.83 0.329 0.324);
  --t-snack-bar-error-background-color: #f3000d14;
  --t-snack-bar-warning-color: color(display-p3 0.9 0.45 0.2);
  --t-snack-bar-warning-background-color: #ff9c0029;
  --t-snack-bar-info-color: color(display-p3 0.276 0.384 0.837);
  --t-snack-bar-info-background-color: #0047f112;
  --t-snack-bar-default-color: color(display-p3 0.2 0.2 0.2);
  --t-snack-bar-default-background-color: color(display-p3 0 0 0 / 0.039);
  --t-code-text-gray: color(display-p3 0.514 0.514 0.514);
  --t-code-text-sky: color(display-p3 0.555 0.845 0.959);
  --t-code-text-pink: color(display-p3 0.748 0.27 0.581);
  --t-code-text-orange: color(display-p3 0.877 0.597 0.379);
  --t-code-text-green: color(display-p3 0.585 0.707 0.378);
  --t-illustration-icon-color-blue: color(display-p3 0.569 0.639 0.916);
  --t-illustration-icon-color-gray: color(display-p3 0.6 0.6 0.6);
  --t-illustration-icon-fill-blue: color(display-p3 0.831 0.87 1);
  --t-illustration-icon-fill-gray: color(display-p3 0.922 0.922 0.922);
  --t-accent-primary: color(display-p3 0.831 0.87 1);
  --t-accent-secondary: color(display-p3 0.831 0.87 1);
  --t-accent-tertiary: color(display-p3 0.933 0.948 0.992);
  --t-accent-quaternary: color(display-p3 0.971 0.977 0.998);
  --t-accent-accent3570: color(display-p3 0.569 0.639 0.916);
  --t-accent-accent4060: color(display-p3 0.569 0.639 0.916);
  --t-tag-text-gray: color(display-p3 0.4 0.4 0.4);
  --t-tag-text-mauve: color(display-p3 0.395 0.388 0.424);
  --t-tag-text-slate: color(display-p3 0.379 0.392 0.421);
  --t-tag-text-sage: color(display-p3 0.377 0.395 0.389);
  --t-tag-text-olive: color(display-p3 0.38 0.395 0.374);
  --t-tag-text-sand: color(display-p3 0.388 0.388 0.37);
  --t-tag-text-tomato: color(display-p3 0.755 0.259 0.152);
  --t-tag-text-red: color(display-p3 0.744 0.234 0.222);
  --t-tag-text-ruby: color(display-p3 0.728 0.211 0.311);
  --t-tag-text-crimson: color(display-p3 0.731 0.195 0.388);
  --t-tag-text-pink: color(display-p3 0.698 0.219 0.528);
  --t-tag-text-plum: color(display-p3 0.543 0.263 0.619);
  --t-tag-text-purple: color(display-p3 0.473 0.281 0.687);
  --t-tag-text-violet: color(display-p3 0.383 0.317 0.702);
  --t-tag-text-iris: color(display-p3 0.337 0.326 0.748);
  --t-tag-text-cyan: color(display-p3 0.08 0.48 0.63);
  --t-tag-text-turquoise: color(display-p3 0.08 0.5 0.43);
  --t-tag-text-sky: color(display-p3 0.193 0.448 0.605);
  --t-tag-text-blue: color(display-p3 0.256 0.354 0.755);
  --t-tag-text-jade: color(display-p3 0.15 0.5 0.37);
  --t-tag-text-green: color(display-p3 0.19 0.5 0.32);
  --t-tag-text-grass: color(display-p3 0.263 0.488 0.261);
  --t-tag-text-mint: color(display-p3 0.203 0.463 0.397);
  --t-tag-text-lime: color(display-p3 0.386 0.482 0.227);
  --t-tag-text-bronze: color(display-p3 0.471 0.373 0.336);
  --t-tag-text-gold: color(display-p3 0.433 0.386 0.305);
  --t-tag-text-brown: color(display-p3 0.485 0.374 0.288);
  --t-tag-text-orange: color(display-p3 0.76 0.34 0);
  --t-tag-text-amber: color(display-p3 0.64 0.4 0);
  --t-tag-text-yellow: color(display-p3 0.6 0.44 0);
  --t-tag-background-gray: color(display-p3 0.976 0.976 0.976);
  --t-tag-background-mauve: color(display-p3 0.946 0.938 0.952);
  --t-tag-background-slate: color(display-p3 0.94 0.941 0.953);
  --t-tag-background-sage: color(display-p3 0.935 0.944 0.94);
  --t-tag-background-olive: color(display-p3 0.939 0.945 0.937);
  --t-tag-background-sand: color(display-p3 0.943 0.942 0.936);
  --t-tag-background-tomato: color(display-p3 0.985 0.924 0.909);
  --t-tag-background-red: color(display-p3 0.985 0.925 0.925);
  --t-tag-background-ruby: color(display-p3 0.983 0.92 0.928);
  --t-tag-background-crimson: color(display-p3 0.987 0.917 0.941);
  --t-tag-background-pink: color(display-p3 0.981 0.917 0.96);
  --t-tag-background-plum: color(display-p3 0.973 0.923 0.98);
  --t-tag-background-purple: color(display-p3 0.963 0.931 0.989);
  --t-tag-background-violet: color(display-p3 0.953 0.943 0.993);
  --t-tag-background-iris: color(display-p3 0.943 0.945 0.992);
  --t-tag-background-cyan: color(display-p3 0.888 0.965 0.975);
  --t-tag-background-turquoise: color(display-p3 0.895 0.971 0.952);
  --t-tag-background-sky: color(display-p3 0.899 0.963 0.989);
  --t-tag-background-blue: color(display-p3 0.933 0.948 0.992);
  --t-tag-background-jade: color(display-p3 0.912 0.965 0.932);
  --t-tag-background-green: color(display-p3 0.913 0.964 0.925);
  --t-tag-background-grass: color(display-p3 0.923 0.965 0.917);
  --t-tag-background-mint: color(display-p3 0.888 0.972 0.95);
  --t-tag-background-lime: color(display-p3 0.939 0.965 0.851);
  --t-tag-background-bronze: color(display-p3 0.958 0.932 0.919);
  --t-tag-background-gold: color(display-p3 0.947 0.94 0.909);
  --t-tag-background-brown: color(display-p3 0.959 0.936 0.909);
  --t-tag-background-orange: color(display-p3 0.989 0.938 0.85);
  --t-tag-background-amber: color(display-p3 0.994 0.969 0.782);
  --t-tag-background-yellow: color(display-p3 0.997 0.982 0.749);
  --t-gray-scale-gray1: color(display-p3 1 1 1);
  --t-gray-scale-gray2: color(display-p3 0.988 0.988 0.988);
  --t-gray-scale-gray3: color(display-p3 0.976 0.976 0.976);
  --t-gray-scale-gray4: color(display-p3 0.945 0.945 0.945);
  --t-gray-scale-gray5: color(display-p3 0.922 0.922 0.922);
  --t-gray-scale-gray6: color(display-p3 0.839 0.839 0.839);
  --t-gray-scale-gray7: color(display-p3 0.8 0.8 0.8);
  --t-gray-scale-gray8: color(display-p3 0.702 0.702 0.702);
  --t-gray-scale-gray9: color(display-p3 0.6 0.6 0.6);
  --t-gray-scale-gray10: color(display-p3 0.514 0.514 0.514);
  --t-gray-scale-gray11: color(display-p3 0.4 0.4 0.4);
  --t-gray-scale-gray12: color(display-p3 0.2 0.2 0.2);
  --t-color-red: color(display-p3 0.83 0.329 0.324);
  --t-color-ruby: color(display-p3 0.83 0.323 0.408);
  --t-color-crimson: color(display-p3 0.843 0.298 0.507);
  --t-color-tomato: color(display-p3 0.831 0.345 0.231);
  --t-color-orange: color(display-p3 0.9 0.45 0.2);
  --t-color-amber: color(display-p3 1 0.77 0.26);
  --t-color-yellow: color(display-p3 1 0.92 0.22);
  --t-color-lime: color(display-p3 0.78 0.928 0.466);
  --t-color-grass: color(display-p3 0.38 0.647 0.378);
  --t-color-green: color(display-p3 0.332 0.634 0.442);
  --t-color-jade: color(display-p3 0.319 0.63 0.521);
  --t-color-mint: color(display-p3 0.62 0.908 0.834);
  --t-color-turquoise: color(display-p3 0.297 0.637 0.581);
  --t-color-cyan: color(display-p3 0.282 0.627 0.765);
  --t-color-sky: color(display-p3 0.585 0.877 0.983);
  --t-color-blue: color(display-p3 0.276 0.384 0.837);
  --t-color-iris: color(display-p3 0.357 0.357 0.81);
  --t-color-violet: color(display-p3 0.417 0.341 0.784);
  --t-color-purple: color(display-p3 0.523 0.318 0.751);
  --t-color-plum: color(display-p3 0.624 0.313 0.708);
  --t-color-pink: color(display-p3 0.775 0.297 0.61);
  --t-color-bronze: color(display-p3 0.611 0.507 0.455);
  --t-color-gold: color(display-p3 0.579 0.517 0.41);
  --t-color-brown: color(display-p3 0.651 0.505 0.368);
  --t-color-gray: color(display-p3 0.6 0.6 0.6);
}

.dark {
  --t-background-primary: color(display-p3 0.09 0.09 0.09);
  --t-background-secondary: color(display-p3 0.106 0.106 0.106);
  --t-background-tertiary: color(display-p3 0.114 0.114 0.114);
  --t-background-quaternary: color(display-p3 0.133 0.133 0.133);
  --t-background-inverted-primary: color(display-p3 0.922 0.922 0.922);
  --t-background-inverted-secondary: color(display-p3 0.702 0.702 0.702);
  --t-background-danger: color(display-p3 0.211 0.081 0.099);
  --t-background-transparent-primary: color(display-p3 0 0 0 / 0.5);
  --t-background-transparent-secondary: color(display-p3 0 0 0 / 0.4);
  --t-background-transparent-strong: color(display-p3 1 1 1 / 0.141);
  --t-background-transparent-medium: color(display-p3 1 1 1 / 0.102);
  --t-background-transparent-light: color(display-p3 1 1 1 / 0.059);
  --t-background-transparent-lighter: color(display-p3 1 1 1 / 0.031);
  --t-background-transparent-danger: #ff173f2d;
  --t-background-transparent-blue: #3566ff57;
  --t-background-transparent-orange: #ff590039;
  --t-background-transparent-success: #11ff992d;
  --t-background-overlay-primary: #000000b8;
  --t-background-overlay-secondary: #0000005c;
  --t-background-overlay-tertiary: #0000005c;
  --t-background-radial-gradient: radial-gradient( 50% 62.62% at 50% 0%, color(display-p3 0.506 0.506 0.506) 0%, color(display-p3 0.482 0.482 0.482) 100% );
  --t-background-radial-gradient-hover: radial-gradient( 76.32% 95.59% at 50% 0%, color(display-p3 0.482 0.482 0.482) 0%, color(display-p3 0.702 0.702 0.702) 100% );
  --t-background-primary-inverted: color(display-p3 0.922 0.922 0.922);
  --t-background-primary-inverted-hover: color(display-p3 0.702 0.702 0.702);
  --t-border-color-strong: color(display-p3 0.282 0.282 0.282);
  --t-border-color-medium: color(display-p3 0.133 0.133 0.133);
  --t-border-color-light: color(display-p3 0.114 0.114 0.114);
  --t-border-color-secondary-inverted: color(display-p3 0.702 0.702 0.702);
  --t-border-color-inverted: color(display-p3 0.922 0.922 0.922);
  --t-border-color-danger: color(display-p3 0.348 0.11 0.142);
  --t-border-color-blue: color(display-p3 0.245 0.309 0.575);
  --t-border-color-transparent-strong: color(display-p3 1 1 1 / 0.071);
  --t-font-color-primary: color(display-p3 0.922 0.922 0.922);
  --t-font-color-secondary: color(display-p3 0.702 0.702 0.702);
  --t-font-color-tertiary: color(display-p3 0.506 0.506 0.506);
  --t-font-color-light: color(display-p3 0.4 0.4 0.4);
  --t-font-color-extra-light: color(display-p3 0.298 0.298 0.298);
  --t-font-color-inverted: color(display-p3 0.09 0.09 0.09);
  --t-font-color-danger: color(display-p3 0.83 0.329 0.324);
  --t-box-shadow-color: rgba(0, 0, 0, 0.6);
  --t-box-shadow-light: 0px 2px 4px 0px rgba(0, 0, 0, 0.04), 0px 0px 4px 0px rgba(0, 0, 0, 0.08);
  --t-box-shadow-strong: 2px 4px 16px 0px rgba(0, 0, 0, 0.16), 0px 2px 4px 0px rgba(0, 0, 0, 0.08);
  --t-box-shadow-underline: 0px 1px 0px 0px rgba(0, 0, 0, 0.32);
  --t-box-shadow-super-heavy: 2px 4px 16px 0px rgba(0, 0, 0, 0.12), 0px 2px 4px 0px rgba(0, 0, 0, 0.04);
  --t-blur-light: blur(6px) saturate(200%) contrast(100%) brightness(130%);
  --t-blur-medium: blur(12px) saturate(200%) contrast(100%) brightness(130%);
  --t-blur-strong: blur(20px) saturate(200%) contrast(100%) brightness(130%);
  --t-snack-bar-success-color: color(display-p3 0.297 0.637 0.581);
  --t-snack-bar-success-background-color: #11ff992d;
  --t-snack-bar-error-color: color(display-p3 0.83 0.329 0.324);
  --t-snack-bar-error-background-color: #ff173f2d;
  --t-snack-bar-warning-color: color(display-p3 0.9 0.45 0.2);
  --t-snack-bar-warning-background-color: #ff590039;
  --t-snack-bar-info-color: color(display-p3 0.276 0.384 0.837);
  --t-snack-bar-info-background-color: #3566ff57;
  --t-snack-bar-default-color: color(display-p3 0.922 0.922 0.922);
  --t-snack-bar-default-background-color: color(display-p3 1 1 1 / 0.059);
  --t-code-text-gray: color(display-p3 0.482 0.482 0.482);
  --t-code-text-sky: color(display-p3 0.718 0.925 0.991);
  --t-code-text-pink: color(display-p3 0.808 0.356 0.645);
  --t-code-text-orange: color(display-p3 0.601 0.359 0.201);
  --t-code-text-green: color(display-p3 0.365 0.456 0.25);
  --t-illustration-icon-color-blue: color(display-p3 0.354 0.445 0.866);
  --t-illustration-icon-color-gray: color(display-p3 0.4 0.4 0.4);
  --t-illustration-icon-fill-blue: color(display-p3 0.848 0.881 0.99);
  --t-illustration-icon-fill-gray: color(display-p3 0.133 0.133 0.133);
  --t-accent-primary: color(display-p3 0.163 0.22 0.439);
  --t-accent-secondary: color(display-p3 0.163 0.22 0.439);
  --t-accent-tertiary: color(display-p3 0.105 0.141 0.275);
  --t-accent-quaternary: color(display-p3 0.081 0.089 0.144);
  --t-accent-accent3570: color(display-p3 0.285 0.362 0.674);
  --t-accent-accent4060: color(display-p3 0.285 0.362 0.674);
  --t-tag-text-gray: color(display-p3 0.702 0.702 0.702);
  --t-tag-text-mauve: color(display-p3 0.707 0.7 0.735);
  --t-tag-text-slate: color(display-p3 0.692 0.704 0.728);
  --t-tag-text-sage: color(display-p3 0.685 0.709 0.697);
  --t-tag-text-olive: color(display-p3 0.69 0.709 0.682);
  --t-tag-text-sand: color(display-p3 0.707 0.703 0.68);
  --t-tag-text-tomato: color(display-p3 1 0.585 0.455);
  --t-tag-text-red: color(display-p3 1 0.57 0.55);
  --t-tag-text-ruby: color(display-p3 1 0.57 0.59);
  --t-tag-text-crimson: color(display-p3 1 0.56 0.66);
  --t-tag-text-pink: color(display-p3 1 0.535 0.78);
  --t-tag-text-plum: color(display-p3 0.86 0.602 0.933);
  --t-tag-text-purple: color(display-p3 0.8 0.62 1);
  --t-tag-text-violet: color(display-p3 0.72 0.65 1);
  --t-tag-text-iris: color(display-p3 0.685 0.662 1);
  --t-tag-text-cyan: color(display-p3 0.446 0.79 0.887);
  --t-tag-text-turquoise: color(display-p3 0.388 0.835 0.719);
  --t-tag-text-sky: color(display-p3 0.536 0.772 0.924);
  --t-tag-text-blue: color(display-p3 0.63 0.69 1);
  --t-tag-text-jade: color(display-p3 0.4 0.835 0.656);
  --t-tag-text-green: color(display-p3 0.434 0.828 0.573);
  --t-tag-text-grass: color(display-p3 0.535 0.807 0.542);
  --t-tag-text-mint: color(display-p3 0.482 0.825 0.733);
  --t-tag-text-lime: color(display-p3 0.771 0.893 0.485);
  --t-tag-text-bronze: color(display-p3 0.81 0.707 0.655);
  --t-tag-text-gold: color(display-p3 0.784 0.728 0.635);
  --t-tag-text-brown: color(display-p3 0.835 0.715 0.597);
  --t-tag-text-orange: color(display-p3 1 0.63 0.38);
  --t-tag-text-amber: color(display-p3 1 0.8 0.29);
  --t-tag-text-yellow: color(display-p3 0.948 0.885 0.392);
  --t-tag-background-gray: color(display-p3 0.098 0.098 0.098);
  --t-tag-background-mauve: color(display-p3 0.138 0.134 0.144);
  --t-tag-background-slate: color(display-p3 0.13 0.135 0.145);
  --t-tag-background-sage: color(display-p3 0.128 0.135 0.131);
  --t-tag-background-olive: color(display-p3 0.131 0.135 0.126);
  --t-tag-background-sand: color(display-p3 0.135 0.135 0.129);
  --t-tag-background-tomato: color(display-p3 0.205 0.097 0.083);
  --t-tag-background-red: color(display-p3 0.211 0.081 0.099);
  --t-tag-background-ruby: color(display-p3 0.208 0.088 0.117);
  --t-tag-background-crimson: color(display-p3 0.203 0.091 0.143);
  --t-tag-background-pink: color(display-p3 0.198 0.098 0.179);
  --t-tag-background-plum: color(display-p3 0.192 0.105 0.202);
  --t-tag-background-purple: color(display-p3 0.175 0.112 0.224);
  --t-tag-background-violet: color(display-p3 0.154 0.123 0.256);
  --t-tag-background-iris: color(display-p3 0.128 0.134 0.272);
  --t-tag-background-cyan: color(display-p3 0.073 0.168 0.209);
  --t-tag-background-turquoise: color(display-p3 0.087 0.175 0.165);
  --t-tag-background-sky: color(display-p3 0.089 0.154 0.244);
  --t-tag-background-blue: color(display-p3 0.105 0.141 0.275);
  --t-tag-background-jade: color(display-p3 0.091 0.176 0.138);
  --t-tag-background-green: color(display-p3 0.1 0.173 0.133);
  --t-tag-background-grass: color(display-p3 0.118 0.163 0.122);
  --t-tag-background-mint: color(display-p3 0.077 0.17 0.168);
  --t-tag-background-lime: color(display-p3 0.13 0.16 0.099);
  --t-tag-background-bronze: color(display-p3 0.147 0.132 0.125);
  --t-tag-background-gold: color(display-p3 0.141 0.136 0.122);
  --t-tag-background-brown: color(display-p3 0.151 0.13 0.115);
  --t-tag-background-orange: color(display-p3 0.189 0.12 0.056);
  --t-tag-background-amber: color(display-p3 0.178 0.128 0.049);
  --t-tag-background-yellow: color(display-p3 0.168 0.137 0.039);
  --t-gray-scale-gray1: color(display-p3 0.09 0.09 0.09);
  --t-gray-scale-gray2: color(display-p3 0.106 0.106 0.106);
  --t-gray-scale-gray3: color(display-p3 0.098 0.098 0.098);
  --t-gray-scale-gray4: color(display-p3 0.114 0.114 0.114);
  --t-gray-scale-gray5: color(display-p3 0.133 0.133 0.133);
  --t-gray-scale-gray6: color(display-p3 0.282 0.282 0.282);
  --t-gray-scale-gray7: color(display-p3 0.298 0.298 0.298);
  --t-gray-scale-gray8: color(display-p3 0.4 0.4 0.4);
  --t-gray-scale-gray9: color(display-p3 0.506 0.506 0.506);
  --t-gray-scale-gray10: color(display-p3 0.482 0.482 0.482);
  --t-gray-scale-gray11: color(display-p3 0.702 0.702 0.702);
  --t-gray-scale-gray12: color(display-p3 0.922 0.922 0.922);
  --t-color-red: color(display-p3 0.83 0.329 0.324);
  --t-color-ruby: color(display-p3 0.83 0.323 0.408);
  --t-color-crimson: color(display-p3 0.843 0.298 0.507);
  --t-color-tomato: color(display-p3 0.831 0.345 0.231);
  --t-color-orange: color(display-p3 0.9 0.45 0.2);
  --t-color-amber: color(display-p3 1 0.77 0.26);
  --t-color-yellow: color(display-p3 1 0.92 0.22);
  --t-color-lime: color(display-p3 0.78 0.928 0.466);
  --t-color-grass: color(display-p3 0.38 0.647 0.378);
  --t-color-green: color(display-p3 0.332 0.634 0.442);
  --t-color-jade: color(display-p3 0.319 0.63 0.521);
  --t-color-mint: color(display-p3 0.62 0.908 0.834);
  --t-color-turquoise: color(display-p3 0.297 0.637 0.581);
  --t-color-cyan: color(display-p3 0.282 0.627 0.765);
  --t-color-sky: color(display-p3 0.585 0.877 0.983);
  --t-color-blue: color(display-p3 0.276 0.384 0.837);
  --t-color-iris: color(display-p3 0.357 0.357 0.81);
  --t-color-violet: color(display-p3 0.417 0.341 0.784);
  --t-color-purple: color(display-p3 0.523 0.318 0.751);
  --t-color-plum: color(display-p3 0.624 0.313 0.708);
  --t-color-pink: color(display-p3 0.775 0.297 0.61);
  --t-color-bronze: color(display-p3 0.611 0.507 0.455);
  --t-color-gold: color(display-p3 0.579 0.517 0.41);
  --t-color-brown: color(display-p3 0.651 0.505 0.368);
  --t-color-gray: color(display-p3 0.298 0.298 0.298);
}
```

**Block 3 — the squircle enhancement**, copied verbatim from `packages/twenty-ui/src/theme-constants/theme-light.css:1032-1048`. Both
`.light` and `.dark` need it; the selector below covers `:root` so it applies to whichever class is
on the element.

```css
@supports (corner-shape: squircle) {
  :root, .light, .dark {
    --radius-xs: 4px;
    --radius-sm: 8px;
    --radius-md: 16px;
    --radius-lg: 32px;
    --radius-xl: 40px;
    --radius-xxl: 80px;
  }

  /* Zero specificity on purpose: any component rule can override it. */
  *, *::before, *::after {
    corner-shape: var(--t-corner-shape, squircle);
  }
}
```

Note that `--radius-pill` (`999px`), `--radius-rounded` (`100%`), `--radius-sm-round` and
`--radius-md-round` are deliberately **absent** from block 3. Tags, chips, statuses, toggles and
circular checkboxes must keep `corner-shape: round` at the call site, exactly as §5.2 describes.

**Wiring the semantic aliases to utility classes.** If you want `bg-surface` rather than
`bg-[var(--t-background-primary)]`, add:

```css
@theme inline {
  --color-surface: var(--t-background-primary);
  --color-surface-hover: var(--t-background-secondary);
  --color-surface-press: var(--t-background-tertiary);
  --color-page: var(--t-background-tertiary);
  --color-selected: var(--t-accent-quaternary);
  --color-line: var(--t-border-color-light);
  --color-edge: var(--t-border-color-medium);
  --color-edge-strong: var(--t-border-color-strong);
  --color-ink: var(--t-font-color-primary);
  --color-ink-secondary: var(--t-font-color-secondary);
  --color-ink-tertiary: var(--t-font-color-tertiary);
  --color-ink-light: var(--t-font-color-light);
  --color-ink-inverted: var(--t-font-color-inverted);
  --color-ink-danger: var(--t-font-color-danger);
  --color-hover: var(--t-background-transparent-light);
  --color-press: var(--t-background-transparent-medium);
}
```

`@theme inline` (rather than plain `@theme`) is required here so the generated utilities emit
`var(--t-…)` and therefore follow the `.dark` override, instead of baking in the light value.

### 12.4 Recipes, so a ported screen actually looks like Twenty

Four compositions carry most of the visual identity. In Tailwind terms:

```html
<!-- floating surface: dropdown, cell editor, popover  (§1, OverlayContainer.tsx:5-26) -->
<div class="flex overflow-hidden rounded-md border border-edge
            bg-[var(--t-background-transparent-primary)]
            shadow-strong backdrop-blur-[12px] backdrop-saturate-200
            backdrop-contrast-50 backdrop-brightness-125 z-30">

<!-- table row cell  (§8.7(1)) -->
<div class="flex h-8 items-center border-b border-r border-line
            bg-surface p-0 text-ink select-none">

<!-- tag  (§8.7(2)) -->
<span class="box-content inline-flex h-5 items-center gap-1 overflow-hidden
             rounded-sm-round px-2 text-md font-normal [corner-shape:round]"
      style="background: var(--t-tag-background-blue); color: var(--t-tag-text-blue)">

<!-- menu item  (§8.7(4)) -->
<div class="box-content flex h-4 w-[calc(100%-8px)] items-center justify-between gap-2
            px-1 py-2 text-sm text-ink-secondary select-none
            rounded-[calc(var(--radius-md)-var(--spacing-1))]
            transition-[background] duration-100 ease-linear
            hover:bg-hover data-[focused]:bg-hover data-[key-selected]:bg-hover">
```

Three details that are easy to lose and change the whole feel:

- `box-sizing: content-box` on tags, chips and menu items. Their declared height is the *content*
  height; padding is added on top. A menu item's `h-4` plus `py-2` is what makes 32.
- `transition: background 0.1s ease` and nothing else on interactive rows. 100ms, not 150 or 200.
- `[corner-shape:round]` on every pill and chip, so they survive a squircle-capable browser.

---

## 13 · Not found

Things in the brief that do not exist in this codebase, stated plainly.

- **No Tailwind.** There is no `tailwind.config.*` anywhere in the repo and no Tailwind dependency
  in any `package.json`. §12 is a translation, not a transcription.
- **No letter-spacing / tracking token.** No `letterSpacing`, `tracking` or `letter-spacing` key
  exists in any of the 994 theme tokens, in `packages/twenty-ui/src/theme/constants/FontCommon.ts`, or in `packages/twenty-ui/src/theme/constants/Text.ts`. Individual
  components do not set it either.
- **No easing tokens.** Durations are tokenised; curves are not. Every `transition` writes `ease`,
  `ease-out`, `ease-in-out` or `linear` inline (§6.2).
- **No border-width token.** 1px everywhere, written as a literal (§5.3).
- **No opacity scale.** Transparency is expressed by choosing an alpha colour token, not by an
  `opacity` token. The loose `opacity` values that do exist are one-offs: `0.6` on the filter-chip
  sub-field separator, `0.64` on read-only-hovered images, `--dnd-drag-feedback-opacity: 0.6` /
  `--dnd-drag-source-opacity: 0.3` in `packages/twenty-front/src/index.css:41-44`.
- **Only one breakpoint.** 768px, and it is a plain number rather than a token because custom
  properties do not work in media queries (`packages/twenty-ui/src/theme-constants/constants.ts:1-3`). There is no tablet or desktop
  breakpoint, and no container-query usage in the theme.
- **No documented focus-ring token.** The ring is hard-coded inside a mixin
  (`2px solid var(--t-color-blue)`, `outline-offset: 1px`, `packages/twenty-ui/src/styles/abstracts/_mixins.scss:1-6`); there is no
  `--t-focus-*` token, and no `focus-visible` treatment outside the 11 files listed in §11.
- **No hex values for the palette.** The source stores `color(display-p3 …)`. This document does
  not convert, and no sRGB fallback exists in the repo to copy.
- **The 348 non-gray transparent alpha tokens are not tabled.** `--t-color-transparent-<family><n>`
  for the 29 families other than `gray` are defined in both themes and referenced nowhere. They
  are Radix `<family>A` (light) and `<family>DarkA` (dark) verbatim — see
  `packages/twenty-ui/src/theme/constants/TransparentColorsLight.ts:5-16` for the import pattern, e.g.
  `green1: RadixColors.greenA.greenA1`. To reproduce them, import `@radix-ui/colors@^3.0.0` and
  read the corresponding `*A` / `*DarkA` scales.
- **No design-token export pipeline.** There is no Style Dictionary, no Figma token sync, and no
  generator script for the theme CSS. `packages/twenty-ui/src/theme-constants/theme-light.css` / `packages/twenty-ui/src/theme-constants/theme-dark.css` are hand-maintained and
  described in their own header as "mirrored token-for-token from twenty-ui", kept honest by a
  parity test that only checks the corner-radius invariants and the dist copies.
- **No documented elevation ladder beyond four shadows.** There is no `elevation-1…5`; the four
  shadow tokens are the whole system (§5.4).
- **No motion-token coverage for reduced motion.** No `--t-*` token or global media query disables
  transitions (§6.6).
