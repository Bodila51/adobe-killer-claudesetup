# adobe-killer-claudesetup

**One prompt that connects Claude Code to 12 free, open-source alternatives to Adobe, Office and
CAD apps, and lets it drive them while you watch.**

The apps are made by the [ArtCraft](https://github.com/storytold) team: open source (MIT /
Apache-2.0), native on macOS, Windows and Linux, and every one ships an MCP server. This repo
is the setup layer: it asks what you want, installs only that, connects it to Claude Code, and
shows you a first result in the live app window.

## Get the prompt

Paste this into Claude Code:

```
CRAFT SETUP · Claude Code
Free, open-source Adobe & Office alternatives (ArtCraft apps,
github.com/storytold), installed and connected to you over MCP.

SETUP  git clone https://github.com/Bodila51/adobe-killer-claudesetup ~/.craft-setup
(already there? git -C ~/.craft-setup pull)

RUN  Read ~/.craft-setup/SETUP.md and follow it exactly. That repo is
the source of truth and changes over time: never work from memory of
an older version.

1 ASK  Show me the menu, explain each app in one line, let me pick.
Install only what I choose.

2 INSTALL  Latest release, checksum verified, CLI + MCP connected,
live window so I can watch you work.

3 SHOW  Do the first demo in the open window, check your own result,
then give me 3 starter tasks and the /craft commands.

If a permission blocks a command, don't work around it: give me the
exact line to paste into my terminal.
```

## What happens

1. Claude checks your machine (OS, CPU, disk, what's already installed).
2. It shows the menu below and asks what you want: one app, a stack, or a task in your own words.
3. It downloads the latest release for your OS, verifies the SHA-256, installs it, and gets the CLI.
4. It registers two MCP servers: `<app>` (headless, no window) and `<app>-app` (drives the open window).
5. It opens the app in live mode, does a first demo while you watch, and checks its own result.
6. It installs a `/craft` command so you never need this page again.

## The apps

| # | App | Replaces | Stage* |
|---|---|---|---|
| 1 | [EffectCraft](https://github.com/storytold/effectcraft) | After Effects | alpha · ~45% |
| 2 | [FilmCraft](https://github.com/storytold/filmcraft) | Premiere Pro | alpha · ~56% |
| 3 | [SoundCraft](https://github.com/storytold/soundcraft) | Pro Tools | pre-alpha · ~40% |
| 4 | [PhotoCraft](https://github.com/storytold/photocraft) | Photoshop | alpha · ~45% |
| 5 | [LightCraft](https://github.com/storytold/lightcraft) | Lightroom | alpha · ~61% |
| 6 | [VectorCraft](https://github.com/storytold/vectorcraft) | Illustrator | alpha · ~62-65% |
| 7 | [DesignCraft](https://github.com/storytold/designcraft) | InDesign | pre-alpha · ~47% |
| 8 | [WordCraft](https://github.com/storytold/wordcraft) | Word | alpha · ~60% |
| 9 | [GridCraft](https://github.com/storytold/gridcraft) | Excel | alpha · ~50% |
| 10 | [DeckCraft](https://github.com/storytold/deckcraft) | PowerPoint | alpha · ~55% |
| 11 | [PdfCraft](https://github.com/storytold/pdfcraft) | Acrobat | alpha · ~49% |
| 12 | [CADCraft](https://github.com/storytold/cadcraft) | AutoCAD | pre-alpha · ~38% |

\* The team's own "ready for real work" estimate from each README / ROADMAP, October 2026.

**Stacks:** Motion Studio (EffectCraft + SoundCraft + FilmCraft, with real sound via
[opus-sound-layer](https://github.com/Bodila51/opus-sound-layer)) · Designer (Photo + Vector +
Design) · Office (Word + Grid + Deck + Pdf). See [stacks.md](stacks.md).

## After setup: `/craft`

| Command | Does |
|---|---|
| `/craft add filmcraft` | install and connect another app (or `add motion` for a stack) |
| `/craft open effectcraft` | open the app in live mode so Claude can drive the window |
| `/craft tasks photocraft` | 3 ready-made tasks to try |
| `/craft doctor` | check every app, fix broken connections |
| `/craft update` | install newer releases |
| `/craft remove <app>` | uninstall the app and its connection (asks first) |

Live mode works only when the app is opened by `/craft open` (or the command Claude gives you),
not by double-clicking it: the window needs its control port.

## Good to know

- All apps are **alpha or pre-alpha**. Great for personal work and experiments; not for client
  deadlines. No .aep / .prproj import, no Adobe plugins.
- Claude works on copies of your files in `~/craft-work/`, never on the originals.
- Not affiliated with or endorsed by Adobe, Microsoft, Autodesk or Avid. Product names are used
  only to describe what each open-source app is an alternative to.
- How it works: [SETUP.md](SETUP.md) (what Claude follows), one file per app in [apps/](apps/).

Something failed? [Open an issue](https://github.com/Bodila51/adobe-killer-claudesetup/issues/new?template=install-problem.md)
with your OS and the error.

By [@0xCodila](https://x.com/0xCodila) · MIT
