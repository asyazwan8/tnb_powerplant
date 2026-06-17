# TNB Powerplant — 3D Asset Viewer

An interactive, browser-based viewer for two nuclear-themed 3D models — a
power plant exterior and a pressurized water reactor (PWR) — presented in a
Tenaga Nasional Berhad–styled interface with a tab switcher to toggle between
them. Pure static HTML/CSS/JS — no build step, no server.

## What's inside

```
tnb-powerplant/
├─ index.html                          the app
├─ assets/
│  └─ tnb-logo.png                     logo (transparent)
├─ models/
│  ├─ nuclear_powerplant_low-poly.glb  power plant model (~1 MB, optimized)
│  └─ pwr_nuclear_reactor.glb          reactor model (~165 KB, optimized)
├─ README.md
└─ CREDITS.md                          attribution (CC BY 4.0 — power plant)
```

Both models were re-encoded with [glTF-Transform](https://gltf-transform.dev/)
(Draco compression, mesh deduplication) to shrink them for the web. The power
plant model went from ~31 MB to ~1 MB with under 3% vertex loss. The reactor
model went from ~3.4 MB to ~165 KB with **no** geometry loss at all — only
duplicate vertex data was removed and compression applied; triangle count is
identical to the source file.

The "Power Plant" / "Reactor View" tabs above the viewer swap the model, the
heading text, and the spec panel all at once, using a single `<model-viewer>`
element rather than loading two separate viewers.

The 3D models load locally via Google's [`<model-viewer>`](https://modelviewer.dev/)
web component (pulled from a CDN at runtime — an internet connection is needed the
first time it loads).

## Run locally

Because the page fetches `.glb` files, opening `index.html` directly with
`file://` may be blocked by the browser. Serve it over a local web server instead:

```bash
# from inside the project folder
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a new repository and push these files to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "TNB powerplant 3D viewer"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Set the branch to **main** and the folder to **/ (root)**, then **Save**.
5. After a minute or two your site will be live at:
   `https://<your-username>.github.io/<repo-name>/`

No build configuration is required — it's a static site.

## Notes

- Both model files together are under 1.2 MB, so they upload fine through
  GitHub's web interface (25 MB limit) as well as `git push` (100 MB limit) —
  no Git LFS needed.
- **The reactor model's license is not yet confirmed.** It was supplied directly
  without a source link, so `CREDITS.md` and the in-app license badge don't
  claim a license for it yet. Add the source URL once known so attribution can
  be completed correctly — see `CREDITS.md`.
- This is an independent demo, not an official TNB product. See `CREDITS.md`
  and the disclaimer in the page footer.
