# Yesterday Studio — Landing Page

Static landing page for Yesterday Studio's business credibility package, deployed automatically to GitHub Pages.

## Project structure

```
yesterday-studio-site/
├── public/
│   └── index.html          ← the site itself (plain HTML/CSS, no build step)
├── .github/workflows/
│   └── deploy.yml           ← auto-deploys `public/` to GitHub Pages on every push to main
└── .gitignore
```

This is a single static HTML file with embedded CSS — there's no bundler, no `npm install`, nothing to compile. Edit `public/index.html` directly.

## One-time setup (do this once after pushing to GitHub)

1. Push this repo to GitHub (see commands below).
2. On GitHub, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, select **GitHub Actions** (not "Deploy from a branch").
4. That's it. The workflow in `.github/workflows/deploy.yml` will handle every deploy from here on.

## Pushing for the first time

From inside this folder:

```bash
git init
git add .
git commit -m "Initial commit: Yesterday Studio landing page"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo-name>.git
git push -u origin main
```

Replace `<your-username>` and `<your-repo-name>` with your actual GitHub username and the repo name you create on GitHub (create an empty repo there first — no README/license/gitignore, since this folder already has them).

## Every future update

```bash
git add .
git commit -m "Describe what you changed"
git push
```

Every push to `main` automatically redeploys the live site within about a minute. You can watch progress under the **Actions** tab on GitHub.

## Where the site goes live

Once Pages is enabled (step 3 above), your site will be live at:

```
https://<your-username>.github.io/<your-repo-name>/
```

If you want a custom domain (e.g. `yesterdaystudio.com`), add a `CNAME` file inside `public/` containing just the domain name, then configure the DNS records GitHub gives you under **Settings → Pages → Custom domain**.

## Local preview

No server needed — just open the file directly:

```bash
open public/index.html
```

Or, if you want it served over `http://` (closer to production, useful if you add relative asset paths later):

```bash
cd public && python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
