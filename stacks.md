# Stacks

Install every app in a stack in one go (steps 4-7 of SETUP.md for each), then run the stack's
first demo instead of the per-app ones.

## Motion Studio: EffectCraft + SoundCraft + FilmCraft

Animate, add real sound, cut and export.

Bonus: the sound pass uses **opus-sound-layer** (real CC0 SFX placed from the animation's own
timing, checked by a QA loop): https://github.com/Bodila51/opus-sound-layer

First demo:
1. EffectCraft: 6-second title animation with the user's name (see `apps/effectcraft.md`).
   Render it muted: `effectcraft-cli render --comp <name> --out ~/craft-work/motion/video.mp4`.
2. Sound: `git clone https://github.com/Bodila51/opus-sound-layer ~/craft-work/motion/sound-layer`,
   read its `PROMPT.md` and follow it, working in `~/craft-work/motion`. The picture's timing comes
   from the EffectCraft comp: read the keyframe times with the MCP tools (`get_comp`, keyframes)
   instead of guessing frames.
3. FilmCraft or SoundCraft (optional): open the final MP4 for a last trim or level pass.
4. Deliver `~/craft-work/motion/out/final.mp4` and tell the user where it is.

## Designer: PhotoCraft + VectorCraft + DesignCraft

Image, vector logo, layout.

First demo: VectorCraft draws a logo mark (SVG), PhotoCraft makes a 1500x500 header with it,
DesignCraft places both on a one-page flyer and exports PDF. Work in `~/craft-work/designer`.
VectorCraft and DesignCraft share port 7979: open them in live mode one at a time.

## Office: WordCraft + GridCraft + DeckCraft + PdfCraft

Docs, sheets, slides, PDFs.

First demo: GridCraft builds a small table with a chart from sample numbers, DeckCraft makes a
3-slide summary with that chart, WordCraft writes a one-page memo, PdfCraft combines the memo and
slides into one PDF. Work in `~/craft-work/office`.
