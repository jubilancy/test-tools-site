# JavaScript Tools Repo — Setup Guide

## What You Got

A complete, ready-to-deploy repository with:
- ✅ **15 tool pages** — each tool in a proper HTML boilerplate
- ✅ **Unified styling** — gradient header, sticky nav, responsive design
- ✅ **Navigation system** — click between tools instantly
- ✅ **No build step** — pure HTML/CSS/JS, ready to deploy
- ✅ **GitHub Pages ready** — deploy in seconds

## Quick Start

### Option 1: Deploy to GitHub Pages (Fastest)

1. **Create a GitHub repo** called `js-tools-repo` (or any name)

2. **Extract the zip** (`js-tools-repo.zip`)

3. **Push to GitHub:**
   ```bash
   cd js-tools-repo
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/js-tools-repo.git
   git push -u origin main
   ```

4. **Enable GitHub Pages:**
   - Go to Settings → Pages
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/docs`
   - Click Save

5. **Done!** Your site is live at:
   ```
   https://YOUR_USERNAME.github.io/js-tools-repo
   ```

### Option 2: Run Locally

```bash
cd js-tools-repo

# Using Python 3
python -m http.server 8000

# Using Node.js
npm install --save-dev http-server
npm start

# Open http://localhost:8000/docs
```

### Option 3: Deploy to Netlify/Vercel

1. Extract the zip
2. Connect the repo to Netlify/Vercel
3. Set publish directory to `docs/`
4. Deploy!

## File Structure

```
js-tools-repo/
├── docs/                          ← This folder gets deployed
│   ├── index.html                 ← Home page
│   ├── 01-papa-parse.html         ← Tool pages
│   ├── 02-lunrjs.html
│   ├── ... (12 more)
│   └── 14-dayjs.html
├── README.md                       ← Project info
├── package.json                    ← (Optional) for npm start
└── .gitignore
```

## What Each Tool Page Has

Every page (`docs/*.html`) contains:

```
┌─────────────────────────────────────────┐
│         GRADIENT HEADER                 │  ← Tool title
├─────────────────────────────────────────┤
│  Home | Papa Parse | Lunr.js | Chart.js │  ← Sticky nav (active highlighting)
├─────────────────────────────────────────┤
│                                         │
│         Tool Content (Your HTML)        │  ← The actual tool
│         (from original files)           │
│                                         │
├─────────────────────────────────────────┤
│  © 2024 JavaScript Tools                │  ← Footer
└─────────────────────────────────────────┘
```

## Navigation

The navigation is **auto-generated** by JavaScript. It includes:
- All 15 tools
- Active state highlighting (shows which page you're on)
- Fully responsive (stacks on mobile)
- Sticky (stays at top when scrolling)

## Customization

### Change Header Colors

In `boilerplate.html` (or any `.html` file), find:
```css
header {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

Change `#667eea` and `#764ba2` to your brand colors.

### Change Footer Text

Find in any `.html`:
```html
<footer>
    <p>&copy; 2024 JavaScript Tools. Built with care.</p>
</footer>
```

### Add More Tools

1. Take your new tool's HTML file
2. Extract just the `<body>` content
3. Inject it into the boilerplate template
4. Add it to the `tools` array in the script section

## Troubleshooting

### "CSS not loading" or "Page looks broken"

Make sure you're accessing through the correct path:
- ✓ `https://username.github.io/js-tools-repo/` (correct)
- ✗ `https://username.github.io/` (wrong)

If using a custom domain, it should work fine.

### Navigation not working

- Reload the page
- Check browser console for errors
- Ensure JavaScript is enabled

### Tools not displaying

- Each tool's content is self-contained in the `<main>` element
- No external resources needed (all CDN scripts are in the original HTML)
- If a tool uses external libraries, they're loaded via CDN inside each page

## Browser Support

- Chrome/Edge ✅
- Firefox ✅
- Safari ✅
- Mobile browsers ✅

## What's NOT Included

- No build tools (Webpack, Vite, etc.)
- No backend
- No database
- No authentication

Everything is static HTML that works in any browser.

## Support

Each tool comes from a reputable library. For tool-specific questions:
- Papa Parse docs: https://www.papaparse.com/
- Lunr.js docs: https://lunrjs.com/
- And so on...

---

You're all set! Push to GitHub and share the link. 🚀
