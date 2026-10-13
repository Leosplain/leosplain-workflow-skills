---
name: refuse-when-thin
description: When the source does not carry the answer, stop at pending, not written, or conflict instead of inventing a clean-looking completion.
---

# Refuse When Thin

## Use when
- The source does not actually contain the required fact
- The summary would otherwise sound better than the evidence
- A decision has to be traceable to the text

## Do not use when
- Estimation is explicitly allowed
- The task is intentionally creative
- The evidence has already been verified as sufficient

## Decision rule
Ask three questions:
1. Is the fact present?
2. Is there unresolved conflict?
3. Is the request asking the source to provide something it never promised?

If the answer is no to 1, or yes to 2, do not complete the gap.

## Procedure
1. Judge sufficiency against the question.
2. If insufficient, output one of:
   - `pending`
   - `not written`
   - `conflict`
3. If sufficient, answer only from the source.
4. If conflict exists, preserve both sides before stopping.

## Output format

**Evidence sufficient?** Yes / No

**Output**
- [answer or `pending`]

**Reason**
- [why the source does or does not support it]

## Decision table

| Situation | Required output | Do not |
|---|---|---|
| Fact absent | `pending` | Guess from similar cases |
| Two versions differ | `conflict` + both sides | Pick one silently |
| Partial rule present | Answer the present part, pending the rest | Finish the rule from memory |
| Question exceeds scope | `pending` | Borrow from general knowledge |

## Anti-patterns
- Filling gaps to keep the answer smooth
- Converting absence into probability
- Rewriting conflict as certainty

## Acceptance check
- Missing facts are not hidden
- Conflicts stay visible
- No unsupported completion slips in
