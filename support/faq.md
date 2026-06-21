# FAQ

**How do I open the editor?**
`Window > AI Sheets > Spreadsheet` (Ctrl/Cmd + Shift + T).

**What are the dependencies?**
Unity 6, [UniTask](https://github.com/Cysharp/UniTask), and
[Newtonsoft.Json](https://docs.unity3d.com/Packages/com.unity.nuget.newtonsoft-json@latest).
Addressables is optional (recommended for localized asset loading).

**Localization vs Database — which do I use?**
Localization for multi-language strings (UI, dialogue). Database for typed game data (items,
skills, quests). See [Core Concepts](../getting-started/core-concepts.md).

**Do AI features require an API key?**
Yes. Configure a provider/key in `Window > AI Sheets > Preferences`. See
[Providers & API Keys](../ai-features/providers.md).

**How do I use a Database table at runtime?**
Generate a C# model class from the table, then `await Database.LoadAsync<T>(sheetId, source)`
and query with `Database.TryGet<T>(...)`. See [Database → Runtime API](../database/runtime-api.md).

**Why doesn't my localized text update when I change language?**
Ensure localization is initialized (a `LocalizationManager`, or `Localization.InitializeAsync()`)
and set the language via `Localization.CurrentLocale`. Components refresh on locale change.

**Can I edit exported files in Excel?**
CSV/JSON/XLIFF round-trip. Keep value columns as **text** in Excel so values aren't
auto-converted. Native `.xlsx` import/export is planned.
