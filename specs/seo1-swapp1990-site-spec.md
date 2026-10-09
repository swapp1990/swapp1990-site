# seo1-swapp1990-site: robots.txt, sitemap.xml, remove dead TORN City link

Repo: `swapp1990/swapp1990-site`, branch `seo1-robots-sitemap` off `origin/master` (51e0b37).
Source audit: `/workspace/specs/seo-audit-2026-10-08.md` §15. Implementer: Grok 4.6 CLI. Do NOT commit, push or deploy.

## Context
- Plain hand-written static site (no build step, no package.json). Files: `index.html`, `style.css`, `favicon.svg`,
  `privacy/index.html`, `google60518079161b607a.html`, `preview-*.png`.
- Live root `/var/www/swapp1990-site` is served by nginx as static files. Today `/robots.txt` and `/sitemap.xml` return 404.
- `https://gta.swapp1990.org` is NXDOMAIN. The "TORN City" `<li>` in `index.html` is a broken link. It was already removed
  live by hand; the repo must now match the live file exactly (live == repo minus that one `<li>` line).
- Public pages: `https://swapp1990.org/` and `https://swapp1990.org/privacy/` (the privacy page self-canonicals to `/privacy/`).

## Changes (exactly these, nothing else)
1. `index.html`: delete the single line containing `https://gta.swapp1990.org` (the `<li>…TORN City…</li>`). Change no other
   byte of the file: keep encoding (UTF-8), line endings and the SwapAnalytics `<script>` block untouched.
2. New `robots.txt` at repo root, exact content (LF line endings, trailing newline):
   ```
   User-agent: *
   Allow: /

   Sitemap: https://swapp1990.org/sitemap.xml
   ```
3. New `sitemap.xml` at repo root, exact content:
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
     <url><loc>https://swapp1990.org/</loc><lastmod>2026-10-08</lastmod></url>
     <url><loc>https://swapp1990.org/privacy/</loc><lastmod>2026-10-08</lastmod></url>
   </urlset>
   ```
4. Keep `google60518079161b607a.html` exactly as is (Search Console verification). Do not touch `privacy/`, `style.css`, images.

## Acceptance checks (run them and paste the output)
- `git diff --stat` shows only `index.html` (1 deletion), plus untracked `robots.txt`, `sitemap.xml`, `specs/…`.
- `Select-String -Path index.html -Pattern 'gta\.swapp1990|TORN'` → no matches.
- `Select-String -Path index.html -Pattern 'analytics.swapp1990.org/api/events'` → still matches (analytics intact).
- `sitemap.xml` parses as XML: `[xml](Get-Content sitemap.xml -Raw)` succeeds and has 2 `<url>` entries.
- `robots.txt` contains the `Sitemap:` line.
- `Test-Path google60518079161b607a.html` → True.
