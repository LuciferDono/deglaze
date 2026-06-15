# GitHub Copilot install

GitHub Copilot supports custom instructions at the repo level (`.github/copilot-instructions.md`) and the user level (VS Code settings).

## Install (per-repo)

In any repo where you want deglaze active:

```bash
mkdir -p .github
curl -fsSL https://raw.githubusercontent.com/LuciferDono/deglaze/main/dist/copilot/copilot-instructions.md -o .github/copilot-instructions.md
```

If you already have `.github/copilot-instructions.md`, append the contents rather than overwriting.

## Install (VS Code user-level)

1. Open VS Code settings.json (Cmd/Ctrl+Shift+P → "Preferences: Open User Settings (JSON)").
2. Add the `github.copilot.chat.codeGeneration.instructions` setting and paste in the `copilot-instructions.md` body.

```jsonc
{
  "github.copilot.chat.codeGeneration.instructions": [
    {
      "text": "<paste copilot-instructions.md contents here>"
    }
  ]
}
```

## JetBrains IDEs

Copilot for JetBrains supports custom instructions via Settings → GitHub Copilot → Instructions. Paste the contents of `copilot-instructions.md` there.

## Verify

After Copilot Chat finishes any task, type "did you do your best?" The model should run the audit protocol.

## Caveat

Copilot's adherence to long custom instructions is less reliable than Claude Code or Codex CLI. Short trigger phrases (`/deglaze`) sometimes get missed; longer challenges like "what did you skip and why did you stop there" usually work better.
