# Tagging Strategy

> Comprehensive guide to using tags effectively in the Second Brain system

---

## Core Philosophy

**Tags vs Folders:**
- **Folders** = WHERE (organization based on actionability - PARA)
- **Tags** = WHAT (discovery and categorization)

**When to use what:**
- Use folders for ONE primary organizational dimension (actionability)
- Use tags for EVERYTHING else (topic, status, type, business, etc.)

---

## Tag Hierarchy

Use nested tags with forward slashes (`/`) to create hierarchical structure:

```
#parent/child
#parent/child/grandchild
```

**Benefits:**
- Organized categorization
- Can query at any level
- Clear relationships
- Scalable structure

---

## Standard Tag Categories

### 1. Type Tags (Required - ONE per note)

Every note gets exactly ONE type tag defining its purpose:

**GTD Working Documents (Execution):**
```
#project          # Active project with deadline (multi-step outcome)
#task             # Single actionable item
#area             # Ongoing responsibility (no end date)
```

**Knowledge Notes (Learning):**
```
#permanent-note   # Atomic, evergreen knowledge (Zettelkasten)
#fleeting-note    # Temporary capture (process within 48 hours)
#reference-note   # Summary of external source
#literature-note  # Notes from books, articles, videos
```

**System Notes:**
```
#moc              # Map of Content (navigation hub)
#meeting-note     # Meeting summary (was: meeting-notes)
#review           # Weekly/monthly review summary
#brain-dump       # Archived brain dump
#template         # Note template
#system           # System documentation
#video-idea       # YouTube video idea
#daily-note       # Daily journal entry
#brainstorm       # Brainstorming session
#decision-log     # Decision documentation
```

**Usage:**
- Required on ALL notes
- Exactly ONE type tag per note
- Enables filtering by note purpose

---

### 2. Status Tags

Track workflow state - different for GTD working documents vs knowledge notes:

**For GTD Working Documents (projects, tasks, areas):**
```
#status/inbox      # Just captured, not yet processed
#status/next       # Ready to work on, next action defined
#status/active     # Currently working on this
#status/waiting    # Blocked by external dependency
#status/someday    # Might do later, deprioritized
#status/deferred   # Paused temporarily
#status/done       # Completed, not yet archived
#status/archived   # Completed and filed away
#status/cancelled  # Decided not to do
```

**For Knowledge Notes (permanent notes, reference notes):**
```
#status/fleeting     # Temporary thought (same as fleeting-note type)
#status/developing   # Being refined into permanent note
#status/evergreen    # Mature, stable permanent note
```

**Usage:**
- Required for projects, tasks, and areas
- Optional for knowledge notes (permanent notes are inherently evergreen)
- Update as work progresses
- Used heavily in Bases for filtering

**Status Progression:**
```
GTD: inbox → next → active → waiting → done → archived
              ↓
          someday

Knowledge: fleeting → developing → evergreen
```

---

### 2. Business/Area Tags

Identify which business, project area, or life domain the note relates to.

**These are customized during `/setup` based on your specific needs.**

**Common examples:**
```
#work                  # Work-related
#personal              # Personal life
#side-business          # Side projects or business
#learning              # Educational pursuits
#health-fitness        # Health and wellness
#content-creation      # If you create content
```

**Usage:**
- Add to notes related to specific areas
- Allows filtering all notes for one business/area
- Can have multiple area tags if relevant
- These are **your** tags - customize them!

**Examples:**
```yaml
tags:
  - work
  - project
  - status/active
```

---

### 3. Type Tags

Categorize by the kind of note or content.

```
#video-idea           # YouTube video concepts
#meeting-notes        # Notes from meetings
#project-plan         # Project planning documents
#reference            # Reference material
#permanent-note       # Zettelkasten permanent notes
#literature-note      # Notes from external sources
#daily-note           # Daily journal entries
#brainstorm           # Brainstorming sessions
#decision-log         # Decision documentation
```

**Usage:**
- Identifies the note format/purpose
- Usually one type tag per note
- Helps with template application

**Examples:**
```yaml
tags:
  - meeting-notes
  - work
  - status/active
```

---

### 4. Content Category Tags (Optional - For Content Creators)

If you create content (videos, blog posts, etc.), categorize by content theme:

**Customize these based on your content themes:**

```
#content/tutorial         # How-to and educational
#content/opinion          # Commentary and perspectives
#content/review           # Product/service reviews
#content/story            # Narrative and storytelling
#content/showcase         # Project showcases
```

**Usage:**
- Helps organize content ideas by theme
- Ensures variety across content types
- Can query by content category
- **Optional** - Only use if you create content

---

### 5. Priority Tags

For tasks and projects:

```
#priority/high
#priority/medium
#priority/low
#priority/urgent
```

**Usage:**
- Optional, use for task/project prioritization
- Useful in combination with status tags
- Can filter in Bases for priority views

---

### 6. Context Tags (GTD - for tasks only)

