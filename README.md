# SutraKatha website — sutrakatha.kolethe.com and www.sutrakatha.ca

Source repository for the SutraKatha website. The working pages publish to the
password-protected Turbify subdomain **sutrakatha.kolethe.com** over encrypted
FTPS. The future GoDaddy cPanel deployment for www.sutrakatha.ca is kept on
file but disabled until its connection is validated.

## Structure

- `index.html` — brand-themed hub page linking the three working areas
- `coming-soon.html` — coming-soon landing page with launch email signup
- `wireframe.html` — draft wireframe of the full sutrakatha.ca site structure
- `assets/` — favicon and shared assets (v3 brand palette: plum `#421742`, gold `#CBA370`, off-white `#F5EFE6`, sage `#7C8B6F`, ink `#2A1A28`, Montserrat)

## How publishing works (Turbify)

1. Commit site changes to `main`.
2. The **Deploy site to Turbify** workflow uploads the site to
   `public_html/sutrakatha` on the Turbify hosting account.
3. Changes are live on sutrakatha.kolethe.com within about a minute.

The subdomain folder is password-protected in Turbify (Hosting → Directory
Privacy), so visitors must sign in before any page loads.

### Required repository secrets

Set under **Settings → Secrets and variables → Actions**. These are the same
Turbify hosting credentials used by the koletheWeb repository; only the
directory differs:

| Secret | What it is |
| --- | --- |
| `YAHOO_FTP_SERVER` | Turbify FTP host (same as koletheWeb) |
| `YAHOO_FTP_USERNAME` | Turbify FTP username (same as koletheWeb) |
| `YAHOO_FTP_PASSWORD` | Turbify FTP password (same as koletheWeb) |
| `YAHOO_FTP_DIR` | `/public_html/sutrakatha` — the subdomain's document root |

Before deploying for the first time, run the **Test Turbify connection**
workflow manually from the Actions tab. It is read-only and confirms the
credentials and folder work.

## GoDaddy deployment for www.sutrakatha.ca (disabled)

`deploy-to-godaddy.yml.disabled` and `test-connection.yml` hold the original
GoDaddy FTPS configuration. The deploy workflow is renamed so it cannot run
until the GoDaddy connection test passes; rename it back to
`deploy-to-godaddy.yml` when sutrakatha.ca is ready to launch.

## Email signups

The coming-soon form routes through FormSubmit to `reach@sutrakatha.ca`. The
first submission triggers a one-time FormSubmit activation email to that
address — the activation link must be clicked once before signups are
delivered.
