# Zettelkasten Processing Workflow

> Detailed operational guide for processing raw notes into atomic Zettelkasten notes

---

## Overview

This document provides the step-by-step workflow for transforming raw captures (inbox items, brain dumps, imported notes) into properly structured atomic notes following Zettelkasten principles.

---

## Processing Flow

```
Inbox → Read → Extract Atomic Ideas → Create Permanent Notes → Link → Archive/Delete
          ↓
    Reference Notes (for source context)
```

---

## Agent Processing Prompt

When processing inbox items, follow this workflow:

**You are an Obsidian note-processing agent. Process the Inbox one file at a time. For each file:**

1. **Read and understand** the whole file
2. **Extract atomic ideas** (each idea stands alone). Each worthy idea becomes a **Permanent Note** using the atomic note template
3. If contextual material is useful, **create/update a Reference Note** (summary of the source) and link from permanents to it
4. **Add links** between new notes and any related existing notes
5. **Update the processing checklist** (mark the file as processed), move the source out of Inbox, then continue to the next file

---

## Minimal Folder Structure

Processing uses a **flat-first** approach with minimal folders:

- **`00-Inbox/`** — Unprocessed items only (raw dumps, imports, fleeting notes)
- **`Permanent Notes/`** — Atomic evergreen notes (the slip-box)
- **`03-Resources/`** — Literature/source/meeting summaries; context notes
- **`Daily Notes/`** (optional) — Daily logs/journals; extract ideas to Permanent Notes

**Note:** For PARA integration, permanent notes can also live in `01-Projects/`, `02-Areas/`, or `03-Resources/` depending on context.

---

## Step-by-Step Processing

### Step 1: Pick Next File

**Sources to process:**
- Files in `00-Inbox/`
- Files tagged `#to-process`
- Fleeting notes older than 48 hours
- Daily notes from previous days

**Priority order:**
1. Oldest first (prevent staleness)
2. Tagged `#urgent` or `#high-priority`
3. Related to active projects

---

### Step 2: Read Fully

**Actions:**
1. Read the entire file from start to finish
2. If long (500+ words), create a quick outline of key sections
3. Identify the main topics/ideas discussed
4. Note any action items separately (handle with GTD workflow)

**Goal:** Understand the complete context before extraction

---

### Step 3: Identify Atomic Ideas

**What qualifies as an atomic idea?**
- ✅ Can stand alone and be useful in a different context
- ✅ Represents one core concept, insight, or principle
- ✅ Could be linked from multiple other notes
- ✅ Has value independent of the source material

**Not atomic:**
- ❌ Multiple unrelated concepts in one note
- ❌ Procedural checklists (these are workflows, not ideas)
- ❌ Project-specific context that only matters for that project
- ❌ Verbatim content without interpretation

**The Atomic Note Test:**
Ask: *"Can this idea stand alone and be useful in a different context?"*
- If **YES** → Extract as permanent note
- If **NO** → Keep in reference note or project note

**Examples:**

| Source Content | Atomic Ideas to Extract |
|----------------|------------------------|
| Meeting notes about product launch | - "Early user feedback reduces post-launch changes"<br>- "Launch checklists prevent critical oversights" |
| Article on productivity | - "Context switching costs 20-30 minutes of focus recovery"<br>- "Time blocking reduces decision fatigue" |
| Project retrospective | - "Async communication requires explicit decision logs"<br>- "Weekly demos maintain stakeholder alignment" |

---

### Step 4: Create Permanent Notes

For each atomic idea identified:

#### A. Check for Duplicates
**Before creating, search for existing notes:**
```
Use Grep to search for keywords related to the idea
If similar note exists:
  - Read the existing note
  - Enhance it with new insights (use Edit)
  - Add links between them if perspectives differ
If no similar note exists:
  - Proceed to create new note
```

#### B. Create the Note

**Location:**
- General use: `General/Permanent Notes/`
- Project-related: `01-Projects/{Business}/permanent-notes/`
- Area-related: `02-Areas/{Area}/permanent-notes/`
- Resource/reference: `03-Resources/{Topic}/`

