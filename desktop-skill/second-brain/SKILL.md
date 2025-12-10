---
name: Second Brain
description: |
  Personal knowledge management and productivity system combining GTD (Getting Things Done), Zettelkasten note-taking, and PARA organization for Obsidian vaults.

  Use this skill when:
  - User wants to capture thoughts, ideas, tasks, or notes ("capture this", "save this thought", "remember this", "note this down", "add to my inbox")
  - User wants to plan their day ("plan my day", "what should I work on today", "daily planning", "morning planning")
  - User wants to process their inbox ("process my inbox", "organize my captures", "clarify my tasks", "GTD processing")
  - User wants to review their day ("daily closeout", "review my day", "end of day review", "evening reflection")
  - User wants to set up or configure their Second Brain ("set up my second brain", "configure my vault", "second brain setup")
  - User asks about their projects, tasks, priorities, or goals
  - User is doing research or brainstorming and might want to preserve insights

  PROACTIVE BEHAVIOR: When the user is researching topics, discussing ideas, or working through problems, offer to capture valuable insights to their Second Brain. Ask: "Would you like me to capture this insight to your Second Brain?"
---

# Second Brain

A personal knowledge management and productivity system for Obsidian, combining:
- **GTD (Getting Things Done)** - Task and project management
- **Zettelkasten** - Atomic note-taking for knowledge building
- **PARA Method** - Folder organization (Projects, Areas, Resources, Archives)

## Configuration (PERSISTENT)

**CRITICAL FIRST STEP:** Before any operation, check for configuration.

### How Configuration Works

Configuration is stored at `~/.second-brain/config.json` and **persists across all sessions**.

Once set up, the skill remembers:
- Your vault path
- Your name
- Whether setup is complete
- Your preferences

### Configuration Check Flow

1. **Check** for `~/.second-brain/config.json`
2. **If exists and setupComplete=true**: Read vaultPath and proceed with requested action
3. **If exists but setupComplete=false**: Continue setup workflow
4. **If doesn't exist**: Ask for vault path, save config, run full setup

### If No Configuration Found (First Time)

Ask the user for their vault path:

```
Welcome to Second Brain!

I need to know where your Obsidian vault is located so I can save and organize your notes.

Please provide the full path to your Obsidian vault folder.

Examples:
- macOS: /Users/yourname/Documents/MyVault
- Windows: C:\Users\yourname\Documents\MyVault
- Linux: /home/yourname/Documents/MyVault

What's the path to your vault?
```

Once you have the path:
1. Create `~/.second-brain/` directory: `mkdir -p ~/.second-brain`
2. Create `config.json` with vault path and `setupComplete: false`
3. Run the full [setup workflow](workflows/setup.md) to complete onboarding
4. Mark `setupComplete: true` when done

**The config file is now saved and will be remembered in all future sessions.**

### Config File Format

```json
{
  "vaultPath": "/absolute/path/to/obsidian/vault",
  "setupComplete": true,
  "userName": "User Name",
  "userContext": "Permanent Notes/Assisting-User-Context.md",
  "preferences": {
    "proactiveCapture": true,
    "inboxThreshold": 5
  }
}
```

### If Configuration Exists

Read the config and use `vaultPath` for ALL file operations.

**Alternative:** Environment variable `SECOND_BRAIN_VAULT_PATH` can override config file.

---

## Core Capabilities

### 1. Quick Capture

**Trigger phrases:** "capture this", "save this thought", "remember this", "note this down", "add to my inbox"

**What it does:** Instantly captures thoughts, tasks, or ideas to today's inbox without categorization.

**GTD Principle:** "Capture first, clarify later."

See: [Capture Workflow](workflows/capture.md)

---

### 2. Daily Planning

**Trigger phrases:** "plan my day", "what should I work on", "daily planning", "morning planning"

**What it does:**
- Checks inbox (prompts to process if 5+ items)
- Scans all projects for next actions
- Asks about energy, context, time available
- Generates prioritized task list (must-do, should-do, quick-wins)

See: [Daily Plan Workflow](workflows/daily-plan.md)

---

### 3. Inbox Processing

**Trigger phrases:** "process my inbox", "organize my captures", "clarify my tasks", "GTD processing"

**What it does:**
- Asks clarifying questions for vague items (batched, not one-by-one)
- Routes actionable items to Projects/Areas
- Routes knowledge items to Permanent Notes
- Reviews all active projects
- Archives completed projects

See: [Process Inbox Workflow](workflows/process-inbox.md)

---

### 4. Daily Closeout

**Trigger phrases:** "daily closeout", "review my day", "end of day review", "evening reflection"

**What it does:**
- Reads today's plan
- Asks what was accomplished
- Marks completed/partial/deferred items
- Asks about tomorrow's priorities
- Creates tomorrow's DRAFT plan

See: [Daily Closeout Workflow](workflows/daily-closeout.md)

---

### 5. Setup & Configuration

**Trigger phrases:** "set up my second brain", "configure my vault", "second brain setup", "reconfigure"

**What it does:**
- First-time: Full interactive setup (goals, relationships, first project)
- Re-run: Update existing configuration

See: [Setup Workflow](workflows/setup.md)

---

## Proactive Capture

