# VectorCraft → Adobe Illustrator

- **Good for:** vector illustration: pen and shape tools, pathfinder, effects, 3D, text, image trace, brushes; SVG, PDF, EPS export.
- **Stage:** alpha · team estimate ~62-65% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/vectorcraft · **Page:** https://getartcraft.com/apps/vectorcraft
- **CLI:** `vectorcraft-cli` (macOS: separate `vectorcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\VectorCraft\vectorcraft-cli.exe`; Linux: `/usr/bin/vectorcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user vectorcraft -- "$CLI" mcp --automation-read-root ~/craft-work/vectorcraft --automation-write-root ~/craft-work/vectorcraft
"$CLAUDE" mcp add --scope user vectorcraft-app -- "$CLI" mcp --connect 127.0.0.1:7979
```

- **Live mode:** start the app with `--control 7979 --automation-read-root ~/craft-work/vectorcraft --automation-write-root ~/craft-work/vectorcraft` (port 7979), then the `vectorcraft-app` server bridges to it.
- **macOS executable:** `/Applications/VectorCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/VectorCraft.app/Contents/MacOS/<check with ls>" --control 7979 --automation-read-root ~/craft-work/vectorcraft --automation-write-root ~/craft-work/vectorcraft >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 7979 --automation-read-root ~/craft-work/vectorcraft --automation-write-root ~/craft-work/vectorcraft`)
- Create `~/craft-work/vectorcraft` first and expand `~` to an absolute path in the real command.

## Notes

- Files are reachable only under the automation roots (use absolute paths in the actual command).
- Port 7979 is shared with GridCraft, CADCraft and DesignCraft: run one at a time.
- On Linux KDE Plasma 6.3+ Wayland, a tablet pen moves the cursor but may not draw (README).

## First demo

Draw a simple geometric logo mark for the user's handle (circle + bold monogram), apply a gradient, and export SVG and PNG; show the PNG.

## Starter tasks

1. Design a set of 6 matching line icons (home, search, user, bell, gear, play), export each as SVG.
2. Make an A3 poster with bold typography for "<your event>" and export PDF.
3. Trace this bitmap logo into clean vectors and export SVG.
