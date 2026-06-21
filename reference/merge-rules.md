# Merge Rules

When you **Merge** an import (or pull from Google Sheets), AI Sheets compares imported rows to
existing rows by key and resolves automatically where it's safe — only real conflicts prompt you.

## Automatic resolution

* **Auto-skip** — the imported row is empty, or identical to the existing row. No prompt.
* **Auto smart-merge** — the imported row only fills cells that are **empty** in the existing
  row (no existing value is overwritten). No prompt.

## Conflicts

A conflict occurs only when an imported value would **overwrite a different existing value**.
Those rows appear in the Merge Conflicts window.

> 📷 **Image — `merge-conflicts.png`:** The Merge Conflicts window — per-row action dropdown
> (Smart Merge / Skip / Overwrite) and the "Smart Merge All / Skip All / Overwrite All" buttons.

Per row (or in bulk) you choose:

| Action | Effect |
|---|---|
| **Smart Merge** (default) | Fill only the existing row's empty cells; keep existing values |
| **Skip** | Keep the existing row; ignore the imported one |
| **Overwrite** | Replace the existing row with the imported one |

## Caution

Renaming a row's **key** during merge can break references — components or code that look up
that key will no longer find it.
