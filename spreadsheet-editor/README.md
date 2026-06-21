# Spreadsheet Editor

Open it with `Window > AI Sheets > Spreadsheet` (**Ctrl/Cmd + Shift + T**).

## Window layout

* **Menu / Toolbar** — table selector, category switch, import/export, AI actions, undo/redo.
* **Grid** — the table; edit cells inline, multi-select, copy/paste.
* **Side panel** — selection details, generation actions, and the Spreadsheet Agent.

> 📷 **Image — `window-layout.png`:** The Spreadsheet window with callout labels on the
> Menu/Toolbar, the grid, and the side panel.

## Editing tables

* **Create** tables from the New Table dialog (choose Localization or Database).
* **Columns** — add/remove and set each column's data type (Column Manager).
* **Rows / Cells** — add, insert, delete, sort by key; edit cells inline.
* **Find, Replace, Selection** — search/replace and multi-cell bulk operations.
* **Cell notes & version history** — annotate cells and restore previous values.
* **Undo / Redo** — explicit edits are undoable (toolbar, shortcuts, or `Edit > Undo`).

## Import & Export

Round-trip your data through:

| Format | Notes |
|---|---|
| CSV / TSV | Plain tabular text |
| JSON | Structured; also used for snapshots |
| XLIFF (1.2 / 2.0) | Localization only; for professional translation tools |
| ScriptableObject | Export a table as a `.asset` |
| Excel (.xlsx) | *Planned* |

Imports can **create a new table, merge, or overwrite**. See
[File Formats & Import/Export](../reference/file-formats.md) for details and merge rules.

You can also sync with **Google Sheets** (push/pull) directly from the editor.

## AI in the editor

* [Content Generation](../ai-features/content-generation.md) — fill rows/cells from prompts.
* [AI Translation](../ai-features/translation.md) — fill missing localization cells.
* [Spreadsheet Agent](../ai-features/agent.md) — natural-language, multi-step edits.

## Registries (Window > AI Sheets)

* **Tables** — all registered tables.
* **Enum Types** — enums usable as column types.
* **JSON Classes** — custom JSON class column types.
* **Contextual Keys (Localization)** — context hints that improve AI translation/generation.
