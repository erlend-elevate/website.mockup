# elevate-demos

Static website mockups used as door-openers for Elevate Marketing's UK cold-outreach workflow. Each mockup lives in its own folder under `demos/` and is deployed as a static site via Netlify.

> **Note:** this repo currently lives at `erlend-elevate/website.mockup` (branch `claude/uk-law-firm-outreach-BEeka`). If/when moved to a standalone `elevate-demos` repo, nothing about the structure or Netlify config needs to change.

## Purpose

- **Who it's for:** the Elevate team (currently Erlend; next Sondre) generating personalised mockups for cold UK prospects.
- **What it is not:** not a CMS, not a live client site, not a template engine. Each folder is a hand-edited single-file mockup.

## Structure

```
.
├── README.md                          — this file
├── netlify.toml                       — deploy config (publish = repo root)
├── index.html                         — internal landing page listing active demos
├── prompts/
│   └── uk-law-demo-master-prompt.md   — reusable master prompt for UK solicitor mockups
└── demos/
    └── [prospect-slug]/
        └── index.html                 — one self-contained mockup per prospect
```

## Prospect-slug convention

- Lowercase kebab-case based on the firm's recognisable short name.
- Strip "solicitors", "limited", "llp", "ltd" unless needed to disambiguate.
- Example: `Colin Brown & Kidson Solicitors` → `colin-brown-kidson`.

## Workflow (for Sondre)

1. **Research** — pick a real UK firm from the target segment (see master prompt for criteria). Verify: single/small office, 2–15 employees, on Companies House, weak existing site, realistic commission attribution.
2. **Fill in variables** — copy `prompts/uk-law-demo-master-prompt.md`, fill in every `[BRACKETED]` field with verified facts. Use `[placeholder]` markers for anything unverified — never fabricate.
3. **Generate HTML** — paste the filled prompt into Claude/GPT. Save the output as `demos/[prospect-slug]/index.html`.
4. **Sanity-check locally** — open the file in a browser, resize to 375px, check: page loads under 2s, one clear CTA, no broken links, no fabricated testimonials, mockup footer visible.
5. **Commit + push** — `git add demos/[slug]/ && git commit -m "Add demo: [firm name]"`, then `git push`.
6. **Update landing** — add a line to the root `index.html` with a link to the new demo (internal use only).
7. **Verify live** — visit `https://[netlify-subdomain]/demos/[slug]/` once Netlify redeploys (usually under a minute). Click the phone number, submit the form (should open mail client), confirm form opens mailto.
8. **Record in tracking doc** — note the prospect, URL, date, and who to loop in for the Loom recording.

## Hard rules

- No external CDN, no Google Fonts, no JavaScript frameworks, no tracking scripts.
- No fabricated testimonials, awards, or statistics. Use `[placeholder]` markers instead.
- Keep each `index.html` under 40 KB.
- Every mockup carries the subtle footer line: `Mockup designed by Elevate Marketing · elevatemarketing.no`.

## Hosting

- Netlify is connected to this repo; every push to the working branch auto-deploys.
- URL pattern: `https://[netlify-site-name].netlify.app/demos/[prospect-slug]/`
- `netlify.toml` sets the publish directory to the repo root so the folder structure maps 1:1 to URLs.

## Out of scope for this repo

- Email copy, deliverability, warmup, Loom scripts — handled elsewhere.
- Client-facing production websites — if a prospect converts, build the real site separately.
