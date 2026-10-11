# SoundCraft → Avid Pro Tools

- **Good for:** a DAW: multitrack editing, mixer with plugins, sends and automation, MIDI, recording, bouncing. `session.inspect` reports exactly what changed, so you can check your own work.
- **Stage:** pre-alpha · team estimate ~40% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/soundcraft · **Page:** https://getartcraft.com/apps/soundcraft
- **CLI:** `soundcraft-cli` (macOS: separate `soundcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\SoundCraft\soundcraft-cli.exe`; Linux: `/usr/bin/soundcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user soundcraft -- "$CLI" mcp --demo
"$CLAUDE" mcp add --scope user soundcraft-app -- "$CLI" mcp --connect 7801
```

- **Live mode:** start the app with `--demo --control 7801` (port 7801), then the `soundcraft-app` server bridges to it.
- **macOS executable:** `/Applications/SoundCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/SoundCraft.app/Contents/MacOS/<check with ls>" --demo --control 7801 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--demo --control 7801`)

## Notes

- Pre-alpha: translations missing, some workflows incomplete.
- Programmatic calls never open dialogs.
- Quick CLI against the live app: `soundcraft-cli app --port 7801 transport.play`, `soundcraft-cli app --port 7801 ui.screenshot '{"path":"shot.png"}'`.
- Headless bounce: `soundcraft-cli run --demo --cmd 'mix.volume={"track":"Kick","db":-6}' --bounce mix.wav`.

## First demo

In the demo session: turn the Kick down 6 dB, put a 7-band EQ on the Bass, start playback, and take a screenshot of the mixer.

## Starter tasks

1. Level this voice-over (I'll give the file): clean up, EQ, compress, normalize to -16 LUFS, bounce WAV.
2. Build a 30-second music bed from these stems with a fade-in and a hard stop at 0:30.
3. Mix my motion video's sound: duck the music under the voice and bounce a stereo mix.
