# GitHub Actions Auto-Nav Setup

This setup automatically generates `nav.json` whenever you push new folders/files to your repo.

## How It Works

1. **You push new files** to `src/` (any folder structure)
2. **GitHub Actions runs** `generate-nav.js`
3. **nav.json is generated** from your folder structure
4. **nav.json is auto-committed** back to the repo
5. **Your HTML files load nav.json** and render the navigation dynamically

## Files

- `generate-nav.js` — Node.js script that scans `src/` and creates `nav.json`
- `.github/workflows/deploy.yml` — GitHub Actions workflow (runs generate-nav.js on every push)
- `nav-example.html` — Example HTML showing how to load/render nav.json
- `nav.json` — Auto-generated (don't edit manually)

## Setup Steps

1. **Add these files to your GitHub repo:**
   - `generate-nav.js` (root)
   - `.github/workflows/deploy.yml` (GitHub Actions workflow)

2. **In your HTML files**, load and render nav.json:

```html
<script>
  async function loadNav() {
    const response = await fetch("/nav.json");
    const navItems = await response.json();
    // Render navItems into your nav element
  }
  loadNav();
</script>
```

See `nav-example.html` for a complete example with dropdowns.

## Folder Structure Example

```
src/
├── index.html
├── about.html
├── js/
│   ├── tool1.html
│   ├── tool2.html
├── tools/
│   ├── converter.html
│   ├── generator.html
```

Results in `nav.json`:
```json
[
  {
    "name": "about",
    "type": "file",
    "url": "/about.html"
  },
  {
    "name": "index",
    "type": "file",
    "url": "/index.html"
  },
  {
    "name": "js",
    "type": "folder",
    "children": [
      { "name": "tool1", "type": "file", "url": "/js/tool1.html" },
      { "name": "tool2", "type": "file", "url": "/js/tool2.html" }
    ]
  },
  {
    "name": "tools",
    "type": "folder",
    "children": [
      { "name": "converter", "type": "file", "url": "/tools/converter.html" },
      { "name": "generator", "type": "file", "url": "/tools/generator.html" }
    ]
  }
]
```

## Customization

**Change what gets scanned**: Edit `generate-nav.js`
- Filter file types (currently `.html` only)
- Change sorting logic
- Add metadata (dates, descriptions)

**Add to GitHub Actions**: Edit `.github/workflows/deploy.yml`
- Add build steps before `generate-nav.js` runs
- Change commit message

## No Manual Config Needed

Just add files → push → nav updates automatically.
