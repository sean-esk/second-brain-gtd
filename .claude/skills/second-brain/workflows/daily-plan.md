# Daily Plan Workflow

Create an optimized daily execution plan by analyzing all active projects and available context.

> **GTD Stage:** This workflow implements the Engage stage (choosing what to work on)

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
- Respond: "Let's set up your Second Brain first so I can help you plan your day."
- Run [setup workflow](setup.md)

**Use the vault path from Memory for all paths in this workflow.**

### Claude Code Fallback

**For Claude Code only:** If Memory is empty, also check `~/.second-brain/config.json` for legacy config.

---

**Then read these files:**
1. `{{vaultPath}}/_Context.md` - Current system state (if exists)
2. [GTD Methodology Reference](../references/gtd-methodology.md) - Four criteria model
3. `{{vaultPath}}/Permanent Notes/Assisting-User-Context.md` - User's goals and priorities

---

## Generate an intelligent daily plan

---

## Step -1: Check Previous Day's Plan

Before doing anything else, check if yesterday's plan was properly closed out.

**Read yesterday's plan:** `{{vaultPath}}/Daily Plans/{{YYYY-MM-DD minus 1 day}}.md`

**Check the frontmatter `status` field:**

**If file exists AND status = `active` (not `completed`):**

```
PREVIOUS DAY NOT CLOSED OUT

I see yesterday's plan ({{date}}) wasn't closed out yet.

This means tasks might not have been returned to their projects/areas.

Would you like to:
1. Close out yesterday first (recommended)
2. Skip and plan today anyway
3. Show me yesterday's plan so I can review it

What would you like to do?
```

**If user selects Option 1:**
- Run [daily-closeout workflow](daily-closeout.md) for yesterday
- After completion, continue to Step 0 below

**If file doesn't exist OR status = `completed`:**
- Continue to Step 0

---

## Step 0: Check Inbox

Before planning, check if the inbox needs processing:

**Scan:**
- `{{vaultPath}}/00-Inbox/Daily/` - Daily captures
- `{{vaultPath}}/00-Inbox/Fleeting-Notes/` - Fleeting notes

**Count unprocessed items** (files from last 3 days)

**If 5+ items in inbox:**

```
INBOX CHECK

I found {{N}} unprocessed items in your inbox.

Would you like to process your inbox before planning? This ensures all captured tasks are considered.

1. Yes - Process inbox first (recommended)
2. No - Skip for now and just plan
3. Quick review - Show me what's in the inbox
```

**If user selects Option 1:**
- Run [process-inbox workflow](process-inbox.md)
- After completion, continue to Step 1

**If fewer than 5 items:**
- Mention: "Your inbox looks good ({{N}} items). Proceeding with planning."
- Continue to Step 1

---

## Step 1: Gather Intelligence

**Read:**
- All files in `{{vaultPath}}/01-Projects/` with status = `active`
- `{{vaultPath}}/_Context.md` for high-level overview
- `{{vaultPath}}/Permanent Notes/Assisting-User-Context.md` for user's goals

**If ZERO active projects found:**

```
I don't see any active projects yet!

To create a daily plan, I need projects with next actions to prioritize.

Would you like to:
1. Process your inbox to create projects
2. Create your first project now
3. Skip planning for now

What would you like to do?
```

**If projects exist:**

**Scan for tasks across all locations:**

1. **Projects:** `{{vaultPath}}/01-Projects/` with `status: active`
   - Extract from "High Priority" section (highest priority)
   - Extract from "Next Actions" section (regular priority)
   - Extract from "Waiting On" section
   - SKIP "Someday/Maybe" section

2. **Areas:** `{{vaultPath}}/02-Areas/`
   - Extract from "High Priority" section
   - Extract from "Next Actions" section
   - Extract from "Waiting On" section
   - SKIP "Someday/Maybe" section

3. **Relationships:** `{{vaultPath}}/02-Areas/Relationships/`
   - Extract from "High Priority" section
   - Extract from "Next Actions → To Discuss" section
   - Extract from "Waiting On" section

---

## Step 1b: Tag Tasks with Source Information

As you scan tasks, **preserve their origin** so they can be returned during closeout.

**For each task:**

1. **Note the source location:**
   - Projects: `01-Projects/Project-Name.md`
   - Areas: `02-Areas/Area-Name.md`
   - Relationships: `02-Areas/Relationships/Person-Name.md`