Physical location or tools required to complete tasks:

```
#context/office      # At office desk with office resources
#context/computer    # Any computer work (home or office)
#context/phone       # Phone calls, mobile work
#context/home        # Home-specific errands or tasks
#context/errands     # Out and about (shopping, appointments)
#context/anywhere    # Can do from any location
```

**Usage:**
- Use ONLY on tasks (not projects, areas, or permanent notes)
- Required for task filtering in `/what-next` and `/daily-plan`
- Enables context-based work filtering in Bases
- One context per task (pick the primary requirement)

**Examples:**
```yaml
# Computer work task
tags:
  - task
  - side-business
  - status/next
  - context/computer
  - energy/high
  - time/2h

# Phone call task
tags:
  - task
  - consulting
  - status/next
  - context/phone
  - energy/medium
  - time/15m
```

---

### 7. Energy Tags (GTD - for tasks only)

Energy level required to complete tasks (ADHD optimization):

```
#energy/high      # Peak focus, creativity, complex thinking
#energy/medium    # Standard work, moderate concentration
#energy/low       # Admin, simple tasks, minimal thinking
```

**Usage:**
- Use ONLY on tasks (not projects, areas, or permanent notes)
- Helps match tasks to current energy state
- Used in `/daily-plan` to match tasks to your energy level
- Consider time of day (high energy typically = morning)

**Energy Level Guidelines:**

**High Energy:**
- Writing, coding, creative work
- Complex problem-solving
- Strategic planning
- Important presentations

**Medium Energy:**
- Email responses
- Standard meetings
- Research and reading
- Project planning

**Low Energy:**
- Filing, organizing
- Data entry
- Routine admin
- Simple cleanup tasks

---

### 8. Time Tags (GTD - for tasks only)

Estimated time to complete task:

```
#time/5m       # Quick wins (< 5 minutes)
#time/15m      # Short tasks (5-15 minutes)
#time/30m      # Half-hour tasks (15-30 minutes)
#time/1h       # Hour-long focus work (30-60 minutes)
#time/2h       # Deep work sessions (1-2 hours)
#time/4h+      # Project marathons (2+ hours)
```

**Usage:**
- Use ONLY on tasks (not projects, areas, or permanent notes)
- Helps fill gaps between meetings
- Enables time-based filtering
- Be realistic (add buffer to estimates)

---

### 9. Topic Tags

General topic/subject tags (use sparingly):

**Knowledge Topics (for permanent notes):**
```
#productivity        # Productivity systems, time management
#content-production    # Video creation, editing, YouTube
#business-strategy   # Business planning, operations
#ai-technology       # AI, machine learning, automation
#marketing           # Marketing, growth, content strategy
#development         # Software development, coding
#learning            # Learning techniques, education
#health              # Health, fitness, wellness
#creativity          # Creative process, ideation
#communication       # Communication skills, writing
#finance             # Financial management
```

**Work Topics (for projects/tasks):**
```
#research            # Research-heavy work
#content-creation    # Creating content
#client-work         # Client-facing work
#operations          # Business operations
#strategy            # Strategic planning
#admin               # Administrative tasks
```

**Usage:**
- 1-2 topic tags per note maximum
- Use for both working documents and knowledge notes
- Enables cross-domain knowledge discovery
- Don't go overboard - folder structure handles much of this
- Use for cross-cutting themes

---

## Tagging Rules & Best Practices

### Required Tags

**Every note MUST have:**
1. **Status tag** - `#status/*`
2. **Type tag** - What kind of note it is

**Additionally include:**
3. **Business tag** - If applicable
4. **Topic tags** - As relevant (1-3 max)

### Tag Naming Conventions

1. **Use lowercase** - `#video-idea` not `#Video-Idea`
2. **Use hyphens for spaces** - `#meeting-notes` not `#meeting_notes` or `#meetingnotes`
3. **Be consistent** - Pick one naming pattern and stick to it
4. **Keep short** - `#content-creation` not `#content-creation-channel-content`
5. **Nested hierarchy** - Use `/` for parent/child relationships

### Tag Limits

**Don't go tag-crazy:**
- Maximum 5-7 tags per note
- More tags = less useful
- Quality over quantity
- If you need more than 7 tags, rethink your approach

### YAML Frontmatter Format

**Always use list syntax:**

```yaml
# ✅ Correct
tags:
  - youtube
  - video-idea
  - status/active

# ❌ Wrong
tags: [youtube, video-idea, status/active]

# ❌ Wrong
tags: youtube, video-idea, status/active
```

---

## Tag Usage by Note Type

### GTD Working Documents

**Project Note:**
```yaml
tags:
  - project
  - youtube  # Business
  - content-creation  # Topic
  - status/active
```

**Task Note:**
```yaml
tags:
  - task
  - side-business  # Business
  - development  # Topic
  - status/next
  - context/computer
  - energy/high
  - time/2h
```

