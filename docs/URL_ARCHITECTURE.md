# URL architecture — design candidate, not deployed

Updated: 2026-10-10 KST. No DNS or canonical production domain is selected.

## Hostname separation
- Target site: `tax.<root-domain>` where the root may be `evococoons.com` or `prince-in-wonderworld.com`.
- While testing, use the actual GitHub Pages **project** base path if enabled (for example `https://david12448.github.io/tax-guide/`), not invented live subdomains.
- Centralize `SITE_URL` including any prefix: all canonical, Open Graph URL, sitemap loc and absolute cross-project links derive from it. Never write the final hostname in many pages.

## Proposed public routes
| Function | Stable pathname | Notes |
|---|---|---|
| Home | `/` | Search, tax categories and guided start |
| Tax explanation | `/taxes/vat/` | Evergreen; legislation effective dates in content |
| Tax explanation | `/taxes/income-tax/` | Evergreen; link to filing-year editions |
| Filing guide | `/filings/income-tax/2026/` | Filing year 2026, taxation year 2025; clearly display BOTH |
| Filing guide | `/filings/vat/2026-first-final/` | Tax kind + filing period; validation before publishing |
| Scenario | `/situations/no-sales/` | Qualified, legally checked guidance |
| Glossary | `/glossary/tax-base/` | Unique educational explanation |
| Embeddable tool | `/embed/tax-calendar/` | Lightweight calendar with no redundant navigation |

Slug: lowercase a-z, digits as needed, hyphens only between words. Stable once published; avoid internal database IDs. On collision namespace by type and additional meaningful slug. Status changes should preserve history and redirect/alias rather than erase old URLs.

## Deployment design
Prefer a shared template + structured data + static-site generation to physically create `<route>/index.html` on GitHub Pages. Every published route must load directly and survive refresh; add link and HTML build checks. An SSG is preferable over a JS-only SPA router. Consider Cloudflare Pages only after testing GitHub Pages build time/file limits at scale.

## SEO and migration
- Unique, substantive HTML pages with descriptive title, meta description, headings, links and accessible images; no thin near-duplicates.
- Generate robots.txt, sitemap.xml and canonical from the approved deployed `SITE_URL`. During preview, avoid claiming a not-yet-live canonical hostname.
- Maintain a tested `legacy_url -> new_path` mapping; preserve query URLs, blog links and iframe entry points. Since static hosting lacks general-purpose 301 responses, evaluate old HTML landing/redirect pages or a future edge redirect layer.
- Keep historical tax-year guides accessible with clear 'archived' labels, while linking current guidance.

## Pilot and acceptance checks (pending)
1. Build 3 representative paths (home, tax explanation, filing-year walkthrough) with approved factual content.
2. Verify HTTP 200 and reload for each deep URL, responsive viewport, navigation and basic accessibility.
3. Verify all internal links, old URL compatibility (where any exist), iframe routes, sitemap entries and canonical exactly match deployment base.
4. Test site generation under larger datasets; record build duration/file counts before rollout.
5. Write DNS/CNAME/Cloudflare handoff separately; do not set a custom domain until explicit approval.

## Current audit 2026-10-10
- This project started with just `README.md`; no existing query routes, IDs, embeds or deployment were found in either new tax repository.
- This document defines routes only. No public pages, live URLs, Actions, redirects or SEO output are claimed as implemented.
