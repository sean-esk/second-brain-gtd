---
name: obsidian-mastery
description: This skill provides comprehensive knowledge of Obsidian-specific markdown formatting, YAML frontmatter conventions, Bases syntax (.base files), PARA methodology, tagging strategy, and Second Brain organization principles. Claude should use this skill whenever working with Obsidian vault files, creating or editing notes, configuring Bases, or organizing knowledge using the PARA + Zettelkasten system.
---

# Obsidian Mastery

This skill equips Claude with deep knowledge of Obsidian vault organization, markdown conventions, and specialized features like Bases, YAML frontmatter, and the PARA + Zettelkasten methodology.

## When to Use This Skill

Use this skill whenever:
- Creating or editing notes in an Obsidian vault
- Setting up YAML frontmatter properties
- Creating or configuring `.base` files
- Organizing notes using PARA methodology (Projects, Areas, Resources, Archives)
- Applying tagging strategies
- Working with Zettelkasten-style atomic notes
- Processing inbox items into permanent notes
- Building or debugging Bases views, filters, and formulas

## Core Principles

### PARA + Zettelkasten Hybrid System

This vault uses **PARA for organization** (folder structure) and **Zettelkasten for note-taking** (atomic notes, bidirectional linking).

**PARA Decision Framework:**
- Has deadline or end state? → `01-Projects/`
- Continuous responsibility? → `02-Areas/`
- Just reference material? → `03-Resources/`
- Done/inactive? → `04-Archives/`
- Not sure yet? → `00-Inbox/` (process later)

**Zettelkasten Principles:**
- **Atomic** - One idea per permanent note
- **Connected** - Link liberally using `[[double brackets]]`
- **Own Words** - Paraphrase, don't copy
- **Progressive** - Notes evolve over time

### Folder Structure

```
General/
├── 00-Inbox/              # Unprocessed captures
├── 01-Projects/           # Active projects with deadlines
├── 02-Areas/              # Ongoing responsibilities
├── 03-Resources/          # Reference materials
├── 04-Archives/           # Completed/inactive
├── 05-Meta/               # System docs, templates, MOCs
├── Templates/             # Note templates
└── Workflows/             # .base files for dashboards
```

## YAML Frontmatter Conventions

Every note should include YAML frontmatter following these conventions:

### Standard Properties

```yaml
---
title: "Note Title"
created: "YYYY-MM-DD"
tags:
  - tag1
  - tag2
status: active|draft|completed
type: project|area|resource|reference-note|permanent-note
related:
  - "[[Related Note]]"
---
```

### Obsidian-Specific Property Types

Obsidian recognizes specific property types:
- **Text** - Plain strings
- **List** - Arrays (use YAML list syntax)
- **Number** - Integers or decimals
- **Checkbox** - Boolean (true/false)
- **Date** - ISO format `YYYY-MM-DD`
- **Date & Time** - ISO format `YYYY-MM-DDTHH:mm:ss`

### Important Rules

1. **Always use YAML lists for tags:**
   ```yaml
   tags:
     - youtube
     - video-idea
   ```

2. **Quote string values with special characters:**
   ```yaml
   title: "Building a Second Brain: Complete Guide"
   ```

3. **Date format must be ISO:**
   ```yaml
   created: "2025-10-18"
   ```

4. **Custom properties are supported:**
   - Can create any property name (use kebab-case for consistency)
   - Bases and Dataview can query custom properties

## Obsidian Bases Syntax

Bases are dynamic table views stored as `.base` files in YAML format.

### File Structure

```yaml
formulas:
  # Calculated properties

properties:
  # Column display configuration

views:
  # Table views with filters and sorting
```

### Critical Bases Rules

1. **No source/FROM section** - Bases include ALL vault files by default
2. **MUST filter by folder in each view:**
   ```yaml
   filters:
     and:
       - file.inFolder("folder-path")
   ```

3. **Formula syntax:**
   - Arithmetic operators MUST have spaces: `(a + b)` not `(a+b)`
   - Use null coalescing for missing values: `(value ?? 0)`
   - Wrap entire formula in single quotes: `'expression'`

4. **Filter syntax:**
   - String comparisons: `'status == "active"'` (double quotes inside single quotes)
   - Numeric comparisons: `'score > 10'` (no quotes on numbers)
   - Root-level filters MUST have and/or/not wrapper

For complete Bases reference, load `references/bases-syntax.md`.

## Tagging Strategy

Use nested tags for hierarchical organization:

### Status Tags
```
#status/fleeting
#status/developing
#status/active
#status/completed
```

### Business Tags
```
#youtube
#level-method
#eskerium
#polar-gold
#consulting
```

