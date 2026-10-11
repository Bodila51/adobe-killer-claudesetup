# DesignCraft → Adobe InDesign

- **Good for:** page layout: master pages, text frames and threading, styles, typography, images, PDF/PNG export.
- **Stage:** pre-alpha · team estimate ~47% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/designcraft · **Page:** https://getartcraft.com/apps/designcraft
- **CLI:** `designcraft-cli` (macOS: separate `designcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\DesignCraft\designcraft-cli.exe`; Linux: `/usr/bin/designcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user designcraft -- "$CLI" mcp
"$CLAUDE" mcp add --scope user designcraft-app -- "$CLI" mcp --connect 7979
```

- **Live mode:** start the app with `--sample --control 7979` (port 7979), then the `designcraft-app` server bridges to it.
- **macOS executable:** `/Applications/DesignCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/DesignCraft.app/Contents/MacOS/<check with ls>" --sample --control 7979 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--sample --control 7979`)

## Notes

- Pre-alpha. Known gaps: docs/gaps.md in the repo.
- Port 7979 is shared with GridCraft, VectorCraft and CADCraft: run one at a time.
- Headless export: `designcraft --export page.pdf --export page.png`.

## First demo

Open the sample magazine, change the cover headline to the user's name, swap the accent color, export the page as PNG and show it.

## Starter tasks

1. Lay out a one-page event flyer from this text, export print PDF.
2. Build a 4-page zine with a master page, page numbers and threaded text.
3. Turn my CV text into a clean two-column one-page resume PDF.
