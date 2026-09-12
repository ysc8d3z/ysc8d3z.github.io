# Hybrid Workout Plan — home screen app

Single-page plan that opens on today's session, works offline, and installs to your phone's
home screen with no browser chrome.

## Deploy (GitHub Pages, ~2 min)

1. Create a repo, e.g. `workout-plan`.
2. Drop these files in the root (`index.html`, `sw.js`, `manifest.webmanifest`, the three icons).
3. Push. Then Settings → Pages → Source: `main` / root.
4. Wait ~60s for `https://<user>.github.io/workout-plan/`.

Any static host works — Netlify drag-and-drop, Cloudflare Pages, S3 + CloudFront.
The only requirement is **HTTPS**, because service workers won't register over plain HTTP.
Paths are all relative, so a subdirectory is fine.

## Install on iPhone

Open the URL in **Safari** (not Chrome — only Safari can install to the home screen on iOS),
then Share → Add to Home Screen.

Launch it once while online so the service worker caches the fonts. After that it opens
offline, which is what you want in a gym basement.

## Android

Chrome will prompt to install, or use ⋮ → Add to Home screen.

## Updating the plan

Edit `index.html`, then bump the cache name in `sw.js` (`hybrid-plan-v1` → `v2`) and push.
Without the bump, the old version stays cached and your change won't appear.
