# C2PA Strip

Browser-based tool to detect and remove C2PA Content Credentials from images. Nothing is uploaded anywhere — all processing happens client-side.

- **`index.html`** — JavaScript port of the detection/strip logic. Loads instantly, no dependencies.
- **`python-engine.html`** — runs the actual `convert_image.py` (`strip_c2pa_jpeg()`, `strip_by_resave()`) unmodified, in-browser, via Pyodide (WebAssembly Python). ~20 MB one-time load, but it's your real script executing, not a reimplementation.

Both link to each other so you can switch depending on whether you want speed or "actually my Python."

## Deploy to GitHub Pages

From this folder:

```bash
git init
git add .
git commit -m "Initial commit: C2PA strip tool"
git branch -M main
git remote add origin https://github.com/<your-username>/c2pa-strip-web.git
git push -u origin main
```

Then on GitHub:

1. Go to the repo → **Settings** → **Pages**
2. Under **Build and deployment**, set **Source** to `Deploy from a branch`
3. Set **Branch** to `main` and folder to `/ (root)` → **Save**
4. Wait ~1 minute, then your tool is live at:

```
https://<your-username>.github.io/c2pa-strip-web/
```

`python-engine.html` will be at `https://<your-username>.github.io/c2pa-strip-web/python-engine.html`.

## Notes

- Repo needs to be public (or you're on a paid GitHub plan) for Pages to serve for free.
- Any time you edit either HTML file, just `git add . && git commit -m "..." && git push` — Pages redeploys automatically within a minute or two.
- If `python-engine.html` fails to load Pyodide even on Pages, open the browser console — it's usually a transient CDN hiccup on first load, a retry (hard refresh) resolves it.
