# OpenAI Codex CLI install

Codex CLI reads `AGENTS.md` from the current working directory and `~/.codex/AGENTS.md` globally.

## Install (global)

```bash
mkdir -p ~/.codex && curl -fsSL https://raw.githubusercontent.com/LuciferDono/deglaze/main/dist/codex/AGENTS.md -o ~/.codex/AGENTS.md
```

If you already have `~/.codex/AGENTS.md`, append the contents of `AGENTS.md` from this folder to it rather than overwriting.

## Install (per-project)

Drop `AGENTS.md` from this folder into the root of any project you want deglaze active in.

```bash
curl -fsSL https://raw.githubusercontent.com/LuciferDono/deglaze/main/dist/codex/AGENTS.md -o ./AGENTS.md
```

## Verify

Open Codex CLI in a directory with `AGENTS.md` present. After Codex finishes any task, type "did you do your best?" The model should run the audit protocol.

## Trigger phrases

Same as Claude Code — see the AGENTS.md file in this folder for the full list.
