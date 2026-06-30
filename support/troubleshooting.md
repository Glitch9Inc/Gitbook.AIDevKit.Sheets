# Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Compile errors after import | Missing UniTask / Newtonsoft.Json | Install both dependencies |
| AI actions disabled or error | No provider/API key | Set a key in `Window > AI Sheets > Preferences` |
| `Tr()` returns the key or empty | Localization not initialized | Call `Localization.InitializeAsync()` or add a `LocalizationManager` |
| Localized text doesn't change with language | Locale not set / components not refreshed | Set `Localization.CurrentLocale`; ensure components are active |
| `Database.TryGet` returns false | Table not loaded/registered, or wrong sheetId/key | `await Database.LoadAsync<T>(sheetId, source)` first; check ids |
| `GameDB.*` throws "not registered" / data is empty | No Database Manager in the scene, or GameDB wasn't regenerated after changes | Add a **Database Manager**; re-open **Game Database Setup** and **Generate** |
| `Generate` is disabled in Game Database Setup | No table included, or an included table's model class isn't generated/validated | Include ≥1 table and generate/find each model class (button tooltip lists the cause) |
| Database works in editor but not on device | IL2CPP/AOT stripping of reflection paths | Use generated model classes; test on-device |
| Generated image/audio not removed by Undo | External asset files are outside Unity Undo | Delete generated assets manually |
| Import created the wrong table name | Name is taken from the file name | Rename file to `[TableName]_[date].ext` |

If a problem persists, check the Unity Console for `AI Sheets` log messages — they usually name
the table/cell and the failing step.
