# File Formats & Import/Export

Import/Export lives in the Spreadsheet window's Import / Export menus.

## Formats

| Format | Extension | Use | Notes |
|---|---|---|---|
| CSV | `.csv` | Tabular text | Header row, then data |
| TSV | `.tsv` | Tab-separated text | Same as CSV with tabs |
| JSON | `.json` | Structured / snapshots | |
| XLIFF 1.2 | `.xliff` | Localization → translation tools | Localization tables only |
| XLIFF 2.0 | `.xlf` | Localization → translation tools | Localization tables only |
| ScriptableObject | `.asset` | Export a table as a Unity asset | |
| Excel | `.xlsx` | Planner/translator handoff | *Planned* |

Each file holds **one table**. The table name is taken from the file name on import
(`[TableName]_[date].ext`).

## Import modes

When importing, you choose how it applies to the table:

* **Create New Table** — add a new table.
* **Merge** — combine the imported rows with the existing table (see Merge Rules below).
* **Overwrite** — replace the existing table's data. (Destructive.)

## Merge rules

On merge, AI Sheets compares imported rows against existing rows by key and resolves
automatically where it's safe:

* **Auto-skip** — the imported row is empty, or identical to the existing row (no prompt).
* **Auto smart-merge** — the imported row only fills cells that are empty in the existing row
  (no existing value is overwritten).
* **Conflict** — only when an imported value would overwrite a different existing value. These
  are shown in the Merge Conflicts window, where you can **Smart Merge / Skip / Overwrite**
  (per row or in bulk). Default is Smart Merge.

> Renaming a row's **key** on merge can break references (components/code that use that key).

## Google Sheets sync

You can push to and pull from **Google Sheets** directly from the editor, keeping a shared
team sheet in sync with your Unity tables.
