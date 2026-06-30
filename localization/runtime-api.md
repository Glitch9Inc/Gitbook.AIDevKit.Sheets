# Localization — Runtime API

All runtime types live in the `Glitch9.AI.Sheets` namespace.

## Initialize

Load the localization tables once before use:

```csharp
using Glitch9.AI.Sheets;

await Localization.InitializeAsync();
bool ready = Localization.IsInitialized;
```

If you use a **LocalizationManager** component, it initializes for you on `Awake`
(see [Unity Components](components.md)).

## Set / get the locale

```csharp
Localization.CurrentLocale = Locale.Korean;   // switch language
Locale current = Localization.CurrentLocale;
```

Changing the locale refreshes registered localization components automatically.

## Translate text — `Tr()`

`Tr()` returns a fluent task you can chain and then resolve with `.ToString()`:

```csharp
string title  = "menu.title".Tr();                       // simple
string apples = "apple".Tr().Count(3).ToString();        // pluralization
string greet  = "hello".Tr().Gender(TextGender.Feminine).Format(playerName).ToString();
```

### Fallback

```csharp
string text = "unknown.key".Tr().FallBack("Default Text");
```

## Dates & weekdays

Date and weekday formatting use .NET `CultureInfo` for the current locale — no table required:

```csharp
string when = System.DateTime.Now.Tr(TimeFormat.FullDate); // locale-formatted date/time
string day  = System.DateTime.Now.DayOfWeek.Tr();          // localized weekday name
```

## Notes

* Call `InitializeAsync()` (or use a `LocalizationManager`) before `Tr()` lookups.
* A missing key returns a safe fallback; use `.FallBack(...)` to control it.
* See [Realtime Translation](realtime-translation.md) for translating text that isn't in a table.
