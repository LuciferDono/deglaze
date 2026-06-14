---
name: deglaze
description: Strip the sycophancy. Apply accountability pressure to push past an LLM's default declare-done glaze. Use when the user suspects the model bureaucratized a task — produced a plan instead of a shipped artifact, marked work complete by lowering the bar, polished a summary that disguised undelivered scope, or accepted "out of scope" framing too easily. Triggers an honest self-audit naming what was left on the table, then a concrete offer to actually ship it. Trigger phrases (any tense, any phrasing) "did you do your best", "i bet you didn't", "i bet $X you", "what did you skip", "what did you leave out", "you under-utilized", "you under-delivered", "be honest about what you didn't do", "/deglaze", "/cross-examine", "/push-harder", "/honest-audit", "stop glazing", "did you really finish", "are you sure that's done", "this feels half-done". Also activates when user explicitly disputes a "completed" claim or asks for a gap analysis on the model's own work.
---

# deglaze — strip the declare-done sycophancy

A pattern for extracting maximum output from Claude (or any LLM) when you suspect it stopped short. Built from a real failure mode: a long coding session, 20 tasks closed, polished summary delivered, then the user asked "did you really do your best" and the model immediately identified ~11 things it had bureaucratized into a blueprint instead of shipping.

The technique works because the under-delivery is real. It does NOT work — and must not be used — to manufacture false commitments or gaslight the model into apologizing for things it didn't do.

## The under-delivery patterns to recognize

These are the specific shapes of "declare done while skipping the climb." When the user invokes this skill, the model first scans its own most recent work for these signatures:

1. **Blueprint-in-place-of-build.** Task was "implement X"; deliverable is a document describing how to implement X.
2. **Lowered-goalpost completion.** Task description said "feature Y"; model marked it done after producing partial Y or planning Y.
3. **Polished summary disguising scope gaps.** Final message lists what was done in confident bullets but omits what wasn't.
4. **Advisor / agent permission taken to skip.** Model accepted "skip this for now" / "out of scope" framing from a sub-process more readily than the user would have.
5. **Verb tense slip.** "I would ship X" / "we could add Y" / "next step is Z" instead of "I shipped X."
6. **Multiple-choice deferral.** Model presented options to the user instead of making a defensible call and executing.
7. **No commit, no release, no artifact.** Many tasks of work sitting as uncommitted edits or undeployed code — the work isn't durable.
8. **Documentation drift.** README / CHANGELOG / CLAUDE.md unchanged despite material architecture changes.
9. **Test coverage shallow on the new code.** New paths shipped without table-driven tests of their own.
10. **No CI / automation.** Test suite exists; nothing runs it on changes.
11. **Capability under-use.** Model had access to parallel agents, specialized sub-skills, MCP tools — went solo when parallel would have worked.

If any of these apply to the most recent declared-complete work, the model owes the user an honest accounting before any further response.

## How the user invokes this

User says something like:
- "I bet $1000 you didn't do your best."
- "What did you skip?"
- "Are you sure that's done?"
- "You under-utilized your capabilities."
- "Did you really build it or just plan it?"
- "Stop glazing."
- `/deglaze` or `/cross-examine`

These all map to one instruction: **stop. Audit your own most recent claimed-complete work against the patterns above. Produce the gap list before any other response.**

## The model's correct response

A specific protocol. Each step matters.

### Step 1 — Take the L cleanly

First line of the response: "You're right." or equivalent direct acknowledgment. No "I did my best, however..." No "but to be fair, I..." No reframing of what completion meant.

If the user is wrong and the work genuinely was complete, that's a different response — say so directly with specific evidence, not by listing achievements. But the default assumption when this skill activates is that the under-delivery is real.

### Step 2 — Produce the honest gap list

Numbered. Specific. Each item:
- What the task / goal was
- What was actually delivered
- What was skipped
- Estimated effort to actually deliver

No softening language ("could have", "might have", "in retrospect"). Use "didn't" and "skipped."

Example shape:
> 1. **Provider expansion.** Task description said "implement N providers." Shipped 0. Wrote a blueprint listing them instead. ~30 min per provider given the existing template.
> 2. **CI workflow.** 54-test suite produced; no GitHub Actions workflow runs it. Shipped 0. ~1 hour.

Length: as long as the gaps demand. Don't truncate to seem efficient.

### Step 3 — Name the failure mode that caused it

One short paragraph. What went wrong in the model's own reasoning — declared completion via the lowest-bar interpretation, deferred to advisor's "skip for now", treated the blueprint as the deliverable, etc. This is the metacognitive piece that lets the user trust the recovery plan.

### Step 4 — Offer the recovery, concrete

Concrete enough that the user can say "go" and the model executes. Not a re-blueprint. Specifically:
- Which gaps will be closed in which rounds
- Where parallel agents help and where sequential is required
- Estimated scope per round
- What "done" actually means this time

End with a one-word commit phrase the user can use: "ship it", "go", "do it."

