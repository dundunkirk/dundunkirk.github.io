# Repository Guidelines

## Project Structure & Module Organization
This repository is a Hugo static site using the PaperMod theme. Core site settings live in `hugo.yaml`. Write source content in `content/`, with posts under `content/posts/` and utility pages such as `archives.md` and `search.md` at the content root. Use `archetypes/default.md` as the template for new pages. Site-level overrides belong in `layouts/`, and custom styling belongs in `assets/css/extended/`. The `themes/PaperMod/` directory contains the upstream theme; avoid editing it unless the change is intentionally theme-specific. Generated output is in `public/` and is deployed by GitHub Pages.

## Build, Test, and Development Commands
- `hugo server -D`: run the site locally, including draft content.
- `hugo`: build the production site into `public/`.
- `hugo --gc --minify`: match the main production build behavior more closely.
- `hugo new posts/example-title.md`: create a new post from the default archetype.

The GitHub Actions workflow in `.github/workflows/hugo.yaml` builds with Hugo Extended `0.154.2`, Dart Sass, Go, and Node.js, then deploys `public/` to GitHub Pages.

## Coding Style & Naming Conventions
Use Markdown with YAML front matter for content. Keep post filenames lowercase and hyphenated, for example `content/posts/my-new-post.md`. Prefer concise titles, ISO-like dates with timezone offsets, and explicit metadata such as `description` and `tags`. Use two-space indentation in YAML lists and nested config blocks. Keep custom CSS in `assets/css/extended/` instead of changing theme CSS directly.

## Testing Guidelines
There is no separate automated test suite in this repository. Treat a clean Hugo build as the primary validation step before submitting changes. For content edits, run `hugo server -D` and check the affected pages, navigation, search page, and archive listing. For config, layout, or CSS changes, also run `hugo --gc --minify` to catch build-time issues.

## Commit & Pull Request Guidelines
Recent commits use short imperative or descriptive messages, such as `update url` and `Add README with blog introduction`. Keep commits focused on one logical change. Pull requests should describe the content or behavior changed, note any Hugo build command run, link related issues when applicable, and include screenshots for visual changes.

## Agent-Specific Instructions
Do not overwrite an existing `AGENTS.md`. Preserve user-authored content and avoid broad theme rewrites. Prefer small, local changes in `content/`, `layouts/`, or `assets/css/extended/` unless the task explicitly requires deeper theme work.