**IMPORTANT:** When you notice the user:
- Discovering valuable information during research
- Having insights or realizations
- Discussing ideas worth preserving
- Solving problems in interesting ways

**Offer to capture:**
```
That's an interesting insight about [topic]. Would you like me to capture this to your Second Brain?
```

If they agree:
- Use the capture workflow
- Add context about where the insight came from
- Suggest relevant tags or connections

---

## Vault Structure

The system uses PARA + Zettelkasten organization:

```
{{vaultPath}}/
├── 00-Inbox/
│   ├── Daily/              # Captures go here (YYYY-MM-DD.md)
│   └── Fleeting-Notes/     # Knowledge items during processing
├── 01-Projects/            # Multi-step outcomes with deadlines
├── 02-Areas/               # Ongoing responsibilities
│   ├── Career-Development.md
│   ├── Health-Fitness.md
│   ├── Personal-Development.md
│   ├── Errands.md
│   ├── Personal-Todos.md
│   └── Relationships/      # Individual notes per person
├── 03-Resources/
│   └── Reference-Notes/    # Summaries of external sources
├── 04-Archives/            # Completed/inactive projects
├── Daily Plans/            # Generated daily plans
├── Meeting Notes/          # Meeting documentation
├── Permanent Notes/        # Zettelkasten - synthesized insights
│   └── Assisting-User-Context.md  # User's goals & context
└── Templates/              # Reusable templates
```

See: [PARA + Zettelkasten Guide](references/para-zettelkasten.md)

---

## Unified Task Structure

**ALL Projects, Areas, and Relationship notes use identical priority sections:**

```markdown
## High Priority / Critical
- Urgent/important items (scanned FIRST by daily planning)

## Next Actions / Current Tasks
- Regular priority items (scanned SECOND)

## Someday/Maybe
- Lower priority/exploratory (SKIPPED by daily planning)

## Waiting On
- Blocked by external dependencies

## Completed
- Finished tasks with dates
```

---

## Templates

Use these templates when creating new notes:

| Template | Use When |
|----------|----------|
| [project.md](templates/project.md) | Creating a new project (multi-step outcome) |
| [area.md](templates/area.md) | Creating a new area of responsibility |
| [permanent-note.md](templates/permanent-note.md) | Creating a Zettelkasten permanent note |
| [fleeting-note.md](templates/fleeting-note.md) | Quick knowledge capture for later processing |
| [relationship.md](templates/relationship.md) | Tracking an important person |
| [meeting-note.md](templates/meeting-note.md) | Meeting documentation |
| [daily-plan.md](templates/daily-plan.md) | Daily execution plan |
| [daily-inbox.md](templates/daily-inbox.md) | Daily capture file |
| [user-context.md](templates/user-context.md) | User goals and preferences |

---

## Key References

- [GTD Methodology](references/gtd-methodology.md) - David Allen's Getting Things Done
- [PARA + Zettelkasten](references/para-zettelkasten.md) - Folder organization
- [Obsidian Mastery](references/obsidian-mastery.md) - Obsidian conventions
- [Tagging Strategy](references/tagging-strategy.md) - Tag taxonomy

---

## ADHD-Friendly Principles

The system is designed for users who may have ADHD:

1. **Read entire documents first** - Understand existing structure
2. **Make targeted edits** - Update specific sections, don't append
3. **Never just add to bottom** - Unless explicitly asked
4. **Keep it concise** - Remove redundancy
5. **One plan, not many** - Replace old plans, don't add "revised" sections

**Bad:** Adding "REVISED PLAN" below "TODAY'S PLAN"
**Good:** Replacing "TODAY'S PLAN" content with updated tasks

---

## Daily Workflow Summary

**The Complete Loop:**

1. **Throughout day:** Capture thoughts (30 sec each)
2. **3x per week:** Process inbox - Clarify + Organize (15 min)
3. **Every morning:** Daily plan - Choose what to work on (5 min)
4. **Every evening:** Daily closeout - Reflect + Prep tomorrow (5 min)

**Total time:** ~20-25 min/day + 45 min/week processing = Sustainable!

---

## Examples

### Example 1: Quick Capture

**User:** "Capture: Need to call the dentist and also research new project management tools"

**You:**
1. Read config to get vault path
2. Find/create today's inbox file at `{{vaultPath}}/00-Inbox/Daily/YYYY-MM-DD.md`
3. Append the capture with timestamp
4. Confirm: "Captured at 14:32. You have 3 captures today."

### Example 2: Daily Planning

**User:** "What should I work on today?"

**You:**
1. Check inbox count (process if 5+ items)
2. Scan all projects in `01-Projects/` for next actions
3. Ask: "How's your energy today? Any context constraints?"
4. Generate prioritized list based on goals from user context
5. Create/update `Daily Plans/YYYY-MM-DD.md`

### Example 3: Proactive Capture

**During conversation about a topic:**

**You:** "That insight about [topic] seems valuable. Would you like me to capture it to your Second Brain? I can add it to your inbox for later processing, or create a permanent note if it's already well-formed."

---

## Tool Usage

The skill uses these tools:
- **Read** - Check files, load context
- **Write** - Create new files
- **Edit** - Update existing files
- **Glob** - Find files by pattern
- **Bash** - Create directories if needed

Always use the configured `vaultPath` from `~/.second-brain/config.json` for all operations.
