# PhotoCraft → Adobe Photoshop

- **Good for:** raster editing: layers, groups, masks, adjustment and fill layers, smart objects with smart filters, 27 blend modes, filters, PSD/PSB, batch actions. 500+ commands.
- **Stage:** alpha · team estimate ~45% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/photocraft · **Page:** https://getartcraft.com/apps/photocraft
- **CLI:** `photocraft-cli` (macOS: separate `photocraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\PhotoCraft\photocraft-cli.exe`; Linux: `/usr/bin/photocraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user photocraft -- "$CLI" mcp --automation-read-root ~/craft-work/photocraft --automation-write-root ~/craft-work/photocraft
"$CLAUDE" mcp add --scope user photocraft-app -- "$CLI" mcp --bridge 127.0.0.1:7878 --control-token-file ~/craft-apps/photocraft/control.token
```

- **Live mode:** start the app with `--control 7878 --control-token-file ~/craft-apps/photocraft/control.token` (port 7878), then the `photocraft-app` server bridges to it.
- **macOS executable:** `/Applications/PhotoCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/PhotoCraft.app/Contents/MacOS/<check with ls>" --control 7878 --control-token-file ~/craft-apps/photocraft/control.token >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 7878 --control-token-file ~/craft-apps/photocraft/control.token`)
- Create `~/craft-work/photocraft` first and expand `~` to an absolute path in the real command.

## Notes

- Files are reachable only under the automation roots: put inputs in ~/craft-work/photocraft (create it first; use absolute paths in the actual command).
- The live channel is authenticated with the token file; the app creates it on first start. Keep it in a private folder, never /tmp. Exact flags: docs/mcp.md and docs/control-protocol.md in the repo.
- No generative AI features, no Photoshop plugins; 15 tools still missing (README).
- Batch without MCP: `photocraft-cli batch --actions grade.json --in ./raw --out ./graded`.

## First demo

Create a 1500x500 canvas (an X header), dark gradient background, the user's name in large type, a Curves adjustment layer for contrast, then render a preview and show it.

## Starter tasks

1. Take this photo (I'll give the path), copy it to ~/craft-work/photocraft, smart-sharpen it, add a Curves adjustment layer, export PNG.
2. Make a 1080x1350 post: my photo, a soft vignette, a headline with a drop shadow. Save as PSD and PNG.
3. Apply one grade to this whole folder of images and export them as JPG 90.
