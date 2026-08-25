# NG-N website — publishing notes

Static site, hosted free on GitHub Pages, domain at Simply.com.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole site. One page, bilingual (EN/DA). |
| `CNAME` | Tells GitHub Pages the custom domain. Contains exactly: `nextgen-nordic.dk` |
| `404.html` | Shown when a URL doesn't exist. |
| `robots.txt` | Lets search engines index the site. |
| `sitemap.xml` | Lists the pages for search engines. Update `lastmod` when the site changes. |
| `logo-header.png` | Logo used in the page header. |
| `logo.png` | Full-size logo, also used as the favicon. |

## Before publishing — the one thing left

Search `index.html` for `YOUR_ACCESS_KEY_HERE` and replace it with the Web3Forms
access key (see "Contact form" below). Until that is done, the form will not send.

## Publish (once)

1. Create a **public** repository on GitHub, e.g. `nextgen-nordic-web`.
   Public matters: GitHub Pages on private repos requires a paid plan.
2. Upload all files to the **root** of the repo (not inside a folder).
3. Repo → **Settings → Pages**.
   Source: **Deploy from a branch**. Branch: `main`, folder: `/ (root)`. Save.
4. Same page, **Custom domain**: type `nextgen-nordic.dk`. Save.
5. Configure DNS at Simply.com (see below).
6. Return to Settings → Pages and tick **Enforce HTTPS** once it becomes available.
   It stays greyed out until DNS resolves — this can take a few hours.

## DNS at Simply.com

Delete any old A / CNAME / ALIAS records for the domain that point at Canva.
**Do not touch MX records** — those carry email.

| Type | Name / Host | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `USERNAME.github.io.` |

Replace `USERNAME` with the GitHub account or organisation name that owns the repo.

Optional IPv6 (add alongside the A records, do not replace them):
`2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` as AAAA on `@`.

DNS changes can take up to 24 hours.

## Also worth doing

- Update the "Last edited" date in the footer when the page changes.

## Updating the site later

Edit `index.html` in the repo (GitHub's web editor is fine) and commit.
The live site updates in about a minute. No rebuild, no deploy step.

## Contact form (Web3Forms)

The form posts to Web3Forms, which forwards the message to nextgen.nordic@gmail.com.
Free, unlimited, no account.

1. Go to web3forms.com, enter nextgen.nordic@gmail.com, request an access key.
2. The key arrives by email — a long string of letters and numbers.
3. In `index.html`, find `YOUR_ACCESS_KEY_HERE` and replace it with that key.
4. Commit. Test by submitting the form yourself.
5. Check the spam folder for the first message and mark it as not spam.

The key is visible in the page source. That is normal and by design — it only
allows sending to the address it was registered to.

Spam protection: a hidden `botcheck` field catches simple bots. If real spam
starts arriving, add hCaptcha through the Web3Forms dashboard.

## Known limitations

- No analytics installed.
- Danish text has not been proofread yet.
