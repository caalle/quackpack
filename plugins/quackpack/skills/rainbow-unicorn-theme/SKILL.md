---
name: rainbow-unicorn-theme
description: Restyle an existing HTML artifact in a light, bright pastel "rainbow and unicorn" theme (Fredoka/Nunito, rainbow gradients, chunky rounded cards, emoji eyebrows) while keeping every piece of content and structure unchanged. Use when asked to apply the rainbow, unicorn, pastel or "quackpack" theme to an artifact, page, report or dashboard, or to make one "more fun/colourful" in this style.
---

# Rainbow Unicorn Theme

Light, bright pastel "rainbow and unicorn" styling: rounded and chunky, but still easy to read.

## Hard rules
- **Change styling only:** colors, fonts, spacing, borders, radii, shadows and decoration.
- **Keep content and structure exactly as they are.** Don't add, remove, reword or reorder text, sections, rows or elements. The decorative additions below (🦄 after the H1, eyebrow emoji, footer emoji, rainbow stripe) go in through CSS (`::before` / `::after`, backgrounds) wherever possible, not as new markup.
- If the artifact has no element of a given kind (no tables, no footer…), skip that rule. Don't create one.
- Keep text readable: body text stays `#3a2a5c` on white or near-white. Rainbow gradients are for headings, stripes and decoration, never for body copy.
- The theme is light-only. Set `color-scheme: light` and don't add a dark variant unless the user asks.

## Workflow
1. Read the artifact and list the element kinds it uses (headings, eyebrows, tables, cards, pills, figures, notes, numbered lists, footer…).
2. Start from [references/theme.css](references/theme.css). Map its selectors onto the artifact's existing classes and elements. Retarget the selectors to fit the markup; don't rename classes in the HTML.
3. Replace the artifact's old style rules with the themed ones. Remove old colors and fonts that would fight the theme.
4. Load the fonts from Google Fonts (the `<link>` in the reference file).
5. Check at desktop and phone width (16px side gutter, no horizontal scroll). Diff the visible text before and after: it must be identical, apart from the CSS-generated decoration.

## Theme spec

### Fonts (Google Fonts)
| Use | Font |
|---|---|
| Headings, eyebrows, table headers | Fredoka 600 |
| Body | Nunito, 15px, weight 600, line-height 1.55 |
| Codes, IDs, numbers | Source Code Pro, `font-variant-numeric: tabular-nums` |

### Colors
| Token | Value |
|---|---|
| Page | `#fff8fd` |
| Cards | `#fff` |
| Text | `#3a2a5c` |
| Muted text | `#6b5a8a` |
| Borders | `#f0d9f5` |
| Accent (links, eyebrows, IDs) | `#c2338a` |
| Rainbow | `linear-gradient(90deg, #ff6b6b, #ffa94d, #ffd43b, #69db7c, #4dabf7, #9775fa, #f06595)` |

Status pills (background / text):

| Status | Background | Text |
|---|---|---|
| Green | `#d3f9d8` | `#1b7a34` |
| Amber | `#fff0cf` | `#b35400` |
| Blue | `#e0f0ff` | `#1c5d99` |
| Lavender | `#efe5ff` | `#6a3fb5` |

### Page
- Soft, fixed radial glows on the background: pink `#ffe3f3` top-left, blue `#e0f0ff` top-right, cream `#fff3cf` bottom.
- An 8px rainbow stripe across the top of the page.
- A centered column, max 1100px wide, with 56px between sections.

### Headings
- **H1:** `clamp(32px, 5vw, 52px)` in rainbow gradient text, followed by 🦄. Keep the emoji in its own colors; don't clip it with the gradient.
- **H2:** 26px, with an 84×5px rainbow pill under it.
- **Eyebrow labels:** uppercase, accent-colored Fredoka, each starting with a themed emoji, cycling 🌈 ✨ 🌸 🌟.

### Components
- **Containers** (tables, cards, list items): white, 3px `#f0d9f5` border, 20–22px radius, shadow `0 6px 18px rgba(194,51,138,.08)`.
- **Tables:** Fredoka uppercase headers on a pastel gradient (`#fff0f6 → #f3f0ff → #e7f5ff`), cells padded `10px 14px`, group rows on a pastel rainbow gradient.
- **Cards:** an 8px top border in their category color.
- **Nav links and tags:** fully rounded pills.
- **Key figures:** chunky boxes with a `0 4px 0` shadow, border colors cycling `#ffc9c9`, `#ffe8a3`, `#b2f2bb`, `#d0bfff`.
- **Notes:** 3px dashed `#e9c9f2` border.
- **Numbered items:** round badges, cycling through the same pastels.
- **Footer:** rainbow top border, ending with 🦄🌈✨.
