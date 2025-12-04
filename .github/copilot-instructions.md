# AI Coding Agent Guide: single-page-resume

This repo is a Hugo (JAMstack) single‑page resume site. The key is data‑driven content (`data/resume.json`) rendered through a Hugo theme (`themes/hugo-orbit-theme`) with minimal custom JS/CSS. Agents should prioritize editing content and config, not generated output.

## Big Picture
- **Static site generator:** Hugo builds pages from `config.toml`, `data/resume.json`, and theme layouts.
- **Theme:** `themes/hugo-orbit-theme` provides layouts/partials in `layouts/` and assets in `static/assets/`.
- **Generated output:** `public/` is the build output. Do not edit files here directly.
- **Assets:** Project images live in `static/assets/images/`. Frontend scripts in `public/assets/js/` are part of theme output.

## Primary Workflow
- **Local dev:** Run `hugo serve -D` from repo root to preview drafts.
- **Build:** Run `hugo -D` to generate the site into `public/`.
- **Deploy (GitHub Pages):** Set `baseurl` in `config.toml` to your Pages URL. A workflow directory may be used at `.github/workflows` if present.

## What To Edit
- **Content data:** `data/resume.json` holds resume sections used by theme partials. Update entries (e.g., experiences, education, projects, skills) here.
- **Profile image:** Place `profile.png` in `static/assets/images/`.
- **Site config:** `config.toml` controls base URL, language, menus, and toggles for sections. Use it to enable/disable sections displayed by the theme.

## Theme Structure & Key Files
- **Layouts:** `themes/hugo-orbit-theme/layouts/` contains:
  - `_default/single.html`, `_default/list.html`: Base templates
  - `index.html`: Home page layout
  - `partials/*.html`: Section renderers (e.g., `experiences.html`, `projects.html`, `skills.html`, `education.html`, `summary.html`, `profile.html`, `sidebar.html`, `scripts.html`, `head.html`). These typically read from `data/resume.json`.
- **i18n:** `themes/hugo-orbit-theme/i18n/*.yaml` contains translation strings.
- **Theme assets:** `themes/hugo-orbit-theme/static/assets/` for CSS/JS/images shipped with theme. Customizations should prefer overriding via the project’s `static/` rather than editing theme directly.

## Conventions & Patterns
- **Data‑driven sections:** Theme partials expect specific keys in `data/resume.json`. Keep structure consistent when adding fields.
- **Overrides:** To customize theme assets, add files under `static/` with matching paths to override theme static files during build.
- **Do not commit build artifacts:** Avoid hand‑editing anything under `public/`. Regenerate via Hugo.
- **Minimal JS:** `public/assets/js/main.js` is generated/copied; prefer Hugo templating and data edits over JS changes.

## Commands (Windows PowerShell)
```powershell
# Preview with drafts
hugo serve -D

# Build production site to ./public
hugo -D
```

## Examples
- **Add a new experience:** Edit `data/resume.json` under the `experiences` array; preview with `hugo serve -D` and verify `themes/.../partials/experiences.html` renders correctly.
- **Hide a section:** Toggle flags in `config.toml` that the theme reads to conditionally include partials (e.g., disable `projects` or `awards`).
- **Update profile photo:** Place `static/assets/images/profile.png` and rebuild; header `profile.html` will pick it up.

## Integration Notes
- **GitHub Pages:** Ensure `baseurl` in `config.toml` matches your Pages URL. If a workflow exists under `.github/workflows`, verify it runs `hugo` and publishes `public/`.

## Guardrails for Agents
- Do not modify `public/` files; treat as ephemeral output.
- Avoid breaking `data/resume.json` schema used by partials; keep keys consistent.
- Prefer `static/` overrides for images/assets; avoid changing theme sources unless necessary.
- Validate changes by running `hugo serve -D` and checking rendered sections.

## Open Questions for Maintainer
- Which keys in `data/resume.json` are considered required vs optional per partial?
- Exact config toggles in `config.toml` for each section (document names and expected values)?
- Confirm CI workflow location/name and deployment target when not using GitHub Pages.
