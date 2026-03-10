# Google Design System Summary

> This document synthesizes two complementary Google design systems:
> - **[Material Design 3 (M3)](https://m3.material.io/)** — Google's open-source UI design system covering visual styles, components, tokens, and interaction patterns across platforms.
> - **[Google Style Guides](https://google.github.io/styleguide/)** — Google's code authoring conventions across every major language, defining the "design language" for writing consistent, readable, and maintainable code.

---

## Table of Contents

1. [Core Design Principles](#1-core-design-principles)
2. [Color System](#2-color-system)
3. [Typography](#3-typography)
4. [Shape System](#4-shape-system)
5. [Elevation](#5-elevation)
6. [Motion & Interaction](#6-motion--interaction)
7. [Interaction States](#7-interaction-states)
8. [Design Tokens](#8-design-tokens)
9. [Components](#9-components)
10. [Layout & Accessibility](#10-layout--accessibility)
11. [Code Style — Universal Rules](#11-code-style--universal-rules)
12. [HTML / CSS Guidelines](#12-html--css-guidelines)
13. [JavaScript & TypeScript Guidelines](#13-javascript--typescript-guidelines)
14. [Python Guidelines](#14-python-guidelines)
15. [Go Guidelines](#15-go-guidelines)
16. [Shell / Bash Guidelines](#16-shell--bash-guidelines)
17. [C# Guidelines](#17-c-guidelines)
18. [Objective-C Guidelines](#18-objective-c-guidelines)
19. [R Guidelines](#19-r-guidelines)
20. [Documentation / Markdown Guidelines](#20-documentation--markdown-guidelines)
21. [Naming Conventions Cheat Sheet](#21-naming-conventions-cheat-sheet)

---

## 1. Core Design Principles

### Material Design 3 Philosophy
> *"Material Design is an adaptable system of guidelines, components, and tools that support the best practices of user interface design."* — [m3.material.io](https://m3.material.io/)

M3 is anchored by **M3 Expressive** — a design philosophy that combines emotion, usability, and beauty:

- **Design with emotion** — Use vibrant color, intuitive motion, adaptive components, expressive typography, and contrasting shapes to create products people want to use.
- **Adaptable** — The system scales from wearables to TVs, supports light/dark themes, and enables user-controlled personalization through dynamic color.
- **Accessible by default** — Every color role, component state, and typographic style is built with WCAG contrast requirements in mind.
- **Token-driven** — All style decisions flow through a three-tier token model, enabling consistent updates across design and code simultaneously.

### Google Code Style Philosophy

Shared across every code style guide:

| Principle | Definition |
|---|---|
| **Clarity** | Code's purpose and rationale is self-evident to the reader |
| **Simplicity** | Achieves its goal the simplest way possible; complexity is justified |
| **Concision** | High signal-to-noise ratio; no redundant code or comments |
| **Maintainability** | Written to be easily evolved; docs updated in lockstep with code |
| **Consistency** | Conforms to the surrounding codebase — "Be consistent" closes every guide |

> **Optimize for the reader, not the writer.** Code is read far more often than it is written.

---

## 2. Color System

*Reference: [m3.material.io/styles/color/overview](https://m3.material.io/styles/color/overview)*

### How the System Works

The M3 color system maps a palette of tones to **26+ named color roles**, which are then assigned to components. This decouples specific hex values from usage decisions.

#### Color Roles (Key Groups)

| Group | Roles | Usage |
|---|---|---|
| **Primary** | `primary`, `on-primary`, `primary-container`, `on-primary-container` | Key actions, FABs, prominent buttons |
| **Secondary** | `secondary`, `on-secondary`, `secondary-container`, `on-secondary-container` | Less prominent actions, filters |
| **Tertiary** | `tertiary`, `on-tertiary`, `tertiary-container`, `on-tertiary-container` | Accent contrasts, decorative moments |
| **Error** | `error`, `on-error`, `error-container`, `on-error-container` | Destructive actions, validation |
| **Surface** | `surface`, `surface-variant`, `surface-container-*`, `inverse-surface` | Backgrounds, cards, sheets |
| **Outline** | `outline`, `outline-variant` | Borders, dividers |
| **Background** | `background`, `on-background` | Page/screen background |

#### Dynamic Color

Products with dynamic color can automatically generate and assign colors based on:
- **User-generated** — derived from the user's wallpaper (Android 12+)
- **Content-based** — derived from the product's imagery or brand hue
- **Baseline** — a static default scheme when dynamic color is unavailable

Dynamic color provides: personalized UI, accessible contrast, user-controlled contrast, and automatic dark theme.

#### Contrast Levels (New in M3)

Color roles support three contrast levels — **Standard**, **Medium**, and **High** — all tokenized, allowing users to select the level that best suits their vision needs.

#### Key Rules
- Tone-based surface colors replace the old elevation-overlay approach (`surface +1` through `+5`).
- Fixed color roles (`primary-fixed`, `secondary-fixed`, etc.) stay constant across light and dark themes.
- Always pair a color role with its corresponding `on-*` role for text/icons on top of it.

---

## 3. Typography

*Reference: [m3.material.io/styles/typography/overview](https://m3.material.io/styles/typography/overview)*

### Type Scale

M3 defines **30 type styles**: 15 baseline + 15 emphasized (added in M3 Expressive).

#### Five Type Roles

| Role | Purpose | Sizes |
|---|---|---|
| **Display** | Large, expressive text — hero moments, editorial | Large, Medium, Small |
| **Headline** | Section headers, sub-hero labels | Large, Medium, Small |
| **Title** | Component titles, dialog headers | Large, Medium, Small |
| **Body** | Long-form reading content | Large, Medium, Small |
| **Label** | UI labels, captions, buttons | Large, Medium, Small |

Emphasized variants (e.g. `display-large-emphasized`) add visual weight for highlighted moments.

#### Typefaces
- **Roboto Flex** — Variable font with axes for weight, width, grade, slant, and optical size. Preferred for expressive UI.
- **Roboto Serif** — Variable serif for editorial contexts.
- **Roboto Mono** — Monospace for code, data.

#### Typography Tokens

Token structure: `md.sys.typescale.<role>.<attribute>`

Example: `md.sys.typescale.body-large.font`, `md.sys.typescale.label-medium.size`

Attributes: `font`, `line-height`, `size`, `tracking`, `weight`.

Type roles describe size (small/medium/large) enabling them to adapt and respond to device context.

---

## 4. Shape System

*Reference: [m3.material.io/styles/shape/overview-principles](https://m3.material.io/styles/shape/overview-principles)*

### Overview

The M3 shape system includes a corner radius scale, a library of **35 shapes**, and built-in **shape morphing** (added in M3 Expressive).

### Corner Radius Scale

| Token | Value | Example usage |
|---|---|---|
| `shape.corner.none` | 0dp | Banners, full-bleed images |
| `shape.corner.extra-small` | 4dp | Menu items, tooltips |
| `shape.corner.small` | 8dp | Cards, chips |
| `shape.corner.medium` | 12dp | Dialogs, sheets |
| `shape.corner.large` | 16dp | Navigation drawers |
| `shape.corner.large-increased` | 20dp | *(M3 Expressive)* |
| `shape.corner.extra-large` | 28dp | FABs, extended FABs |
| `shape.corner.extra-large-increased` | 32dp | *(M3 Expressive)* |
| `shape.corner.extra-extra-large` | 48dp | *(M3 Expressive)* |
| `shape.corner.full` | 50% (fully rounded) | Buttons, badges, switches |

### Shape Principles

- **Shape and text in harmony** — Shape echoes key visual attributes of typography. Round shapes pair with round letterforms.
- **Shape morphing** — Shapes should morph to communicate interaction (e.g. a button being selected) or change in environment (e.g. loading).
- **Tension through contrast** — Using both sharp and rounded shapes creates dynamism and memorability. Do not default exclusively to rounded.
- **Shape is not semantic** — Avoid assigning a specific meaning to a single shape; the same shape can serve multiple unrelated UI contexts.
- **Use abstract shapes sparingly** — Be intentional; don't compromise clarity for visual decoration.
- **2.5D illusion** — Motion and layered shapes can give 2D visuals the illusion of depth.

---

## 5. Elevation

Elevation in M3 is expressed through **tone-based surface color** (not drop shadows as the primary indicator).

| Level | Token | Surface Tint |
|---|---|---|
| Level 0 | `md.sys.elevation.level0` | No tint — base surface |
| Level 1 | `md.sys.elevation.level1` | +5% primary tint (cards, menus) |
| Level 2 | `md.sys.elevation.level2` | +8% (navigation drawers) |
| Level 3 | `md.sys.elevation.level3` | +11% (FABs) |
| Level 4 | `md.sys.elevation.level4` | +12% (top app bar, pinned) |
| Level 5 | `md.sys.elevation.level5` | +14% (bottom sheets open) |

Drop shadows may be used in addition to tint for clarity on elevation-critical surfaces.

---

## 6. Motion & Interaction

*Reference: [m3.material.io/styles/motion/overview](https://m3.material.io/styles/motion/overview)*

### Motion Physics System (M3 Expressive)

M3 replaced duration/easing curves with a **physics-based spring system**, making interactions feel alive, fluid, and natural.

#### Motion Schemes

| Scheme | Character | Recommended for |
|---|---|---|
| **Expressive** | Overshoots final value → bounces into place | Hero moments, key interactions, most UI |
| **Standard** | Eases smoothly into final value, minimal bounce | Utilitarian products, functional transitions |

Custom schemes can be created by tuning three spring attributes: **stiffness**, **damping**, and **initial velocity**.

#### Spring Tokens

Token structure: `md.sys.motion.spring.<speed>.<style>`

| Type | Behavior |
|---|---|
| **Spatial** | Animates position, rotation, size, corners — overshoots are intentional |
| **Effects** | Animates color, opacity — no overshoot |

| Speed | Use case |
|---|---|
| **Fast** | Small components: switches, buttons, chips |
| **Default** | Standard transitions: bottom sheets, navigation |
| **Slow** | Full-screen transitions, large layout changes |

Spring token values automatically adapt to device context (phone, tablet, wearable).

#### CSS Interaction Rules (from Google HTML/CSS Guide)
- Hover, focus, and active states must be expressed in CSS — never inline `style=""` or JS-injected styles.
- No `!important` for state overrides — use specificity or cascade.
- Toggle state classes via JS; let CSS own the visual output.

---

## 7. Interaction States

*Reference: [m3.material.io/foundations/interaction-states](https://m3.material.io/foundations/interaction-states)*

States show the interaction status of a component using **two visual indicators** to ensure accessibility.

| State | Description | Visual indicator |
|---|---|---|
| **Enabled** | Default interactive state | Full color and contrast |
| **Disabled** | Inoperable — cannot be interacted with | Reduced opacity (38% on content, 12% on container) |
| **Hover** | Cursor positioned over the element (pointer devices) | State layer at 8% opacity |
| **Focused** | Highlighted via keyboard or voice navigation | Focus ring + state layer at 10% opacity |
| **Pressed** | User tap or click | Ripple + state layer at 10–12% opacity |
| **Dragged** | User press-and-move | Elevated shadow + state layer at 16% opacity |

### State Layers

State layers are semi-transparent overlays applied on top of a component's container using the `on-*` color role for that container:

- All state colors use the component's `on-surface` (or equivalent) color role.
- States can be **combined** — e.g. selected + hover simultaneously.
- Apply states **consistently** across all components in a product.

---

## 8. Design Tokens

*Reference: [m3.material.io/foundations/design-tokens/overview](https://m3.material.io/foundations/design-tokens/overview)*

### What is a Design Token?

A design token is a named, reusable design decision: a **code-like name** paired with a **style value** (color hex, typeface, size, or another token).

> Example: `md.ref.palette.secondary90` → `#E8DEF8`

Tokens replace hardcoded values with self-explanatory names. Even if the underlying value changes, the token name and assignment remain stable.

### Three Token Classes

#### 1. Reference Tokens (`md.ref.*`)
All available style options in the system — a palette of approved values.

- Point to static values (hex codes, font names, px sizes).
- Do not change based on context.
- Examples: `md.ref.palette.primary40`, `md.ref.typeface.plain-medium`

#### 2. System Tokens (`md.sys.*`)
Design decisions that give the system its character — colors, typography scale, elevation, shape, motion.

- Point to reference tokens (not hardcoded values).
- Change based on context (light vs. dark theme, device type).
- Examples: `md.sys.color.primary`, `md.sys.typescale.body-large.size`, `md.sys.motion.spring.fast.spatial`

#### 3. Component Tokens (`md.comp.*`)
Style properties assigned to specific elements within a component.

- Point to system or reference tokens whenever possible.
- Grouped by state (enabled, disabled, hover…) then by element (container, label, icon…).
- Examples: `md.comp.filled-button.container.color`, `md.comp.fab.primary.container.color`

### Token Naming Structure

```
md  .  sys  .  color  .  secondary-container
│      │        │          └─ Role / purpose
│      │        └─ Category (color, typescale, shape, motion…)
│      └─ Token class: ref | sys | comp
└─ System prefix (Material Design)
```

### Token Contexts

The same system token can resolve to different reference tokens depending on **context**:
- Light / dark theme
- Dense vs. standard layout
- Device form factor (phone, tablet, TV, wearable)
- Right-to-left writing direction

### Why Tokens Matter

- **Single source of truth** — Design and engineering reference the same token.
- **Consistency at scale** — One token update propagates through an entire product suite.
- **Design-to-code handoff** — Designers and engineers "speak the same language."
- **Theming** — Dynamic color, high-contrast mode, and custom themes are all expressed through token contexts.

---

## 9. Components

*Reference: [m3.material.io/components](https://m3.material.io/components)*

Components are interactive building blocks organized by purpose.

### Buttons
| Component | Use |
|---|---|
| **Buttons** (filled, outlined, text, elevated, tonal) | Primary and secondary actions |
| **Button Groups** | Organize related buttons with shape-shifting layout |
| **FAB / Extended FAB** | Most important action on a screen |
| **FAB Menu** | FAB that expands into a set of related actions |
| **Icon Buttons** | Compact toggle or action |
| **Segmented Buttons** | Selection from a set of 2–5 options |
| **Split Buttons** | A button paired with a connected menu of related actions |

### Navigation
| Component | Use |
|---|---|
| **Navigation Bar** | Bottom navigation for 3–5 top-level destinations (mobile) |
| **Navigation Drawer** | Side panel for many destinations (tablet/desktop) |
| **Navigation Rail** | Compact side navigation (tablet/desktop) |

### Containment & Display
| Component | Use |
|---|---|
| **Cards** | Contained, related content groupings |
| **Dialogs** | Time-critical decisions or information |
| **Bottom Sheets / Side Sheets** | Supplementary content overlaying the main view |
| **Carousel** | Horizontally browsable collection |
| **Lists** | Continuous, vertically arranged groups of items |

### Input & Selection
| Component | Use |
|---|---|
| **Checkbox** | Multi-select from a list |
| **Radio Button** | Single select from a list |
| **Switch** | Toggle a single setting on/off |
| **Sliders** | Select a value from a continuous range |
| **Chips** | Compact elements for input, filtering, or actions |
| **Menus** | Temporary list of choices |
| **Search** | Query bar with optional suggestions |

### Communication & Progress
| Component | Use |
|---|---|
| **Progress Indicators** (linear, circular) | Show ongoing process status |
| **Loading Indicator** | Expressive loading state (M3 Expressive) |
| **Snackbar** | Brief, non-blocking messages |
| **Badges** | Numeric or status markers on icons |
| **Tooltips** | Short label on hover/focus |

### Date, Time & Structure
| Component | Use |
|---|---|
| **Date Pickers** | Calendar-based date selection |
| **Time Pickers** | Clock-based time selection |
| **Tabs** | Horizontal navigation within a page |
| **App Bars** (top, bottom) | Navigation and contextual actions |
| **Divider** | Visual separation between content groups |
| **Toolbars** | Flexible action bar (M3 Expressive) |

---

## 10. Layout & Accessibility

### Layout Principles
*Reference: [m3.material.io/foundations/layout](https://m3.material.io/foundations/layout)*

- **Responsive**: Layouts adapt to the device's screen size using a fluid grid and breakpoints (compact, medium, expanded).
- **Adaptive**: Components change form at breakpoints — e.g. navigation bar collapses to navigation rail on tablets.
- **Consistent margin/padding**: Use the 4dp grid system. Prefer multiples of 4 for all spacing values.

### Accessibility Principles
*Reference: [m3.material.io/foundations/accessible-design](https://m3.material.io/foundations/accessible-design)*

- **Every interactive element must be reachable** via keyboard and assistive technologies.
- **Minimum touch-target size**: 48×48dp.
- **Color is never the sole indicator** of meaning — always pair color with a second visual indicator (shape, text, icon).
- **Contrast**: All text must meet WCAG AA (4.5:1 normal text, 3:1 large text). All state changes must be distinguishable.
- **Focus indicators**: Visible focus rings on all interactive elements.

---

## 11. Code Style — Universal Rules

Shared rules from the [Google Style Guides](https://google.github.io/styleguide/):

| Rule | Guideline |
|---|---|
| **Encoding** | UTF-8, no BOM |
| **Indentation** | 2 spaces (HTML/CSS/JS/TS/C#) · 4 spaces (Python/Shell) · no tabs |
| **Line length** | 80 cols (Python, Markdown, Shell, Go) · 100 cols (C#) |
| **Trailing whitespace** | Always remove |
| **TODOs** | `TODO:` keyword only — never `@@`, `FIXME`, etc. |
| **File names** | `kebab-case` (web) · `PascalCase` (C#) · `snake_case` (Python/Shell) |
| **Comments** | Explain *why*, not what; use per-language doc-comment formats |
| **Protocol in URLs** | Always `https:` — never omit or use `http:` |

---

## 12. HTML / CSS Guidelines

### HTML Rules

| Rule | Detail |
|---|---|
| **Doctype** | Always `<!doctype html>` — no quirks mode |
| **Charset** | `<meta charset="utf-8">` in every document |
| **Semantics** | Use elements for their purpose: `<a>`, `<button>`, `<h1>`–`<h6>`, `<p>` |
| **Accessibility** | `alt` on all `<img>`; captions/transcripts for media |
| **Separation of concerns** | Structure → HTML · Presentation → CSS · Behavior → JS |
| **`type` attributes** | Omit on `<link>` and `<script>` (HTML5 defaults) |
| **`id` vs `class`** | Prefer `class` for styling; use `data-*` for scripting |
| **`id` values** | Must contain a hyphen — `user-profile`, not `userProfile` |
| **Quotes** | Double quotes `""` for HTML attribute values |
| **Casing** | All element names, attributes, values lowercase |
| **Indentation** | 2 spaces; new line per block/list/table element |

### CSS Rules

#### Selectors & Naming

| Rule | Detail |
|---|---|
| **Class names** | Reflect purpose, not presentation — `.nav`, not `.blue-text` |
| **Delimiter** | Hyphen-case only — `.video-id` |
| **No ID selectors** | Use classes — IDs are too high-specificity |
| **No type-qualified selectors** | `.error`, not `div.error` |
| **Namespacing** | App-specific prefix for large projects: `.adw-`, `.maia-` |

#### Properties & Values

| Rule | Detail |
|---|---|
| **Shorthand** | `padding: 0 1em 2em` not four separate rules |
| **Zero units** | `margin: 0` not `margin: 0px` |
| **Leading zeros** | `font-size: 0.8em` |
| **Hex colors** | 3-char where possible — `#ebc` not `#eebbcc`; always lowercase |
| **`!important`** | Avoid — use selector specificity instead |
| **Hacks** | Last resort only |

#### Formatting

- One space after `:` in declarations: `color: blue;`
- One space before `{`: `.video {`
- New line per selector and per declaration; `;` after every declaration.
- Blank line between rules; single quotes `''` in CSS values.
- Alphabetize declarations (optional, but be consistent within a project).
- Indent content inside `@media` blocks.

---

## 13. JavaScript & TypeScript Guidelines

> Google recommends **TypeScript** for all new projects. The JavaScript guide is no longer updated.

### Source File Structure (both JS and TS, in order)
1. License / copyright comment
2. `@fileoverview` JSDoc (if present)
3. Imports (`import` / `goog.module` / `goog.require`)
4. File implementation

Exactly **one blank line** separates each section.

### Key Rules

| Rule | Detail |
|---|---|
| **Encoding** | UTF-8 |
| **File names** | Lowercase, `_` or `-` separators, `.js` / `.ts` extension |
| **Unicode** | Use actual Unicode characters (`μs`) over escapes for printable symbols |
| **Whitespace** | No tab characters; only ASCII horizontal space (0x20) |
| **Escape sequences** | Use `\n`, `\t` etc. over numeric escapes |
| **Modules** | All code in ES modules (`import`/`export`) or `goog.module` |
| **Types (TS)** | Type annotations and interfaces are first-class; prefer over `typeof` |

---

## 14. Python Guidelines

### Language Rules

| Topic | Decision |
|---|---|
| **Linter** | `pylint` with the Google `pylintrc` config |
| **Imports** | `import module`; no `from module import *` |
| **Exceptions** | Raise specific exception types; never silently suppress |
| **Global state** | Avoid mutable global state |
| **Type annotations** | Encouraged across all new code |
| **Power features** | Metaclasses, `__slots__`, etc. — sparingly, with justification |

### Style Rules

| Rule | Detail |
|---|---|
| **Indentation** | 4 spaces — no tabs |
| **Line length** | 80 characters |
| **Blank lines** | 2 between top-level defs; 1 between methods |
| **Semicolons** | Never |
| **Import order** | Standard lib → Third-party → Local; alphabetical within groups |
| **Strings** | Prefer single quotes; f-strings for formatting |
| **Trailing commas** | Use in multi-line sequences |

### Naming Conventions

| Symbol | Convention | Example |
|---|---|---|
| Modules | `snake_case` | `my_module.py` |
| Classes | `PascalCase` | `MyClass` |
| Functions / Methods | `snake_case` | `my_function()` |
| Constants | `UPPER_SNAKE_CASE` | `MAX_COUNT` |
| Private | Leading `_` | `_internal` |

### Docstrings
- Required for every public module, function, class, and method.
- First line: one-sentence summary. Then `Args:`, `Returns:`, `Raises:` for non-trivial functions.

---

## 15. Go Guidelines

### Style Principles (priority order)
1. **Clarity** — purpose is self-evident
2. **Simplicity** — simplest correct solution
3. **Concision** — high signal-to-noise
4. **Maintainability** — easy to evolve
5. **Consistency** — matches the broader codebase

### Naming
- Functions that return → noun-like: `JobName()`
- Functions that act → verb-like: `WriteDetail()`
- No `Get` prefix on getters: `Name()` not `GetName()`
- No repetition of package name, receiver type, or parameter types in function names
- Disambiguate with suffix: `WriteTextTo` vs `WriteBinaryTo`

### Least Mechanism Principle
1. Core language construct (channel, slice, map, loop, struct)
2. Standard library
3. Shared Google library
4. New dependency (only if nothing above suffices)

---

## 16. Shell / Bash Guidelines

### When to Use Shell
- Small utilities or simple wrapper scripts only.
- > ~100 lines or complex control flow → rewrite in a structured language.

### Rules

| Rule | Detail |
|---|---|
| **Language** | Only `#!/bin/bash`; no SUID/SGID |
| **File extension** | Executables: `.sh` or none · Libraries: `.sh`, not executable |
| **Indentation** | 2 spaces |
| **Line length** | 80 chars; `\` for continuation |
| **Errors** | Always send to `STDERR` |
| **Conditionals** | `; then` / `; do` on same line as `if` / `while` |

### Naming

| Symbol | Convention |
|---|---|
| Functions | `snake_case` |
| Local variables | `snake_case` (declare with `local`) |
| Constants / Env vars | `UPPER_SNAKE_CASE` (use `readonly`) |
| Source files | `snake_case.sh` |

---

## 17. C# Guidelines

### Naming

| Element | Convention |
|---|---|
| Classes, Methods, Public fields, Namespaces | `PascalCase` |
| Local variables, Parameters | `camelCase` |
| Private / Protected fields | `_camelCase` |
| Interfaces | `IPascalCase` |
| Files / Directories | `PascalCase` |
| Acronyms | Treated as one word — `MyRpc`, not `MyRPC` |

### Organization
- Modifier order: `public protected internal private new abstract virtual override sealed static readonly extern unsafe volatile async`
- `using` at top; `System` first, then alphabetical
- Class members: nested types → fields → constructors → methods; public before private within each group

### Formatting
- 2-space indentation · 100-char column limit · no tabs
- No line break before `{` · braces always required
- One statement/assignment per line

---

## 18. Objective-C Guidelines

### Core Principles
1. **Optimize for the reader** — clarity over brevity
2. **Be consistent** — uniform style lets engineers focus on logic
3. **Follow Apple SDK conventions** — Cocoa naming patterns
4. **Rules must earn their place** — only enforce rules with clear benefit

### Key Rules
- Names as descriptive as possible; no non-standard abbreviations.
- All interfaces, categories, and protocols must have `/** ... */` doc comments adjacent to the symbol.
- Comments explain *why*; self-documenting names explain *what*.

---

## 19. R Guidelines

| Rule | Detail |
|---|---|
| **Function names** | `BigCamelCase` |
| **Private function names** | `.DotBigCamelCase` (leading dot) |
| **Assignment** | Left-hand `<-` only; no right-hand `->` |
| **Return** | Always explicit `return()` |
| **Namespace qualification** | `purrr::map()` for all external functions |

---

## 20. Documentation / Markdown Guidelines

### Philosophy
- **Radical simplicity** — scalability and interoperability over features
- **Plain text is superior** — content and presentation must stay separate
- **Minimum viable documentation** — fresh and accurate beats large and stale
- **Better is better than best** — incremental improvement over prolonged debate

### Document Layout
```markdown
# Document Title

Short 1–3 sentence introduction.

[TOC]

## Topic

Content.

## See also

* https://link-to-more-info
```

### Formatting Rules

| Rule | Detail |
|---|---|
| **Line length** | 80 characters |
| **Headings** | ATX-style `##`, not Setext `---` underlines |
| **Single H1** | One `#` heading per document |
| **Trailing whitespace** | Always remove |
| **Code blocks** | Fenced ` ``` ` with language declared; never indented |
| **Links** | Informative text — never "click here" |
| **Images** | Always include alt text |
| **Tables** | Use sparingly; prefer lists |
| **HTML in Markdown** | Strongly avoid — use Markdown syntax |

---

## 21. Naming Conventions Cheat Sheet

| Language | Variables | Functions / Methods | Classes | Constants | Files |
|---|---|---|---|---|---|
| **HTML/CSS** | `kebab-case` (classes) | — | — | — | `kebab-case.html` |
| **JavaScript** | `camelCase` | `camelCase` | `PascalCase` | `UPPER_SNAKE_CASE` | `kebab-case.js` |
| **TypeScript** | `camelCase` | `camelCase` | `PascalCase` | `UPPER_SNAKE_CASE` | `kebab-case.ts` |
| **Python** | `snake_case` | `snake_case` | `PascalCase` | `UPPER_SNAKE_CASE` | `snake_case.py` |
| **Go** | `camelCase` | `camelCase` / `PascalCase` (exported) | `PascalCase` | `PascalCase` (exported) | `snake_case.go` |
| **Shell** | `snake_case` | `snake_case` | — | `UPPER_SNAKE_CASE` | `snake_case.sh` |
| **C#** | `camelCase` · `_camelCase` (private fields) | `PascalCase` | `PascalCase` | `PascalCase` | `PascalCase.cs` |
| **Objective-C** | `camelCase` | `camelCase` | `PascalCase` | `kPascalCase` | `PascalCase.m` |
| **R** | `snake_case` | `BigCamelCase` | — | — | `snake_case.R` |

---

*Visual design system: [Material Design 3](https://m3.material.io/) — licensed under [Apache 2.0](https://github.com/material-components/material-components-android/blob/master/LICENSE).*
*Code style guides: [Google Style Guides](https://google.github.io/styleguide/) — licensed under [CC-By 3.0](https://creativecommons.org/licenses/by/3.0/).*
