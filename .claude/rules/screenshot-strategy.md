---
description: When and how to take screenshots during design recreation — full-page vs. section-by-section
---

## Order of operations

1. **Full-page first** — `browser_take_screenshot` with `fullPage: true` after each major batch of changes. Gives a bird's-eye view of all sections at once.
2. **Section-by-section** — After a full-page pass, scroll to each section with `browser_evaluate(() => window.scrollTo(0, N))` and take a viewport screenshot to inspect detail. Do this after every significant section update.

## Naming convention
Save files with a version suffix so you can compare across rounds:
- `screenshot-v1.png`, `screenshot-v2.png` — full-page iterations
- `our-hero.png`, `our-pricing.png` — our viewport shots per section
- `ref-hero.png`, `ref-pricing.png` — reference viewport shots per section

## Avoid fixed/sticky navbars in full-page screenshots
Navbars with `position: sticky` or `position: fixed` appear at their natural document position in Playwright full-page screenshots, causing them to render twice (once at top, once mid-page). Remove `sticky`/`fixed` positioning for the purposes of static recreation, or use `position: relative` instead.
