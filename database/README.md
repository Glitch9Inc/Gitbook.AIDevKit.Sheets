# Database

A Database table models structured game data — items, skills, quests, dialogue, stats — as a
**key column + typed columns** (your schema). You author it in the
[Spreadsheet Editor](../spreadsheet-editor/README.md), generate a C# model class from it, then
load and query the data at runtime.

## Editor workflow

1. Create a table with the **Database** category.
2. Define columns and their **data types** (string, int, float, bool, enum, Sprite, AudioClip,
   custom JSON class, localized reference, …). See [Supported Data Types](../reference/data-types.md).
3. Fill rows manually, with [AI generation](../ai-features/content-generation.md), or by import.
4. **Configure the C# model class** in the table's **DB Model** settings tab:
   * If no class is linked yet: **Generate New DB Model Class** (opens a popup to name it and pick a
     model type) or **Find Existing DB Model Class** (link a class you already wrote).
   * **PureCSharp** model — a plain class. **ScriptableObject** model — a `ScriptableObject` subclass.
   * Once linked, the tab shows the class info plus **Update DB Class** and **Generate GameDB Code**.
5. Load the table at runtime — either the **GameDB** typed facade (recommended) or the low-level
   `Database` API (manual). See below.

> 📷 **Image — `database-table-codegen.png`:** A Database table with typed columns next to the
> DB Model settings tab (model type PureCSharp / ScriptableObject, namespace/class name).

## Two ways to load at runtime

| Path | Best for | How |
|---|---|---|
| **GameDB facade** (recommended) | Zero-boilerplate typed access across many tables | Mark tables for GameDB, generate the `GameDB` class, add a **Database Manager** to your scene. See [GameDB & Database Manager](gamedb.md). |
| **`Database` API** (manual) | Custom loading pipelines, a single table, full control | Call `Database.LoadAsync<T>(sheetId, source)` yourself. See [Runtime API](runtime-api.md). |

Both share the same building blocks (`DatabaseSheet<T>`, `ITableSource`); GameDB just generates the
wiring for you.

## Cross-Reference to Localization

A Database column can reference keys in a **Localization** table, so a field (e.g. an item's
display name) resolves to the current locale automatically at runtime. When you load through the
**Database Manager**, enable *Initialize Localization First* so those fields resolve to the current
locale on load.

## Next

* [GameDB & Database Manager](gamedb.md) — the recommended, generated runtime path.
* [Runtime API](runtime-api.md) — loading and querying with the low-level `Database` facade.
