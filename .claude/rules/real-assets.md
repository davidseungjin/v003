---
description: How to handle images and assets when the reference is a live website
---

When the reference is a live site (not just a static screenshot):

1. Navigate to the site with Playwright and run `browser_evaluate` to extract all image URLs and their positions:
   ```js
   () => {
     return Array.from(document.querySelectorAll('img')).map(img => ({
       src: img.src,
       absTop: Math.round(img.getBoundingClientRect().top + window.scrollY),
       w: img.naturalWidth,
       h: img.naturalHeight
     })).filter(i => i.src).sort((a, b) => a.absTop - b.absTop);
   }
   ```
2. Sort by `absTop` to map images to page sections.
3. Use the real image URLs directly in `<img src="...">` — do NOT use `placehold.co` when real assets exist.
4. Framerusercontent, Contentful, Cloudinary, and similar CDN URLs are publicly accessible and safe to hotlink in static HTML.
