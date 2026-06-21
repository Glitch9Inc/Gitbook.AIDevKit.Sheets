# Core Concepts

## The table model

Everything is built on one structure:

```
Table
 ├─ Columns   (each has a name + data type)
 └─ Rows
     └─ Cells (one per column; value is interpreted by the column's data type)
```

* The **first column is the Key** — every row is identified by a unique key string.
* A **cell's value** is always interpreted according to its **column's data type**
  (string, int, float, bool, enum, Sprite, AudioClip, …). See [Supported Data Types](../reference/data-types.md).

## Two table categories

| | **Database** | **Localization** |
|---|---|---|
| Purpose | Model your game data | Localize display text |
| Columns | Typed columns (your schema) | One per language (Locale) |
| Value | Typed field values | Translated text per locale |
| Runtime entry point | `Database.LoadAsync<T>` / `TryGet` | `Localization` + `Tr()` / components |
| Typical use | Items, skills, quests, stats | UI strings, dialogue |

You choose the category when creating a table. **Database** is the primary data model;
**Localization** supplies the localized text that data and UI display.

## Cross-Reference (Database → Localization)

A Database cell can **reference a key in a Localization table** instead of storing raw text.
At runtime the value resolves to the current locale's translation. This is the main integration
point between the two: a single item row drives a localized display name without duplicating
strings — the dependency flows **Database → Localization**.

## Editor vs Runtime

* **Editor** (the Spreadsheet window): create/edit tables, AI generation & translation,
  import/export, and **C# class generation** for Database tables.
* **Runtime** (your game): load and read data through `Database`, and localized text through
  `Localization` / the localization components.

> C# model classes for Database tables are produced by the editor's code generator; at
> runtime you load tables *as* those generated types.

## Next steps

* [Database → Runtime API](../database/runtime-api.md)
* [Localization → Runtime API](../localization/runtime-api.md)
