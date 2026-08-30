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

hPanel, Websites, **the subdomain's own entry**, then **Git** under Advanced.

1. Repository:
   `https://github.com/nfamaraceesay2018-svg/sublex-demo5-garage.git`
   This repository is public, so no key and no token is needed.
2. Branch: `main`
3. Install path: leave it empty, so the files land in the document root of
   **this subdomain**. Check you are on the `demo5.sublexchat.com` entry and
   not the parent domain, or the files deploy to the wrong site's root.
4. Deploy. Optionally enable auto deployment with the webhook Hostinger shows.

Everything in this repository is served publicly, which is why no build scripts
or source files live here.

### If the deployment fails

**`could not read Username for 'https://github.com'`** means the repository is
private and the URL is HTTPS. A Hostinger deploy key is an **SSH** key and is
never used on an HTTPS clone, so the clone stops to ask for a password that
nobody can type. Either make the repository public and use the HTTPS URL above,
or use the SSH URL `git@github.com:nfamaraceesay2018-svg/sublex-demo5-garage.git` with the
key added under Settings, Deploy keys.

Note that **a GitHub deploy key can only belong to one repository ever**, and
Hostinger issues one key per hosting account. Five private repositories
therefore cannot share it. That is why these are public.

**403 on the site with 404 on `/index.html`** means the document root is being
served but is empty: the deployment did not run, or it wrote to a different
folder. Check the Git panel's last result, then look in File Manager for
`index.html` in this subdomain's own directory.

## Changing it

The pages are generated, not hand-edited. The generator is
`demo-sites/site5-garage.mjs` in the Sublex Chat launch folder, with the shared layout
in `shared.mjs`. Run `node build.mjs`, check with `node audit.mjs`, then
commit the regenerated HTML here.

## Making a site indexable, later

Every page ships with `<meta name="robots" content="noindex, nofollow">`,
written by `shared.mjs` at about line 57. That is deliberate. These businesses
are invented, and a fictional hotel in Kololi turning up in Google results is a
problem for whoever is searching for a real one.

**Only lift it once the site describes a real business** — sold to a client,
rebranded, with a real address, real prices and a real phone number. There is
no case for indexing a site full of invented facts.

When that is true:

1. In `demo-sites/shared.mjs`, remove the robots meta line.
2. Rebuild and check: `node build.mjs`, then `node audit.mjs`.
3. Fix these three before pushing, because indexing is what makes them matter:
   - **The JSON-LD block** near the foot of every page names the business, its
     address, its opening hours and its prices. Every field has to be true.
     Structured data that lies is worse than none.
   - **`rel="canonical"` and `og:url`** point at `demoN.sublexchat.com`. Point
     them at the real domain, or the client's real site will tell Google the
     demo is the original and outrank itself.
   - **The photographs are hotlinked from Unsplash.** Fine for a demo. A real
     business should use its own.
4. Commit and push. Hostinger redeploys from `main`.
5. Add the domain in Google Search Console and request indexing, or it can be
   weeks before anything is noticed.

**Do not use a `robots.txt` `Disallow` as a way to hide a site instead.** A
blocked page cannot be fetched, so the crawler never sees the `noindex`, and
the URL can still be indexed from a link somewhere else. Allowing the crawl and
serving `noindex` is what actually keeps a page out.
