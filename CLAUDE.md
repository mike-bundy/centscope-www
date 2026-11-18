# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

Static marketing site for CentScope, a financial wellness platform (rebranded from Rise). No build step, no package.json, no framework — just HTML files that load Tailwind and Nunito from CDNs. Serve locally with `python -m http.server 8000` or `npx serve .`, or open the HTML directly.

**The product is pre-launch.** It is coming soon to iOS, Android, and the web, and the site must not link to anything backend-related: no sign-in, sign-up, demo booking, store listings, or app URLs. CTAs either scroll within the page or go to `about.html`. Don't add usage numbers or testimonials either; there are no users yet. `README.md` has an "At Launch" list of what to wire up when that changes.

## Files

- `index.html` — landing page with three-way audience toggle (Members / Institutions / Community).
- `about.html` — mission, values, launch facts, team.
- `name-research.html` — standalone internal artifact from the naming research that led to CentScope. It still talks about "Rise" as the brand being replaced, which is correct for that document. Independent styling — do not treat its conventions as canonical for the marketing pages, and do not link to it.
- `logo.png` (light backgrounds), `logo-reversed.png` (dark backgrounds), `mark.png` (pinwheel only), `favicon.png`.

## Architecture notes that aren't obvious from one file

**Everything shared is duplicated per HTML file.** There is no shared config or include mechanism, so `index.html` and `about.html` each carry their own copy of the `tailwind.config` block, the `<style>` block, the `#coming-soon` band, and the footer. Change one, change the other.

**Brand tokens (keep in sync across pages):**
- From the logo: `cs-blue` `#4879a4` · `cs-sky` `#8abee3` · `cs-sun` `#f7e769` · `cs-lime` `#cbd25d`
- Derived: `cs-navy` `#1f3a56` · `cs-mist` `#eaf3fa` · `cs-slate` `#3d4b5a`
- Font: Nunito (400/600/700/800). Buttons use `rounded-2xl`.

**Contrast rule.** `cs-sky`, `cs-sun`, and `cs-lime` are light: text and icons on them are `cs-navy`, never white. White text goes on `cs-blue` and `cs-navy` only. `cs-sun` and `cs-lime` are also too pale to use as text on white.

**Section backgrounds.** `bg-brand-blue`, `bg-brand-navy`, and `bg-brand-citrus` are plain CSS classes (not Tailwind) that layer the plus-sign texture over a colour or gradient in one `background-image`. Don't combine them with a Tailwind `bg-*` class or an inline `background`; either would wipe out the texture or the gradient.

**Audience toggle pattern (`index.html`).** `setAudience(audience)` in the inline `<script>` at the bottom shows/hides DOM nodes by id convention: for each audience in `['members', 'institutions', 'community']` it toggles `hero-{audience}` and `features-{audience}` plus the matching `toggle-{audience}` / `mobile-toggle-{audience}` buttons. When adding audience-specific sections, follow this id naming or the toggle won't pick them up. Adding a fourth audience means updating the array in the script, adding both desktop and mobile buttons, and adding the matching `hero-*` / `features-*` sections.

**Audience deep links.** The three `features-*` sections sit inside `<div id="features">`, the scroll target. Footer links are written `href="index.html#members" data-audience="members"`: on `index.html` the script intercepts the click, switches audience, and scrolls to `#features`; from `about.html` the same link navigates and the script reads the hash on load. Keep both attributes on any new link of this kind.

**Placeholder graphics are tracked in `README.md`.** The "Placeholder Graphics Needed" section enumerates every image spec (dimensions, style). When swapping in real assets, cross-check that list rather than inferring from the current DOM.
