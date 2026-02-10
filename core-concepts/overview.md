# Overview

AIDevKit.Sheets is built on a modular architecture designed for flexibility, performance, and extensibility.

## Architecture Layers

```
┌─────────────────────────────────────────┐
│         Editor UI Layer (UIToolkit)     │
│  SpreadsheetWindow, Headers, Cells      │
└─────────────────────────────────────────┘
                    │
┌─────────────────────────────────────────┐
│         Command/Event System            │
│  SpreadsheetCommand, SpreadsheetEvent   │
└─────────────────────────────────────────┘
                    │
┌─────────────────────────────────────────┐
│         Data Management Layer           │
│  TableEntry, ColumnEntry, RowEntry      │
└─────────────────────────────────────────┘
                    │
┌─────────────────────────────────────────┐
│         Runtime Access Layer            │
│  Sheet, LocalizationManager             │
└─────────────────────────────────────────┘
                    │
┌─────────────────────────────────────────┐
│         Storage Layer                   │
│  ScriptableObjects, JSON, Resources     │
└─────────────────────────────────────────┘
```

## Core Components

### Sheet System
The **Sheet** class provides runtime read-only access to table data:
* Async loading with `Sheet.LoadAsync()`
* Type-safe data access with `Get()` / `TryGet()`
* Efficient O(1) dictionary lookups
* Contract validation for data integrity

[Learn more about Sheet System →](sheet-system.md)

### Table Registry
Central management system for all tables:
* Singleton pattern for global access
* ScriptableObject-based persistence
* Table metadata and versioning
* Editor-runtime data bridge

[Learn more about Table Registry →](table-registry.md)

### Column Types
Extensible type system for different data:
* Built-in types: Text, Number, Boolean, Enum
* Specialized types: Localization, Reference, Asset
* Custom column types via extension
* Type-specific cell rendering

[Learn more about Column Types →](column-types.md)

### Data Model
Hierarchical entry system:
* **TableEntry** - Table-level metadata and configuration
* **ColumnEntry** - Column definition and properties
* **RowEntry** - Row data and key mapping
* **CellId** - Unique cell identifier (RowId + ColumnId)

[Learn more about Data Model →](data-model.md)

## Design Patterns

### Command Pattern
All state mutations go through commands:
```csharp
SheetsEditor.DispatchCommand(new AddNewRowEntry(tableEntry, rowData));
```
* Undoable operations
* Operation history
* Batch command execution

### Event-Driven Updates
UI updates propagate through events:
```csharp
SheetsEditor.DispatchEvent(new ColumnWidthChanged(columnId, newWidth));
```
* Decoupled components
* Reactive UI updates
* Event handler registration

### Factory Pattern
UI element creation through factories:
```csharp
var cell = CellView.Create(rowEntry, columnEntry, cellManager);
```
* Polymorphic cell types
* Centralized creation logic
* Easy to extend

## Data Flow

### Editor → Runtime
```
User Edit in Editor
    → SpreadsheetCommand dispatched
    → TableEntry/RowEntry/ColumnEntry updated
    → ScriptableObject serialized
    → Runtime Sheet.LoadAsync() reads data
```

### Runtime → Game
```
Sheet.LoadAsync("MyTable")
    → Load TableSource from Resources
    → Build in-memory dictionary
    → Game code calls sheet.Get("key")
    → O(1) lookup returns value
```

## Key Principles

1. **Separation of Concerns** - Clear boundaries between layers
2. **Compile-time Safety** - Code generation for type-safe accessors
3. **Performance First** - Dictionary-based lookups, virtualized UI
4. **Extensibility** - Plugin-based column types and cell renderers
5. **Editor Experience** - Full undo/redo, keyboard shortcuts, drag-drop

## Next Steps

Dive deeper into specific components:
* [Sheet System](sheet-system.md) - Runtime data access
* [Table Registry](table-registry.md) - Central management
* [Column Types](column-types.md) - Type system
* [Data Model](data-model.md) - Entry hierarchy
