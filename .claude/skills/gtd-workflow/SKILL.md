---
name: gtd-workflow
description: Comprehensive Getting Things Done (GTD) methodology for task and project management. Provides knowledge of core GTD principles (capture, clarify, organize, reflect, engage) AND implementation guidance for our Obsidian-based system. Use when processing inbox items, creating or organizing tasks and projects, clarifying next actions, conducting reviews, or explaining GTD concepts.
---

# GTD Workflow Skill

This skill provides two types of knowledge:

1. **GTD Methodology** - David Allen's core principles and workflow (universal)
2. **Our Implementation** - How we apply GTD in this Obsidian-based system (specific)

---

## When to Use This Skill

- Explaining GTD concepts and methodology to users
- Processing inbox items with `/process-inbox`
- Creating or organizing tasks and projects using GTD principles
- Clarifying next actions and desired outcomes
- Conducting project reviews
- Planning daily work with `/daily-plan`
- Routing items between GTD (actionable) and Zettelkasten (knowledge)

---

## References

### Core GTD Methodology

**File:** `references/gtd-methodology.md`

**Load this reference for:**
- Complete explanation of the 5 stages (Capture, Clarify, Organize, Reflect, Engage)
- What makes a good next action (with examples)
- Projects vs tasks distinction
- Contexts and how to use them
- Waiting-for lists
- Weekly review principles and checklist
- Two-minute rule
- Four criteria for choosing actions
- Common GTD pitfalls and solutions
- David Allen's core philosophy

**Use when:** User asks about GTD methodology, needs help understanding principles, or wants to know why the system works this way.

### Our Implementation

**File:** `references/folder-structure.md`

**Load this reference for:**
- How GTD elements map to PARA folder structure
- Where projects, tasks, and reference items live
- Command-to-GTD-stage mapping
- Folder purposes and usage

**Use when:** Processing items, creating notes, organizing content.

---

## Quick Overview: GTD in Our System

### The 5 Stages → Our Commands

| GTD Stage | Our Command | What It Does |
|-----------|-------------|--------------|
| **Capture** | `/capture` | Single quick items OR full brain dumps → inbox |
| **Clarify** | `/process-inbox` | Asks: Actionable? Outcome? Next action? Where? |
| **Organize** | `/process-inbox` | Routes to Projects/Areas/Resources (PARA structure) |
| **Reflect** | `/process-inbox` (3x/week) | Reviews projects + processes inbox |
| **Engage** | `/daily-plan` | Chooses tasks by context, time, energy, priority |

**Key Innovation:** `/process-inbox` combines Clarify + Organize + Reflect in one command. Run it 3x/week for continuous system health.

---

## GTD + PARA Integration

**How We Map GTD to Folders:**

| GTD Element | Folder Location | Notes |
|-------------|-----------------|-------|
| **Projects** (multi-step) | `ObsidianVault/01-Projects/` | Time-bound, have deadlines |
| **Areas** (ongoing) | `ObsidianVault/02-Areas/` | No end date, maintain standards |
| **Relationships** (people) | `ObsidianVault/02-Areas/Relationships/` | Individual notes per person |
| **Next Actions** | Inside project/area/relationship notes | In priority sections |
| **Waiting For** | "Waiting On" sections | Across all note types |
| **Someday/Maybe** | "Someday/Maybe" sections | Across projects/areas |
| **Reference** | `ObsidianVault/03-Resources/` | Non-actionable information |
| **Completed** | `ObsidianVault/04-Archives/` | Done and reviewed |

---

## Unified Task Structure

**All Projects, Areas, AND Relationship notes use the SAME priority-based sections:**

### Section Structure (Consistent Across All)

```markdown
## 🚨 High Priority / High Priority Tasks / Critical

{{Urgent/important - /daily-plan scans FIRST}}

- [ ] Task `#context/X #energy/X #time/Xm`

## 📋 Next Actions / Current Tasks

{{Regular priority - /daily-plan scans SECOND}}

- [ ] Task `#context/X #energy/X #time/Xm`

## 💭 Someday/Maybe

{{Lower priority - /daily-plan SKIPS these}}

- [ ] Task

## ⏳ Waiting On