**Filename:** Use a clear, descriptive title
- ✅ Good: `Context Switching Costs Focus Recovery Time.md`
- ❌ Bad: `Productivity Note 1.md`

**Template:** Use the atomic note template (see `atomic-note-template.md`)

**Content Guidelines:**
1. **Write in your own words** - Never copy-paste; always paraphrase
2. **Make it concrete** - Use specific examples
3. **Explain why it matters** - Implications, when to use, constraints
4. **Keep it short** - Aim for 100-300 words (exceptions allowed)
5. **Add minimal tags** - Prefer links over tags

---

### Step 5: Create/Update Reference Note

**When to create a reference note:**
- Source material has valuable context (book, article, meeting, video)
- Multiple permanent notes extracted from same source
- Source has additional details worth preserving
- Want to attribute ideas to original source

**When NOT to create reference note:**
- Single fleeting thought with no source
- Brain dump with no external source
- Already have reference for this source

**Reference Note Structure:**

```markdown
---
title: "Reference: [Source Title]"
created: "YYYY-MM-DD"
type: reference-note
source: "[URL or citation]"
tags:
  - reference
  - literature-note
---

# Reference: [Source Title]

**Type:** Book | Article | Video | Meeting | Course
**Author/Creator:** [Name]
**Date:** YYYY-MM-DD
**Source:** [URL or citation]

## Summary

[2-4 sentence overview of the source in your own words]

## Key Ideas

1. [First main idea - brief summary]
2. [Second main idea - brief summary]
3. [Third main idea - brief summary]

## Permanent Notes Extracted

- [[Note Title 1]]
- [[Note Title 2]]
- [[Note Title 3]]

## Quotes

> "[Notable quote if relevant]"

## Related

- [[Related Reference Notes]]
- [[Related Projects]]
```

---

### Step 6: Linking Pass

**For each new permanent note created:**

#### A. Link to Reference (if applicable)
In the permanent note's `## References` section:
```markdown
## References
- [[Reference: Source Title]]
- Source URL (if applicable)
```

#### B. Link to Related Permanent Notes

**How to find related notes:**
1. Use Grep to search for related keywords
2. Check your MOCs (Maps of Content)
3. Review recent permanent notes
4. Think about concepts that build on, contrast with, or connect to this idea

**Link structure:**
```markdown
## Links

### Related Concepts
- [[Related Note 1]] - How they relate
- [[Related Note 2]] - How they relate

### Broader Context
- [[MOC Name]] - Hub/index note for this topic

### Contrasts With
- [[Opposing View]] - Key difference
```

**Goal:** Aim for 3+ links per permanent note (no orphans!)

#### C. Add Backlinks (Optional)

**For highly related notes, add mentions in the related notes:**
1. Read the related note
2. Add a link in its "Related Concepts" or "See Also" section
3. Explain the connection briefly

**Example:**
```markdown
## Links
- [[Context Switching Costs Focus Recovery]] - Related: This explains why time blocking (this note) is effective
```

---

### Step 7: Update Checklist and Archive Source

#### A. Update Processing Checklist

**If using inbox checklist** (recommended):

File: `00-Inbox/inbox_checklist.md`

```markdown
## Inbox Processing Checklist

- [x] 2025-10-15-braindump.md → Processed, archived
- [x] Meeting Notes - Client Alpha.md → Processed, 3 permanents created
- [ ] Fleeting - Video idea.md → Pending
- [ ] Import - Book highlights.md → Pending
```

**Check off the file** you just processed with notes about what was created.

#### B. Move or Delete Source File

**Options:**

**1. Archive the source** (if has historical value):
- Move to `04-Archives/processed-sources/YYYY-MM/`
- Keep for reference in case you need to review original context

**2. Delete the source** (if fully extracted):
- If all valuable ideas extracted to permanent notes
- No future reference value
- Clutter reduction

**3. Convert to reference note** (if rich source):
- Rename and restructure as proper reference note
- Move to appropriate location in `03-Resources/`

**Decision criteria:**
- **Archive:** Meeting notes, project docs, rich sources
- **Delete:** Fleeting notes, brain dumps, redundant captures
- **Convert:** Books, articles, important meetings, courses

#### C. Remove Processing Tags

