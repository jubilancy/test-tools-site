# 11ty Auto-Nav Site

A minimal 11ty setup that auto-generates navigation from your HTML files—no config updates needed.

## How It Works

- **Auto-discovery**: Any `.html` file in `src/` with frontmatter automatically appears in nav
- **Layout wrapping**: All pages get consistent styling + navigation
- **GitHub Pages**: One workflow file handles builds & deployment
- **Zero friction**: Add a file → it appears in nav → push → live

## Setup

```bash
# Install dependencies
npm install

# Run locally (live reload)
npm run dev

# Build for production
npm run build
```

Visit `http://localhost:8080` to see your site with live reload.

## Adding New Pages

Create a new `.html` file in `src/`:

```html
---
layout: layout.njk
title: My New Page
---

<h1>My New Page</h1>

<p>Content here...</p>
```

That's it. It appears in the nav automatically.

## Deploying to GitHub Pages

1. Push this folder to GitHub (new repo)
2. Go to **Settings → Pages → Build & Deployment**
3. Set source to **GitHub Actions**
4. The workflow will trigger automatically on push
5. Site deploys to `https://username.github.io/repo-name`

## Customizing

- **Navigation order**: Edit `.eleventy.js` and change the `sort()` logic
- **Styling**: Edit `src/css/style.css`
- **Layout**: Edit `src/_includes/layout.njk`

## Adding Folders / Subpages

If you want a deeper structure (e.g., `portfolio/project1.html`), the current setup treats files at the root only. To handle subfolders:

1. Edit `.eleventy.js` to recursively walk directories
2. Or use 11ty's built-in collections + dynamic paths

Ask if you need that setup.
