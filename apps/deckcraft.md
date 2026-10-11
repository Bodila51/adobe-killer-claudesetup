# DeckCraft → Microsoft PowerPoint

- **Good for:** slides: themes, layouts, shapes, pictures, tables, charts, transitions and animations; opens and saves .pptx; full-screen presenting.
- **Stage:** alpha · team estimate ~55% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/deckcraft · **Page:** https://getartcraft.com/apps/deckcraft
- **CLI:** `deckcraft-cli` (macOS: separate `deckcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\DeckCraft\deckcraft-cli.exe`; Linux: `/usr/bin/deckcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user deckcraft -- "$CLI" mcp
"$CLAUDE" mcp add --scope user deckcraft-app -- "$CLI" mcp --connect 7990
```

- **Live mode:** start the app with `--control 7990` (port 7990), then the `deckcraft-app` server bridges to it.
- **macOS executable:** `/Applications/DeckCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/DeckCraft.app/Contents/MacOS/<check with ls>" --control 7990 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 7990`)

## Notes

- Covers ~79% of PowerPoint features by breadth (README).

## First demo

Create a 3-slide deck: title slide with the user's name, a bullet slide, a chart slide; apply a dark theme and a fade transition; screenshot slide 1.

## Starter tasks

1. Turn this outline into a 10-slide pitch deck with a consistent theme, save .pptx.
2. Make a chart slide from this data and animate the bars in.
3. Redesign this .pptx with a cleaner layout and fewer words per slide.
