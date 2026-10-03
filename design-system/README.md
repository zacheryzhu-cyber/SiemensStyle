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

## Technical diagrams (HUD layer)

Use this layer for architecture, data-flow and platform slides. The base system is flat and ruled; diagrams need depth and signal. Stylesheet: `design-system/hud.css`. Reference build: `design-system/deck/architecture-demo.html`.

Why plain cards look flat: thick borders, one fill colour, no depth, no flow. Fix it with these recipes.

1. **Stage, not a box.** Put the diagram on a teal-black floor (`#010E13` to `#02171E`) with a radial mint glow, an inner glow edge, a 9 degree `rotateX` tilt, faint scanlines and a slow sweeping band (`.hud-stage`, `.hud-tilt`, `.hud-scan`).
2. **Hairlines, not borders.** Nodes use 1.2 px strokes in their source colour. Hover raises the stroke to 2 px and adds a coloured glow. No 4 px frames.
3. **Colour codes the source.** OT is Data Blue 500, IT is Data Blue 700, ET and existing systems are Data Purple 400, future scope is Data Orange 200, live signal is Data Turquoise 400. One hue per meaning, always with a text label.
4. **Flow, not arrows.** Connect nodes with curved paths. Animate dashes (`stroke-dashoffset`) and send small packets along each path with `animateMotion`. Idle edges are 16% white.
5. **Mono for machine text.** Courier New for node labels, protocol names and readouts, uppercase with letter spacing. Arial stays for headings and body.
6. **HUD furniture.** Corner brackets, a pulsing live dot, and small readouts in the stage corners (`LIVE · 3 SOURCES`, `LAYER 01 / 03`). Keep to three readouts.
7. **Hover focus.** Hovering a node dims everything not on its path to 20% and brightens its flow. Layer cards on the left are glass panels with a colour-coded left edge that glow when active.
8. **Glow budget.** Glow marks what is live or selected. If everything glows, nothing does.

Keep the no scroll bar, hover, entrance and reduced-motion rules from the HTML slides section. Respect `prefers-reduced-motion` by stopping the sweep, the dash flow and the pulse.
