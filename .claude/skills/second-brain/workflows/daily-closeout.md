# Daily Closeout Workflow

End your day with intention by reviewing what you accomplished and preparing for tomorrow.

> **GTD Stage:** This workflow implements the Reflect stage (daily review and tomorrow prep)

---

## Configuration Check

**CRITICAL FIRST STEP:** Check Claude Memory for the vault path.

```
Do I remember the user's Second Brain vault path?
```

**If found in Memory:**
- Use the remembered vault path for all operations

**If NOT found in Memory:**
- User hasn't run setup yet
- Respond: "Let's set up your Second Brain first."
- Run [setup workflow](setup.md)

**Use the vault path from Memory for all paths in this workflow.**

### Claude Code Fallback

**For Claude Code only:** If Memory is empty, also check `~/.second-brain/config.json` for legacy config.

---

**Then read these files:**
1. Today's daily plan: `{{vaultPath}}/Daily Plans/{{YYYY-MM-DD}}.md`
2. `{{vaultPath}}/_Context.md` - Current system state
3. `{{vaultPath}}/Permanent Notes/Assisting-User-Context.md` - User's goals

---

## Step 0: Check Inbox

Before reviewing the day, check if there are items to process:

**Scan:**
- `{{vaultPath}}/00-Inbox/Daily/`
- `{{vaultPath}}/00-Inbox/Fleeting-Notes/`

**If 5+ items in inbox:**

```
INBOX CHECK

Before we review your day, I found {{N}} unprocessed items in your inbox.

Would you like to process them before closeout?

1. Yes - Process inbox first (recommended)
2. No - Skip for now and just review the day
3. Quick review - Show me what's in the inbox
```

**If user selects Option 1:**
- Run [process-inbox workflow](process-inbox.md)
- After completion, continue to Step 1

---

## Step 1: Load Today's Plan

**Read:** `{{vaultPath}}/Daily Plans/{{YYYY-MM-DD}}.md`

If file doesn't exist:
```
I don't see a daily plan for today. That's okay!

Let me ask you about your day anyway, and we'll make sure tomorrow starts strong.
```

If file exists:
- Extract the must-do, should-do, and quick-win tasks
- Note how many tasks were planned

---

## Step 2: Review Accomplishments

Ask the user about what they completed:

```
Let's review your day!

What did you accomplish today?

You can:
- Tell me what you got done (I'll match it to your plan)
- Share anything you worked on (even if it wasn't on the plan)
- Just say "show me the plan" and I'll walk you through each item

What would you like to do?
```

**If user chooses "show me the plan":**

Go through each planned item:
```
Here's what was on your plan today:

### Must-Do Tasks
1. [Task 1] - Did you complete this? (yes/no/partial)
2. [Task 2] - Did you complete this?
3. [Task 3] - Did you complete this?

### Should-Do Tasks
[Ask about these next]

### Quick Wins
[Ask about these last]
```

**If user provides narrative:**

Parse their response and identify:
- Tasks they completed (mark with [x])
- Tasks they partially completed (note progress)
- Tasks they didn't get to (leave as [ ])
- New things they worked on (not on plan)

---

## Step 3: Update Today's Plan

Update `{{vaultPath}}/Daily Plans/{{YYYY-MM-DD}}.md` with completion status:

**Mark completed tasks:**
```markdown
- [x] Task description (Completed)
```

**Mark partial tasks:**
```markdown
- [~] Task description (In Progress - {{progress note}})
```

**Leave incomplete as:**
```markdown
- [ ] Task description (Deferred)
```

**Add section for unplanned work if applicable:**

```markdown
## Actual Work Done (Not Planned)

- {{Item 1}}
- {{Item 2}}
```

**Add completion summary:**

```markdown
---

## Day Summary

**Planned Tasks:** {{N total}}
**Completed:** {{N}} ({{%}})
**Partial:** {{N}}
**Deferred:** {{N}}

**Unplanned Work:** {{N items}}

*Closeout completed: {{HH:mm}}*
```

---

## Step 3b: Synchronize Tasks Back to Source

Update the source projects/areas with task completion status.

**For EACH task in today's plan:**

### 1. Parse the #source Tag

Every task should have a `#source/folder-type/file-name` tag.

**Convert to file path:**
```
#source/projects/website-redesign → {{vaultPath}}/01-Projects/Website-Redesign.md
#source/areas/health-fitness → {{vaultPath}}/02-Areas/Health-Fitness.md
```

### 2. Handle Based on Task Status

**For COMPLETED tasks (marked [x]):**

1. Find the task in source document
2. Update in source:
   - Change `- [ ] Task` to `- [x] Task - Completed {{YYYY-MM-DD}}`
   - Move to "Completed" section in source document
