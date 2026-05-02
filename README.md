# site/

Static landing page for waelgabsi.com. Single-developer hub: one page lists every app, each app has its own privacy/terms/support pages alongside.

## Structure

```
site/
├── index.html           — hub home (lists apps)
├── styles.css           — shared styles, mirrors the app's design system
└── quitimer/
    ├── icon.png         — app icon (192px)
    ├── privacy.html
    ├── terms.html
    └── support.html
```

## Design

Same palette as the app — midnight navy `#1a1a2e`, warm cream `#e8d5b7`, ember amber `#f5a623`. IBM Plex Mono throughout (loaded from Google Fonts CDN). Single column, max 720px wide. No frameworks, no JavaScript except a one-line copyright year.

## Local preview

```sh
python3 -m http.server -d site 8000
# then open http://localhost:8000
```

## Deploy

GitHub Pages from this directory:

```sh
git checkout -b gh-pages
git rm -rf --cached . && git add site
git commit -m "publish hub site"
git subtree push --prefix site origin gh-pages
```

Or simpler: push to main and configure Pages → "deploy from /site folder".

Or any static host (Vercel, Netlify, Cloudflare Pages) — point it at `site/` as the publish directory, no build command needed.

## Before going live

1. Replace the placeholder app store link in `index.html` (the `href="#"` on the "app store →" anchor) with the real App Store URL after submission.
2. Update `<link rel="canonical">` URLs if the domain isn't `waelgabsi.com`.
3. Update the `last updated` date in `privacy.html` and `terms.html` to the publish date.

## Adding a second app later

1. Create `site/<appname>/` with `icon.png`, `privacy.html`, `terms.html`, `support.html` (copy quitimer's, edit content).
2. Duplicate the `<article class="app">` block in `index.html` for the new app.

That's the entire scaling story.
