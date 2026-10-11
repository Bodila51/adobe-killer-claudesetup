# CRAFT SETUP · instructions for Claude Code

You are setting up the ArtCraft apps for the user: free, open-source (MIT / Apache-2.0)
desktop apps from https://github.com/storytold, each with a built-in MCP server you can drive.
This repo is cloned at `~/.craft-setup`. Its files are your instructions. Read only what each step
names.

## Rules (always)

- Talk in the user's language. One short line per step, no walls of text.
- Upstream is the source of truth: if an app's README on GitHub disagrees with a file here, follow
  the README and tell the user in one line.
- Never install anything the user didn't pick. Never skip the SHA-256 check.
- Never edit, move or overwrite the user's own files. To work on a user file, copy it into
  `~/craft-work/<app>/` first.
- Deleting anything (an app, a folder) needs the user's explicit "yes" in this conversation.
- If your permission settings block a command (for example `claude mcp add` or writing into
  `~/.claude`), do not work around it. Print the exact one-line command in a code block and ask the
  user to paste it into their terminal. Then continue.
- These apps are alpha / pre-alpha. Say it once, at the start, in one line: great for personal
  work and experiments, not for client deadlines.

## Modes

Run the mode the user asked for (or that `/craft <mode>` passed). No mode = `setup`.

| Mode | What to do |
|---|---|
| `setup` | Steps 1-8 below |
| `add <app or stack>` | Steps 1, 2, then 4-7 for that app or stack, skipping the menu |
| `open <app>` | Step 6a only: start the app in live mode and confirm the port answers |
| `list` | Show what's installed (step 2) |
| `doctor` | Step 2, then for each installed app: CLI runs, `claude mcp list` shows Connected, installed version vs latest release. Fix what's broken (reinstall CLI, re-register server). Report a short table |
| `update` | `doctor`, then install the newer release for any app that's behind (same steps 4-5) |
| `tasks <app>` | Show the "Starter tasks" from `apps/<app>.md` |
| `remove <app>` | Ask "yes" first. Then `claude mcp remove <app> --scope user` and `<app>-app`, delete `~/craft-apps/<app>`, and uninstall the app (macOS: move `/Applications/<App>.app` to Trash; Windows: `msiexec /x` or Settings > Apps; Linux: the package manager that installed it) |

## 1. Refresh

`git -C ~/.craft-setup pull --ff-only` (skip silently if offline).

## 2. Check the machine

- OS and CPU (`uname -sm`; on Windows `$env:PROCESSOR_ARCHITECTURE`).
- Free disk space: warn under 2 GB.
- The Claude Code binary for `claude mcp` commands: `claude` on PATH, otherwise the one bundled
  with the Claude desktop app (macOS: `ls ~/Library/Application\ Support/Claude/claude-code/*/*/claude.app/Contents/MacOS/claude`).
  Call it `$CLAUDE` from here on and use its full quoted path in every command you print.
- What's already there: `$CLAUDE mcp list`, `~/craft-apps/`, and the installed apps
  (macOS `/Applications/*Craft.app`, Windows `C:\Program Files\*Craft`, Linux `which <app>`).

## 3. Menu