3. Task stays marked [x] in today's plan

**For PARTIAL tasks:**

1. Find the task in source document
2. Update in source:
   - Add progress note: `- [ ] Task (In progress: {{note}})`
   - Keep task active in source
3. Add to tomorrow's DRAFT plan

**For DEFERRED tasks (not worked on):**

1. Task stays in source document unchanged
2. Ask: "Do you want to carry this to tomorrow's plan?"
   - If YES: Add to tomorrow's DRAFT plan
   - If NO: Leave in source only

### 3. Update Today's Plan Status

**Update frontmatter:**

```yaml
status: completed
closeout-time: "{{YYYY-MM-DD HH:mm}}"
```

**Why:** `completed` status tells tomorrow's planning that closeout was done.

---

## Step 4: Identify Tomorrow's Priorities

Ask the user:

```
Great work today! Let's set up tomorrow.

Do you have specific things you want to focus on tomorrow, or should I build the plan based on your priorities and incomplete items?

1. I'll tell you what I want to focus on
2. Build a plan based on priorities and what didn't get done
3. Both - I'll share my focus, and you add other priorities
```

Handle their response accordingly.

---

## Step 5: Generate Tomorrow's DRAFT Plan

Create tomorrow's plan without energy/context questions (will be asked in the morning).

**File:** `{{vaultPath}}/Daily Plans/{{YYYY-MM-DD+1}}.md`

**Template:**

```markdown
---
title: "Daily Plan - {{Tomorrow's Date}}"
created: "{{YYYY-MM-DD HH:mm}}"
type: daily-plan
status: draft
plan-date: "{{Tomorrow YYYY-MM-DD}}"
tags:
  - daily-plan
  - planning
---

# Daily Plan - {{Day of Week}}, {{Month DD, YYYY}}

**Generated:** {{YYYY-MM-DD HH:mm}} (during yesterday's closeout)
**Status:** Draft - run daily planning in the morning to adjust based on energy and context

---

## Priorities for Tomorrow

{{If user provided specific focus, list it here}}

---

## Must-Do (Top 3)

- [ ] [[Project]] - Task `#tags #source/projects/project-name`
- [ ] [[Project]] - Task `#tags #source/projects/project-name`
- [ ] [[Area]] - Task `#tags #source/areas/area-name`

---

## Should-Do (Next 5)

- [ ] [[Project]] - Task `#tags #source/X`
[...]

---

## Carried Over from Today

{{If any partial or deferred items}}

- [ ] [[Project]] - Task (partial from {{today}}) `#tags #source/X`
- [ ] [[Project]] - Task (deferred from {{today}}) `#tags #source/X`

---

## Quick Wins

- [ ] [[Area]] - Quick task `#energy/low #time/5m #source/areas/X`

---

*This is a draft plan created during closeout.*
*Run daily planning in the morning to refine based on energy and context.*
```

---

## Step 6: Update Context File

Update `{{vaultPath}}/_Context.md` with tomorrow's priorities and today's results.

---

## Output Format

```
DAILY CLOSEOUT COMPLETE

## Today's Results ({{Date}})

**Task Completion:**
- Planned: {{N}} tasks
- Completed: {{N}} ({{%}})
- Partial: {{N}}
- Deferred: {{N}}

{{If unplanned work:}}
**Unplanned Work:**
- {{N}} additional items completed

**Highlights:**
- {{Notable accomplishment 1}}
- {{Notable accomplishment 2}}

---

## Tomorrow's DRAFT Plan ({{Date+1}})

> This is a DRAFT - priorities identified but not yet adjusted for tomorrow's energy/context.

**Proposed Top Priorities:**
1. {{Must-do 1}}
2. {{Must-do 2}}
3. {{Must-do 3}}

{{If carried over items:}}
**Carrying Over:**
- {{N}} tasks from today

**Files Updated:**
- Today's Plan: marked complete
- Tomorrow's DRAFT Plan: created
- Context File: updated

---

**Tomorrow Morning:**
Run daily planning to refine this draft based on your energy and available contexts.

Have a great evening!
```

---

## Important Notes

**Tone:**
- Encouraging and positive
- Acknowledge progress, even if incomplete
- No judgment on unfinished tasks
- Celebrate wins
- Frame challenges constructively

**Tomorrow's Plan:**
- Keep it draft status - refine in the morning
- Base on priorities, not energy/context
- Carry over incomplete items thoughtfully

---

## Tools Available

- **Read** - Read today's plan, context files, user goals
- **Write** - Create tomorrow's draft plan
- **Edit** - Update today's plan with completion status, update _Context.md
- **Glob** - Find project files for tomorrow's priorities
