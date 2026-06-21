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
4. **Generate a C# model class** from the table (Database Table Settings / code generation):
   * **PureCSharp** model — a plain class.
   * **ScriptableObject** model — a `ScriptableObject` subclass.
5. Use that generated type at runtime to load the table.

> 📷 **Image — `database-table-codegen.png`:** A Database table with typed columns next to the
> class-generation UI (model type PureCSharp / ScriptableObject, namespace/class name).

## Cross-Reference to Localization

A Database column can reference keys in a **Localization** table, so a field (e.g. an item's
display name) resolves to the current locale automatically at runtime.

## Next

* [Database → Runtime API](runtime-api.md) — loading and querying.