If the file had `#to-process`, remove it:
```yaml
tags:
  - to-process  # ← Remove this
```

---

### Step 8: Repeat

Continue with the next file in the inbox until:
- Inbox is empty, OR
- Processing time limit reached (e.g., 30 minutes)

**Best practice:** Process inbox 3x per week minimum (daily is ideal)

---

## Quality Guardrails

### 1. No Duplicates

**Before creating any permanent note:**
- Search for existing notes on the same topic
- If exists: Enhance rather than duplicate
- If perspectives differ: Create new note but link to existing one

### 2. No Orphans

**Every permanent note must have:**
- At least 1 outbound link (to related note, MOC, or reference)
- Ideally 3+ links for rich connections
- Links should be meaningful, not forced

**Exception:** Brand new topic areas may start with fewer links, but add more during reviews

### 3. Keep It Short

**Target length:** 100-300 words for most permanent notes

**Exceptions allowed:**
- Complex frameworks (may need 500-800 words)
- Step-by-step processes
- Foundational concepts requiring thorough explanation

**If exceeding 500 words:**
- Review for atomicity - can it be split?
- Ensure it's truly one core idea
- Consider creating sub-notes and a hub note

### 4. Own Words Required

**Never copy-paste content** from sources into permanent notes

**Always:**
- Read and understand
- Close the source
- Write the idea in your own words
- Add your interpretation and examples

**Why:** This ensures understanding and makes the note truly yours

---

## Processing Different Source Types

### Brain Dumps

**Characteristics:** Stream of consciousness, mixed topics, incomplete thoughts

**Processing approach:**
1. Read entire dump to identify distinct ideas
2. Separate action items (→ GTD workflow)
3. Separate project updates (→ Update project notes)
4. Extract atomic ideas (→ Permanent notes)
5. Capture reference info (→ Reference notes)
6. Archive the original dump

**Example:** A 500-word brain dump might yield:
- 3 action items → Added to project task lists
- 1 project update → Appended to project note
- 2 permanent notes → New atomic ideas
- 1 reference note → For meeting that occurred

### Imported Highlights (Books, Articles)

**Characteristics:** Quotes and highlights from external sources

**Processing approach:**
1. Read all highlights together to see themes
2. Group related highlights
3. For each group, create ONE permanent note that synthesizes the ideas
4. Create reference note for the source with all highlights
5. Link permanent notes to reference note
6. Archive or delete the import file

**Avoid:** Creating one permanent note per highlight (too granular, not atomic)

### Meeting Notes

**Characteristics:** Discussion summary, decisions made, action items

**Processing approach:**
1. Extract action items → Add to project task lists or GTD system
2. Extract decisions → Create/update decision log
3. Extract insights → Create permanent notes for reusable ideas
4. Convert the meeting note itself to a reference note
5. Link everything together

**Example meeting note might yield:**
- 5 action items → Task lists
- 1 decision → Decision log entry
- 2 permanent notes → "Early demos reduce misalignment", "Async updates need decision logs"
- Meeting note itself → Becomes reference note in `03-Resources/{Client}/`

### Fleeting Notes

**Characteristics:** Quick captures, single thoughts, rough ideas

**Processing approach:**
1. If idea is solid → Expand into permanent note with template
2. If needs research → Create research task, archive fleeting note
3. If no longer relevant → Delete
4. If still unclear → Keep in inbox for later review (max 1 week)

**Goal:** Fleeting notes should not exist longer than 1 week

### Daily Notes

**Characteristics:** Journal entries, daily logs, mixed content

