# AGENTS.md

**Security and reliability are paramount.** Prefer a correct, boring change over a clever one. Do not invent backends, credentials, tracking, or third-party services.

## Template

- **Name:** Crossings
- **Catalog id:** `crossings`
- **Repository:** `https://github.com/Little-Devs/template-crossings`
- **Demo:** `https://crossings.little.website/`
- **Stack:** Static HTML · hand CSS · self-hosted Source Serif 4 + Source Sans 3 (`/fonts/`) · CSS scroll-driven motion
- **Catalog:** https://github.com/Little-Devs/web-templates (`templates.json`)

## Agent / LLM setup

1. Read `README.md`, `template.json`, this file, `PROMPT.md`, and `MOTION.md`.
2. Discover tokens from `site.css` `:root` — do not restyle from memory.
3. Keep static HTML/CSS; no framework unless the task explicitly migrates.
4. Work in small diffs. Match local naming and formatting.
5. Verify by serving the folder root. There is no build step.
6. Never commit secrets, `.env` files, or API keys.

## Security and reliability

- No secrets in source or docs.
- No new analytics, pixels, or third-party scripts without an explicit request.
- Forms/CTAs stay `mailto:hello@crossings.example` unless asked otherwise.
- Preserve `_headers` (HSTS, CSP, frame-ancestors for little.website, no X-Frame-Options, no ACAO *).
- Put JS in `/js/*.js` only — CSP `script-src 'self'` forbids inline scripts.
- Self-host photos under `/images/` — CSP `img-src 'self'` forbids remote images.
- Respect `prefers-reduced-motion` (MOTION.md intensity 6).

## Design tokens

| Token | Value | Notes |
|-------|-------|-------|
| `--paper` | `#F5F7FA` | Paper |
| `--navy` | `#0B1F3A` | Navy |
| `--teal` | `#0E7C86` | Teal |
| `--stamp` | `#C45C26` | Stamp |
| `--rule` | `#C9D2DE` | Rule |
| Display / body | Source Serif 4 + Source Sans 3 | Never Inter/Roboto/Arial/Space Grotesk |

## Copy rules

Intentional fake brand **Crossings**. Thesis: **Clarity at the border.** Mailto `hello@crossings.example` only. No Buy. No checkout. No CMS. No auth.

## Deploy

Cloudflare Pages Direct Upload (`lw-demo-crossings`). Oppy maps `crossings.little.website`. Screenshot before listing.
