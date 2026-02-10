# Sheet System

The **Sheet** class provides a runtime read-only interface for accessing table data in your game code.

## Core Concept

Sheet acts as a **Key-Value Database** optimized for read-heavy operations:
* Dictionary-based O(1) lookups
* Async loading from Resources
* Immutable after load
* Contract validation

## Loading Sheets

### Async Loading (Recommended)

```csharp
using Glitch9.AIDevKit.Sheets;
using UnityEngine;

public class GameManager : MonoBehaviour
{
    private Sheet m_ItemsSheet;
    
    async void Start()
    {
        // Load sheet by table name
        m_ItemsSheet = await Sheet.LoadAsync("GameItems");
        
        // Now safe to access data
        string swordName = m_ItemsSheet.Get("sword_name");
    }
}
```

### Sync Loading (Editor Only)

```csharp
#if UNITY_EDITOR
// Only use in editor tools, not in runtime game code
Sheet sheet = Sheet.LoadSync("GameItems");
#endif
```

## Accessing Data

### Get Methods

#### Get() - Throws if missing
```csharp
// Throws exception if key doesn't exist
string value = sheet.Get("my_key");
```

#### TryGet() - Safe check
```csharp
// Returns false if key doesn't exist
if (sheet.TryGet("my_key", out string value))
{
    Debug.Log($"Found: {value}");
}
else
{
    Debug.Log("Key not found");
}
```

#### GetRequired() - Contract validation
```csharp
// Validates required keys at load time
// Throws descriptive error if any key is missing
var requiredKeys = new[] { "sword_name", "sword_damage", "sword_price" };
sheet.GetRequired(requiredKeys);
```

## Data Contracts

Use contracts to ensure data integrity:

```csharp
public class ItemData
{
    public string Name { get; }
    public int Damage { get; }
    public int Price { get; }
    
    public ItemData(Sheet sheet, string keyPrefix)
    {
        // Define required keys - will throw if missing
        Name = sheet.GetRequired($"{keyPrefix}_name");
        Damage = int.Parse(sheet.GetRequired($"{keyPrefix}_damage"));
        Price = int.Parse(sheet.GetRequired($"{keyPrefix}_price"));
    }
}

// Usage
var sword = new ItemData(sheet, "sword");
```

## Type Conversion

Sheet returns strings - convert as needed:

```csharp
// Integer
int damage = int.Parse(sheet.Get("sword_damage"));

// Float
float weight = float.Parse(sheet.Get("sword_weight"));

// Boolean
bool isMagic = bool.Parse(sheet.Get("sword_is_magic"));

// Enum
ItemRarity rarity = System.Enum.Parse<ItemRarity>(sheet.Get("sword_rarity"));

// Asset Reference
string spritePath = sheet.Get("sword_sprite_path");
Sprite sprite = Resources.Load<Sprite>(spritePath);
```

## Key Naming Conventions

Establish consistent key patterns:

```csharp
// Pattern: {category}_{item}_{property}
"weapon_sword_name"
"weapon_sword_damage"
"weapon_axe_name"
"weapon_axe_damage"

// Pattern: {system}_{feature}_{setting}
"ui_button_color"
"ui_panel_size"
"audio_music_volume"
```

## Loading Multiple Sheets

```csharp
async void LoadAllSheets()
{
    // Load in parallel
    var itemsTask = Sheet.LoadAsync("GameItems");
    var enemiesTask = Sheet.LoadAsync("Enemies");
    var settingsTask = Sheet.LoadAsync("GameSettings");
    
    await Task.WhenAll(itemsTask, enemiesTask, settingsTask);
    
    var items = await itemsTask;
    var enemies = await enemiesTask;
    var settings = await settingsTask;
}
```

## Caching Strategy

```csharp
public class SheetCache : MonoBehaviour
{
    private static Dictionary<string, Sheet> s_Cache = new();
    
    public static async Task<Sheet> GetSheet(string tableName)
    {
        if (s_Cache.TryGetValue(tableName, out var cached))
            return cached;
        
        var sheet = await Sheet.LoadAsync(tableName);
        s_Cache[tableName] = sheet;
        return sheet;
    }
    
    public static void ClearCache()
    {
        s_Cache.Clear();
    }
}
```

## Performance Considerations

### ✅ Best Practices
* Load sheets once at scene start
* Cache Sheet instances
* Use TryGet() for optional keys
* Batch data access operations

### ❌ Avoid
* Loading sheets every frame
* Repeated Get() calls for same key (cache locally)
* Sync loading in runtime builds
* Large sheets without pagination

## Error Handling

```csharp
async Task<Sheet> SafeLoadSheet(string tableName)
{
    try
    {
        return await Sheet.LoadAsync(tableName);
    }
    catch (SheetNotFoundException ex)
    {
        Debug.LogError($"Sheet '{tableName}' not found: {ex.Message}");
        return null;
    }
    catch (System.Exception ex)
    {
        Debug.LogError($"Failed to load sheet '{tableName}': {ex.Message}");
        return null;
    }
}
```

## API Reference

| Method | Description | Throws |
|--------|-------------|--------|
| `LoadAsync(string)` | Load sheet by table name | SheetNotFoundException |
| `Get(string)` | Get value by key | KeyNotFoundException |
| `TryGet(string, out string)` | Safe get with bool return | No |
| `GetRequired(string)` | Get with contract validation | KeyNotFoundException |
| `ContainsKey(string)` | Check if key exists | No |

## Next Steps

* [Table Registry](table-registry.md) - Managing multiple tables
* [Data Model](data-model.md) - Understanding entries
* [Code Generation](../features/code-generation.md) - Type-safe accessors
