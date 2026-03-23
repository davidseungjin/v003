---
description: Starter HTML template to use when beginning a new design recreation from scratch
---

Use this as the base for every new `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Page Title</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            // Add design tokens here, e.g.:
            // 'brand-dark': '#1e1e1e',
            // 'brand-blue': '#004370',
          },
          fontFamily: {
            sans: ['Inter', 'system-ui', 'sans-serif'],
          },
          keyframes: {
            marquee: { '0%': { transform: 'translateX(0)' }, '100%': { transform: 'translateX(-50%)' } },
          },
          animation: {
            marquee: 'marquee 30s linear infinite',
          },
        }
      }
    }
  </script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet" />
  <style>
    body { font-size: 14px; }
    /* Add any one-off CSS here */
  </style>
</head>
<body class="bg-white text-gray-900 font-sans antialiased overflow-x-hidden">

  <!-- NAVBAR -->
  <nav class="bg-white border-b border-gray-100">
    <div class="max-w-6xl mx-auto px-6 py-3 flex items-center justify-between">
      <span class="font-bold text-base">Logo</span>
      <div class="flex items-center gap-6 text-sm text-gray-600">
        <a href="#">Link</a>
      </div>
      <a href="#" class="bg-gray-900 text-white text-sm px-5 py-2.5 rounded-full font-semibold">CTA</a>
    </div>
  </nav>

  <!-- SECTIONS GO HERE -->

</body>
</html>
```

**Checklist before writing sections:**
- [ ] Design tokens added to `tailwind.config`
- [ ] Font matches reference (Inter, or swap as needed)
- [ ] `overflow-x-hidden` on body (prevents horizontal scroll from absolute floats)
- [ ] Navbar is `relative` not `sticky`/`fixed` (avoids full-page screenshot duplication)
