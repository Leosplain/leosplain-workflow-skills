# Workflow Skills v3

A zero-guess skill pack for workflows that keep drifting, inventing, or mixing old and current sources.

## What makes this version different
- One failure mode per skill
- Evidence before correction
- Current / archived / pending states instead of vague confidence
- Explicit stop rules when the source is thin
- A router so the agent does not guess which skill to use first

## The operating frame
1. **Start with scope** — current only, no mixed versions.
2. **Start with evidence** — what was actually sent, what was not.
3. **Start with the failure** — the first thing that broke, not the last symptom.
4. **Start with limits** — if the source does not support the claim, write `pending` or `conflict`.
5. **Only then tune the prompt** — never fix wording before fixing the evidence set.

## Which skill to use

| Skill | Trigger | What it should do |
|---|---|---|
| triage-router | Several skills could apply | Pick the first failure to fix |
| folder-hygiene | Current and old versions are mixed | Clean the retrieval scope |
| evidence-first | You do not trust what was actually sent | List sent / excluded / unsupported |
| refuse-when-thin | The source does not carry the answer | Stop at `pending`, `not written`, or `conflict` |
| one-step-test | You need to isolate one change | Compare baseline vs one changed class |
| output-constraint | The model keeps expanding beyond evidence | Force tighter limits and smaller outputs |

## Core rules
- Fix the scope before fixing the prompt.
- Separate current files from archived files.
- Do not convert absence into a guess.
- Do not treat one successful run as proof.
- Do not report an accuracy number unless you measured it.

## Suggested flow
1. `triage-router` decides the first failure mode.
2. `folder-hygiene` removes old-version contamination.
3. `evidence-first` verifies the actual sent set.
4. `refuse-when-thin` blocks unsupported completion.
5. `one-step-test` isolates a single variable.
6. `output-constraint` clamps the final output.

## Examples
See `examples/` for short before/after notes.

## Maintenance standard
If a skill starts answering too many different problems, split it.
If two skills keep being chosen together, tighten their trigger boundaries.
If a rule cannot be checked after the run, it is too vague.
