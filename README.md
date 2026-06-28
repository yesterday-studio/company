# Yesterday Studio — Landing Page

Static landing page for Yesterday Studio's business credibility package, deployed on Vercel at **https://yesterday-studio.vercel.app/**.

## Project structure

```
yesterday-studio-site/
├── public/
│   ├── index.html          ← the site itself (plain HTML/CSS, no build step)
│   └── assets/
│       └── og-image.png     ← link-preview image used by og:image / twitter:image
└── .gitignore
```

This is a single static HTML file with embedded CSS — there's no bundler, no `npm install`, nothing to compile. Edit `public/index.html` directly.

## Deploying on Vercel

If the project is already connected to Vercel, every push to your main branch redeploys automatically — nothing else to do.

If you're setting it up fresh:

1. Push this repo to GitHub (see commands below).
2. On [vercel.com](https://vercel.com), **Add New → Project**, and import the GitHub repo.
3. Set **Root Directory** to `public` (since `index.html` lives there, not at the repo root).
4. Framework preset: **Other** (it's plain HTML, no build command needed).
5. Deploy. Vercel will give you a `.vercel.app` URL — or attach your own domain under **Settings → Domains**.

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

## Link preview image (og:image)

`public/index.html` has Open Graph and Twitter Card tags so the site shows a proper preview card when shared on WhatsApp, Twitter, or Facebook. The image lives at `public/assets/og-image.png`, and the tags already point to the live domain:

```html
<meta property="og:image" content="https://yesterday-studio.vercel.app/assets/og-image.png" />
<meta name="twitter:image" content="https://yesterday-studio.vercel.app/assets/og-image.png" />
<meta property="og:url" content="https://yesterday-studio.vercel.app/" />
```

If you ever move to a custom domain, update those three lines (the `og:image:width` / `og:image:height` tags stay as-is at `1200`×`630`).

After any domain change, re-paste the URL into [Facebook's Sharing Debugger](https://developers.facebook.com/tools/debug/) or [Twitter Card Validator](https://cards-dev.twitter.com/validator) to force a re-scrape — these platforms cache old previews aggressively.

## Every future update

```bash
git add .
git commit -m "Describe what you changed"
git push
```

Vercel picks up the push and redeploys automatically. You can watch progress in the **Deployments** tab on your Vercel dashboard.

## Local preview

No server needed — just open the file directly:

```bash
open public/index.html
```

Or, if you want it served over `http://` (closer to production, useful since the og-image and any relative asset paths behave more accurately):

```bash
cd public && python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
