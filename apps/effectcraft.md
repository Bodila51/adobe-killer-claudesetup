# EffectCraft → Adobe After Effects

- **Good for:** motion graphics: keyframes, graph editor, text animators, 306 effects, puppet pins, 3D cameras and lights, render queue (ProRes incl. 4444 with alpha, HEVC, AV1, WebM, GIF, Lottie).
- **Stage:** alpha · team estimate ~45% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/effectcraft · **Page:** https://getartcraft.com/apps/effectcraft
- **CLI:** `effectcraft-cli` (macOS: separate `effectcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\EffectCraft\effectcraft-cli.exe`; Linux: `/usr/bin/effectcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user effectcraft -- "$CLI" mcp --demo
"$CLAUDE" mcp add --scope user effectcraft-app -- "$CLI" mcp --bridge 9877
```

- **Live mode:** start the app with `--demo --control 9877` (port 9877), then the `effectcraft-app` server bridges to it.
- **macOS executable:** `/Applications/EffectCraft.app/Contents/MacOS/EffectCraft`
- **Reopen later (macOS):** `nohup "/Applications/EffectCraft.app/Contents/MacOS/EffectCraft" --demo --control 9877 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--demo --control 9877`)

## Notes

- No .aep import and no After Effects plugins.
- macOS is the most tested platform; Linux and Windows users have hit basic interaction bugs (README).
- Bridge mode adds `screenshot` and the `ui_*` tools. Check work with `render_frame` (headless) or `screenshot {"panel":"Timeline"}` (live).
- One-shot CLI against the live app: `effectcraft-cli exec <command> '<json>' --bridge 9877`. Headless render: `effectcraft-cli render --comp <name> --out out.mp4`.
- Add `--gpu` to the headless server to render on the GPU.

## First demo

Create a new 1920x1080, 5-second comp. Add a text layer with the user's name or handle, centered. Animate it in over the first second: opacity 0→100, scale 80→100%, position slightly from below, Easy Ease on the last keys. Add a subtle Glow. Play it in the window, then render a frame at 1.5 s and look at it.

## Starter tasks

1. Make a lower third: my name and title slide in from the left, hold 3 s, slide out. Export ProRes 4444 with alpha.
2. Logo reveal: put my logo (I'll give you the file) on a dark background, burst of particles + glow on the reveal, 4 s, export MP4.
3. 10-second kinetic typography of this quote: "<your quote>", with a slow 3D camera push. Then run the Motion Studio stack to add sound.
