# GridCraft → Microsoft Excel

- **Good for:** spreadsheets: formulas, formats, conditional rules, charts, frozen panes; .xlsx. MCP tools include `read_range`, `write_range`, `set_cell`, `evaluate_formula`.
- **Stage:** alpha · team estimate ~50% ready for real work (Oct 2026; the current number is in the README "Status" / ROADMAP).
- **Repo:** https://github.com/storytold/gridcraft · **Page:** https://getartcraft.com/apps/gridcraft
- **CLI:** `gridcraft-cli` (macOS: separate `gridcraft-cli-<ver>-macos-universal.zip`; Windows: `C:\Program Files\GridCraft\gridcraft-cli.exe`; Linux: `/usr/bin/gridcraft-cli`)

## Connect

```
"$CLAUDE" mcp add --scope user gridcraft -- "$CLI" mcp
"$CLAUDE" mcp add --scope user gridcraft-app -- "$CLI" mcp --connect 7979
```

- **Live mode:** start the app with `--sample budget --control 7979` (port 7979), then the `gridcraft-app` server bridges to it.
- **macOS executable:** `/Applications/GridCraft.app/Contents/MacOS/<check with ls>`
- **Reopen later (macOS):** `nohup "/Applications/GridCraft.app/Contents/MacOS/<check with ls>" --sample budget --control 7979 >/dev/null 2>&1 &`  (Windows: run the app's .exe in its install folder with `--sample budget --control 7979`)

## Notes

- No VBA/macros.
- XLSX fidelity on real-world files is still being improved.
- Port 7979 is shared with VectorCraft, CADCraft and DesignCraft: run one at a time.

## First demo

In the sample budget, add a 'Remaining' column with a formula, color it red/green with a conditional rule, add a bar chart of budget vs actual, and take a screenshot.

## Starter tasks

1. Import this CSV, clean it, and build a monthly summary with a pivot-style table and a chart.
2. Build a personal budget with categories, totals and a color scale on % used.
3. Check this .xlsx for broken formulas and explain what each sheet does.