{{Blocked items - shown separately in plan}}

- [ ] Person - What - Asked: Date

## ✅ Completed

{{Finished tasks}}

- [x] Task - Date
```

**Benefits:**
- `/daily-plan` knows exactly where to scan
- Consistent across all note types
- Priority determines what gets recommended
- Someday items don't clutter daily plans

---

## Default Areas Created During Setup

**Standard areas everyone gets:**

1. **Career-Development.md** - Professional growth, skills, networking
2. **Health-Fitness.md** - Physical health, mental wellness, fitness
3. **Personal-Development.md** - Learning, hobbies, personal growth
4. **Errands.md** - Shopping, errands, things to buy/pick up
5. **Personal-Todos.md** - Miscellaneous one-off personal tasks
6. **Relationships/** (folder) - Individual notes for important people

**Relationships folder contains:**
- One note per important person (business partners, family, key colleagues)
- Uses Relationship Note template
- Same task structure for consistency
- Tracks discussions, commitments, waiting-on items

---

## Determining Task Priority (CRITICAL for Routing)

**When processing tasks during `/process-inbox`, determine which section to add them to:**

### High Priority / Critical Indicators

**Route to "High Priority" or "Critical" section if ANY of these apply:**

1. **Urgency keywords:**
   - "urgent", "ASAP", "critical", "important", "emergency"
   - "need to X immediately", "must do today"

2. **Timeframe indicators:**
   - "today", "tomorrow", "by Friday", "this week"
   - "before [date]", "deadline [date]"
   - Any deadline <7 days

3. **Blocking work:**
   - "blocking", "waiting on this", "need this before"
   - Enables other work to proceed

4. **Aligns with user's top goals:**
   - Check Assisting-User-Context.md for user's stated priorities
   - If task relates to their #1-3 priorities → HIGH PRIORITY
   - Example: User's top goal is "grow business revenue"
     - "Follow up with potential client" → HIGH PRIORITY
     - "Research CRM tools" → NEXT ACTION

5. **Time-sensitive opportunities:**
   - "Sale ends Friday", "offer expires", "limited time"
   - Opportunity cost if delayed

6. **High-value impact:**
   - Relates to user's highest-priority business/area
   - Significant outcome or consequence

**Examples:**

| Capture | Priority | Why |
|---------|----------|-----|
| "Need to call John ASAP about Q4 budget approval" | HIGH | ASAP keyword + likely important |
| "Follow up with Sarah about proposal by Friday" | HIGH | Deadline this week |
| "Schedule dentist appointment this week" | NEXT ACTION | "This week" = regular priority |
| "Research new project management tools when I have time" | SOMEDAY | "When I have time" = not urgent |

---

### Next Actions / Current Tasks Indicators

**Route to "Next Actions" or "Current Tasks" section if:**

1. **Regular workflow language:**
   - "Need to", "should", "want to", "have to"
   - No specific urgency indicated

2. **Timeframe is flexible:**
   - "This week", "soon", "in the next few days"
   - No hard deadline

3. **Medium importance:**
   - Relates to user's goals but not top priority
   - Regular operational work
   - Maintenance tasks

4. **Default routing:**
   - When unclear, default to NEXT ACTION (better than guessing HIGH or SOMEDAY)

---

### Someday/Maybe Indicators

**Route to "Someday/Maybe" section if ANY of these:**

1. **Explicit someday language:**
   - "someday", "eventually", "might", "could"
   - "when I have time", "if I get around to it"

2. **Exploratory/aspirational:**
   - "Would be nice to...", "interesting idea to explore"
   - Learning goals without timeline
   - "Look into", "consider", "think about"

3. **Low priority:**
   - Doesn't relate to stated goals
   - Nice-to-have, not need-to-have

**Examples:**
- "Someday learn Spanish" → SOMEDAY (explicit)
- "Might be interesting to explore AI tools" → SOMEDAY (exploratory)
- "Could reorganize filing system when I have time" → SOMEDAY ("when I have time")

---

### Decision Tree for Priority

```
Step 1: Check for SOMEDAY indicators
  - Contains "someday/eventually/when I have time"? → SOMEDAY

