# CADCraft → Autodesk AutoCAD

- **Good for:** 2D drafting: the command line, object snaps, layers, dimensions, hatches, blocks, DXF drawings. MCP tool `command_line` types at the prompt like a user.
- **Stage:** pre-alpha · team estimate ~38% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/cadcraft · **Page:** https://getartcraft.com/apps/cadcraft
- **CLI:** `cadcraft-cli` (macOS: separate `cadcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\CADCraft\cadcraft-cli.exe`; Linux: `/usr/bin/cadcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user cadcraft -- "$CLI" mcp
"$CLAUDE" mcp add --scope user cadcraft-app -- "$CLI" mcp --connect 127.0.0.1:7979
```

- **Live mode:** start the app with `--control 7979` (port 7979), then the `cadcraft-app` server bridges to it.
- **macOS executable:** `/Applications/CADCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/CADCraft.app/Contents/MacOS/<check with ls>" --control 7979 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 7979`)

## Notes

- Pre-alpha. Missing features: docs/gaps.md in the repo.
- Port 7979 is shared with GridCraft, VectorCraft and DesignCraft: run one at a time.
- Over the drawing area CADCraft draws its own crosshair; screen recorders may lose the cursor (View > Accessibility > Show System Cursor).

## First demo

Draw a 6 x 4 m room plan with a door and a window, dimension the walls on a 'DIM' layer, and take a screenshot.

## Starter tasks

1. Draw a simple floor plan of a 2-room apartment with dimensions, save DXF.
2. Make a parametric bracket: 120 x 80 plate with 4 holes, hatched section, dimensions.
3. Open this DXF, list its layers and blocks, and clean up unused ones.
