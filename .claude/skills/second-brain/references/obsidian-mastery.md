# Obsidian Conventions & Best Practices

> Guide to working with Obsidian vaults in the Second Brain system

---

## YAML Frontmatter

Every note should have YAML frontmatter at the top:

```yaml
---
title: "Note Title"
created: "YYYY-MM-DD"
type: project|area|permanent-note|fleeting-note|reference-note|daily-plan
status: active|draft|completed|inbox
tags:
  - tag1
  - tag2
related:
  - "[[Related Note 1]]"
  - "[[Related Note 2]]"
---
```

### Required Fields

| Field | Description |
|-------|-------------|
| `title` | Human-readable title |
| `created` | Date created (YYYY-MM-DD) |
| `type` | Note type (see below) |
| `status` | Current state |
| `tags` | List of tags |

### Note Types

- `project` - Multi-step outcome with deadline
- `area` - Ongoing responsibility
- `permanent-note` - Atomic Zettelkasten note
- `fleeting-note` - Temporary capture
- `reference-note` - External source summary
- `daily-plan` - Daily planning document
- `meeting-note` - Meeting documentation
- `excalidraw` - Visual diagram (flowchart, concept map, etc.)

---

## Linking Strategy

### Internal Links

Use `[[double brackets]]` for all internal links:

```markdown
See [[Project Name]] for details.
Related to [[Concept Note]].
```

### Link Guidelines

1. **Link liberally** - More connections = more value
2. **Explain relationships** - Don't just link, explain why
3. **Minimum 3 links** - For permanent notes
4. **Bidirectional aware** - Obsidian tracks backlinks automatically

### Link Patterns

**Contextual linking:**
```markdown
This relates to [[Time Management]] because...
```

**List linking:**
```markdown
## Related
- [[Note 1]] - How it relates
- [[Note 2]] - Why it's connected
```

---

## File Naming

### Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Projects | Descriptive | `Website-Redesign.md` |
| Daily Plans | Date | `2025-12-10.md` |
| Permanent Notes | Concept | `Context-Switching-Reduces-Focus.md` |
| Meeting Notes | Date + Topic | `2025-12-10 - Team Sync.md` |
| MOCs | MOC - Topic | `MOC - Productivity.md` |
| Excalidraw | Descriptive | `System-Architecture.excalidraw.md` |

### Rules

- Use hyphens for spaces
- Use Title-Case
- Be descriptive but concise
- No special characters except hyphens

---

## Tagging Strategy

### Tag Categories

**Status Tags:**
```
#status/inbox
#status/active
#status/completed
#status/someday
```

**Type Tags:**
```
#project
#permanent-note
#fleeting-note
#meeting-note
```

**Context Tags (for tasks):**
```
#context/computer
#context/phone
#context/office
#context/home
#context/errands
```

**Energy Tags (for tasks):**
```
#energy/high
#energy/medium
#energy/low
```

**Time Tags (for tasks):**
```
#time/5m
#time/15m
#time/30m
#time/1h
#time/2h
#time/4h+
```

### Tag Rules

1. Use lowercase with hyphens
2. Use hierarchy with `/` (e.g., `#status/active`)
3. Maximum 5-7 tags per note
4. Every note needs at least `type` and `status` tags

---

## Note Templates

### Project Template

```markdown
---
title: "{{Project Name}}"
created: "{{YYYY-MM-DD}}"
type: project
status: active
priority: high|medium|low
tags:
  - project
  - {{area-tag}}
---

# {{Project Name}}

## Desired Outcome

What does "done" look like?

---

## High Priority

<!-- Urgent/important tasks -->

## Next Actions

<!-- Regular priority tasks -->

## Someday/Maybe

<!-- Lower priority items -->

## Waiting On

<!-- Blocked by others -->

## Completed

<!-- Finished tasks with dates -->

---

## Notes

```

### Permanent Note Template

```markdown
---
title: "{{Concept Title}}"
created: "{{YYYY-MM-DD}}"
type: permanent-note
status: active
tags:
  - permanent-note
  - {{topic-tag}}
related:
  - "[[Related Note 1]]"
  - "[[Related Note 2]]"
---

# {{Concept Title}}

## Core Idea

[Your insight in your own words]

## Why This Matters

[Explanation of significance]

## Connections

- [[Note 1]] - How it relates
- [[Note 2]] - Why connected
- [[Note 3]] - Application

## Sources

[If applicable]
```

### Area Template

```markdown
---
title: "{{Area Name}}"
created: "{{YYYY-MM-DD}}"
type: area
status: active
tags:
  - area
  - {{area-tag}}
---

# {{Area Name}}

> {{Brief description}}

---

## High Priority Tasks

<!-- Urgent/important items -->

## Next Actions / Current Tasks

<!-- Regular priority items -->

## Someday/Maybe

<!-- Lower priority/exploratory -->

## Waiting On

<!-- Blocked by dependencies -->

## Completed

<!-- Finished tasks with dates -->
```

---

## ADHD-Friendly Editing Principles

The system is designed for users who may have ADHD:

1. **Read the entire document first** - Understand existing structure
2. **Make targeted edits** - Update specific sections, don't append
3. **Never just add to the bottom** - Unless explicitly asked
4. **Keep it concise** - Remove redundancy
5. **One plan, not many** - Replace old plans, don't add "revised" sections

**Bad:** Adding "REVISED PLAN" section below "TODAY'S PLAN"
**Good:** Replacing "TODAY'S PLAN" content with updated tasks

---

## Unified Task Structure

**ALL Projects, Areas, and Relationship notes use identical priority sections:**

```markdown
## High Priority / Critical

Urgent/important items - scanned FIRST by daily planning

## Next Actions / Current Tasks

Regular priority items - scanned SECOND

## Someday/Maybe

Lower priority/exploratory - SKIPPED by daily planning

## Waiting On

Blocked by external dependencies

## Completed

Finished tasks with dates
```

This consistency allows automated scanning across all note types.

---

## Working with Files

### Before Editing

1. **Read the entire file first**
2. **Understand existing structure**
3. **Identify the specific section to update**

### When Editing

1. **Make targeted changes** - Don't rewrite entire file
2. **Preserve formatting** - Match existing style
3. **Update metadata** - Modify frontmatter if status changed
4. **Maintain links** - Don't break existing connections

### Creating New Files

1. **Use appropriate template**
2. **Fill all required frontmatter**
3. **Add initial links** (minimum 3 for permanent notes)
4. **Place in correct folder**

---

## Folder Guidelines

### Max Depth: 3 Levels

Good:
```
01-Projects/
  Client-Work/
    Project-Name.md
```

Too Deep:
```
01-Projects/
  2025/
    Q1/
      Client-Work/
        Project-Name.md
```

### Required Folders

```
{{vaultPath}}/
├── 00-Inbox/Daily/
├── 00-Inbox/Fleeting-Notes/
├── 01-Projects/
├── 02-Areas/
├── 02-Areas/Relationships/
├── 03-Resources/Reference-Notes/
├── 04-Archives/
├── Daily Plans/
├── Meeting Notes/
├── Permanent Notes/
└── Templates/
```

---

## Quality Checklist

### For Permanent Notes

- [ ] **Atomic** - One clear idea, 100-300 words
- [ ] **Connected** - 3+ meaningful links with explanation
- [ ] **Own Words** - Paraphrased, not copied
- [ ] **Complete Metadata** - All required frontmatter

### For Projects

- [ ] **Has Next Action** - Concrete physical action defined
- [ ] **Has Status** - Current workflow state tracked
- [ ] **Has Priority** - Relative importance specified
- [ ] **Links to Resources** - Connected to relevant notes