**Area Note:**
```yaml
tags:
  - area
  - work-project  # Business
  - status/active
```

---

### Knowledge Notes

**Permanent Note:**
```yaml
tags:
  - permanent-note
  - productivity  # Topic
  - status/evergreen
```

**Reference Note:**
```yaml
tags:
  - reference-note
  - business-strategy  # Topic
  - learning
```

**Fleeting Note:**
```yaml
tags:
  - fleeting-note
  - ai-technology  # Topic
  - status/fleeting
```

---

### System Notes

**MOC (Map of Content):**
```yaml
tags:
  - moc
  - productivity  # Topic
```

**Meeting Note:**
```yaml
tags:
  - meeting-note
  - work-project  # Business
```

**YouTube Video Idea:**
```yaml
tags:
  - video-idea
  - youtube
  - spark  # Content type
  - youtube/building  # Content pillar
```

**Daily Note:**
```yaml
tags:
  - daily-note
```

**Brain Dump:**
```yaml
tags:
  - brain-dump
```

**Review:**
```yaml
tags:
  - review
  - weekly-review
```

---

## Tag Queries in Bases

Tags can be filtered in Bases using the `taggedWith()` function:

```yaml
filters:
  and:
    - file.inFolder("01-Projects")
    - taggedWith(file.file, "youtube")
```

**Multiple tag filter (OR):**
```yaml
filters:
  and:
    - file.inFolder("01-Projects")
    - or:
        - taggedWith(file.file, "youtube")
        - taggedWith(file.file, "work-project")
```

**Nested tag matching:**
```yaml
# This matches #status/active, #status/developing, etc.
filters:
  and:
    - taggedWith(file.file, "status")
```

---

## Tag Search Patterns

### Find All Active YouTube Ideas

```
tag:#content-creation tag:#status/active
```

### Find All Meeting Notes for Level Method

```
tag:#meeting-notes tag:#work-project
```

### Find High Priority Active Projects

```
tag:#project-plan tag:#priority/high tag:#status/active
```

### Find All Content in a Pillar

```
tag:#content/business
```

---

## Tag Maintenance

### Weekly Review Checklist

During weekly reviews, check:

- [ ] All new notes have required tags
- [ ] Status tags are up-to-date
- [ ] No orphaned tags (typos, unused)
- [ ] Tag usage is consistent
- [ ] Notes properly categorized

### Tag Cleanup

**Periodically review:**
- Unused tags (can delete)
- Misspelled tags (fix)
- Redundant tags (consolidate)
- Overly specific tags (generalize)

**Use Obsidian's tag pane:**
- See all tags in vault
- Click to see tagged notes
- Identify outliers

---

## Common Tag Patterns

### Active Work Queue

```yaml
tags:
  - status/active
  - priority/high
  - youtube
```

Query these for "what to work on now"

### Knowledge Base

```yaml
tags:
  - permanent-note
  - reference
  - status/active
```

Query these for evergreen knowledge

### Business-Specific Projects

```yaml
tags:
  - project-plan
  - work-project
  - status/active
```

Filter by business for focused context

### Content Pipeline

```yaml
tags:
  - youtube
  - video-idea
  - status/developing
```

Track video ideas through production

---

## Anti-Patterns (Things to Avoid)

### ❌ Tag Explosion

**Problem:** 50+ unique tags, most used once

**Solution:** Consolidate, use folders instead

### ❌ Redundant Tags

**Problem:** `#video-idea #content-creation-video-idea #content-creation`

**Solution:** Pick ONE consistent tag

### ❌ No Tag Hierarchy

**Problem:** `#status-active`, `#status-developing`, etc. (flat)

**Solution:** Use hierarchy: `#status/active`, `#status/developing`

### ❌ Inconsistent Naming

**Problem:** `#YouTube`, `#content-creation`, `#Youtube`

**Solution:** Pick one: `#content-creation`

### ❌ Tag Soup

**Problem:** 15 tags on a single note

**Solution:** Limit to 5-7 max, rethink structure

---

## Tag Migration Workflow

When migrating from other systems:

1. **Audit existing tags** - List all current tags
2. **Map to new system** - Decide new tag structure
3. **Batch update** - Use find/replace or scripts
4. **Document** - Add to this guide
5. **Review** - Check consistency after migration

---

## Quick Reference

### Must-Have Tags

```yaml
# Minimum for every note
tags:
  - status/[status]
  - [type-tag]
```

### Recommended Full Tag Set

```yaml
# Complete tagging
tags:
  - status/active           # Status (required)
  - video-idea              # Type (required)
  - youtube                 # Business (if applicable)
  - youtube/building        # Category (if applicable)
  - priority/high           # Priority (optional)
```

---

**Remember:**
- Tags are for WHAT (discovery)
- Folders are for WHERE (organization)
- Less is more - keep it simple
- Consistency beats perfection

---

**Tags:** #tagging #strategy #knowledge-management #obsidian
