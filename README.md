# Apex Auto Works — Sublex Chat demo site

A complete, self-contained demo website. **The business is fictional.** It
exists to show what a Sublex Chat assistant does on a real multi-page site,
and to demonstrate the standard of site Sublex Digital builds.

Live at **demo5.sublexchat.com**.

## What is here

5 pages of static HTML. Nothing to build and nothing to install.

| File | Page |
| --- | --- |
| `index.html` | Home |
| `servicing.html` | Servicing |
| `prices.html` | Prices |
| `warranty.html` | Warranty |
| `questions.html` | Frequently asked questions |

Every page is self-contained: the CSS is inline, the favicon is a data URI,
and the only external requests are Google Fonts, photographs hotlinked from
Unsplash, and the Sublex Chat widget.

## Deploying on Hostinger

hPanel, Websites, the domain, then **Git** under Advanced.

1. Repository: this repo's URL. It is private, so add the deploy key Hostinger
   shows you to **Settings, Deploy keys** on this repo first.
2. Branch: `main`
3. Install path: leave empty so it deploys into `public_html`
4. Deploy, and optionally enable auto deployment with the webhook Hostinger
   gives you

Everything in this repository is served publicly, which is why no build
scripts or source files live here.

## Changing it

The pages are generated, not hand-edited. The generator is
`demo-sites/site5-garage.mjs` in the Sublex Chat launch folder, with the shared layout
in `shared.mjs`. Run `node build.mjs`, check with `node audit.mjs`, then
commit the regenerated HTML here.
