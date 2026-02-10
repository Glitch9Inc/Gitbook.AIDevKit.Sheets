# Project Setup

Configure AIDevKit.Sheets for your Unity project.

## Settings Location

Access the settings through:
* `Edit > Project Settings > AI Dev Kit > Sheets`

Or create a settings asset:
* `Assets > Create > Glitch9 > AIDevKit > Sheets Settings`

## Basic Configuration

### Data Storage Path

Configure where sheet data is stored:

```
Default: Assets/Resources/AIDevKit/Sheets/
```

You can change this path in the settings:
* `Data Path` - Root folder for all sheet data
* `Tables Path` - Subfolder for table definitions
* `Localization Path` - Subfolder for localization files

### Code Generation

Configure automatic code snippet generation:

* `Enable Code Generation` - Auto-generate type-safe accessors
* `Snippets Output Path` - Where generated code is saved
* `Namespace` - Root namespace for generated classes

Example:
```csharp
// Generated in Assets/Scripts/Generated/
namespace MyGame.Generated
{
    public static class GameItemsKeys
    {
        public const string SwordName = "sword_name";
        public const string SwordDamage = "sword_damage";
    }
}
```

## Localization Setup

### Supported Languages

Add languages in the settings panel:
1. Click `Add Language`
2. Select from SystemLanguage enum
3. Set default language

### Translation Services

Configure automatic translation:
* `Translation Provider` - Google Translate, DeepL, etc.
* `API Key` - Your translation service API key
* `Auto-translate` - Automatically fill missing translations

## Import/Export Settings

### Google Sheets Integration

Connect to Google Sheets for team collaboration:

1. Enable Google Sheets integration
2. Configure OAuth credentials:
   * `Client ID`
   * `Client Secret`
3. Set sync interval (manual, on save, automatic)

### CSV Import/Export

Configure CSV format preferences:
* `Delimiter` - Comma, Tab, Semicolon
* `Encoding` - UTF-8, UTF-16, etc.
* `Include Headers` - Export column names

## Performance Settings

### Caching

* `Enable Cache` - Cache loaded sheets in memory
* `Cache Size` - Maximum cached sheets
* `Cache Duration` - Time before automatic cleanup

### Editor Performance

* `Virtualized Scrolling` - For large tables (1000+ rows)
* `Lazy Loading` - Load rows on-demand
* `Max Visible Rows` - Limit rendered rows

## Best Practices

1. **Use Version Control** - Include generated code in VCS
2. **Separate Concerns** - Different tables for different systems
3. **Key Naming** - Use consistent naming conventions (e.g., `system_category_item`)
4. **Backup** - Regular backups before bulk operations

## Next Steps

* [Core Concepts Overview](../core-concepts/overview.md)
* [Sheet System Details](../core-concepts/sheet-system.md)
