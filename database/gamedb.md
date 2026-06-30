# GameDB & Database Manager

**GameDB** is a generated, typed facade over your Database tables. Instead of loading each table by
hand, you mark the tables you want, generate a `GameDB` class, and drop a **Database Manager**
component in your scene. At runtime you read data through strongly-typed accessors:

```csharp
// GameDB is generated for you — accessor names and model types come from your tables.
DatabaseSheet<ItemModel> items = GameDB.Items;

if (GameDB.Items.TryGet("sword", out ItemModel sword))
    Debug.Log(sword.Name);
```

This is the recommended path. The low-level [`Database` API](runtime-api.md) is still available for
custom pipelines.

## 1. Mark tables & generate — Game Database Setup

Open **Window ▸ AI Sheets ▸ Game Database Setup** (the same window opens from a table's DB Model tab
via **Generate GameDB Code**, and from the **Database Manager** inspector via **Open Game Database
Setup**).

In that window you:

* Set the **DB Class Name** — the generated facade type. Use `GameDB` or a namespace-qualified name
  such as `MyGame.Data.GameDB`.
* For each Database table, set its membership:
  * **Include in GameDB** — expose this table through the facade.
  * **Accessor Name** — the name you'll use in code: `GameDB.<Accessor>` (must be a valid C#
    identifier).
  * **Load from Google Sheets (testing)** — load this table from its own Google Sheets settings
    instead of its offline asset while testing. **Turn this off before a release build.** It is only
    available when the table has Google Sheets configured (see
    [Google Sheets Sync](../spreadsheet-editor/google-sheets.md)).
* Press **Generate**.

> Membership is stored per table (it is the source of truth) and edited centrally here. The first
> time you generate, you choose where to save the generated `GameDB.cs` file.

**Generation is blocked** (the button is disabled, with the reason in its tooltip) when:

* no table is included, or
* an included table's model class isn't generated/validated yet.

This prevents emitting code that wouldn't compile. Fix the listed tables, then generate.

> 📷 **Image — `gamedb-setup-window.png`:** The Game Database Setup window — DB class name, the
> per-table include / accessor / online-loading list, and the Generate button.

## 2. Load at runtime — Database Manager

Add a **Database Manager** component (`Add Component ▸ AI Sheets ▸ Database Manager`) to a GameObject
in your first scene.

| Field | Meaning |
|---|---|
| **Auto-Initialize** | Load all GameDB tables on `Awake`. |
| **Initialize Localization First** | Initialize Localization before loading so localized (cross-referenced) fields resolve to the current locale. |
| **Don't Destroy On Load** | Keep the manager alive across scene loads (the database itself is static). |
| **On Initialized** | UnityEvent raised once all configured tables are loaded. |

The manager loads every table in [`GameDbConfig`](#gamedbconfig) into the static `Database` registry,
so `GameDB.*` works everywhere afterward. `DatabaseManager.IsReady` becomes `true` when loading
finishes.

```csharp
// Or drive it yourself instead of Auto-Initialize:
await GetComponent<DatabaseManager>().InitializeAsync();
```

You can also wait on the generated facade directly:

```csharp
if (GameDB.IsReady) { /* all GameDB tables are loaded */ }
await GameDB.LoadAllAsync();
```

## GameDbConfig

`GameDbConfig` is a generated artifact — a `ScriptableObject` singleton in **Resources** that the
Database Manager reads at runtime. **You don't edit it by hand;** it's rebuilt from your tables every
time you generate. It records, per table: the sheet id (the table asset's GUID), accessor and model
type, the offline source (the table asset), and — when *Load from Google Sheets* is on — a remote
source built from the table's Google Sheets settings.

At runtime `GameDbConfig.CreateSource(sheetId)` returns the remote source when online loading is
enabled for that table and a usable Google Sheets configuration exists, otherwise the offline source.

## Notes

* There is only **one** `GameDbConfig` per project (a Resources singleton). Generating updates that
  single config.
* The generated `GameDB` class references your model types by full name and registers its loader
  automatically — the Database Manager never needs a direct reference to it.
* On IL2CPP/AOT platforms, prefer the generated model classes and test on-device (see the
  [AOT note](runtime-api.md#typed-values--aot-note)).
