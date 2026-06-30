# Quick Start

A 5-minute tour: open the editor, make a table, and use the data at runtime.

## 1. Open the editor

`Window > AI Sheets > Spreadsheet`  (shortcut: **Ctrl/Cmd + Shift + T**)

> 📷 **Image — `quickstart-window.png`:** The Unity `Window` menu open with `AI Sheets >
> Spreadsheet` highlighted, and the opened Spreadsheet window beside it.

Create a table and pick a category:

* **Database** — a key column + typed columns (string, int, enum, Sprite, …) for your game data.
* **Localization** — a key column + one column per language.

Edit it like a normal spreadsheet: typed columns, multi-select, copy/paste, find & replace.

## 2. Database at runtime

Generate a C# model class from your Database table (in the editor). Then either use the generated
**GameDB** facade with a Database Manager (recommended), or load tables yourself:

```csharp
using Glitch9.AI.Sheets;

// Recommended: mark the table for GameDB, generate, add a Database Manager to your scene, then:
if (GameDB.Items.TryGet("sword", out var sword))
    Debug.Log(sword.Name);

// Or load manually with the low-level Database API:
// "items" is the sheetId you choose; ItemModel is the generated model class.
var sheet = await Database.LoadAsync<ItemModel>("items", source);
if (Database.TryGet<ItemModel>("items", "sword", out var swordManual))
    Debug.Log(swordManual.Name);
```

See [GameDB & Database Manager](../database/gamedb.md) for the generated path, and
[Database → Runtime API](../database/runtime-api.md) for sources and the manual API.

## 3. Localize the display text

For text shown to players, use a Localization table.

```csharp
using Glitch9.AI.Sheets;

await Localization.InitializeAsync();         // load tables once
Localization.CurrentLocale = Locale.Korean;   // switch language

string title = "menu.title".Tr();             // fluent translation
```

Or drop a **TextLocalization** component on a UI Text / TextMeshPro object and set its key —
no code needed. A Database row can also **reference** a localization key for its display name
(Cross-Reference). See [Localization → Unity Components](../localization/components.md).

## 4. AI features

* **Generate** rows and cells from natural-language prompts.
* **Translate** missing localization cells.
* **Spreadsheet Agent** — describe a task in plain language and let it edit the sheet.

These require an AI provider/API key — see [Providers & API Keys](../setup/providers.md).

## Next steps

* [Core Concepts](core-concepts.md) — the table model and editor-vs-runtime split.
* [Spreadsheet Editor](../spreadsheet-editor/README.md) — editing, import/export.
