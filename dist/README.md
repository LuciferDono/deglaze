# deglaze — per-agent packagings

The canonical skill lives in `../SKILL.md`. This directory holds platform-specific wrappers so you can install deglaze into whichever AI coding agent you actually use.

| Agent | Install file | Path on disk |
|-------|-------------|-------------|
| [Claude Code](./claude-code/) | `../SKILL.md` (with YAML frontmatter) | `~/.claude/skills/deglaze/` |
| [Cursor](./cursor/) | `cursor/deglaze.mdc` (or `.cursorrules`) | `.cursor/rules/` or project root |
| [OpenAI Codex CLI](./codex/) | `codex/AGENTS.md` | `~/.codex/AGENTS.md` or `./AGENTS.md` |
| [GitHub Copilot](./copilot/) | `copilot/copilot-instructions.md` | `.github/copilot-instructions.md` or VS Code settings |
| [Google Antigravity](./antigravity/) | `antigravity/deglaze.md` | `~/.antigravity/agents/` (best-effort, format evolving) |
| [Any system-prompt LLM](./generic-system-prompt/) | `generic-system-prompt/system-prompt.md` | paste into system prompt field |

## Why a wrapper per agent?

The skill content is the same across all platforms. What differs:

- **Filename** — Claude Code wants `SKILL.md`, Codex wants `AGENTS.md`, Copilot wants `copilot-instructions.md`.
- **Frontmatter** — Claude Code needs YAML frontmatter (`name`, `description`); the others reject it.
- **Auto-discovery path** — each platform reads from a different directory.
- **Trigger semantics** — some platforms auto-detect natural-language triggers; others need explicit `/command` syntax.

Each folder in this directory packages the skill in the right shape for its target agent and ships a one-page README with the install command.

## Contributing a new agent

If your AI coding agent isn't here yet, open a PR:

1. Create `dist/<agent-name>/`
2. Add the skill in whatever format your agent reads
3. Add a `README.md` with install instructions
4. Update the table above

Currently planned: Continue.dev, Aider, Cody (Sourcegraph), Hermes (specify which Hermes when filing).
