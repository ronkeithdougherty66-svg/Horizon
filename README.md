# Horizon — Balance the Moons

A tilt-to-balance arcade game. Drag your thumb left or right to tilt the
beam, keep the moon(s) from rolling off either end, and try to beat your
high score. Packaged as a installable web app (PWA) so it can live on
your phone's home screen like a native app.

## 1. Host it on GitHub Pages

1. Create a new GitHub repository (public), e.g. `horizon-balance`.
2. Upload everything in this folder to the repo, keeping the structure:
   ```
   index.html
   manifest.json
   service-worker.js
   icons/
     icon-192.png
     icon-512.png
     icon-512-maskable.png
   ```
   You can do this by dragging the files into the GitHub web UI
   ("Add file" → "Upload files"), or via git:
   ```bash
   git init
   git add .
   git commit -m "Horizon balance game"
   git branch -M main
   git remote add origin https://github.com/<your-username>/horizon-balance.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch",
   pick the **main** branch and the **/(root)** folder, then save.
5. GitHub will publish the site at:
   ```
   https://<your-username>.github.io/horizon-balance/
   ```
   It can take a minute or two for the first deploy to go live.

## 2. Install it on your phone

Open the GitHub Pages URL above in your phone's browser, then:

**iPhone (Safari)**
1. Tap the Share icon (square with an arrow).
2. Tap **Add to Home Screen**.
3. Tap **Add**. A "Horizon" icon appears on your home screen and opens
   full-screen, without Safari's address bar.

**Android (Chrome)**
1. Tap the **⋮** menu in the top right.
2. Tap **Add to Home screen** (or you may see an **Install app** banner —
   tap that instead).
3. Confirm. The game installs like a normal app, with its own icon and
   launcher entry.

Once installed, the service worker caches the game so it keeps working
even without a signal after the first load.

## Updating the game later

If you change `index.html` (or anything else) and re-upload, bump the
`CACHE_NAME` value at the top of `service-worker.js` (e.g. `horizon-balance-v2`)
so phones that already installed the app pick up the new version instead
of serving the old cached copy.

## What's new in this version

- The first moon's weight now tips the beam the moment it lands — the
  balancing act starts on impact instead of waiting for your first touch.
- Sound effects (landing thuds, danger beeps, a fall whoosh, a high-score
  chime) with a mute toggle in the top-left corner, remembered between
  sessions.
- A second moon drops in after a few seconds for extra difficulty.
- Pause / End game controls, and a persistent high score.
