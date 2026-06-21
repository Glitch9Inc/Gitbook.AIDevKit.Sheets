# AI Translation

Fill missing translations in a [Localization](../localization/README.md) table automatically.

## Backends

Choose the translation service per table/column:

* **AI** translation (your configured AI provider — context-aware)
* **Google Translate**
* **Microsoft Translator**

Each needs the matching key configured (see [Providers & API Keys](providers.md)).

## Workflow

1. Open a Localization table with one or more language columns.
2. Detect/select the missing cells (gaps across languages).
3. Run translation — the chosen backend fills the empty target cells from the source language.
4. Review with **Compare Translations** if needed.

## Context for better results

* **Contextual Keys (Localization)** — register context hints so the AI understands your
  game's terms and tone.
* Per-cell context and existing translations are passed to the AI backend as additional context.

## Editing existing text

To refine wording (not translate), use **Text Revision** — select a text cell and let the AI
rewrite/clean it up.

> This is editor-time, table-based translation. To translate dynamic/UGC text at runtime, see
> [Realtime Translation](../localization/realtime-translation.md).
