# Homeschool Command Center — installable (PWA) version

This is the **hosted** version of the app: the same product, plus the small extra files
that let a phone "install" it to the home screen and run it **offline** after the first
load. This is the folder whose URL you share with customers.

> Keep this repo **public** (GitHub Pages needs that) — it only contains the finished
> app a buyer already receives, never your source or build tooling.

## Files

- `index.html` — the app, with a manifest link + service-worker registration added.
- `manifest.webmanifest` — name, colours, and icons used when the app is installed.
- `sw.js` — the service worker; caches the app so it works offline.
- `icon-192.png`, `icon-512.png`, `*-maskable.png`, `apple-touch-icon.png` — home-screen icons.
- `.nojekyll` — tells GitHub Pages to serve everything as-is.

## Host it (GitHub Pages)

1. Put these files at the **root** of a public repo.
2. **Settings → Pages → Deploy from a branch → main → / (root)**.
3. Open the `https://<you>.github.io/<repo>/` URL — that's the link you give customers.

Every path here is relative, so it works whether the site is at a root domain or a
`/<repo>/` subpath.

## When you update the product

The service worker caches the app, so returning customers keep the cached copy until the
cache name changes. **Every time you replace `index.html`, bump `CACHE_VERSION` in
`sw.js`** (e.g. `hcc-v1` → `hcc-v2`). On their next online open, customers automatically
get the new version.

## Tell your customers (one short note in your listing / delivery)

- **On iPhone/iPad:** open the link in **Safari**, tap the **Share** button, then **Add to
  Home Screen**. It then opens full-screen like an app and works offline.
- **On Android:** open the link in **Chrome**; it offers **Install** / "Add to Home
  screen" automatically.
- **Pick one home for your data.** The installed app and the downloaded file each keep
  their **own** separate records — use one or the other, not both. To move between your
  own devices, use **Back up** to export a file and **Restore** to load it on the other
  device.
