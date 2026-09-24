# SutraKatha website — www.sutrakatha.ca

Source repository for the SutraKatha website, hosted on GoDaddy cPanel hosting
and published automatically by GitHub Actions over encrypted FTPS.

## Structure

- `index.html` — coming-soon homepage (brand landing page with launch email signup)
- `assets/` — favicon and shared assets

## How publishing works

1. Commit site changes to `main`.
2. The **Deploy site to GoDaddy** workflow uploads the site to the hosting web root.
3. Changes are live on www.sutrakatha.ca within about a minute.

## Required repository secrets

Set under **Settings → Secrets and variables → Actions**:

| Secret | What it is |
| --- | --- |
| `GODADDY_FTP_SERVER` | FTP host from cPanel → FTP Accounts → FTP Configuration (usually the domain or server hostname) |
| `GODADDY_FTP_USERNAME` | cPanel FTP username |
| `GODADDY_FTP_PASSWORD` | cPanel FTP password |
| `GODADDY_FTP_DIR` | Web root path, usually `/public_html` |

Before deploying for the first time, run the **Test GoDaddy connection** workflow
manually from the Actions tab. It is read-only and confirms the credentials work.

## Email signups

The coming-soon form routes through FormSubmit to `reach@sutrakatha.ca`. The first
submission triggers a one-time FormSubmit activation email to that address — the
activation link must be clicked once before signups are delivered.
