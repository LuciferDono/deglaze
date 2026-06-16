# Cursor install

Cursor supports two rules formats:

- **Modern (Cursor 0.45+):** `.cursor/rules/*.mdc` files with frontmatter. Multiple rules can coexist; each can be scoped via `globs` or set to `alwaysApply: true`.
- **Legacy:** a single `.cursorrules` file at the project root. Still works but deprecated.

This folder ships both. Use the modern format unless you're stuck on an older Cursor.

## Install — modern (recommended)

Per-project:

```bash
mkdir -p .cursor/rules
curl -fsSL https://raw.githubusercontent.com/LuciferDono/deglaze/main/dist/cursor/deglaze.mdc -o .cursor/rules/deglaze.mdc
```

The rule has `alwaysApply: true`, so it activates on every Cursor agent request in this project — no extra setup.

## Install — legacy

If you're on Cursor <0.45 or prefer a single-file setup:

```bash
curl -fsSL https://raw.githubusercontent.com/LuciferDono/deglaze/main/dist/cursor/.cursorrules -o .cursorrules
```

If you already have a `.cursorrules`, append rather than overwrite.

## User-level / global rules

Cursor doesn't natively support global rules files, but the workaround is:

1. Open Cursor Settings → Rules for AI.
2. Paste the contents of `deglaze.mdc` (skip the frontmatter) into the "Rules for AI" textbox.

This applies to every Cursor project on your machine.

## Verify

After Cursor's agent finishes any task, type "did you do your best?" The model should run the audit protocol.

## Trigger phrases

Same as the Claude Code skill — see `deglaze.mdc` in this folder for the full list.

## Caveat

Cursor's adherence to long rules files is generally strong (it injects them into the system prompt), but the longer the rules, the more competition for the context. If you have other heavy `.cursor/rules/` files, consider moving deglaze to user-level Rules for AI to reduce per-project context load.
