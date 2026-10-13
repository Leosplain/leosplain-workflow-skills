---
name: folder-hygiene
description: Separate current and archived sources so old rules stop contaminating retrieval and summaries.
---

# Folder Hygiene

## Use when
- The same document exists in multiple versions
- Retrieval keeps pulling old rules
- The agent cannot tell what is current

## Do not use when
- There is only one usable file
- Version control already guarantees current-only retrieval

## Input needed
- Current files
- Archived files
- A clear scope boundary

## Procedure
1. Label the current set.
2. Push superseded files out of the retrieval path.
3. Keep archive and current in different locations.
4. Re-run the retrieval.
5. Check whether old content still leaks in.
6. If it does, inspect the path and the chunking, not just the filename.

## Output format

**Separation**
- Current: [location / files]
- Archived: [location / files]

**Leak check**
| | Before | After |
|---|---|---|
| Old citations | [ ] | [ ] |
| Current citations | [ ] | [ ] |

**Limitation**
- Separation does not create missing content.

## Decision table

| Problem | First action | Why |
|---|---|---|
| Old rule cited | Move archive out of scope | Scope beats wording |
| Both versions retrieved | Tighten retrieval path | Filename alone is not enough |
| Current file incomplete | Mark the gap | Separation cannot invent text |
| Unclear current file | Add an explicit current marker | Date-only assumptions are fragile |

## Anti-patterns
- Keeping old and new together “for reference”
- Relying on filenames to do version control
- Renaming files instead of changing scope

## Acceptance check
- Current and archived sets are explicit
- Retrieval scope is reduced
- Old content stops leaking or the limitation is written
