# Public GitHub landing repo — setup

**Status: done and live.**

- Repo: [`github.com/mchandrahasreddy/hpoexplorer`](https://github.com/mchandrahasreddy/hpoexplorer) (public, no application source code)
- Pages: [`mchandrahasreddy.github.io/hpoexplorer`](https://mchandrahasreddy.github.io/hpoexplorer/) — a crawlable SEO page (not a bare redirect) that canonicals to hpoexplorer.com and sends human visitors on after ~3s

This folder is the source for that repo — a **public** project home for
[hpoexplorer.com](https://hpoexplorer.com) **without exposing application source
code**. It helps Google and registries associate the project with the correct
entity (and disambiguates it from the unrelated
[neurogenomics/HPOExplorer](https://github.com/neurogenomics/HPOExplorer) R package).

## 1. Create the public repo on GitHub

1. Go to [github.com/new](https://github.com/new).
2. Name: **`hpoexplorer`** (matches the domain; avoid `HPOExplorer` which collides with the R package).
3. Visibility: **Public**.
4. Do **not** initialize with a README (we provide one).

## 2. Push these files

From this directory:

```bash
cd github-landing
git init
git add README.md CITATION.cff index.html .nojekyll .github
git commit -m "Public project home for HPO Explorer web app"
git branch -M main
git remote add origin https://github.com/mchandrahasreddy/hpoexplorer.git
git push -u origin main
```

## 3. Enable GitHub Pages

1. Repo → **Settings** → **Pages**.
2. Source: **GitHub Actions** (not "Deploy from branch" — `.github/workflows/pages.yml`
   in this folder builds and deploys the repo root on every push to `main`).
3. After the workflow runs, the page is live at
   `https://mchandrahasreddy.github.io/hpoexplorer/`.

To update the live page, edit `index.html` here and push — the workflow
redeploys automatically.

## 4. Wire into registries (after repo is live)

| Where | What to add | Status |
|-------|-------------|--------|
| **bio.tools** | Repository URL → `https://github.com/mchandrahasreddy/hpoexplorer` | [ ] pending |
| **Zenodo** | Optional “Related identifier” (URL, not source archive) | [ ] pending |
| **ORCID** | Work entry can list the public repo as related URL | [ ] pending |
| **About page** | Link “Project home (GitHub)” | [x] done |
| **Site footer** | GitHub link | [x] done |
| **JSON-LD `sameAs` / `codeRepository`** | Main site + this repo's `index.html` | [x] done |

Do **not** link your **private** development repo anywhere public.

## 5. Google Search Console

1. Add property [https://hpoexplorer.com](https://hpoexplorer.com) at [search.google.com/search-console](https://search.google.com/search-console).
2. Verify via DNS (recommended) or HTML tag in `index.html`.
3. Submit sitemap: `https://www.hpoexplorer.com/sitemap.xml`.
4. Request indexing for `/`, `/about`, and `/clinical-note-to-hpo`.

See [`docs/DISCOVERABILITY.md`](../docs/DISCOVERABILITY.md) for the full PubMed + SEO timeline.
