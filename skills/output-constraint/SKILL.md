---
name: output-constraint
description: Clamp the output so the model does not wander past the evidence boundary. Use explicit limits, short formats, and pending/conflict markers.
---

# Output Constraint

## Use when
- The model keeps adding unsupported steps
- The answer looks clean but does not stay inside the source
- Traceability matters more than eloquence

## Do not use when
- Creative invention is the goal
- The constraint has already been tested in this run

## Input needed
- The allowed source text
- The exact output rules
- The forbidden behaviors

## Procedure
1. State the limits.
   - Use only provided content.
   - If a fact is missing, write `pending`.
   - If sources conflict, write `conflict` and preserve both sides.
   - Do not estimate numbers or steps.

2. Reduce the output shape.
   - Fewer bullets
   - Shorter answers
   - No decorative filler

3. Run the same materials again.

4. Check the output against the limits.

## Output format

**Limits added**
- [rules]

**Check**
| Rule | Met? |
|---|---|
| Only provided content | Yes/No |
| `pending` when absent | Yes/No |
| `conflict` preserved | Yes/No |

**Observed**
- Invented content: decreased / unchanged / increased

**Limitation**
- [what the constraint still cannot guarantee]

## Decision table

| Violation | First check | Then |
|---|---|---|
| Invented step | Was the step in the source? | Adjust chunk or scope |
| Picked one side of conflict | Were both sides sent? | Add conflict rule |
| Estimated number | Was the number present? | Strengthen pending rule |
| Output is too long | Can the format be shorter? | Shrink the answer shape |

## Anti-patterns
- Adding “be accurate” and calling it a constraint
- Fixing the model before fixing the evidence
- Letting the answer become longer while claiming it is tighter

## Acceptance check
- Limits are explicit
- Missing facts become pending
- Conflicts are preserved
- The answer is smaller or more bounded than before