### Type Tags
```
#video-idea
#meeting-notes
#project-plan
#reference
#permanent-note
```

### Tagging Rules

1. **Always include:**
   - Status tag (#status/*)
   - Type tag (#video-idea, #meeting-notes, etc.)
   - Business tag (if applicable)

2. **Tags vs Folders:**
   - Folders = WHERE (organization/actionability)
   - Tags = WHAT (discovery/categorization)

3. **Tag liberally but consistently**

## Note Creation Guidelines

### File Naming Conventions

- **Projects:** Descriptive names (`Product Launch 2025.md`)
- **Daily Notes:** `YYYY-MM-DD` format
- **Video Ideas:** Descriptive title (`Video Idea - Building Second Brain.md`)
- **Meeting Notes:** `YYYY-MM-DD - Meeting Topic.md`

### Where to Create Files

**New Ideas/Captures** → `00-Inbox/` (process later)

**YouTube Video Ideas** → `00-Inbox/Video-Ideas/`

**Projects** → `01-Projects/{Business-Name}/`

**Reference Material** → `03-Resources/{Topic}/`

**Templates** → `General/Templates/`

### Note Structure Best Practices

1. **Include descriptive title** in frontmatter AND as H1
2. **Add creation date** in `created` property
3. **Link to related notes** using `[[double brackets]]`
4. **Use atomic note principle** - one core idea per permanent note
5. **Write for future self** - assume context will be forgotten

## Working with Existing Files

### Before Editing

1. **Read the file first** to understand current state
2. **Check frontmatter** for existing properties
3. **Preserve existing formatting** and conventions
4. **Maintain existing links** and references

### Updating Files

To update existing notes:
- Use `Edit` tool for targeted changes
- Preserve YAML frontmatter structure
- Maintain existing tagging patterns
- Keep related links intact

## References

For detailed information on specific topics, load these reference files as needed:

- **Bases Syntax:** `references/bases-syntax.md` - Complete .base file syntax reference
- **PARA Methodology:** `references/para-zettelkasten.md` - Organization principles
- **Tagging Strategy:** `references/tagging-strategy.md` - Comprehensive tag hierarchy and usage guide
- **Linking Strategy:** `references/linking-strategy.md` - How to create meaningful connections between notes, MOC management
- **Zettelkasten Processing:** `references/zettelkasten-processing.md` - Step-by-step workflow for processing raw notes into atomic permanent notes
- **Atomic Note Template:** `references/atomic-note-template.md` - Streamlined template structure and usage guide
- **Processing Decision Tree:** `references/processing-decision-tree.md` - When to use `/process-inbox` vs `/process-raw-notes`

**When to load references:**
- Load `zettelkasten-processing.md` when processing inbox items, converting fleeting notes, or extracting ideas from sources
- Load `atomic-note-template.md` when creating new permanent notes or refining existing notes
- Load `linking-strategy.md` when creating MOCs, adding links to notes, or managing knowledge connections
- Load `processing-decision-tree.md` when uncertain which processing command to use
- Load `tagging-strategy.md` when setting up tags or reviewing tagging consistency
- Load `bases-syntax.md` when creating or debugging .base files
- Load `para-zettelkasten.md` when organizing notes or deciding folder placement

Load references only when needed to keep context lean.

## Key Principles for Note Creation

### Permanent Notes Must Be Connected

**Requirement:** Every permanent note needs at least 3 links.

**Why:** Isolated notes are useless. The power is in the connections.

**When creating permanent notes:**
1. **Search for related notes** using Grep (search for keywords from the concept)
2. **Identify connections:**
   - What does this build on?
   - What does this contrast with?
   - What examples or applications exist?
3. **Add meaningful link explanations:**
   - Not just `[[Note]]`
   - But `[[Note]] - How they relate (builds on, contrasts, supports, etc.)`

**Load `linking-strategy.md` reference for:**
- Types of links (hierarchical, associative, source)
- How to explain relationships
- MOC (Map of Content) concepts
- Building knowledge networks

### Processing Workflow Integration

**During `/process-inbox` when creating fleeting notes:**
- Capture the thought quickly
- Mark for later development
- User will manually convert fleeting → permanent when they have time

**When user creates permanent notes manually:**
- Use Permanent Note template
- Search vault for related notes
- Add 3+ meaningful links
- Link to MOC if topic area exists
- Explain all relationships

---

## Integration with Commands

This skill works with:
- `/process-inbox` - Provides structure for fleeting notes and reference notes
- `/setup` - Creates initial folder structure
- Standard Read/Write/Edit tools - File operations
- Grep/Glob tools - Search for related notes when linking
