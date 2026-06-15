# Claude Code install

Claude Code auto-discovers skills under `~/.claude/skills/`. The canonical `SKILL.md` at the repo root is the file Claude Code reads.

## Install

```bash
git clone https://github.com/LuciferDono/deglaze ~/.claude/skills/deglaze
```

Windows (PowerShell):

```powershell
git clone https://github.com/LuciferDono/deglaze "$env:USERPROFILE\.claude\skills\deglaze"
```

## Verify

In any Claude Code session, type `/deglaze`. The skill should fire and produce the response protocol described in `../../SKILL.md`.

## Update

```bash
cd ~/.claude/skills/deglaze && git pull
```

## Trigger phrases

Anything in the shape of "did you do your best", "what did you skip", "I bet $X you didn't", "stop glazing", `/deglaze`, `/cross-examine`. Full list in `../../SKILL.md`.
