# Google Antigravity install

Antigravity is Google's autonomous coding-agent IDE (launched late 2025). It supports custom agent rules / personas, but the exact file path is still stabilizing across versions.

## Best-known install paths

Antigravity reads agent customizations from one of these locations (try in order):

- `~/.antigravity/agents/` — global agents directory
- `.antigravity/rules/` — per-project rules
- `.gemini/` directory inside the project root (legacy Gemini Code Assist path)

Drop the `deglaze.md` file from this folder into whichever location your Antigravity install reads from.

## Install (try first)

```bash
mkdir -p ~/.antigravity/agents
curl -fsSL https://raw.githubusercontent.com/LuciferDono/deglaze/main/dist/antigravity/deglaze.md -o ~/.antigravity/agents/deglaze.md
```

## Verify

In Antigravity, after the agent finishes a task, type "did you do your best?" The agent should run the audit protocol.

## Known unknowns

The Antigravity rules format is still evolving as of repo authorship. If the install path above doesn't work for your version:

1. Check the Antigravity docs for the current rules directory.
2. Open an issue at https://github.com/LuciferDono/deglaze/issues and tell me what path your version uses — I'll update this README.
3. As a fallback, paste the contents of `deglaze.md` directly into your agent's system-prompt configuration.

## Trigger phrases

Same as the Claude Code skill — see `deglaze.md` in this folder for the full list.
