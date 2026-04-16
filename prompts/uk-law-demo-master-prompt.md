# Master Prompt — UK High-Street Solicitor Demo Mockup

Purpose: generate a single static `index.html` mockup that Elevate Marketing can use as a door-opener with a cold UK high-street solicitor prospect. The output must be trust-building, fast, and clearly branded as a mockup — never misleading.

**How to use:** fill in every `[BRACKETED]` variable below with verified data about the prospect, then paste the entire filled-in prompt into a capable LLM. Do not invent facts you cannot verify. For any signal you cannot confirm (reviews, numbers, awards), use the `[placeholder]` pattern described below.

---

## PROSPECT VARIABLES (fill in all before running)

- `[FIRM_NAME]` — full legal name as shown on their current site or Companies House
- `[FIRM_SHORT_NAME]` — short form used in the page header (e.g. "CBK Solicitors")
- `[FIRM_TAGLINE]` — one-line positioning based on their actual site (e.g. "Trusted legal advice in Whitby since 1914")
- `[TOWN]` — primary town (e.g. "Whitby")
- `[REGION]` — wider region or county (e.g. "North Yorkshire")
- `[FULL_ADDRESS]` — street address on one line
- `[POSTCODE]`
- `[PHONE]` — in UK local format (e.g. "01947 603391")
- `[EMAIL]` — primary contact email
- `[YEAR_FOUNDED]` — only if verified (else omit the "since" phrase entirely)
- `[PRACTICE_AREAS]` — an array of 4–8 actual practice areas the firm lists on their current site. Choose the short, consumer-friendly label, not legal jargon. Example: `["Family Law & Divorce", "Wills, Trusts & Probate", "Residential Conveyancing", "Commercial Property", "Employment Advice", "Personal Injury"]`
- `[AREAS_SERVED]` — 4–8 nearby towns/villages the firm realistically serves (helps local SEO copy; never invent)
- `[ACCREDITATIONS]` — real accreditations only (e.g. "Lexcel", "CQS", "Resolution", "Law Society Accredited")
- `[PRIMARY_CTA_TEXT]` — one of: `"Request a callback"`, `"Book a consultation"`, `"Speak to a solicitor"`. Default: `"Request a callback"`.
- `[PRIMARY_CTA_ACTION]` — one of: `"tel"` (links to phone), `"scroll"` (to contact form). Default: `"scroll"`.
- `[COLOR_PRIMARY]` — hex, from this palette only: `#14213d` (navy), `#5c2018` (burgundy), `#1f3d2b` (forest green). Default: navy.
- `[COLOR_ACCENT]` — a muted neutral: `#c9a96e` (muted gold) or `#8a8a8a` (warm grey). Default: muted gold.

---

## OUTPUT REQUIREMENTS (strict)

1. **Single file:** one complete `index.html` with all CSS inline in a `<style>` tag inside `<head>`. No external CSS, no JavaScript frameworks, no CDN links, no Google Fonts. Use a system font stack.
2. **No dependencies:** zero network requests beyond the HTML itself. Use inline SVG for any icons; no image files unless you include them as data URIs (avoid if possible — a clean type-led layout is preferred).
3. **Mobile-first:** design for 375px viewport first; use `@media (min-width: 768px)` for desktop refinements.
4. **Performance budget:** total file size under 40 KB. Full render ready in under 2 seconds on 3G.
5. **Brochure site only:** no shopping cart, no pricing table, no e-commerce patterns, no "plans". This is a professional-services informational site.
6. **Tone:** conservative, trust-building, understated. No "game-changing", no "unlock", no emojis, no exclamation marks in body copy. Short sentences. Plain English.
7. **No fabrications:** never invent testimonials, client names, case outcomes, award years, or statistics. Where social proof is expected but unverified, insert clearly marked placeholders like `[sample testimonial — replace with a real review from Google]` or `[placeholder: X years combined experience]`.
8. **Mockup footer notice:** include a small, subtle line in the footer: `Mockup designed by Elevate Marketing · elevatemarketing.no` (muted colour, small font). This must not look like a live site credit.
9. **Accessibility basics:** semantic HTML5 (`<header>`, `<main>`, `<section>`, `<footer>`), visible focus states on links and buttons, colour contrast ≥ 4.5:1 for body text.
10. **No tracking:** no analytics, no pixels, no cookie banner. It's a mockup, not a live site.

---

## REQUIRED PAGE STRUCTURE (in order)

1. **Top bar** — firm short name on the left, phone number on the right, click-to-call on mobile. One line only.
2. **Nav** — horizontal on desktop, collapsed to a simple anchor list (no JS hamburger) on mobile. Links: `Practice Areas`, `About`, `Areas We Serve`, `Contact`.
3. **Hero** — firm name, tagline, one primary CTA button, one secondary "Call [PHONE]" link. No hero image unless an inline SVG decoration. Keep above-the-fold uncluttered.
4. **Practice Areas** — grid of cards (2 cols mobile → 3 cols desktop), one card per `[PRACTICE_AREAS]` entry. Each card: area name, one-sentence description in the firm's voice, plain-text anchor like "Learn more ↗" that jumps to contact.
5. **About** — 2–3 short paragraphs. Reference `[YEAR_FOUNDED]` and `[TOWN]` only if verified. Highlight local, long-standing, plain-English positioning. End with the accreditations listed as plain text badges (text only, no logos).
6. **Testimonials** — exactly two or three testimonial cards, **each clearly marked** `[sample testimonial — replace with a real review from the firm's Google profile]`. Never put fake names or fake quotes.
7. **Areas We Serve** — plain list of `[AREAS_SERVED]`, introduced with one sentence (e.g. "We support clients across [REGION], including:").
8. **Contact** — two columns on desktop, stacked on mobile:
   - Left: address block, phone, email, opening hours (Mon–Fri 9–5 unless specified).
   - Right: a simple form with Name / Phone / Email / "How can we help?" / submit button. The form's `action` must be `mailto:[EMAIL]` so it works without a backend. Method `post`, enctype `text/plain`.
9. **Footer** — firm name, SRA reminder line ("Authorised and regulated by the Solicitors Regulation Authority"), copyright year, and the Elevate Marketing mockup notice.

---

## DESIGN RULES

- System font stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`.
- Base font-size 17px mobile, 18px desktop. Line-height 1.6.
- Max content width 1100px, centred, 20px side padding on mobile.
- Section vertical rhythm: 48px mobile / 80px desktop between sections.
- Buttons: solid `[COLOR_PRIMARY]` background, white text, 14px padding, 4px radius, no uppercase, no letter-spacing tricks.
- Links in body copy: underlined, `[COLOR_PRIMARY]`.
- Cards: 1px border in `#e5e5e5`, 6px radius, 24px padding, no shadow.
- Never use gradients, glassmorphism, neumorphism, or animated backgrounds.
- One accent touch only: a thin 3px top-border in `[COLOR_ACCENT]` on the header — nothing else uses accent colour.

---

## DO NOT

- Do not add prices or "from £X" text.
- Do not include a blog feed, news ticker, or case-study carousel.
- Do not add language switchers, "book online" booking widgets, or chat bubbles.
- Do not use stock imagery or decorative photography.
- Do not fabricate any fact — when in doubt, use a `[placeholder]` marker.
- Do not claim the firm is "the best", "the leading", "award-winning" unless the variable `[ACCREDITATIONS]` explicitly includes a specific award.

---

## DELIVERABLE

Return only the final `index.html` content, ready to save to `demos/[firm-slug]/index.html`. Do not wrap it in markdown fences. Do not add commentary before or after.
