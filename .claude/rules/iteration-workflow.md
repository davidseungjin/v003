---
description: Workflow for recreating a web design from a reference screenshot — generate, screenshot, compare, fix, repeat
---

When given a reference image (screenshot) and optional CSS/style notes, follow this loop:

1. **Generate** a single `index.html` using Tailwind CSS (CDN). All content inline.
2. **Screenshot** the rendered page using Playwright MCP (`browser_navigate` → `browser_take_screenshot` with `fullPage: true`). Capture distinct sections separately if needed.
3. **Compare** screenshot against the reference. Check every detail:
   - Spacing and padding (measure in px)
   - Font sizes, weights, and line heights
   - Colors (exact hex values)
   - Alignment and positioning
   - Border radii, shadows, and effects
   - Image/icon sizing and placement
4. **Fix** every mismatch found. Edit the HTML/Tailwind code.
5. **Re-screenshot** and compare again.
6. **Repeat** steps 3–5 until result is within ~2–3px of the reference everywhere.

Do NOT stop after one pass. Always do at least 2 full comparison rounds. Only stop when the user says so or when no visible differences remain.
