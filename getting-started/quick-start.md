# Quick Start

A 5-minute tour: open the editor, make a table, and use the data at runtime.

## 1. Open the editor

`Window > AI Sheets > Spreadsheet`  (shortcut: **Ctrl/Cmd + Shift + T**)

Create a table and pick a category:

* **Localization** — a key column + one column per language.
* **Database** — a key column + typed columns (string, int, enum, Sprite, …).

Edit it like a normal spreadsheet: typed columns, multi-select, copy/paste, find & replace.

## 2. Localization at runtime

```csharp
using Glitch9.AI.Sheets;

await Localization.InitializeAsync();        // load tables once
Localization.CurrentLocale = Locale.Korean;  // switch language

string title  = "menu.title".Tr();           // fluent translation
string apples = "apple".Tr().Count(3).ToString();
```

Or drop a **TextLocalization** component on a UI Text / TextMeshPro object and set its key —
no code needed. It updates automatically when the locale changes.
See [Localization → Unity Components](../localization/components.md).

## 3. Database at runtime

Generate a C# model class from your Database table (in the editor), then load and query it:

```csharp
using Glitch9.AI.Sheets;

var sheet = await Database.LoadAsync<ItemModel>("items", source); // load + register
if (Database.TryGet<ItemModel>("items", "sword", out var sword))
    Debug.Log(sword.Name);
```

See [Database → Runtime API](../database/runtime-api.md) for sources and model generation.

## 4. AI features

* **Generate** rows and cells from natural-language prompts.
* **Translate** missing localization cells.
* **Spreadsheet Agent** — describe a task in plain language and let it edit the sheet.

These require an AI provider/API key — see [Providers & API Keys](../ai-features/providers.md).

## Next steps

* [Core Concepts](core-concepts.md) — the table model and editor-vs-runtime split.
* [Spreadsheet Editor](../spreadsheet-editor/README.md) — editing, import/export.
