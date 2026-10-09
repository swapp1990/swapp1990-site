# seo2-swapp1990-site: home canonical, Person JSON-LD, FAQ + FAQPage, founder line + cross-links footer

Repo: `swapp1990/swapp1990-site`, branch `seo2-swapp1990-site` off `origin/master` (8931143). Live: https://swapp1990.org
(static files in `/var/www/swapp1990-site`, already real 404s; LCP 1.7 s). Audit: `/workspace/specs/seo-checklist-status-2026-10-08.md` (swapp1990.org).
Shared blocks: `specs/seo2-shared-blocks.md` (use exactly). Implementer: Grok CLI. Commit when checks pass. **Do NOT push, PR or deploy.**

## Changes — `index.html` and `style.css` only (hand-written HTML, no build step, no JS framework)
1. In `<head>`, right after the `<meta name="description">` line: `<link rel="canonical" href="https://swapp1990.org/">`.
2. In `<head>` before `</head>`: the Person JSON-LD (shared B) and a `FAQPage` JSON-LD matching §3 word for word.
3. A visible FAQ: new `<section id="faq">` after `#contact`, `<h2>FAQ</h2>`, `<h3>` + `<p>` per item, exactly:
   1. **Who is Swapnil Sawant?** — A Senior Software Engineer at Phoenix Bioinformatics in the SF Bay Area. I keep the world's reference plant-biology database running by day — and ship AI products, games, and agent tooling at night.
   2. **What is Phoenix Bioinformatics?** — The nonprofit that runs TAIR, the reference genomics database for plant biology, used by researchers worldwide. I've worked there since 2018.
   3. **What is Molty?** — My agent-powered studio: a stack of AI agents that build, test, record, and market alongside me. Most of what I ship comes out of it.
   4. **Do your products share one account?** — Yes. One Swapp1990 account signs you in to DesignForYou, WriteForYou, LetMeActForYou and SnapForYou.
   5. **How do I contact you?** — Email me at swapp19902@gmail.com.
   (Visible answers may link the product names / email exactly as the page already does; the JSON-LD answer is the plain text.)
4. Footer: keep both existing `<p>` lines; add above them the cross-links nav (shared C **without** the swapp1990.org link) and a short
   line `Made by <a href="https://swapp1990.org/">Swapnil (swapp1990)</a>` (no repeated bio — the header already is the bio).
5. `style.css`: minimal rules for `#faq h3` (same font as the page, ~1rem, margin) and `.sister-sites` (wrap, small gaps, muted).
6. Do **not** change anything else: the header, existing sections and links, the SwapAnalytics `<script>` and its comment, encoding
   (UTF-8, no BOM) and line endings. Exactly one `<h1>`. No `<img>` added. Don't add links to agency/analytics/taxes/keywords/
   stockbroker/videogen/moltbot/vncreator/cars/destruction hosts (existing body links are out of scope — leave them).

## Acceptance (paste output)
- Python check: every `application/ld+json` block in `index.html` parses with `json.loads`; types = {Person, FAQPage}; FAQ has 5
  questions and each question text is in the visible HTML; one canonical = `https://swapp1990.org/`; one `<h1`;
  `analytics.swapp1990.org/api/events` count unchanged vs origin/master.
- `git diff origin/master -- index.html | grep '^-'` shows only the `---` header line (pure additions) — unless a footer line had to move; explain.
- `git diff --stat origin/master`: only `index.html`, `style.css`, `specs/**`.
