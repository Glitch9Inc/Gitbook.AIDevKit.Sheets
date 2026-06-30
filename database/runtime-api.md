# Database — Runtime API

All runtime types live in the `Glitch9.AI.Sheets` namespace. The entry point is the static
`Database` facade.

> This is the **manual / low-level** path: you load tables yourself and register them under a
> `sheetId` string you choose. For the generated, zero-boilerplate path (typed `GameDB.*` accessors +
> a Database Manager component), see [GameDB & Database Manager](gamedb.md).

> There is **no global initialization** for this path — tables are loaded on demand.

## Load & register a table

```csharp
using Glitch9.AI.Sheets;

// Load a table from a source and register it under "items".
DatabaseSheet<ItemModel> sheet = await Database.LoadAsync<ItemModel>("items", source);
```

* `ItemModel` is the C# model class generated from your Database table (see the
  [Database overview](README.md)).
* `"items"` is the **sheetId** — your handle for later lookups (the same model type can back
  several tables, so the id, not the type, is the key).
* `source` is an `ITableSource` (see **Sources** below).
* Optional: `Database.LoadAsync<ItemModel>("items", source, loadAllObjectReferences: false)` defers
  loading of asset references (Sprites, AudioClips, …) until you ask for them.

You can also register an already-built sheet:

```csharp
Database.Register("items", sheet);
```

## Query rows

```csharp
if (Database.TryGet<ItemModel>("items", "sword", out var sword))
    Debug.Log(sword.Name);

// Throws if the sheet isn't registered (or wrong type) or the key is missing:
ItemModel required = Database.GetRequired<ItemModel>("items", "sword");

DatabaseSheet<ItemModel> items = Database.GetSheet<ItemModel>("items");

bool loaded = Database.IsRegistered("items");
Database.Unregister("items");
```

## Sources

A table is loaded from an `ITableSource`:

| Source | From |
|---|---|
| `AssetTableSource` | A `SheetTableAsset` — the in-project (offline) table asset |
| `CsvTableSource` / `TsvTableSource` / `JsonTableSource` | A CSV / TSV / JSON `TextAsset`, file path, or URL |
| `GoogleSheetSource` | A Google Sheet (spreadsheet id + sheet name) |

When you use [GameDB](gamedb.md), these sources are built for you from each table's settings
(`GameDbConfig.CreateSource`), so you rarely construct them by hand.

## Typed values & AOT note

Cell values map to your model's field types (primitives, enums, Unity types, localized
references). On IL2CPP/AOT platforms (consoles, iOS, WebGL), prefer the generated model
classes and test on-device — runtime reflection paths can be stripped.

## Errors

* `DatabaseLoadException` — the source could not be loaded/parsed.
* `DatabaseModelBuildException` — a row could not be mapped to the model type.
