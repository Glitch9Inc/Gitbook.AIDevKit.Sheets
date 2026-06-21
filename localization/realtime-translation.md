# Realtime Translation

Realtime translation translates text **on the fly at runtime** — useful for user-generated
content or strings that don't exist in your localization tables.

## Providers

Pick the translation backend:

* **AI** translation (your configured AI provider)
* **Google Translate**
* **Microsoft Translator**

Each needs the corresponding API key configured (see [Providers & API Keys](../ai-features/providers.md)).

## Caching

Realtime translation caches results to avoid repeat calls and cost:

* **Memory** — in-memory for the session.
* **Persistent** — cached across sessions.
* **Negative** — remembers failures so they aren't retried in a tight loop.

## When to use which

| Need | Use |
|---|---|
| Authored UI strings, dialogue | Localization tables + `Tr()` ([Runtime API](runtime-api.md)) |
| Player/UGC text, dynamic strings | Realtime Translation |

> Authored content should live in tables (reviewable, cacheable, offline). Reserve realtime
> translation for text you genuinely cannot author ahead of time.
