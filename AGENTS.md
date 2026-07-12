# AGENTS.md — pflegegrad-web

Device-detection redirect landing page for the **Pflegegrad Begleiter** app. Private
Fruhji app. Live: https://fruhji.github.io/pflegegrad-web/

## What it is
A bare static site, deployed via GitHub Pages. iOS visitors get redirected straight to
the App Store; Android redirect is currently disabled (`PLAY_LIVE = false` in the
inline script) — Pflegegrad Begleiter is a health app on an individual Play developer
account, so production Android release is intentionally held back regardless.

## Files
- `docs/index.html` — the entire site: inline `<script>` does the UA-sniffing redirect
  (`location.replace`), inline `<style>` covers light/dark. No other pages.
- `docs/.nojekyll` — disables Jekyll processing (required, do not remove).
- `.github/workflows/pages.yml` — deploys `docs/` to GitHub Pages via the official
  `actions/*-pages` actions on every push to `main`.

## Making a change
No build step, no dependencies, no tests. Edit `docs/index.html` directly (store URLs
are hardcoded in the script block at the top), commit, push to `main` — the workflow
deploys automatically. Do not flip `PLAY_LIVE` without checking the app's current Play
production status first (see `pflegegrad-begleiter/CLAUDE.md`).

## Conventions
- Git identity: `leon.mons2@gmail.com`. Branding: **Fruhji** (never the real name).
- No emojis — typographic marks (`·` `–` `—`) instead.
