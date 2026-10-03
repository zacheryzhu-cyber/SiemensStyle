# Siemens Style Design System

Extracted from `ColorGuide/*.pdf` and the icon sets in this repo.

- `tokens.json` – brand, neutral and data colours, chart sequence, type, lines, contrast, icons
- `tokens.css` – the same colours as `--sie-*` custom properties, plus `.sie-dark` / `.sie-light` page classes

## Rules
- Dark (Deep Blue `#000028`) is the primary look; light pages use Sand for text-heavy content.
- Accent: Light Petrol `#00C1B6` on dark, Petrol `#009999` on light. Use sparingly.
- Type: Arial Regular/Bold only, sizes 20/18/16/14/12 pt.
- Lines: 1 pt (tables), 1.75 pt (levels in graphics), 3 pt (segment separation); black or white; no 3D effects.
- Surfaces: Deep Blue 80/60/40% tints (black text up to 40%, white beyond); Sand surfaces take black text.
- Contrast: WCAG 2.2 AA, 4.5:1 text, 3:1 large text and graphics.
- Data chart colours are for software products, not online marketing. Prefer yellow over purple.
- Icons: 24px grid, `fill="currentColor"`; SVGs in `sie-ui-icons-svg/`, web font in `sie-ui-icons-web-font/`.

## Open items
- Deep Blue `#000028` and the surface tints are assumed/computed, not stated in the PDFs.
- Chart sequence token 14 lists Orange 700 for both dark and light in the source.
