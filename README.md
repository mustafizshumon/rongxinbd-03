# RONGXIN International Trading Company Limited — V3.4 Local-First Images

All website files and image assets are placed directly in the repository root. No nested asset folders.

## V3.4 changes
- Replaced all remote Unsplash image URLs with local image assets.
- Added `images.js` as the single image registry.
- Added root-level SVG placeholders for hero, about, capabilities and product cards.
- Removed the Google Fonts network import; typography uses local system font stacks.
- Preserved the existing modular page architecture and responsive/print styles.

## Replace placeholders with your own photos
1. Prepare each photo as WebP (recommended) or JPG.
2. Keep the exact filename and root location shown below; replace the corresponding SVG file and update its extension in `images.js` if needed.
3. Recommended source images: hero 1800×1200; supporting and product images 1200×850 or larger. Use clear, licensed company photography.

| Registry key | Current root filename | Intended photo |
|---|---|---|
| `heroMain` | `img-hero-main.svg` | Apparel / sourcing hero |
| `heroDetail` | `img-hero-detail.svg` | Fabric or garment detail |
| `aboutTeam` | `img-about-team.svg` | Company team / collaboration |
| `capabilityProduction` | `img-capability-production.svg` | Production / quality process |
| `productDenim` | `img-product-denim.svg` | Denim products |
| `productWoven` | `img-product-woven.svg` | Woven trousers / casualwear |
| `productShirts` | `img-product-shirts.svg` | Shirts |
| `productKnit` | `img-product-knit.svg` | Knitwear |
| `productLadies` | `img-product-ladies.svg` | Ladies collection |
| `productKids` | `img-product-kids.svg` | Kids collection |

## Run locally
Serve this folder with a static HTTP server and open the local URL. Do not open using `file://`.

## GitHub Pages
Upload the contents of this folder directly to the repository root. `index.html` must remain at root.

## Existing modules
`runtime.js` handles rendering; `images.js` owns image paths; `data.js` owns shared data; `app.js` owns state and page composition; each `module-*.js` file owns one section; `style.css` and `responsive.css` own styling.

The inquiry form still requires the verified company email to be configured in `data.js`.


## Image loading and fallback (V3.7)
The site now resolves photography in this order:
1. Optional real image in the repository root (WebP, JPG, JPEG, PNG).
2. Unsplash CDN image if no matching root photo exists.
3. Existing designed local SVG illustration if the CDN is unavailable.

Root-level image names supported:
- `hero-main.webp` (or `.jpg`, `.jpeg`, `.png`; also `img-hero-main.*`)
- `hero-detail.*` / `img-hero-detail.*`
- `about-team.*` / `img-about-team.*`
- `capability-production.*` / `img-capability-production.*`
- `product-denim.*`, `product-woven.*`, `product-shirts.*`, `product-knit.*`, `product-ladies.*`, `product-kids.*`
  (the matching `img-product-*.{webp,jpg,jpeg,png}` names are also supported)

The original SVG artwork remains in the root and is used as an offline-safe visual fallback.


## Version 4.0.0
- Official contact email: `info@rongxinbd.com`.
- Inquiry form hands off to the visitor's configured email application using `mailto:`; it does not send or store messages on a server.
- Image delivery order: matching photo in repository root, then configured CDN URL, then designed local SVG fallback. Hero sections paint the local fallback immediately while sources are checked, avoiding an empty image block.


## Local image format auto-detection (v4.0.1)

For each registered image slot, place a file in the project root or in `images/` using the matching base name. The resolver checks `.webp`, `.jpg`, `.jpeg`, `.png`, and `.svg` candidates in that order, then tries the configured CDN image, and finally uses the designed SVG fallback. Example names include `hero-main.webp`, `hero-main.jpg`, `hero-main.jpeg`, `hero-main.png`, `hero-main.svg`, and `product-denim.webp`. The built-in `img-*.svg` files remain reserved as designed fallbacks.

Supported image slots and base names: `hero-main`, `hero-detail`, `about-team`, `capability-production`, `product-denim`, `product-woven`, `product-shirts`, `product-knit`, `product-ladies`, and `product-kids`.


## Navigation management (v4.0.2)

The public website uses `nav-managed.js` (Vanilla JavaScript) and reads `navigation.json` from the website root. The private PC control panel is distributed separately and must NOT be uploaded to the public website. Use that local panel to export a new `navigation.json`, then upload only that JSON file to the website root using your hosting file manager. Home is permanently enabled. The site safely shows all navigation items if the JSON file is missing or cannot be read.

The control panel is a local file-based tool, not a server login. The JSON file contains public display settings only; never place passwords or secrets in it.


## Private admin folder

The `admin/` folder contains the PC-only local navigation control utility. It is excluded from Git by the root `.gitignore`. Keep it on your PC for local use. Before deploying the website directly from a ZIP or uploading files manually, remove the `admin/` folder; the public website needs only the root `navigation.json` and `nav-managed.js`. Note: `.gitignore` prevents new untracked admin files from being added, but does not untrack files already committed.


## Public header and admin layout (v4.0.4)
- The public website header displays all enabled navigation links in one horizontal row on wide desktop screens.
- At tablet and mobile widths, the navigation collapses behind the menu button to preserve readability.
- The local admin control page intentionally keeps Primary Navigation and Secondary Navigation in separate management groups, with each item on its own row.
- Public display layout and admin management layout are independent; changing one does not force the other to use the same row arrangement.


## Adaptive header system (v4.1.0)
- Utility strip carries the company mark/name, location, official email and sourcing descriptor.
- The primary navigation is a single continuous horizontal row on wide screens; Contact is the final text link and Inquiry / RFQ is the separate action.
- Navigation items stay clustered with a controlled gap; the layout does not use `space-between` to distribute individual menu links across the entire header.
- At 1240px and below, the menu changes to an accessible expandable panel to protect readability and prevent clipping/overlap. The panel has a bounded height and vertical scrolling for short screens.
- Header sizing uses fluid CSS values and a content-width container; browser zoom and viewport changes naturally trigger the responsive layout.
- The top utility strip scrolls away while the compact primary navigation remains sticky.
- Reduced-motion preference is respected. Navigation retains keyboard focus styles and accessible labels.
- Admin control remains intentionally separate: Primary Navigation and Secondary Navigation are presented as independent, vertically stacked management groups.

## Release validation (v4.1.0)
- JavaScript syntax checked for every root and admin script.
- Both public and admin navigation JSON files parsed successfully.
- Public and admin HTML parsed successfully.
- ZIP archive integrity checked after packaging.

## V4.2.0 — Adaptive header refinement
The public header now measures the actual available width and the natural width of its navigation items. It remains a single horizontal row whenever the full menu and inquiry action fit; otherwise it changes to the compact menu without allowing links to become orphaned or wrap unpredictably. A compact sticky state reduces navigation height after scrolling. The compact menu supports Escape, outside-click close, and clear expanded-state semantics. The local `admin/` navigation manager remains separate and retains its line-by-line management layout.

For deployment, remove the private `admin/` directory before publishing. Keep the public root `navigation.json`, `nav-managed.js`, and `header-responsive.js` files.
