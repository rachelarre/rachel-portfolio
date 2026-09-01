# Rachel Arredondo — Portfolio Site: Handoff Notes

This project was built collaboratively in a Claude Cowork session before moving to Claude Code. This file exists so a fresh Claude Code session (or Rachel herself) can pick up with full context.

## What this is

A single-page personal portfolio site (`index.html`) plus one standalone essay page (`writing/design-ethos-and-values.html`). Built from Rachel's resume, a Headspace case study, and content she edits directly in a linked Notion page ("Portfolio Home").

Layout: sticky left sidebar nav (About / Experience / Education / Writing / Publications / Speaking) at 1fr, main content at 3fr, on a `max-width:1280px` shell. Fully responsive — collapses to a hamburger topbar + dropdown menu below 920px. **Light mode only** — dark mode was deliberately removed (was previously supported via `prefers-color-scheme` + a toggle button; all of that CSS/JS has been stripped).

Fonts: Inter (Google Fonts). Palette: near-black ink on white, minimal greys — no color accents.

## Immediate next steps (in progress when this was handed off)

1. ~~**Create a GitHub repo**~~ — Done. Repo is https://github.com/rachelarre/rachel-portfolio (public), existing git history pushed intact, default branch renamed `master` → `main` to match GitHub's current convention.
2. ~~**Connect Netlify**~~ — Done. Site is https://rachelarre.netlify.app (Netlify site name `rachelarre`, project ID `36b01a2e-06fc-42fb-a390-754c4f4227b6`), linked to the GitHub repo via a deploy key (not the GitHub App/OAuth — Netlify's SSH-based git integration) plus a GitHub webhook (`https://api.netlify.com/hooks/github`, events: push/pull_request/delete) that triggers builds. Pushes to `main` auto-deploy — verified working. No build command needed; publish directory is the repo root (`.`) since this is a static site.
3. **Point rachelarre.com at Netlify.** The domain is currently on Flywheel/WordPress. Rachel confirmed she wants to fully replace the WordPress site (not run them side by side) and manage DNS through Flywheel's DNS settings, pointing to Netlify. Once ready, add the custom domain in Netlify (Site settings → Domain management) and update DNS at Flywheel accordingly.
4. Once both pages are hosted together under one domain, the relative link from the Writing section to `writing/design-ethos-and-values.html` (and the "back" link from that page to `../index.html`) will resolve correctly — right now, as two separate published previews, they don't link to each other. This is expected and not a bug.

## Content source of truth

Rachel edits content directly in Notion — page "Portfolio Home" (https://app.notion.com/p/momolyfe/Portfolio-Home-2d400d4a692680b78bacf914c6ea5373) and its subpage "Design Ethos + Values". If she says she's updated Notion, re-fetch it and sync the changes into `index.html` — don't assume the HTML is current.

## Judgment calls flagged to Rachel, not yet resolved

Two Publications entries are missing a location, on purpose, per Rachel's own instruction ("if no location, ignore" — never fabricate):

- **Memory Portal (CHI 2021)** — CHI 2021 was originally slated for Yokohama, Japan but was actually held virtually. Location was left off rather than listing a city it wasn't actually held in. If Rachel can confirm how she'd like this represented, update the `.org` line in the Publications row.
- **Envisioning New Futuring Models (IASDR 2021)** — no confirmed host city was found via search. Left without a location for the same reason.

If Rachel provides real locations for either, they go in the `.org` div underneath the title, matching the pattern already used for the other entries (e.g. `Creativity & Cognition, Pictorial, Venice, Italy`).

## Formatting conventions established (keep consistent with any new entries)

Experience / Education / Writing / Publications / Speaking all share one `.row` component: `.when` (date only, left column) + `.what` containing `.role` (title, linked if applicable) and `.org` (company/venue + location, comma-separated) and optionally `.blurb`. Do not reintroduce the old `.talk-row` or `.place` patterns — they were consolidated away.

## Previously published previews (from the Cowork session, before real hosting)

- Main site: https://claude.ai/code/artifact/bc00c4c4-0353-4730-a831-3edcba3e25de
- Design Ethos & Values essay: https://claude.ai/code/artifact/96e58a84-e668-4eb5-b0e5-d2dbc345b4c7

These will become redundant once the real domain is live, but are useful for comparing against if something looks different after the move.
