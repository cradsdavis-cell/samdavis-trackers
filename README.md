# samdavis-trackers

Sam Davis's personal progress trackers. Multi-page static site served via GitHub Pages.

**Live:** https://cradsdavis-cell.github.io/samdavis-trackers/

**Privacy:** every page carries `<meta name="robots" content="noindex, nofollow, noarchive">`. Content is pipeline-sensitive (lead names, application stages, productivity grades). Anyone with a URL can read it, but search engines won't index it.

## Trackers

| Slug | Source | Refresh skill |
|---|---|---|
| `sf-trip/` | `EA/demos/sf-trip-tracker.html` | `/sf-tracker` |
| `productivity/` | `EA/demos/productivity-tracker.html` | `/productivity` |

## How updates land here

Source-of-truth lives in the EA repo. The relevant skills (`/sf-tracker`, `/productivity`) write to `EA/demos/*.html`. To deploy:

1. From the EA session, ask the assistant to "push trackers"
2. The assistant uses GitHub MCP (`mcp__github__create_or_update_file`) to push the updated tracker page + a regenerated `index.html` (so the landing's status pills + timestamps stay current)

No CI, no GitHub Actions, no local clone, no scripts. Pure MCP-from-session.

## How to add a new tracker

1. Build the source HTML in `EA/demos/<name>-tracker.html` (inline SVG only — no PNG/JPG; GitHub MCP push is text-only)
2. Add a card to the landing (`index.html`) — copy the existing card markup, swap title/description/href
3. Push the new folder + updated landing via MCP
