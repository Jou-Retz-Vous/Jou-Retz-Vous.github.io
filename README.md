# Jou'Retz-vous? — Link page

Single static landing page (no build step) linking to Facebook, Instagram,
and embedding the association's Google Calendar.

## Before publishing

1. Add your real logo/avatar as `assets/logo.png` (square, e.g. 256x256) and
   a favicon as `assets/favicon.png`. The page still works if these are
   missing (the `<img>` just hides itself), but add them for branding.
2. Double-check the calendar's sharing settings: in Google Calendar settings
   for this calendar → **Access permissions** → enable **"Make available
   to public"**, otherwise the embed will show "This content is not
   available" to visitors.

## Publish on GitHub Pages (org: Jou-Retz-Vous)

1. Create a new repo in the `Jou-Retz-Vous` org named **exactly**
   `Jou-Retz-Vous.github.io`.
2. From this folder:
   ```bash
   git remote add origin git@github.com:Jou-Retz-Vous/Jou-Retz-Vous.github.io.git
   git add -A
   git commit -m "Initial Jou'Retz-vous? link page"
   git branch -M main
   git push -u origin main
   ```
3. In the repo settings → **Pages**, set source to the `main` branch,
   root folder (`/`). It usually auto-detects for a `*.github.io` repo.
4. Site goes live at **https://jou-retz-vous.github.io/** within a minute
   or two.

## Later: custom domain (optional)

To get a domain without hyphens (e.g. `jouretzvous.fr` or `.com`):
1. Buy the domain from any registrar.
2. Add a `CNAME` file at the repo root containing just the domain name.
3. Point the registrar's DNS to GitHub Pages (A/ALIAS records to GitHub's
   IPs, or a CNAME record for a subdomain) — see
   https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site
4. Enable "Enforce HTTPS" in repo Settings → Pages once DNS propagates.
