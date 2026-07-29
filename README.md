# Venue-Ready website

Static site, no build step. `index.html` is the whole marketing and conversion flow.

| File | What it is |
|---|---|
| `index.html` | The site. Scope checker, the seven-requirement spine, pricing, buying info, FAQ. |
| `privacy.html` · `terms.html` | Legal pages, linked from every footer. |
| `training.html` | £49/£199 fulfilment: video, quiz, printable Briefing Completion Record. |
| `checklist.html` | Free printable Mis-selling Checklist (A4). |
| `out-of-scope-letter.html` | Free scope review record for venues under the threshold (1 side of A4). |
| `starter-checklist.html` | Free standard-tier starter checklist (1 sheet, both sides). |
| `enhanced-tier-reading-list.html` | Free reading list for enhanced-tier venues we refer away (1 sheet, both sides). |
| `committee-one-pager.html` | Free summary to circulate with a PCC/council agenda (1 side of A4). |
| `review-sheet.html` | Free printable 20-minute annual review walk-through (1 sheet, both sides). |
| `content/` | Email copy that isn't a web page — currently the annual review automation. |
| `netlify.toml` | Security headers and pretty-URL rewrites. |

Before launch, edit only the `CONFIG` block at the bottom of `index.html`.

## Work on it with Claude Code
1. Put this folder anywhere on your machine (e.g. ~/projects/venue-ready).
2. Terminal: `cd ~/projects/venue-ready && claude`
3. Claude Code reads CLAUDE.md automatically — it contains brand, legal lines, and the TODO list.
4. First command to give it: "Read CLAUDE.md, then start TODO 1 and 2."

## Preview locally
Open index.html in a browser, or: `python3 -m http.server 8000` then http://localhost:8000

## Deploy (free)
Drag the folder into https://app.netlify.com/drop — then connect domain venue-ready.co.uk.
