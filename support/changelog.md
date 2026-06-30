# Changelog

## 1.0.0

Initial release.

* Spreadsheet editor in the Unity Editor (`Window > AI Sheets > Spreadsheet`).
* **Localization**: multi-language tables, `Localization` runtime API + `Tr()`, drop-in
  components (Text/Sprite/Texture/Material/Audio/Asset), `LocalizationManager`, realtime
  translation (AI / Google / Microsoft) with caching.
* **Database**: typed tables, C# model class generation (PureCSharp / ScriptableObject),
  the generated **GameDB** facade + **Database Manager** component (centralized membership in the
  **Game Database Setup** window, per-table accessor and *Load from Google Sheets* testing toggle),
  and the low-level `Database` runtime API (`LoadAsync` / `TryGet` / `GetSheet`).
* **AI**: content generation (rows/cells/image/audio/inpaint), AI translation, text revision,
  and the Spreadsheet Agent.
* **Import/Export**: CSV / TSV / JSON / XLIFF (1.2, 2.0) / ScriptableObject, Google Sheets sync,
  and merge rules with a conflict resolver.
