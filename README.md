# fcm-docs

Client-facing HTML documents published via GitHub Pages for Fifth Castle Media.

**Live URL:** https://docs.fifthcastle.media/
**Repository:** https://github.com/arek-eeva/fcm-docs
**Branch:** `main` (GitHub Pages deploys from main)
**CNAME:** `docs.fifthcastle.media` (DNS via Cloudflare)

## How It Works

Source HTML files are created in the appropriate location within `fcm_os` (typically `Sales/Prospects/[Client]/` or `Clients/[Client]/`). When a document needs a shareable link, it is copied into this repo, committed, and pushed.

GitHub Pages serves the file at `https://docs.fifthcastle.media/[filename].html`.

## Publishing a Document

1. Generate the HTML document (self-contained, FCM-branded).
2. Save the source to the appropriate `fcm_os` location.
3. Copy the file here with a **kebab-case filename** (e.g. `cgt-content-production-proposal.html`).
4. Update `DIRECTORY.md`: add a row for the new page under the right category table (or update the "Last updated" date if replacing an existing page). This file is the live record of every page on the site — it must never drift out of sync.
5. Commit and push, including `DIRECTORY.md` in the same commit:
   ```bash
   cd fcm-docs && git add [file] DIRECTORY.md && git commit -m "Add [file]" && git push
   ```
6. The document is live at `https://docs.fifthcastle.media/[filename].html`.

**Removing or renaming a page:** update `DIRECTORY.md` in the same commit as the `git rm`/rename, so the directory always matches what's actually live.

## File Requirements

- **Self-contained HTML only.** Inline CSS or CDN links. No local file references.
- **Google Fonts:** Use `<link>` tags in `<head>`, not `@import`.
- **Images:** Use base64 data URIs or absolute URLs.
- **Logo:** Always embed as base64 (pre-encoded version at `Skills-and-Automation/client-presentation/assets/logo-base64.txt`).

## Naming Convention

Use kebab-case: `[client]-[document-type]-[optional-date].html`

Examples:
- `cgt-content-production-proposal.html`
- `mit-production-brief-2026-03-24.html`
- `eyes-on-hands-production-brief.html`

## Authentication

The git remote URL in `.git/config` contains a PAT (Personal Access Token). If it expires, generate a new classic token at github.com/settings/tokens with `repo` scope and update the remote URL.
