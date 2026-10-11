# LightCraft → Adobe Lightroom

- **Good for:** photo library and RAW development: culling (flags, ratings), develop sliders, masks (radial, sky…), presets, batch export. Renders come back to you as images.
- **Stage:** alpha · team estimate ~61% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/lightcraft · **Page:** https://getartcraft.com/apps/lightcraft
- **CLI:** `lightcraft-cli` (macOS: separate `lightcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\LightCraft\lightcraft-cli.exe`; Linux: `/usr/bin/lightcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user lightcraft -- "$CLI" mcp ~/craft-work/lightcraft
"$CLAUDE" mcp add --scope user lightcraft-app -- "$CLI" mcp --connect 127.0.0.1:7980
```

- **Live mode:** start the app with `--control 7980` (port 7980), then the `lightcraft-app` server bridges to it.
- **macOS executable:** `/Applications/LightCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/LightCraft.app/Contents/MacOS/<check with ls>" --control 7980 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 7980`)
- Create `~/craft-work/lightcraft` first and expand `~` to an absolute path in the real command.

## Notes

- The headless server takes files or folders to import as arguments (`mcp [--demo] [FILES/FOLDERS…]`).
- Camera color calibration is estimated for many raws, not measured yet.
- `develop.controls` lists every slider with range, default and current value.

## First demo

Import the user's photos (copied into ~/craft-work/lightcraft) or the demo set, pick one, lift shadows, pull highlights, add a radial mask on the subject, and show before/after renders.

## Starter tasks

1. Cull this shoot: flag the best 10 and reject blurry shots. Show me the picks as a contact sheet.
2. Develop my picks in one consistent warm look, mask the sky darker, export web JPGs (2048 px long edge).
3. Make a preset from this edit and apply it to the whole folder.
