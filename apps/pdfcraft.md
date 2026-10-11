# PdfCraft → Adobe Acrobat

- **Good for:** PDF work: comments and highlights (highlight a phrase by naming it), fill and sign forms, organize/rotate/insert pages, combine, split, passwords, render pages to PNG.
- **Stage:** alpha · team estimate ~49% ready for real work (vs all of Acrobat Pro) (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/pdfcraft · **Page:** https://getartcraft.com/apps/pdfcraft
- **CLI:** `pdfcraft-cli` (macOS: separate `pdfcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\PdfCraft\pdfcraft-cli.exe`; Linux: `/usr/bin/pdfcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user pdfcraft -- "$CLI" mcp --root ~/craft-work/pdfcraft --compact
```

- **Live mode:** none over MCP (see notes).
- Create `~/craft-work/pdfcraft` first and expand `~` to an absolute path in the real command.

## Notes

- The MCP server is opt-in and runs headless only (stdio, no network port). `--root` confines it to one folder; `--compact` keeps the tool list small.
- No live MCP mode. To drive the open window, start it with `pdfcraft --control ~/.pdfcraft-control.json` and use `pdfcraft-cli ui --control ~/.pdfcraft-control.json inspect|click|key|command|drag …`.
- Edits stay in memory until `doc_save`; saving appends an incremental update, so original bytes are kept.
- Weak spots: no Office-to-PDF, Word export loses layout.

## First demo

Copy a PDF the user gives you into ~/craft-work/pdfcraft, highlight a key phrase, add a comment, render page 1 to PNG and show it.

## Starter tasks

1. Combine these PDFs in this order, add page numbers as labels, save one file.
2. Fill this PDF form with my details (I'll tell you) and save a copy.
3. Find every mention of "<term>" in this contract and highlight it with a comment.
