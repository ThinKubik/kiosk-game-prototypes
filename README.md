# Tune Into You — Kiosk Game Prototypes

Two ambient touch-toy prototypes for the "time waster" kiosk game, plus a simple
index page linking to both.

- `index.html` — picker page
- `sand.html` — falling-sand toy (sand / water / moss, plus eraser)
- `ripple.html` — tap-to-ripple toy

## Deploy in ~2 minutes

### Option A: Netlify Drop (fastest, no account needed)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page
3. You'll get a public URL immediately (e.g. `random-name-123.netlify.app`)

### Option B: GitHub Pages
1. Create a new repo (or use an existing one)
2. Push this folder's contents to the repo root, e.g.:
   ```
   git init
   git add .
   git commit -m "Kiosk game prototypes"
   git remote add origin <your-repo-url>
   git push -u origin main
   ```
3. In the repo settings, enable GitHub Pages for the `main` branch (root folder)
4. Your site will be live at `https://<username>.github.io/<repo-name>/`

### Option C: Cloudflare Pages
Since you're already on Cloudflare for the R2/Worker virtual tour setup, this may
be the smoothest option:
1. In the Cloudflare dashboard, go to Workers & Pages → Create → Pages
2. Connect a git repo (push this folder first) or use direct upload
3. No build command needed — this is static HTML, so leave build settings blank
4. Deploy; you'll get a `*.pages.dev` URL

## Notes
- Both games are silent by design — no audio playback, just visual/tactile interaction.
- Each includes a 3-minute session ring (top-right) and a `hardReload()` stub in
  the script. Right now it just clears the canvas — swap in
  `window.location.href = "/"` (or your kiosk's real reset route) to match the
  existing "Restart" behavior on tuneintoyouadp.com.
- The collapsed sound-strip bar at the top is a static mockup — you'll want to
  wire it to your real selected-sounds state and soundboard overlay.
