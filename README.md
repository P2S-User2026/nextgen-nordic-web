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

## Before publishing — fill these in

Search `index.html` for these and replace every occurrence:

- `[NAME 1]` and `[NAME 2]` — the two founders' names
- `[EMAIL]` — appears 3 times (form note, footer, mailto link)

Also confirm: the price `1.200 kr`, and that the three cases are factually accurate.

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

## Updating the site later

Edit `index.html` in the repo (GitHub's web editor is fine) and commit.
The live site updates in about a minute. No rebuild, no deploy step.

## Known limitations

- The contact form opens the visitor's own email program. It stores nothing and
  fails silently if no mail app is configured. Replace with a hosted form service later.
- No analytics installed.