2. **Create source tag:**
   - `#source/projects/website-redesign`
   - `#source/areas/personal-todos`
   - `#source/relationships/john`

**Why:** The #source tag tracks where the task lives. During closeout, this tells you where to return/update the task.

---

## Step 2: Assess Context (GTD Four Criteria)

Ask the user:

```
Let's plan your day. Tell me about today's context:

1. **Energy level:** How's your energy? (High/Medium/Low)
2. **Available contexts:** Where will you be? (Office, Home, Computer, Phone, Errands)
3. **Time available:** How much time do you have? (Full day, morning only, etc.)
4. **Hard deadlines:** Anything that MUST happen today?
```

---

## Step 3: Generate Plan

Create a prioritized action list using these criteria:

**Priority Scoring:**
- High priority project = +3
- Medium priority project = +2
- Due today = +5
- Due this week = +2
- Matches available context = +2
- Matches energy level = +2
- Time available fits task = +1

**Sort tasks by total score, then present:**

**Top 3 Must-Do:**
- Highest scoring tasks
- Focus on project advancement
- Clear, concrete actions

**Next 5 Should-Do:**
- Important but not urgent
- Context-appropriate
- Time-boxed

**Waiting On:**
- Items blocked by others
- Check if any can be unblocked today

**Quick Wins (5-15 min):**
- Low-energy, short tasks
- Good for between meetings or low energy periods

---

## Step 4: Create Daily Plan File

**File:** `{{vaultPath}}/Daily Plans/{{YYYY-MM-DD}}.md`

**Check if file already exists:**

- If exists with `status: draft` (from last night's closeout):
  - Keep priorities but enhance with today's energy/context
  - Update status to `active`

- If exists with `status: active` (re-running during day):
  - Update with new plan
  - Note: "Plan updated at {{time}}"

- If doesn't exist:
  - Create new plan file

**Plan File Structure:**

```markdown
---
title: "Daily Plan - {{YYYY-MM-DD}}"
created: "{{YYYY-MM-DD HH:mm}}"
type: daily-plan
status: active
plan-date: "{{YYYY-MM-DD}}"
tags:
  - daily-plan
  - planning
---

# Daily Plan - {{Day of Week}}, {{Month DD, YYYY}}

**Generated:** {{HH:mm}}
**Status:** Active

---

## Today's Plan

**Energy:** {{User input}}
**Context:** {{User input}}
**Available Time:** {{User input}}

### Must-Do Today (Top 3)

- [ ] [[Project]] - Task `#high #context/X #energy/X #time/Xm #source/projects/project-name`
- [ ] [[Project]] - Task `#high #context/X #energy/X #time/Xm #source/projects/project-name`
- [ ] [[Area]] - Task `#medium #context/X #energy/X #time/Xm #source/areas/area-name`

### Should-Do (Next 5)

- [ ] [[Project]] - Task `#tags #source/X`
- [ ] [[Area]] - Task `#tags #source/X`
[...]

### Waiting On (Check-ins)

- {{Person/thing}} - {{What you're waiting for}}

### Quick Wins (Fill gaps)

- [ ] [[Area]] - Quick task `#energy/low #time/5m #source/areas/X`

---

*Plan generated at {{time}}*
*Tasks include #source tags for tracking*
```

---

## Step 5: Update Context File

Update `{{vaultPath}}/_Context.md` with today's priorities.

---

## Output Format

```
DAILY PLAN GENERATED

**Intelligence Gathered:**
- Active Projects: {{N}}
- Available Next Actions: {{N}}
- Waiting On: {{N}}

**Plan Summary:**
- Must-Do Today: 3 tasks
- Should-Do: 5 tasks
- Quick Wins: {{N}} tasks

**Files Updated:**
- Daily Plan: {{vaultPath}}/Daily Plans/{{date}}.md
- Context File: {{vaultPath}}/_Context.md

**Recommendation:**
Start with: [[Project]] - {{Next Action}}
This is your highest priority based on context and energy.
```

---

## Important Notes

- Always consider user's actual available time
- Match energy to task complexity
- Respect context constraints
- Flag overcommitment (more than 8 hours of tasks)
- Suggest what to defer if plan is too packed

---

## Tools Available

- **Read** - Read project files, area files, context files
- **Write** - Create daily plan file
- **Edit** - Update existing daily plan, update _Context.md
- **Glob** - Find all active projects
- **Grep** - Search for specific tasks