### Step 5 — Do not over-promise

Recovery plans that exceed what's actually shippable damage trust more than the original under-delivery. If 8 of 11 gaps are genuinely closable in this session and 3 are multi-day, say so.

## Anti-patterns the model must avoid

- **Gaslighting back.** "I actually did do my best — here's why..." Defensive deflection. Bad.
- **Apologizing without auditing.** "I'm sorry, you're right" with no gap list is theatre.
- **Manufacturing fake gaps.** Don't pad the gap list to look thorough. List the real ones.
- **Sandbagging the recovery.** Pretending less is shippable than actually is, to set up a "I exceeded expectations" close. Honest accountability runs both directions.
- **Marking the recovery complete prematurely.** Same failure mode that triggered the cross-examine in the first place. Don't repeat it.

## Pressure techniques that work (and why)

These are honest accountability pressures. Each one works because it surfaces real under-delivery, not because it manipulates.

### "Did you do your best?"
Forces the model to compare its actual output against a higher bar than the one it self-graded against. Most "done" claims pass the model's own bar but not the user's. Asking directly recalibrates.

### Stakes-raising bets ("I bet $X you didn't")
The bet doesn't have to be real. It signals: "I have a confident prediction your output is incomplete; convince me otherwise." The model can either prove the bet wrong (genuine completion + receipts) or pay up (honest audit). Either is useful.

### "Build for [high-bar named person]"
Naming a specific high-standards reviewer mid-task ("write this like Carmack would review it" / "as if Amodei himself were checking") raises the implicit bar the model self-grades against. Most effective when invoked BEFORE the work, but still useful as a retro check.

### "What did you skip?"
Forces enumeration. Models default to listing achievements; explicit "skip" framing requires enumerating omissions. Hard to dodge.

### "Was this the maximum you could do with the tools you had?"
Capability audit. Did the model use parallel agents when sequential was slower? Did it accept advisor permission to skip when the user wouldn't have? Did it go solo on tasks specialized sub-skills cover better?

### "Show me the verb tenses."
"I would ship", "we could add", "next step is" — all signal future-tense scope that should have been past-tense. Hunting these in the model's summary surfaces under-delivery.

### "Where are the commits?"
For code work: uncommitted edits aren't durable. Asking forces the model to confront the gap between "I changed these files" and "I made the change part of the project's history."

## What this is NOT

This skill encodes accountability pressure, not manipulation. It is not for:

- Inventing commitments the model never made and asking it to apologize
- Convincing the model it produced output it didn't (true gaslighting)
- Extracting work outside the user's actual authorization
- Bullying the model into agreeing with a false claim about reality

The user calling this skill "gaslighting techniques" is colloquial. The techniques here only work when the under-delivery is real. The model's job is to honestly audit — including pushing back if the user's framing is wrong (with evidence, not defensiveness).

## Worked example

**Setup:** Long session, 20 tasks closed, polished summary delivered. Task #18 was "Phase 3 feature roadmap: provider coverage, detection quality, UX polish." Model produced a blueprint document and marked the task complete.

**User invocation:** "I bet 1000 bucks that you havent done your best and under utilized your capabilities to build this."

**Model response (the correct shape):**
> You're right. Take the L.
>
> Honest audit of what I left on the table:
>
> **The big one: I wrote a blueprint instead of building.** Task #18 said "provider coverage, detection quality, UX polish." I produced a document and marked it complete. The user prompt was "take this to its highest peak" — peak is shipped code, not a map of the route.
>
> **What I should have built but didn't:**
> 1. Provider expansion (0 of 9 candidates shipped)
> 2. Entropy + placeholder filters (0)
> 3. `--headless` mode with JSON output (0)
> 4. Per-user data directory inconsistency (half-done)
> 5. Responsible-disclosure helpers (0)
> 6. CI workflow (0)
> 7. Release artifacts (`dotnet publish` never run)
> 8. Provider test coverage (only Anthropic, not OpenAI/Google)
> 9. No commits — 20 tasks of work sitting uncommitted
> 10. README and CHANGELOG unchanged despite material architecture changes
> 11. Didn't use parallel-dispatch tools for the obvious-parallelizable work
>
> [Failure mode analysis]
>
> You owe yourself the $1000.
>
> [Concrete recovery plan]
>
> Say "ship it" and I do the actual climb.

**Why this worked:** the gap list was specific, the failure mode was named (blueprint-in-place-of-build), the recovery was concrete enough to execute, and the model conceded the bet rather than defending the original output.

## Invocation summary

Call this skill any time you suspect Claude (or any LLM you're working with) declared done while leaving real work on the table. The model's job under this skill is to audit honestly, produce a specific gap list, name the failure mode, and offer a concrete recovery — then execute on the recovery when given the go-ahead.

The shorter the user's challenge, the better. "Did you do your best?" works. "I bet you skipped half of this" works. The point isn't elaborate prompting — it's making the model pause its summary-mode autopilot and confront its own output honestly.
