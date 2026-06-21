# Providers & API Keys

AI features (generation, AI translation, the agent, text revision) need an AI provider and an
API key. Translation can also use Google / Microsoft services.

## Where to configure

`Window > AI Sheets > Preferences` (Project Settings).

> 📷 **Image — `provider-settings.png`:** The AI Sheets Preferences (Project Settings) page with
> the provider + API key + model fields.

AI Sheets shares provider configuration with the **AI DevKit** core, so keys you set there are
reused across features.

## What to set

* **AI provider & API key** — e.g. OpenAI, Anthropic (used for generation, AI translation,
  agent, revision). Use the latest capable models.
* **Model selection** — default models for text / translation / image / audio. These can also
  be overridden per table or per column.
* **Google Translate / Microsoft Translator keys** — only if you use those translation backends
  (including [Realtime Translation](../localization/realtime-translation.md)).

## Notes

* Without a valid key, AI actions are disabled or will report an error.
* Keys are credentials — don't commit them to source control or share project settings that
  embed them.
* Translation and generation calls cost money per the provider's pricing; caching (for realtime
  translation) reduces repeat calls.
