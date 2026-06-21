# Import & Export

Round-trip tables to and from files. Both live in the toolbar's **File** menu
(`Import From…` / `Export As…`).

> 📷 **Image — `import-export-menu.png`:** The File menu expanded, showing the Import From… and
> Export As… submenus with the format list (CSV/TSV/JSON/XLIFF/ScriptableObject).

## Formats

CSV, TSV, JSON, XLIFF (1.2 / 2.0), ScriptableObject. Excel (.xlsx) is planned. Each file holds
one table. See the full table and notes in [File Formats & Import/Export](../reference/file-formats.md).

## Export

`Export As… > <format>`, choose a location. The file name is `[TableName]_[date].ext`.

## Import

`Import From… > <format>`, pick a file, then choose how it applies:

* **Create New Table**
* **Merge** — combine with the existing table (see [Merge Rules](../reference/merge-rules.md))
* **Overwrite** — replace the table's data (destructive)

> 📷 **Image — `merge-conflicts.png`:** The Merge Conflicts window showing per-row
> Smart Merge / Skip / Overwrite options and the bulk-action buttons.

## Snapshots

`Save Snapshot` / `Load Snapshot` capture and restore a table's JSON state — useful as a quick
backup before large edits.
