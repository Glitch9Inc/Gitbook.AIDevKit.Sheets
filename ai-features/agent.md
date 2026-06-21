# Spreadsheet Agent

The Spreadsheet Agent edits your sheet from a **natural-language task**. You describe what you
want; it plans and executes multiple steps using built-in tools.

Open it from the **side panel** in the [Spreadsheet Editor](../spreadsheet-editor/README.md).
Requires an AI provider/API key (see [Providers & API Keys](providers.md)).

## Example tasks

* "Fill all missing Korean translations."
* "Generate 20 item entries following this schema."
* "Find rows where damage > 100 and tag them."

## Built-in tools

The agent operates through a fixed tool set, so its actions are predictable:

**Table / data**
`ListTables` · `GetSheetSchema` · `GetRowData` ·
`InsertRow` · `UpdateRow` · `UpdateCell` · `UpdateColumn` · `DeleteRow` ·
`CreateColumn` · `CreateRows` · `DeleteColumn`

**Database**
`AnalyzeColumn` · `BulkUpdate` · `ValidateConstraints`

**Localization**
`FindMissingTranslations` · `GenerateTranslations`

## Tips

* Be specific about the target (which table/columns/rows).
* Review the agent's changes — they go through the normal edit pipeline and are undoable.
* For one-off generation/translation, the dedicated actions
  ([Content Generation](content-generation.md), [AI Translation](translation.md)) are simpler.
