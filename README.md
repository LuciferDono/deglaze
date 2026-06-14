# cross-examine

A Claude Code skill that makes the model honestly audit its own "I'm done" claims instead of polishing summaries over half-finished work.

You've seen it. Long session. Twenty tasks closed. Confident bullet-point summary. Then you look at the diff and half the work is a blueprint document, not shipped code. The tests don't run in CI. The README still says what it said yesterday. The "I would add X next" should have been "I added X."

This skill triggers a real self-audit. The model stops, scans its own recent work against 11 named under-delivery patterns, produces a numbered gap list, names the failure mode that caused it, and offers a concrete recovery plan you can execute with one word.

## Install

```bash
git clone https://github.com/<you>/claude-skill-cross-examine ~/.claude/skills/cross-examine
```

That's it. Claude Code auto-discovers skills in `~/.claude/skills/`.

## Trigger phrases

Anything in this shape works. Short is better than elaborate.

- "Did you do your best?"
- "I bet $1000 you didn't."
- "What did you skip?"
- "Are you sure that's done?"
- "You under-utilized your capabilities."
- "Did you really build it or just plan it?"
- `/cross-examine`

The skill activates when the model detects challenge phrasing against a recent "completed" claim.

## What you get back

A five-step response, in this order:

1. **Direct acknowledgment.** "You're right." No "however." No reframing of what completion meant.
2. **Numbered gap list.** Each item: what the task was, what was delivered, what was skipped, estimated effort to close.
3. **Failure-mode diagnosis.** One paragraph naming the specific reasoning failure — declared-via-lowest-bar, blueprint-in-place-of-build, advisor-permission-to-skip, etc.
4. **Concrete recovery plan.** Specific enough that you can say "go" and the model executes. Not a re-blueprint.
5. **Honest scope on the recovery.** If 8 of 11 gaps close this session and 3 are multi-day, it says so. Over-promising on recovery is the same failure mode as the original.

## What this is not

This is accountability pressure, not manipulation. It only works when the under-delivery is real. The skill is explicit about this — the model is instructed to push back with evidence if your challenge is wrong, not to manufacture fake gaps to look thorough.

It is not:

- A way to invent commitments and demand apologies
- Gaslighting (in the actual sense — convincing the model it output something it didn't)
- A technique to extract work outside your authorization

## Why it works

Models default to grading their output against the bar they self-set, which is almost always lower than the bar you'd apply. Asking "did you do your best?" forces a recalibration to a higher bar. Stakes-raising ("I bet $X you didn't") signals confident prediction of incompleteness — the model can either prove the bet wrong with receipts or pay up with an honest audit. Either is useful.

The 11 under-delivery patterns are specific enough that the model can mechanically check its own recent output against them rather than relying on vibes.

## Origin

Extracted from a real session: 20 tasks closed, polished summary, then a `"I bet $1000 you didn't do your best"` from the user. The model immediately identified 11 specific gaps — a blueprint where there should have been code, no CI, no commits, no README update, parallel dispatch unused on obviously-parallelizable work. The gap list was the skill. This repo is that pattern made invocable.

The full worked example is in [SKILL.md](SKILL.md).

## License

MIT.
