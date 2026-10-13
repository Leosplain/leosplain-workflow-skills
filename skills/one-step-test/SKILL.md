---
name: one-step-test
description: Change exactly one class of condition at a time when output is unstable. Keep the baseline fixed, compare the result, and record what still did not change.
---

# One-Step Test

## Use when
- The result changes across runs and the cause is unclear
- Several things changed at once and attribution is impossible
- You need a clean before/after comparison

## Do not use when
- The source itself is incomplete or contradictory
- The task requires multiple changes by design
- The failing condition is already known

## Input needed
- Baseline materials
- One candidate change only
- The same output requirement for both runs

## Procedure
1. Freeze the baseline.
   - Same source set
   - Same task
   - Same output requirement
   - Record what was sent and what came out

2. Change only one class.
   - Priority order
   - Chunk boundary
   - Folder separation
   - Output constraint
   - Role / verb wording
   Do not combine classes.

3. Run again under the same materials.

4. Compare the runs.
   - What disappeared?
   - What appeared?
   - What stayed the same?

5. Record the limitation.
   - What this change did not test
   - When this change will not help

## Output format

**Direct answer**
- This run changed only: [one class]

**Comparison**
| | Baseline | One change |
|---|---|---|
| Sent | ... | ... |
| Observed | ... | ... |

**Limitation**
- [what remains untested]

## Decision table

| Symptom | First thing to change | Avoid for now |
|---|---|---|
| Cites old rule | Folder separation | Prompt wording |
| Invents missing steps | Output constraint or chunk boundary | Model size |
| Ignores priority | Priority labeling | Adding more examples |
| Unstable across runs | One-step test | Multiple edits at once |

## Anti-patterns
- Changing prompt, chunk size, and folder in the same run
- Treating a single success as proof
- Calling a difference causal without a baseline

## Acceptance check
- Only one class changed
- Baseline stayed fixed
- Limitation is written
