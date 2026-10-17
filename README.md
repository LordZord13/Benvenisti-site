# Atelier Benvenisti — website

Static website for Atelier Benvenisti, handbags made by hand in Zürich's Old Town.
No build step, no dependencies, no environment variables, no API keys.

## Structure

```
index.html       The whole site (Home, Collection, Product, Craft, Atelier, Checkout…)
support.js       Runtime that renders index.html (loads React 18 from unpkg.com)
image-slot.js    Image component used on product cards
assets/          Photography, WebP, max 1600 px wide (~3 MB total)
vercel.json      Headers: caching, security, and noindex while in review
.gitignore
```

## Run locally

Any static server works, e.g.:

```
npx serve .
# or
python3 -m http.server 8000
```

Then open http://localhost:8000. (Opening index.html directly from the file system may block script loading in some browsers.)

## Deploy on Vercel (recommended)

1. vercel.com → **Add New → Project** → import `LordZord13/Benvenisti-site`.
2. Framework preset: **Other**. Build command: *none*. Output directory: `./` (root).
3. Deploy. You get a public HTTPS URL like `benvenisti-site.vercel.app`.

From then on:
- Every push to `main` → **production** deploy, automatically.
- Every other branch or pull request → its own **preview URL**, to share with colleagues before it goes live.

## Making changes

```
git checkout -b my-change      # work on a branch
# edit files
git commit -am "Describe the change"
git push -u origin my-change   # Vercel posts a preview URL
# open a pull request, collect feedback, then merge into main → live
```

Images: keep new photos as WebP, ≤ 1600 px wide, ≤ 250 KB.

## Going public

The site is currently **hidden from search engines** (`noindex` in `index.html` and `vercel.json`).
When ready to launch:
1. Remove `<meta name="robots" content="noindex, nofollow">` from `index.html`.
2. Remove the `X-Robots-Tag` header from `vercel.json`.
3. Optional: Vercel → Project → Settings → **Domains** → add `benvenisti.ch` and follow the DNS instructions (HTTPS is automatic).

## Not yet connected

- Checkout is a front-end mock: no payment is taken. Connect Shopify, Stripe Payment Links or WooCommerce before launch.
- Newsletter form shows a confirmation but stores nothing.
- Language switch (DE / FR) and policy pages (Delivery, Returns, Terms, Privacy) are placeholders.