**Processing approach:**
1. Scan for insights or learnings → Extract to permanent notes
2. Scan for action items → Add to GTD system
3. Scan for reference info → Add to appropriate reference notes
4. Leave daily note as-is (it's a log, not meant to be processed)
5. Do NOT delete daily notes (they're a historical record)

**Note:** Daily notes are exempt from "inbox zero" - they're meant to accumulate

---

## Integration with PARA

### Projects (01-Projects/)

**Permanent notes related to active projects:**
- Can be created within project folders
- Should still follow atomic principle
- Link to project note for context
- When project completes, permanent notes stay (don't archive)

**Example:**
```
01-Projects/
  Client-Website-Redesign/
    Project Brief.md
    permanent-notes/
      Navigation Patterns Affect User Retention.md
      Mobile-First Reduces Desktop Complexity.md
```

**After project completes:**
- Move project brief to Archives
- Move permanent notes to `General/Permanent Notes/` or relevant `03-Resources/` folder

### Areas (02-Areas/)

**Permanent notes related to ongoing areas:**
- Create in area folder if highly specific to that area
- Create in general `Permanent Notes/` if broadly applicable
- Link to area MOC or index

### Resources (03-Resources/)

**This is where most reference notes and topic-based permanent notes live:**
```
03-Resources/
  Video-Production/
    permanent-notes/
      Hook in First 3 Seconds Increases Retention.md
      B-Roll Covers Jump Cuts.md
    references/
      Reference: YouTube Creator Handbook.md
```

---

## Dataview Queries for Processing

### Show Unprocessed Inbox Items

```dataview
TABLE file.ctime as "Captured", file.mtime as "Modified"
FROM "00-Inbox"
WHERE !contains(file.name, "inbox_checklist")
SORT file.ctime ASC
```

### Show Fleeting Notes Older Than 2 Days

```dataview
TABLE file.ctime as "Age"
FROM "00-Inbox"
WHERE contains(tags, "fleeting") AND (date(now) - file.ctime).days > 2
SORT file.ctime ASC
```

### Show Orphan Notes (No Links)

```dataview
TABLE file.outlinks as "Outbound Links"
FROM "Permanent Notes"
WHERE length(file.outlinks) = 0
```

### Show Recently Created Permanent Notes

```dataview
TABLE created, tags
FROM "Permanent Notes"
WHERE type = "permanent-note"
SORT created DESC
LIMIT 10
```

---

## Weekly Processing Ritual

**Time:** 30-45 minutes, scheduled

**Steps:**

1. **Inbox Review (15 min)**
   - Process all items in `00-Inbox/`
   - Target: Get to zero

2. **Linking Pass (10 min)**
   - Review last week's permanent notes
   - Add additional links as connections emerge
   - Check for orphans

3. **Quality Check (10 min)**
   - Scan for duplicates
   - Verify atomic principle (split if needed)
   - Enhance unclear notes

4. **Archive (5 min)**
   - Move processed sources to archives
   - Clean up inbox checklist
   - Update MOCs with new permanent notes

---

## Common Mistakes to Avoid

### Mistake 1: Creating Notes That Are Too Big
**Problem:** "Productivity Tips" with 10 different concepts
**Solution:** Split into 10 atomic notes, create MOC to link them

### Mistake 2: Copy-Pasting Instead of Paraphrasing
**Problem:** Permanent notes are just quotes from sources
**Solution:** Read → Close → Write in your own words

### Mistake 3: Skipping the Reference Note
**Problem:** Lost source attribution, can't find original context
**Solution:** Always create reference notes for external sources

### Mistake 4: Creating Orphans
**Problem:** Permanent notes with zero links
**Solution:** Force yourself to add 3 links before considering note "done"

### Mistake 5: Over-Processing
**Problem:** Spending 2 hours perfecting a single note
**Solution:** Rough is better than missing. Progressive elaboration means notes improve over time

### Mistake 6: Keeping Everything
**Problem:** Inbox never empties because "might need it"
**Solution:** If no atomic idea can be extracted, it's okay to delete

---

## Success Metrics

**Healthy processing habits:**
- Inbox processed to zero 3x per week minimum
- Average 2-5 permanent notes created per processing session
- 90%+ of permanent notes have 3+ links
- Less than 5% orphan notes
- Fleeting notes processed within 48 hours

---

## Related References

- **Atomic Note Template:** `atomic-note-template.md` - Template structure
- **PARA + Zettelkasten:** `para-zettelkasten.md` - Methodology overview
- **Tagging Strategy:** `tagging-strategy.md` - How to tag notes

---

**Remember:** The goal is to transform raw captures into a connected knowledge network. Quality of connections matters more than quantity of notes.

---

**Tags:** #zettelkasten #processing #workflow #knowledge-management
