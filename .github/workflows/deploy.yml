#!/usr/bin/env node

const fs = require("fs");
const path = require("path");

const SRC_DIR = path.join(__dirname, "src");
const OUTPUT_FILE = path.join(__dirname, "nav.json");

/**
 * Recursively scan a directory and build nav structure
 * Returns: { name, type: 'folder'|'file', children: [...], url: '...' }
 */
function scanDirectory(dir, baseUrl = "") {
  const items = fs.readdirSync(dir, { withFileTypes: true });
  const nav = [];

  items
    .filter((item) => !item.name.startsWith(".")) // Skip hidden files
    .forEach((item) => {
      if (item.isDirectory()) {
        // Recursively scan subdirectories
        const children = scanDirectory(path.join(dir, item.name), `${baseUrl}/${item.name}`);
        if (children.length > 0) {
          nav.push({
            name: item.name.replace(/-/g, " "),
            type: "folder",
            children: children,
          });
        }
      } else if (item.isFile() && item.name.endsWith(".html")) {
        // Only include HTML files
        const title = item.name.replace(".html", "").replace(/-/g, " ");
        nav.push({
          name: title,
          type: "file",
          url: `${baseUrl}/${item.name}`,
        });
      }
    });

  // Sort: folders first, then files, both alphabetically
  nav.sort((a, b) => {
    if (a.type !== b.type) return a.type === "folder" ? -1 : 1;
    return a.name.localeCompare(b.name);
  });

  return nav;
}

// Generate nav
const nav = scanDirectory(SRC_DIR, "");

// Write to nav.json
fs.writeFileSync(OUTPUT_FILE, JSON.stringify(nav, null, 2));
console.log(`✓ Generated ${OUTPUT_FILE}`);
console.log(`✓ Found ${countItems(nav)} items`);

/**
 * Count total items (for logging)
 */
function countItems(items) {
  return items.reduce((sum, item) => {
    return sum + 1 + (item.children ? countItems(item.children) : 0);
  }, 0);
}
