---
description: A spreadsheet editor and AI-powered data tool, built into the Unity Editor.
---

# AI Sheets

**AI Sheets** brings a full spreadsheet editor into Unity and combines it with AI to
automate content generation, translation, and data management — without leaving the editor.

It is built around one engine (Table → Column → Row → Cell) that powers two workflows:

* **Localization** — multi-language string tables, AI/Google/Microsoft translation, and
  drop-in Unity components that update text, sprites, audio and more when the locale changes.
* **Database** — model your game data (items, skills, quests, dialogue…) as typed tables,
  generate C# model classes from them, and load/query the data at runtime.

On top of both, an **AI layer** can generate rows and cells from prompts, fill missing
translations, and run a **Spreadsheet Agent** that edits your sheets from natural-language tasks.

## What you can build

* Localization pipelines with AI-assisted translation
* Item / skill / quest / dialogue databases driven by typed tables
* Procedural content tables filled by AI
* Data validation and QA workflows
* Runtime localization with the included components

## Requirements

* Unity 6 (6000.x)
* [UniTask](https://github.com/Cysharp/UniTask)
* [Newtonsoft.Json](https://docs.unity3d.com/Packages/com.unity.nuget.newtonsoft-json@latest)
* Addressables — optional, recommended for localized asset loading

## Next steps

* New here? Start with the [Quick Start](getting-started/quick-start.md).
* Want the mental model first? Read [Core Concepts](getting-started/core-concepts.md).
