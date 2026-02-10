# Quick Start

This guide will help you create and manage your first sheet in AIDevKit.Sheets.

## Creating Your First Sheet

### Step 1: Open the Sheets Editor

1. In Unity Editor, go to `Window > AI Dev Kit > Sheets Editor`
2. The spreadsheet editor window will open

### Step 2: Create a New Table

1. Click the `+` button in the toolbar
2. Enter a name for your table (e.g., "GameItems")
3. Click `Create`

### Step 3: Add Columns

1. Click `Add Column` button in the header
2. Select column type (Text, Number, Localization, etc.)
3. Enter column name
4. Click `OK`

### Step 4: Add Rows

1. Click the `Add Row` button at the bottom
2. Fill in the data for each cell
3. Press `Enter` to confirm and move to the next cell

## Accessing Data in Code

Once you've created your sheet, you can access the data in your code:

```csharp
using Glitch9.AIDevKit.Sheets;
using UnityEngine;

public class SheetExample : MonoBehaviour
{
    async void Start()
    {
        // Load the sheet
        var sheet = await Sheet.LoadAsync("GameItems");
        
        // Get a value by key
        string itemName = sheet.Get("sword_name");
        Debug.Log($"Item Name: {itemName}");
        
        // Check if a key exists
        if (sheet.TryGet("sword_damage", out string damage))
        {
            Debug.Log($"Damage: {damage}");
        }
    }
}
```

## Working with Localization

For localized text, use the LocalizationManager:

```csharp
using Glitch9.AIDevKit.Sheets;

// Get localized text
string greeting = LocalizationManager.GetText("greeting");

// Change language
LocalizationManager.SetLocale(SystemLanguage.Korean);
```

## Next Steps

* [Project Setup](project-setup.md) - Configure advanced settings
* [Core Concepts](../core-concepts/overview.md) - Understand the system architecture
* [Spreadsheet Editor](../features/spreadsheet-editor.md) - Learn all editor features
