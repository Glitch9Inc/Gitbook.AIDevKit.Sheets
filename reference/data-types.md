# Supported Data Types

Each **column** has a data type; a cell's value is interpreted by its column's type.

## Primitive types

`string`, `int`, `long`, `float`, `double`, `bool` — edited inline and serialized as text in
CSV/TSV/JSON.

## Enum types

A column can be an **enum**. Register the enum in `Window > AI Sheets > Enum Types` so it is
selectable as a column type and editable via a dropdown.

### Enum columns in import headers

When importing (CSV/TSV/Google Sheets), a header can declare an enum column with a type token:

```
Type : Enum<NodeType>
Type : Enum<My.Namespace.NodeType>
```

The enum type name is resolved against the enums in your project's loaded assemblies:

* **Simple name** (`Enum<NodeType>`) — only **top-level public** enums are considered. Internal
  enums and enums nested inside other types are excluded, so enums buried in unrelated packages
  (Unity's own assemblies contain several enums with common names) cannot hijack the name. If
  several top-level public enums share the name, enums in your own code win over Unity/System
  assemblies.
* **Qualified name** (`Enum<My.Namespace.NodeType>`, `Enum<OuterClass.NestedEnum>`) — matched
  exactly by full name, and **internal and nested enums are allowed**. Use this form to target
  an internal or nested enum, or to disambiguate when multiple enums share a simple name.

If no matching enum is found, the column is imported as **String** — values are preserved as
plain text and a warning is logged. After adding (or registering) the enum in your project,
re-import to restore the column's Enum type.

## Unity types

Asset and value types are supported, including:

* `Sprite`, `Texture2D`, `AudioClip`, `Material`, generic `Object`
* `Vector2/3/4`, `Color`, `Gradient`, `AnimationCurve`

Asset columns reference project assets (and can be loaded via **Addressables** at runtime).

## Custom JSON classes

For structured data, a column can hold a **custom JSON class**. Register the class in
`Window > AI Sheets > JSON Classes`; a JSON Schema editor helps define the structure. The cell
stores JSON that deserializes to your type.

## Localized references

A Database column can store a **reference to a Localization key** (cross-reference). At runtime
the value resolves to the current locale's translation, so one row drives localized display
text without duplicating strings. See [Core Concepts → Cross-Reference](../getting-started/core-concepts.md).

## Notes

* For import/export, all values round-trip as text; types are restored from the column schema.
* When editing exported files in Excel, keep value columns formatted as **text** to avoid
  Excel auto-converting values (e.g. leading zeros, dates).
