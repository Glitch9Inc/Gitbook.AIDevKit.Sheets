# AIDevKit.Sheets

**AIDevKit.Sheets** is a powerful spreadsheet and localization management system for Unity 6 Editor.

## Key Features

* 📊 **Spreadsheet Editor**: High-performance spreadsheet editing interface built with UIToolkit
* 🌍 **Localization**: Multi-language management with automatic translation support
* 🔄 **Real-time Sync**: Integration with external data sources like Google Sheets
* 📝 **Code Generation**: Automated snippet generation for compile-time safety
* 🎨 **Custom Columns**: Extensible column type system

## Getting Started

```csharp
// Load sheet data
var sheet = await Sheet.LoadAsync("MyTable");
string value = sheet.Get("key");

// Use localization
string localizedText = LocalizationManager.GetText("greeting");
```

## System Requirements

* Unity 6.0 or higher
* UIToolkit support
* .NET Standard 2.1

## Quick Links

* [Installation Guide](getting-started/installation.md)
* [Core Concepts](core-concepts/overview.md)
* [Spreadsheet Editor](features/spreadsheet-editor.md)
* [API Reference](api-reference/sheet.md)