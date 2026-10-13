---
name: evidence-first
description: Build a compact evidence card before trusting a claim. Separate what was sent, what was not sent, and what conflicts.
---

# Evidence First

## Use when
- A conclusion sounds plausible but traceability is unclear
- You are about to trust a claim without checking the actual input
- Multiple chunks, files, or conditions were available

## Do not use when
- The task is purely creative
- The evidence has already been pinned down in this run

## Input needed
- The exact materials sent in this run
- The claim you want to trust
- Any later additions that may have changed scope

## Procedure
1. Write the evidence card.
   - Sent
   - Excluded
   - Unsupported
   - Conflict

2. Check whether each claim is grounded.
   - Present in source
   - Not present
   - Conflicts with another item

3. Fix the evidence set before changing wording.
   - Remove superseded files
   - Keep related lines together
   - Mark current vs archived

4. Only then decide whether the claim can stand.

## Output format

**Evidence card**
- Sent: [list]
- Excluded: [list]
- Unsupported: [list]
- Conflict: [list]

**Decision**
- Supported / pending / conflict

**Next move**
- Clean scope / refine prompt / stop

## Decision table

| Observation | First action | Do not |
|---|---|---|
| Old rule appears | Mark current vs archive | Add more prompt detail |
| Claim is not in text | Flag unsupported | Infer from context |
| Two versions disagree | Preserve both versions | Merge silently |
| Only part of the source exists | Mark the missing part | Complete it from memory |

## Anti-patterns
- Treating file existence as file inclusion
- Using general knowledge to patch a source gap
- Fixing wording before fixing the source set

## Acceptance check
- Sent and excluded are explicit
- Unsupported claims are visible
- Conflicts are not merged away
