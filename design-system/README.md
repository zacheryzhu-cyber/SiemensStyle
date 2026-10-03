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

## HTML slides

Reference build: `design-system/deck/siemens-style-deck.html` (single self-contained file). Follow these rules for every HTML deck.

- **No scroll bar.** Slides fit the viewport and the page never shows a scroll bar on the right. Set `html, body { overflow: hidden }`, hide any inner scroll bars (`scrollbar-width: none`), size type and spacing with `vw`, `vh` and `clamp()`, and split a slide that overflows. Test at 1280 x 720, 1440 x 900 and 1920 x 1080.
- **Layout.** One idea per slide. Prefer interactive layouts over lists: a palette explorer, an accordion, a side inspector that fills in on hover, toggles for dark and light.
- **Hover feedback.** Cards lift 3 to 4 px (`translateY(-4px)`), glow in mint (`rgba(0,215,160,.28)`) and take the Data Turquoise 400 fill with Deep Blue text. Keep each transition under 200 ms.
- **Entrance motion.** When a slide opens, elements rise 16 px and fade in, 70 ms apart. One gentle motion, nothing looping.
- **Navigation.** Arrow keys, Page Up and Down, space, Home and End. A 3 px progress rail on top in `accent`, a `01 / 11` counter and Prev and Next buttons at the bottom.
- **Reduced motion.** Turn off transitions and animations under `prefers-reduced-motion: reduce`.
- **Colour.** Dark first: `surface-100` background, `ink` text, `accent` for eyebrows and highlights. Take every colour from the tokens.
