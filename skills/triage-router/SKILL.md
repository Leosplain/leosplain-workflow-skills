---
name: triage-router
description: Choose the first failure mode to fix when several skills could apply. Prefer scope problems before evidence problems, evidence problems before refusal, and refusal before prompt tuning.
---

# Triage Router

## Use when
- Several skills seem relevant at the same time
- The agent keeps jumping to prompt tweaks too early
- You need a clear first move instead of a long debate

## Do not use when
- Only one failure is present
- The task is already obviously in one skill's lane
- The source is creative by design and does not need triage

## Priority order
1. **Folder hygiene** — mixed current and old versions
2. **Evidence first** — unclear sent set or unsupported claim
3. **Refuse when thin** — missing facts or unresolved conflict
4. **One-step test** — stable baseline but unknown cause
5. **Output constraint** — source is fine, output still drifts

## Procedure
1. Name the first failure.
2. Pick the earliest skill that can actually fix that failure.
3. Explain why later skills are not first.
4. Do not chain multiple repairs unless the first one is done.

## Output format

**First failure**
- [short label]

**Chosen skill**
- [skill name]

**Why this comes first**
- [one sentence]

**Not first**
- [other skills] — why they wait

## Anti-patterns
- Choosing output constraint when the real issue is a mixed folder
- Choosing prompt wording before checking evidence
- Treating a router as a repair tool

## Acceptance check
- The first failure is named
- One skill is selected
- Later skills are explicitly deferred
