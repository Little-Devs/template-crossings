# PROMPT.md — Crossings

Reproduce this site without locking to a provider or framework.

## Goal

A single-page professional-services landing for the staged demo brand **Crossings**. Thesis: **Clarity at the border.** Intensity 6 (see MOTION.md).

## Brand / copy rules

- Brand wordmark: **Crossings**
- Hero thesis: **Clarity at the border.**
- CTAs: `mailto:hello@crossings.example` only — label "Book a consult"
- No Buy, no analytics, no invented backends

## Tokens

| Paper | `#F5F7FA` |
| Navy | `#0B1F3A` |
| Teal | `#0E7C86` |
| Stamp | `#C45C26` |
| Rule | `#C9D2DE` |

Type: Source Serif 4 display + Source Sans 3 body.

## Sections (order)

1. Sticky nav
2. Hero + passport imagery
3. Pathways (work/family/study)
4. Process steps
5. Team
6. Closing consult CTA
7. Footer

## Quality

Skip link, one h1, focus-visible rings, prefers-reduced-motion, mobile @375. Steve Pages `_headers` (HSTS, CSP with little.website frame-ancestors, no XFO, no ACAO *). Put JS in `/js/` — no inline `<script>` blocks. Google Fonts CSS link OK unless `/fonts/` is already self-hosted. Self-host Pixabay photos under `/images/`.

## Deliver

Static files at site root: `index.html`, `site.css`, `js/*` (if needed), `images/*`, `_headers`, `favicon.svg`, `preview.png`, `MOTION.md`, `AGENTS.md`, `PROMPT.md`, `template.json`, `LICENSE`, `README.md`.