Step 2: Check for HIGH PRIORITY indicators
  - Urgent keywords? → HIGH
  - Deadline <7 days? → HIGH
  - Relates to top 1-3 user goals? → HIGH
  - Blocking other work? → HIGH

Step 3: Default
  - Otherwise → NEXT ACTION
```

**When in doubt:** NEXT ACTION is the safe default.

---

## Status Values We Use

```
inbox → next → active → waiting → done → archived
  ↓              ↓                   ↓
someday ←---→ deferred         cancelled
```

**Status meanings:**
- `inbox` - Just captured, not clarified
- `next` - Ready to work on, has defined next action
- `active` - Currently in progress
- `waiting` - Blocked by external dependency
- `someday` - Maybe later, not now
- `done` - Completed
- `archived` - Completed and filed away

---

## Tags We Use for GTD

### Context Tags
`#context/computer`, `#context/phone`, `#context/office`, `#context/home`, `#context/anywhere`

**Based on GTD context concept.** See `gtd-methodology.md` for explanation.

### Energy Tags (Our Enhancement)
`#energy/high`, `#energy/medium`, `#energy/low`

**Not in original GTD, but critical for ADHD-friendly workflow.**

### Time Tags
`#time/5m`, `#time/15m`, `#time/30m`, `#time/1h`, `#time/2h`, `#time/4h+`

**Used for task selection and daily planning.**

---

## How `/process-inbox` Works

**This command does the heavy lifting:**

1. **Scans inbox** - `ObsidianVault/00-Inbox/Daily/` and `Fleeting-Notes/`
2. **Applies GTD clarifying questions** - Uses methodology from `gtd-methodology.md`
3. **Routes appropriately:**
   - Actionable → GTD (projects, tasks)
   - Knowledge → Obsidian-mastery skill (permanent notes)
   - Reference → Filed in Resources
4. **Reviews all projects:**
   - Checks for next actions
   - Archives completed projects
   - Identifies stalled items
5. **Updates _Context.md** - Current system state

**Run 3x/week = continuous review.** No separate weekly review command needed.

---

## How Commands Coordinate

### `/capture` (Capture Stage)
- Creates inbox items
- Doesn't clarify or organize (that's for processing)
- Low friction - just get it out of your head

### `/process-inbox` (Clarify + Organize + Reflect)
- Uses this GTD skill for actionable items
- Hands off to obsidian-mastery for knowledge items
- Combines processing with project review

### `/daily-plan` (Engage Stage)
- Reads active projects
- Applies four criteria (context, time, energy, priority)
- Generates prioritized action list
- See `gtd-methodology.md` for four criteria model

### `/daily-closeout` (Reflect Stage)
- Reviews what was accomplished
- Updates project completion status
- Prepares tomorrow's focus

---

## Integration with Zettelkasten

**GTD handles execution. Zettelkasten handles knowledge.**

**During processing (`/process-inbox`):**
- Item is actionable? → This skill handles it (GTD)
- Item is knowledge/insight? → obsidian-mastery skill handles it (Zettelkasten)

**Both can apply to same item:**
- Extract action items → GTD projects/tasks
- Extract insights → Permanent notes
- Link them together

**Example:**
From meeting notes:
- Action: "Schedule follow-up meeting" → GTD task
- Insight: "Customer prefers async communication" → Permanent note
- Both linked to the project

---

## Key Principles for Implementation

**From GTD methodology:**
1. Every project MUST have a next action
2. Next actions must be physical and concrete
3. Organize by context for efficient action selection
4. Review regularly to maintain trust
5. Use two-minute rule during processing

**See `references/gtd-methodology.md` for detailed explanations and examples.**

---

## Command Summary

Our simple 5-command workflow implements full GTD:

1. `/setup` - Initial configuration
2. `/capture` - Get it out of your head (Capture)
3. `/process-inbox` - Clarify, organize, review (Clarify + Organize + Reflect)
4. `/daily-plan` - Choose what to work on (Engage)
5. `/daily-closeout` - Daily reflection and prep (Reflect)

**That's it!** Simple commands, powerful GTD methodology underneath.

---

*Based on Getting Things Done by David Allen*
*See `references/gtd-methodology.md` for complete methodology reference*
