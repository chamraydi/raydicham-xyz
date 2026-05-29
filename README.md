# raydicham.xyz — Portfolio Site

## Vercel Deployment

1. Push this folder to a GitHub repo (or drag-drop to vercel.com)
2. Connect to Vercel → New Project → Import repo
3. Framework: **Other** (static HTML)
4. Root directory: leave as `/`
5. Hit Deploy — done.

---

## Adding / Replacing Artwork

### Hero Carousel (1280×720px recommended)
Place your images in `/images/carousel/`:
```
images/carousel/01.jpg
images/carousel/02.jpg
images/carousel/03.jpg
...
```
Then in `index.html`, find the section marked `<!-- CAROUSEL SLIDES -->` and replace:
```html
<!-- BEFORE (placeholder) -->
<div class="cs slide-ph-1"><span>Replace with artwork</span></div>

<!-- AFTER (your image) -->
<div class="cs"><img src="images/carousel/01.jpg" alt="Project name"></div>
```

### Strip Thumbnails (any ratio, ~300×200px)
Same folder works. Find `<!-- STRIP SLIDES -->` and swap:
```html
<div class="ss sp-1"></div>
<!-- becomes -->
<div class="ss"><img src="images/carousel/01.jpg" alt=""></div>
```

### Project Card Backgrounds
Place project screenshots in `/images/projects/` and add to the card:
```html
<div class="pc-founders" style="position:absolute;inset:0;">
  <img src="images/projects/founders-forge.jpg" style="width:100%;height:100%;object-fit:cover;opacity:0.6;">
</div>
```

---

## Adding Videos
For video backgrounds in carousels, replace the `<div class="cs">` with:
```html
<div class="cs">
  <video autoplay muted loop playsinline style="width:100%;height:100%;object-fit:cover;">
    <source src="images/carousel/showreel.mp4" type="video/mp4">
  </video>
</div>
```

---

## Recommended Tools for Self-Editing

**Easiest (no-code, drag & drop):**
- **Framer** — framer.com — best for a designer. Import this HTML or rebuild in Framer. 
  Add images/videos by dragging in. CMS built-in for project updates.
- **Webflow** — webflow.com — more powerful CMS, great for updating project cards.

**Code editor (if comfortable):**
- **VS Code** + **Live Server extension** — edit HTML directly, preview in browser
- **Cursor** — AI-assisted code editor, great if you want to make changes by describing them

**Quick image hosting:**
- Drop images into `/images/carousel/` and push to GitHub — Vercel auto-deploys.

---

## File Structure
```
raydicham/
├── index.html          ← main site
├── vercel.json         ← Vercel config
├── README.md           ← this file
└── images/
    ├── carousel/       ← hero carousel & strip artwork (1280×720px)
    └── projects/       ← project card backgrounds
```
