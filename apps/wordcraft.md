# WordCraft → Microsoft Word

- **Good for:** documents: ribbon, styles, tables, track changes, references, mail merge; reads and writes .docx. You can check work with `inspect_document` without screenshots.
- **Stage:** alpha · team estimate ~60% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/wordcraft · **Page:** https://getartcraft.com/apps/wordcraft
- **CLI:** `wordcraft-cli` (macOS: separate `wordcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\WordCraft\wordcraft-cli.exe`; Linux: `/usr/bin/wordcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user wordcraft -- "$CLI" mcp
"$CLAUDE" mcp add --scope user wordcraft-app -- "$CLI" mcp --connect 127.0.0.1:7981
```

- **Live mode:** start the app with `--control 7981` (port 7981), then the `wordcraft-app` server bridges to it.
- **macOS executable:** `/Applications/WordCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/WordCraft.app/Contents/MacOS/<check with ls>" --control 7981 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--control 7981`)

## Notes

- `wordcraft-cli mcp --author "<name>"` sets the author for tracked changes.

## First demo

Create a one-page document: title, two headings, a short table, styled; show it in the window and save as .docx in ~/craft-work/wordcraft.

## Starter tasks

1. Turn these notes into a formatted report with a table of contents, save .docx.
2. Review this .docx with tracked changes: tighten wording, fix grammar, leave comments.
3. Mail merge: make 20 personalized letters from this CSV.
