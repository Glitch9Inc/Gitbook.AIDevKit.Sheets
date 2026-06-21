# Localization — Unity Components

Drop-in `MonoBehaviour` components localize objects without code. They resolve their key on
start and **update automatically when `Localization.CurrentLocale` changes**.

## LocalizationManager

The entry point for no-code setup. Add **LocalizationManager** to a GameObject in your first
scene, configure its table sources in the Inspector, and it loads + initializes localization
on `Awake`. (Equivalent to calling `Localization.InitializeAsync()` yourself.)

## Component reference

| Component | Localizes |
|---|---|
| `TextLocalization` | UI `Text` **and** TextMeshPro (`TMP_Text`) — one component handles both |
| `SpriteLocalization` | `Sprite` (e.g. `Image.sprite`) |
| `TextureLocalization` | `Texture` |
| `MaterialLocalization` | `Material` |
| `AudioLocalization` | `AudioClip` |
| `AssetLocalization` | Any `UnityEngine.Object` (generic fallback) |

## Usage

1. Add the component to the target GameObject.
2. Set its **localization key** (the row key in your Localization table).
3. (Optional) Ensure localization is initialized — via a `LocalizationManager` or
   `Localization.InitializeAsync()` early in startup.

When you set `Localization.CurrentLocale`, all active components refresh to the new language.

## Localized assets & Addressables

Sprite/Texture/Audio/etc. values reference Unity assets. If your project uses **Addressables**,
localized assets can be loaded through the Addressables path (recommended for large projects).