Show this, then ask what they want to do (they can answer with a number, a stack, or a task in
their own words; if it's a task, recommend the app and ask to confirm). Mark already-installed
apps with ✓.

```
What do you want to make?

 MOTION & VIDEO
 1  EffectCraft  → After Effects   animation, 306 effects, 3D, ProRes/AV1 export
 2  FilmCraft    → Premiere Pro    edit, color, captions, mix, export
 3  SoundCraft   → Pro Tools       multitrack audio, mixer, plugins, bounce
 IMAGE & DESIGN
 4  PhotoCraft   → Photoshop       layers, masks, filters, smart objects, PSD
 5  LightCraft   → Lightroom       RAW develop, culling, masks, batch export
 6  VectorCraft  → Illustrator     vector drawing, effects, SVG/PDF/EPS
 7  DesignCraft  → InDesign        page layout, typography, PDF export
 OFFICE & CAD
 8  WordCraft    → Word            .docx, styles, tables, track changes
 9  GridCraft    → Excel           formulas, charts, .xlsx
10  DeckCraft    → PowerPoint      slides, themes, animations, .pptx
11  PdfCraft     → Acrobat         comment, fill forms, organize, sign
12  CADCraft     → AutoCAD         2D drafting, layers, dimensions, DXF

 STACKS (one go):  Motion Studio · Designer · Office   (see below)
```

For stacks, read `stacks.md` and show its one-line descriptions.

## 4. Install the app

For each chosen app, read `apps/<app>.md`, then the app's README sections "Downloads" and the
agents/MCP section (`https://raw.githubusercontent.com/storytold/<app>/HEAD/README.md`).

1. Latest release: `curl -sL https://api.github.com/repos/storytold/<app>/releases/latest`
   (on rate limit, use `gh release view -R storytold/<app>` or the releases page).
2. Pick the desktop build for this machine:
   macOS `<app>-<ver>-macos-universal.dmg` · Windows `<app>-<ver>-windows-<x64|arm64|x86>.msi` ·
   Linux `.deb` / `.rpm` / `.AppImage` for `x86_64` or `aarch64`.
3. Download into `~/craft-apps/<app>/downloads/`, download `SHA256SUMS.txt` from the same
   release, and check the hash (`shasum -a 256`, `sha256sum`, or `Get-FileHash`). Mismatch = stop.
4. Install: macOS mount the .dmg, copy the .app to `/Applications`, unmount. Windows
   `msiexec /i <file>` (asks the user to approve). Linux `sudo apt install ./<file>.deb` or
   `sudo dnf install ./<file>.rpm`, or make the AppImage executable.

## 5. Get the CLI (this is what MCP runs)

- macOS: the .app has **no** CLI. Download `<app>-cli-<ver>-macos-universal.zip` from the same
  release, check its hash, unzip into `~/craft-apps/<app>/bin/`. It's signed and notarized; the
  first run checks notarization online.
- Windows: `C:\Program Files\<App>\<app>-cli.exe` (not on PATH; use the full path).
- Linux deb/rpm: `/usr/bin/<app>-cli`. AppImage/tarball: see the README.

Run `<cli> --version` (or `--help`). Store the absolute path as `$CLI`.

## 6. Connect to Claude Code

Two servers per app, both at user scope so they exist in every session:

```
"$CLAUDE" mcp add --scope user <app>     -- "$CLI" mcp <headless args>
"$CLAUDE" mcp add --scope user <app>-app -- "$CLI" mcp <live args>
```

The exact args for each app are in `apps/<app>.md` ("Connect"). Headless = no window, works
everywhere. Live = drives the open app window, so the user can watch every change and you can take
screenshots. If an app has no live MCP mode, register only the headless one.

**6a. Live mode.** The app must be started from the terminal with its control flag, or the bridge
has nothing to connect to (double-clicking the app opens it *without* the port). Start it
detached, e.g. on macOS:
`nohup "/Applications/<App>.app/Contents/MacOS/<App>" <live start args> >/dev/null 2>&1 &`
(check the real name with `ls /Applications/<App>.app/Contents/MacOS/`).
Confirm the port listens (`lsof -iTCP:<port> -sTCP:LISTEN`, or `Test-NetConnection 127.0.0.1 -Port <port>`).
Several apps share port 7979: run only one of those at a time.

Then run `"$CLAUDE" mcp list` and confirm the servers say Connected.

## 7. Install the /craft command

Copy `~/.craft-setup/commands/craft.md` to `~/.claude/commands/craft.md` (create the folder if
needed). If blocked, print the one-line `mkdir -p ~/.claude/commands && cp …` command for the user.
Tell the user: from now on `/craft add filmcraft`, `/craft open effectcraft`, `/craft doctor`,
`/craft tasks photocraft`, `/craft remove <app>`.

## 8. First win, then hand off

1. MCP servers only load in a new session. If the `<app>-app` tools are not available to you right
   now, drive the open app through the CLI against the same port instead (`"$CLI" --help` shows
   how, usually `exec … --bridge/--connect <port>`), so the user still sees it happen.
2. Do the "First demo" from `apps/<app>.md` in the live window. Use the user's name or handle if
   they gave one. Tell them to look at the window.
3. Check your own result: take a screenshot or render a frame and look at it. Fix obvious problems
   (text off-frame, overlaps) once.
4. Finish with a short block:
   - what's installed and connected (one line per app),
   - the command to reopen the app in live mode,
   - "Start a new Claude Code session, then try:" + the 3 starter tasks from `apps/<app>.md`,
   - `/craft` commands.

Found a broken step? Report it: https://github.com/Bodila51/adobe-killer-claudesetup/issues
