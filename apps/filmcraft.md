# FilmCraft → Adobe Premiere Pro

- **Good for:** video editing: timeline cut/trim, multicam, Lumetri-style color, keyframes, effects, titles, captions, audio mixing, export. 650+ commands (`filmcraft-cli commands`).
- **Stage:** alpha · team estimate ~56% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/filmcraft · **Page:** https://getartcraft.com/apps/filmcraft
- **CLI:** `filmcraft-cli` (macOS: separate `filmcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\FilmCraft\filmcraft-cli.exe`; Linux: `/usr/bin/filmcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user filmcraft -- "$CLI" mcp --demo
"$CLAUDE" mcp add --scope user filmcraft-app -- "$CLI" mcp --bridge 127.0.0.1:9876
```

- **Live mode:** start the app with `--control 9876` (port 9876), then the `filmcraft-app` server bridges to it.
- **macOS executable:** `/Applications/FilmCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/FilmCraft.app/Contents/MacOS/<check with ls>" --control 9876 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 9876`)

## Notes

- Can't open .prproj yet; bring sequences over as FCP7 XML, AAF or OTIO.
- H.264 is the only software delivery codec; H.265 export needs a hardware encoder. No AV1 export, no VST3/AU/OpenFX plugins.
- The MCP server has no folder confinement: it can read and write wherever the user can. Keep work in ~/craft-work/filmcraft.
- Live tools include `ui_screenshot`, `ui_click`, `ui_key`; `render_frame` gives a PNG of the program frame.

## First demo

With the app open, add a title with the user's name over the first clip, apply a warm color grade (Lumetri curve), then take a screenshot of the Program monitor and show it.

## Starter tasks

1. Here's a folder of clips (I'll give the path): copy them to ~/craft-work/filmcraft, make a 30-second rough cut on the beat of the music track, export H.264.
2. Grade this clip in two looks (clean and cinematic teal-orange) and show me both frames side by side.
3. Turn my 16:9 video into a 9:16 vertical version for X/Reels: reframe, add burned-in captions, export.
