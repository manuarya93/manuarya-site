# manuarya.com

Personal site for Manu Arya. Built with [Eleventy](https://www.11ty.dev/) (static site
generator) and [Decap CMS](https://decapcms.org/) (free content dashboard at `/admin`).

**Start here:** see `DEPLOY.md` for the step-by-step guide to getting this live on
manuarya.com, with a working content dashboard, in about 30-45 minutes.

## Structure

- `src/index.njk` — homepage
- `src/content/about.md` — About page copy
- `src/content/projects/*.md` — Work/Projects entries (shown on Home + `/work/`)
- `src/content/blog/*.md` — Writing/Blog posts (shown at `/writing/`)
- `src/_data/home.json` — homepage headline, stats, intro text
- `src/_data/contact.json` — Contact page fields
- `src/_data/site.json` — global settings (name, email, nav, social links)
- `src/css/style.css` — all styling
- `admin/` — Decap CMS dashboard (config + login page)

## Local development

Requires Node.js installed.

```
npm install
npm run serve
```

Opens the site at `http://localhost:8080` with live reload. Note: the `/admin`
CMS dashboard only works once deployed (it needs Netlify Identity + Git Gateway
to log in and save changes) — you can't fully test it locally.

## Build

```
npm run build
```

Outputs the finished static site to `_site/`.
