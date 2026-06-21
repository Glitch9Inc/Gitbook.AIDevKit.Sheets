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

| | **Localization** | **Database** |
|---|---|---|
| Columns | One per language (Locale) | Typed columns (your schema) |
| Value | Translated text per locale | Typed field values |
| Runtime entry point | `Localization` + `Tr()` / components | `Database.LoadAsync<T>` / `TryGet` |
| Typical use | UI strings, dialogue | Items, skills, quests, stats |

You choose the category when creating a table.

## Cross-Reference (Database → Localization)

A Database cell can **reference a key in a Localization table** instead of storing raw text.
At runtime the value resolves to the current locale's translation. This lets a single item
row drive localized display names without duplicating strings.

## Editor vs Runtime

* **Editor** (the Spreadsheet window): create/edit tables, AI generation & translation,
  import/export, and **C# class generation** for Database tables.
* **Runtime** (your game): load and read the data through `Localization` and `Database`,
  or via the localization components.

> C# model classes for Database tables are produced by the editor's code generator; at
> runtime you load tables *as* those generated types.

## Next steps

* [Localization → Runtime API](../localization/runtime-api.md)
* [Database → Runtime API](../database/runtime-api.md)
