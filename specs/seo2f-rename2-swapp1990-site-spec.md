# seo2f-rename2: footer "LetMeActForYou" -> "Let Me Act" on swapp1990.org

Repo swapp1990/swapp1990-site, branch `seo2f-rename-footer` from origin/master (3f46770).
The app is now named **Let Me Act**; Alex's rule is to use the new name everywhere outside legal pages.

## Change (exactly this, nothing else)
- `index.html`, footer line ~121:
  `<p>One Swapp1990 account signs you in to DesignForYou, WriteForYou, LetMeActForYou and SnapForYou &middot; <a href="/privacy/">Privacy Policy</a></p>`
  becomes
  `<p>One Swapp1990 account signs you in to DesignForYou, WriteForYou, Let Me Act and SnapForYou &middot; <a href="/privacy/">Privacy Policy</a></p>`
  (only the word LetMeActForYou changes; keep everything else on the line byte-identical).

## Must NOT change
- `privacy/index.html` (legal) — byte-identical.
- Any URL/hostname, canonical, JSON-LD, FAQ, style.css, robots.txt, sitemap.xml, the beacon. Keep LF line endings.

## Acceptance (run and paste output)
- `git diff --stat origin/master` shows only `index.html` (1 line) plus this spec file.
- `index.html` has 0 case-insensitive matches for `LetMeActForYou|LMAFY|Let\s*Me\s*Act\s*For\s*You|ActForYou` once `actforyou.swapp1990.org` occurrences are excluded.
- Both `application/ld+json` blocks still parse (Person, FAQPage).
- `git diff origin/master -- privacy/` is empty.
