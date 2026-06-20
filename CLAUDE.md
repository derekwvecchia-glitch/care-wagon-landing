# C.A.R.E. Wagon

Mobile-first "linktree"-style site for the Revere Police Department's Behavioral Health Unit C.A.R.E. Wagon ("Community · Access · Resources · Engagement"). Single-page static HTML, no build step, deployed on Vercel.

## Structure

- `index.html` — home/landing page. Self-contained: inline `<style>` in `<head>`, inline `<script>` before `</body>`.
- Additional landing pages should follow the same pattern: one self-contained `.html` file per page, sharing the design system below, placed at the project root (Vercel serves static files directly — `/donate.html` → `/donate`).

## Design system (defined in `index.html` `:root`)

```css
--navy:#0A1B33;       --navy-2:#0F2647;     --blue:#1F4E96;
--gold:#D4A537;        --gold-soft:#E8C76A;
--cream:#F6F2E8;       --paper:#FFFFFF;
--ink:#161B24;         --ink-soft:#5A6473;   --line:#E7E0D0;
--shadow:0 1px 2px rgba(10,27,51,.06), 0 8px 24px rgba(10,27,51,.10);
```

- Fonts (Google Fonts, preconnected): **Bricolage Grotesque** (headings, weight 700/800), **Inter** (body), **DM Mono** (eyebrow/labels, small caps tracking).
- Layout: single `.wrap` column, `max-width:460px`, centered — designed mobile-first/portrait, since this is reached primarily via QR code / phone.
- Signature motifs: navy radial-gradient header (`.top`) with a gold hairline frame inset, a repeating-gradient "awning" stripe divider (`.awning`) as an ice-cream-truck nod, and rounded `.link` cards with a 3px gold top border that turns blue on hover/focus.
- Circular logo badge (`.logo`, 128px, gold border) at top of header.

## Conventions

- Keep each page a single self-contained `.html` file (no separate CSS/JS files) to match `index.html` and simplify Vercel static hosting.
- Real destination URLs are centralized in a `LINKS` object in the bottom `<script>` block, not hardcoded into `href` attributes — this matches `index.html`'s "edit links in one place" pattern. Any link without a real URL yet stays `"#"` and automatically renders a disabled "Coming soon" tag (see the IIFE in `index.html`'s script block).
- Reuse the existing `.link`/`.links` card grid markup for any new page that lists multiple options (e.g. a "Find the wagon" page with multiple location/schedule entries).
- No frameworks, no bundler, no `package.json` — keep it plain HTML/CSS/JS unless the user asks to introduce tooling.
