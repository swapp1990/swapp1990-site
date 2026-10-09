# seo2f-rename: "LetMeActForYou" -> "Let Me Act" in the swapp1990.org FAQ

Repo swapp1990/swapp1990-site, branch `seo2f-rename-letmeact` from origin/master (6dc5058).
The app formerly called LetMeActForYou is now named **Let Me Act** (renamed 2026-10-07).

## Change (exactly these, nothing else)
1. `index.html`, FAQPage JSON-LD in `<head>` (line ~15): in the answer to "Do your products share one account?", replace `LetMeActForYou` with `Let Me Act`. The answer becomes:
   `Yes. One Swapp1990 account signs you in to DesignForYou, WriteForYou, Let Me Act and SnapForYou.`
2. `index.html`, visible `<section id="faq">` (line ~100): in the same answer paragraph, replace the plain text `LetMeActForYou` with `Let Me Act`. Keep the existing DesignForYou/WriteForYou links and their hrefs exactly as they are. Do not add a link.
3. `specs/seo2-swapp1990-site-spec.md` line ~14: same wording change in FAQ item 4 so the spec matches what ships.

## Must NOT change
- The footer line `One Swapp1990 account signs you in to DesignForYou, WriteForYou, LetMeActForYou and SnapForYou · Privacy Policy` (line ~121). It is existing body text outside the FAQ/founder block; leave it byte-identical.
- `privacy/` (legal page) — byte-identical.
- Any URL or hostname (actforyou.swapp1990.org stays), canonical, robots.txt, sitemap.xml, style.css, the beacon.
- No AI model or provider names.

## Acceptance (run and paste output)
- `git diff --stat origin/master` shows only `index.html` and `specs/seo2-swapp1990-site-spec.md`, 2 + 1 lines changed.
- In index.html, within `<section id="faq">…</section>` and the `application/ld+json` scripts: 0 matches for `LetMeActForYou|LMAFY|ActForYou|Let Me Act For You` (case-insensitive, ignoring `actforyou.swapp1990.org`); `Let Me Act` appears in both.
- Both `application/ld+json` blocks still parse as JSON (python -c json.loads) with types Person and FAQPage, and the FAQPage answer text equals the visible FAQ answer text (tags stripped).
- `git diff origin/master -- privacy/` is empty; the footer line ~121 is unchanged.
