# Spreadsheet Editor

The **Spreadsheet Editor** is a powerful UIToolkit-based editor window for managing table data in Unity.

## Opening the Editor

Access the spreadsheet editor:
* `Window > AI Dev Kit > Sheets Editor`
* Keyboard shortcut: `Ctrl+Shift+S` (Windows) / `Cmd+Shift+S` (Mac)

## Interface Overview

```
┌────────────────────────────────────────────────────────┐
│  Toolbar: [Table ▼] [+] [Settings] [Import] [Export]  │
├────────────────────────────────────────────────────────┤
│  Header: [#] [Key] [Name] [Type] [Value] [...]        │
├────────────────────────────────────────────────────────┤
│  Rows:                                                 │
│  1  | key_1  | Item Name | Type  | Value              │
│  2  | key_2  | Item Name | Type  | Value              │
│  3  | key_3  | Item Name | Type  | Value              │
│  ...                                                    │
├────────────────────────────────────────────────────────┤
│  Bottom Bar: [Add Row] [Selected: 3] [Status]         │
└────────────────────────────────────────────────────────┘
```

## Table Management

### Creating a New Table

1. Click the `+` button in the toolbar
2. Enter table information:
   * **Name**: Unique table identifier (e.g., "GameItems")
   * **Category**: Table category for organization
   * **Description**: Optional description
3. Click `Create`

### Switching Tables

* Use the **Table Dropdown** in the toolbar
* Recently used tables appear at the top
* Search by name to filter tables

### Table Settings

Right-click on table dropdown → `Settings`:
* **Auto-save**: Automatically save on changes
* **Validation**: Enable/disable data validation
* **Version**: Table schema version

## Column Operations

### Adding Columns

1. Click `Add Column` in the header
2. Configure column properties:
   * **Name**: Column display name
   * **Type**: Data type (Text, Number, Localization, etc.)
   * **Required**: Whether values are mandatory
   * **Default Value**: Default for new rows
3. Click `OK`

### Column Types

| Type | Description | Example |
|------|-------------|---------|
| **Text** | Plain text values | "Sword", "Magic Potion" |
| **Number** | Integer or float | 100, 25.5 |
| **Boolean** | True/false values | true, false |
| **Enum** | Predefined options | Rarity.Common, Rarity.Rare |
| **Localization** | Multi-language text | {en: "Hello", ko: "안녕"} |
| **Asset Reference** | Unity asset path | "Sprites/sword_icon" |
| **Color** | RGBA color values | #FF0000, rgba(255,0,0,1) |

### Reordering Columns

* **Drag header** to reorder columns
* Visual feedback during drag
* Drop indicator shows insert position

### Editing Column Properties

* **Right-click header** → `Edit Column`
* Modify name, type, or constraints
* Changes apply to entire column

### Deleting Columns

* **Right-click header** → `Delete Column`
* Confirmation dialog appears
* **Warning**: Data in that column will be lost

## Row Operations

### Adding Rows

* Click `Add Row` button at bottom
* New row appears at end of table
* Auto-generates unique key (or enter manually)

### Selecting Rows

* **Click row number** to select entire row
* **Shift+Click** to select range
* **Ctrl+Click** to add/remove from selection

### Editing Rows

* **Double-click cell** to enter edit mode
* **Tab** to move to next cell
* **Shift+Tab** to move to previous cell
* **Enter** to confirm and move down
* **Esc** to cancel editing

### Deleting Rows

* Select rows
* Press `Delete` key or right-click → `Delete Rows`
* Undo available (`Ctrl+Z`)

### Duplicating Rows

* Select row(s)
* Right-click → `Duplicate Row(s)`
* New key auto-generated

## Cell Operations

### Editing Cells

* **Single-click** to focus
* **Double-click** to edit
* **Click away** to confirm changes

### Cell Selection

* **Click cell** for single selection
* **Shift+Click** to select range
* **Ctrl+Click** for multi-select
* **Ctrl+A** to select all

### Copy/Paste

* **Ctrl+C**: Copy selected cells
* **Ctrl+V**: Paste into selected cells
* **Ctrl+X**: Cut selected cells
* Supports Excel/Google Sheets format

### Cell Validation

Visual indicators for validation:
* ✅ **Green border**: Valid data
* ⚠️ **Yellow border**: Warning (non-critical)
* ❌ **Red border**: Error (requires fix)

## Column Selection

### Selecting Entire Columns

* **Click column header** to select all cells in column
* **Shift+Click headers** to select column range
* **Ctrl+Click headers** to multi-select columns

Visual feedback:
* Selected column headers are highlighted
* All cells in selected columns show selection state

### Operations on Selected Columns

Once columns are selected:
* **Delete**: Remove all selected columns
* **Copy**: Copy column data
* **Export**: Export selected columns only
* **Apply Format**: Batch format changes

## Keyboard Shortcuts

### Navigation
* `Arrow Keys` - Move cell focus
* `Tab` - Next cell
* `Shift+Tab` - Previous cell
* `Home` - First cell in row
* `End` - Last cell in row
* `Ctrl+Home` - First cell in table
* `Ctrl+End` - Last cell in table

### Editing
* `F2` - Enter edit mode
* `Enter` - Confirm edit and move down
* `Esc` - Cancel edit
* `Delete` - Clear cell content

### Selection
* `Ctrl+A` - Select all cells
* `Shift+Arrow` - Extend selection
* `Ctrl+Click` - Add to selection

### Commands
* `Ctrl+Z` - Undo
* `Ctrl+Y` - Redo
* `Ctrl+C` - Copy
* `Ctrl+V` - Paste
* `Ctrl+X` - Cut
* `Ctrl+S` - Save table

## Context Menus

### Cell Context Menu
Right-click on cell:
* Copy Cell
* Paste
* Clear Cell
* Insert Row Above
* Insert Row Below
* Delete Row

### Header Context Menu
Right-click on header:
* Edit Column
* Insert Column Left
* Insert Column Right
* Delete Column
* Sort Ascending
* Sort Descending
* Auto-fit Width

### Row Context Menu
Right-click on row number:
* Copy Row
* Duplicate Row
* Insert Row Above
* Insert Row Below
* Delete Row
* Move to Top
* Move to Bottom

## Search and Filter

### Search Box
* Located in toolbar
* Real-time filtering as you type
* Searches across all columns
* Use `Esc` to clear search

### Advanced Filters
Click filter icon in header:
* **Equals**: Exact match
* **Contains**: Substring match
* **Starts With**: Prefix match
* **Ends With**: Suffix match
* **Is Empty**: Find empty cells
* **Is Not Empty**: Find filled cells

## Undo/Redo System

All operations are undoable:
* Single-step history per command
* Undo: `Ctrl+Z`
* Redo: `Ctrl+Y`
* History limit: 100 operations

Undoable operations:
* Cell edits
* Row/column add/delete
* Column reorder
* Copy/paste
* Bulk operations

## Performance Tips

For large tables (1000+ rows):

1. **Enable Virtualization** (automatic for 100+ rows)
2. **Use Search/Filter** to reduce visible rows
3. **Minimize Active Selection** (avoid selecting all)
4. **Close Other Editor Windows** if experiencing lag

## Next Steps

* [Cell Selection](cell-selection.md) - Advanced selection techniques
* [Column Management](column-management.md) - Deep dive into columns
* [Import/Export](import-export.md) - Working with external data
