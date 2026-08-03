# Installing 汉字 Atlas as an app on your Pixel

This folder has everything needed: `index.html`, `manifest.json`, `sw.js`, and three icon files.
They need to stay together, with these exact filenames, in the same folder.

## Step 1 — Host it somewhere (one-time, free)

Easiest option: **GitHub Pages**

1. Create a new public GitHub repo (any name, e.g. `hanzi-atlas`)
2. Upload all 6 files from this folder into the repo root (drag-and-drop on github.com works fine)
3. Repo → Settings → Pages → under "Build and deployment", set Source to "Deploy from a branch", branch `main`, folder `/ (root)` → Save
4. Wait ~1 minute, then your app is live at `https://<your-username>.github.io/hanzi-atlas/`

Other free options that work the same way: Netlify (drag-and-drop the folder at netlify.com), Cloudflare Pages, or Vercel — any static host is fine since there's no backend at all.

## Step 2 — Install on your Pixel

1. Open that URL in Chrome or Brave on your phone
2. Tap the **⋮** menu → **"Install app"** (or **"Add to Home screen"** — wording varies slightly by browser/Android version)
3. Confirm — you'll get a real icon in your app drawer

## Step 3 — Use it

From then on, tap the icon like any other app. No browser, no address bar, works fully offline (fonts and everything else get cached the first time you open it with a connection).

## Notes

- **Your progress is stored on your phone only** (`localStorage`), tied to this specific installed app. It is not backed up anywhere, and uninstalling the app or clearing site data in the browser will erase it. If you want a backup, there's no export button yet — just don't clear your phone's app data for this one.
- If you ever update `index.html` (ask me for changes), re-upload the new version to the same host — your progress stays intact since it lives in the browser, separate from the file itself.
- The "clear all-time progress" link on the Home page is a separate, deliberate reset — everyday use won't trigger it (it asks for confirmation).
