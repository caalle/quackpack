---
name: unicornify-artifact
description: Restyle an existing HTML page, report, dashboard or artifact in a light, bright pastel "rainbow and unicorn" theme (Fredoka/Nunito, rainbow gradients, chunky rounded cards, emoji eyebrows) while keeping every piece of content and structure unchanged. Use when asked to unicornify something, to apply a rainbow, unicorn or pastel theme, or to make a page "more fun/colourful" in this style.
---

# Unicornify Artifact

Light, bright pastel "rainbow and unicorn" styling: rounded and chunky, but still easy to read. [references/theme.css](references/theme.css) is the theme and the single source of truth for fonts, colours and sizes. This file says how to apply it.

## Hard rules
- **Change styling only:** colours, fonts, spacing, borders, radii, shadows and decoration.
- **Keep content and structure exactly as they are.** Don't add, remove, reword or reorder text, sections, rows or elements. All decoration (🦄 after the H1, eyebrow emoji, footer emoji, rainbow stripe) is CSS-generated through `::before`, `::after` and backgrounds. Never add markup for it.
- If the page has no element of a given kind (no tables, no footer…), skip that rule. Don't create one.
- Body text stays dark on white or near-white. Rainbow gradients are for headings, stripes and decoration, never for body copy.
- The theme is light-only. Keep `color-scheme: light` and don't add a dark variant unless the user asks.
- Don't change token values in the theme ad hoc. If the page needs a colour the theme lacks, use the nearest token.

## Workflow
1. Read the page and list the element kinds it uses: headings, eyebrows, nav, tables, cards, pills, key figures, notes, numbered lists, footer.
2. Copy `theme.css` into the page, then retarget its selectors to the page's existing classes and elements. Don't rename classes in the HTML. Cards take their top-border colour from `--cat`; set it per card category in CSS (for example `.card.sales { --cat: var(--p2); }`) or leave the default.
3. Remove the old rules that would fight the theme: colours, fonts, borders, shadows. Keep layout rules (grid, flex, widths) unless they clash.
4. Add the Google Fonts `<link>` from the comment at the top of `theme.css` to `<head>`.
5. Verify:
   - Extract the visible text before and after (strip tags, collapse whitespace, or compare `document.body.innerText`) and diff. The only differences allowed are the CSS-generated emoji.
   - Check desktop and phone width: 16px side gutter, no horizontal scroll. Tables scroll inside themselves on narrow screens; the theme handles that.

## What the theme looks like
The page is near-white with soft pastel radial glows and an 8px rainbow stripe fixed at the top, in a centred column of at most 1100px. The H1 is rainbow-gradient text followed by 🦄. H2s get a short rainbow pill underneath. Eyebrow labels are uppercase, accent-coloured Fredoka, each starting with 🌈 ✨ 🌸 or 🌟 in turn. Containers (cards, tables, panels) are white with a thick pastel border, a large radius and a soft pink shadow; cards also get a coloured top border. Table headers are uppercase Fredoka on a pastel gradient. Nav links and tags are fully rounded pills; status pills come in green, amber, blue and lavender. Key figures are chunky boxes with a solid offset shadow cycling four pastels. Notes have a dashed border. Numbered steps get round pastel badges. The footer has a rainbow top border and ends with 🦄🌈✨.

[references/example.html](references/example.html) is a page with every element kind, styled with the theme.
