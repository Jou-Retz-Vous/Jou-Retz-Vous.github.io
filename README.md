# Jou'Retz-vous? — Link page

Single static landing page (no build step) for the association
**Jou'Retz-vous?**, live at:

➡️ **https://jou-retz-vous.github.io/**

It links to Facebook and Instagram, embeds the association's Google
Calendar, and includes short "À propos" and "Contact" sections.

## Structure

```
.
├── index.html   — all page content and section markup
├── style.css    — layout, colors, responsive styling
├── assets/
│   ├── logo.png     — full association logo (shown in the header)
│   └── favicon.png  — tight die-icon crop used as browser favicon
└── README.md
```

## Content & features

- **Facebook / Instagram**: direct links, open in a new tab, official
  brand colors kept for instant recognition.
- **Calendar**: embedded via `calendar.google.com/calendar/embed?src=...`
  (agenda view, `Europe/Paris` timezone), plus a "+ Ajouter à mon Google
  Calendar" subscribe link using the `newembed` URL.
  ⚠️ The calendar must have **public access** enabled in its Google
  Calendar sharing settings, otherwise the embed shows "This content is
  not available" to visitors.
  - The embed is lightly recolored via URL params: `color=%23EF6C00`
    (closest match in Google's fixed ~24-color palette to our site
    orange `#e4701e` — arbitrary hex is **not** supported, Google snaps
    it to the nearest palette entry) and `bgcolor=%23ffffff`. Other
    available toggles: `showTitle=0`, `showNav=0`, `showDate=0`,
    `showPrint=0`, `showTabs=0`, `showCalendars=0`, `showTz=0`.
- **À propos**: short description of the association, editable directly
  in `index.html` under `id="about"`.
- **Contact**: a "Nous écrire par e-mail" button. The address is **not**
  written as a literal string in the HTML — it's assembled by a small
  inline script at page-load time (see the bottom of `index.html`) as a
  basic deterrent against simple scrapers. To change the address, edit
  the `user` / `domain` variables in that script.
- **Color palette**: extracted from the logo artwork — navy `#142d54`,
  blue `#094c74`, teal `#1c8492`, green `#71992e`, orange `#e4701e`.
  Defined as CSS variables at the top of `style.css`.

## Making changes

This is plain HTML/CSS — edit the files directly and push, no build step:

```bash
git add -A
git commit -m "Describe the change"
git push origin main
```

GitHub Pages redeploys automatically within a minute or two. The
stylesheet is cache-busted via a `?v=N` query string on the `<link>` tag
in `index.html` (`style.css?v=2`); **bump that number** whenever you edit
`style.css` so returning visitors' browsers don't serve a stale cached
copy (browsers may cache it for up to `max-age=600`, i.e. 10 minutes).

## Hosting setup (already done, for reference)

- Repo: `Jou-Retz-Vous/Jou-Retz-Vous.github.io` — the name must match
  this exactly for GitHub Pages to serve it at the root `*.github.io`
  domain (any other repo name would instead serve at
  `jou-retz-vous.github.io/<repo-name>/`).
- GitHub → repo **Settings → Pages** → source: branch `main`, folder
  `/ (root)`.

## Later: custom domain (optional)

To get a domain without hyphens (e.g. `jouretzvous.fr` or `.com`):
1. Buy the domain from any registrar.
2. Add a `CNAME` file at the repo root containing just the domain name.
3. Point the registrar's DNS to GitHub Pages (A/ALIAS records to GitHub's
   IPs, or a CNAME record for a subdomain) — see
   https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site
4. Enable "Enforce HTTPS" in repo Settings → Pages once DNS propagates.
