# TNB Powerplant — 3D Asset Viewer

An interactive, browser-based viewer for a low-poly nuclear power plant 3D model,
presented in a Tenaga Nasional Berhad–styled interface. Pure static HTML/CSS/JS —
no build step, no server.

## What's inside

```
tnb-powerplant/
├─ index.html                          the app
├─ assets/
│  └─ tnb-logo.png                     logo (transparent)
├─ models/
│  └─ nuclear_powerplant_low-poly.glb  the 3D model (~31 MB)
├─ README.md
└─ CREDITS.md                          required attribution (CC BY 4.0)
```

The 3D model loads locally via Google's [`<model-viewer>`](https://modelviewer.dev/)
web component (pulled from a CDN at runtime — an internet connection is needed the
first time it loads).

## Run locally

Because the page fetches a `.glb` file, opening `index.html` directly with
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

- The model file is ~31 MB. That's fine for a normal `git push` (well under
  GitHub's 100 MB hard limit). If you add larger assets later, consider Git LFS.
- This is an independent demo, not an official TNB product. See `CREDITS.md`
  and the disclaimer in the page footer.
