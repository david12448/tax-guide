# Tax Guide — project rules

Updated 2026-10-10 (KST). Project-specific companion to `docs/COMMON_RULES.md`.

## Mission
Provide accessible Korean individual-business tax guidance: accurate explanations of legislation, filing schedules, current Hometax workflow walkthroughs, term glossary and scenario-dependent help. This is educational information, not a substitute for official filing or individualized tax advice.

## Accuracy and user safety
- Distinguish statute text, plain-language interpretation, hypothetical examples and official instructions.
- Store primary source title, official URL, applicable taxation year, effective date, verified date and review status with tax-sensitive entries. Do not publish unverified tax thresholds or dates.
- Industry, current/prior-year revenue, employment and filing type can affect outcomes; never determine a filing requirement from annual income alone.
- Mark instructional Hometax interface mockups clearly; never request RRN, Hometax credentials or sensitive taxpayer data. Actual filing must occur at the official service.
- Reference third-party blogs/video for usability insights; verify factual claims with official sources and honor source rights.

## Deployment/change safeguards
- Public page structure and minimum normalized display data only here; raw screenshots, collector details, source mappings and private validation records remain in `tax-guide-internal`.
- No real DNS, GitHub Pages Custom Domain, canonical production hostname or automatic merge until reviewed and approved.
- Use a base URL injected at build time (e.g. `SITE_URL`); do not hard-code evococoons.com or prince-in-wonderworld.com across templates.
- Direct route loading and refresh must work in a deployed static environment; do not rely on client history routing alone.
- Existing links and embeds must remain functional during any future migration.
- Avoid scheduled status notifications and unsupervised changes to filing advice.
