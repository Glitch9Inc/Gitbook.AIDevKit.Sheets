# Changelog

## [Unreleased]

### Added
- UIToolkit-based spreadsheet editor
- Command/Event architecture
- Fluent API localization system
- AI-powered real-time translation
- Voiced text localization
- Asset localization
- CSV/JSON import/export
- GameDB typed facade + Database Manager component (centralized membership in the Game Database Setup window)

### Changed
- Refactored `TrCallback` → `TrDeferred`
- ScriptableObject-based data structure
- `DateTime.Tr()` / `DayOfWeek.Tr()` now use .NET `CultureInfo` (no localization table required)

### Deprecated
- Legacy IMGUI editor

### Removed
- `TrCallback` (merged into TrDeferred)
- Built-in localization table (Resources asset) — time/date/weekday now come from `CultureInfo`
- `TimeSpan.Tr()` and `TrTimeSpanTask` (relative-duration localization). Format manually or use a library such as Humanizer.

### Fixed
- Editor performance optimization
- Memory leak fixes
