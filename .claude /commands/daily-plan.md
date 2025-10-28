---
description: Generate today's execution plan based on projects, priorities, context, and energy
---

# Daily Plan Generator

Create an optimized daily execution plan by analyzing all active projects and available context.

## Context

**CRITICAL FIRST STEP:** Read `.claude/vault-config.json` to get the vault folder name.

**If vault-config.json doesn't exist:**
- User hasn't run `/setup` yet
- Respond: "Please run `/setup` first to configure your Second Brain!"
- Do not proceed

**Extract `vaultFolder` value and use it for all paths in this command.**

---

**Then read these files:**
1. `{{vaultFolder}}/_Context.md` - Current system state (if exists)
2. `.claude/skills/gtd-workflow/SKILL.md` - GTD principles
3. `{{vaultFolder}}/Permanent Notes/Assisting-User-Context.md` - User's goals and priorities

## Your Task

Generate an intelligent daily plan, checking inbox first.

### Step 0: Check Inbox (NEW)

Before planning, check if the inbox needs processing:

**Scan these locations:**
- `{{vaultFolder}}/00-Inbox/Daily/` - Daily captures
- `{{vaultFolder}}/00-Inbox/Fleeting-Notes/` - Fleeting notes

**Count unprocessed items:**
- Look for files created in the last 3 days
- Count total items across all inbox files

**If 5+ items in inbox:**

Ask the user:
```
📥 INBOX CHECK

I found {{N}} unprocessed items in your inbox from the last few days.

Would you like to process your inbox before planning your day? This ensures all captured tasks and ideas are considered in your plan.

Options:
1. Yes - Run /process-inbox first (recommended)
2. No - Skip for now and just plan with what's in projects
3. Quick review - Show me what's in the inbox first
```

**If user selects Option 1:**
- Inform them: "I'll run /process-inbox for you now. This may take a few minutes."
- Execute the `/process-inbox` command
- After completion, continue to Step 1

**If user selects Option 2:**
- Note: "Skipping inbox processing. I'll plan based on your current projects."
- Continue to Step 1

**If user selects Option 3:**
- List the inbox items briefly
- Then ask Options 1 or 2 again

**If fewer than 5 items:**
- Mention: "Your inbox looks good ({{N}} items). Proceeding with daily plan."
- Continue to Step 1

### Step 1: Gather Intelligence

**Read:**
- All files in `{{vaultFolder}}/01-Projects/` with status = `active` (check frontmatter)
- `{{vaultFolder}}/_Context.md` for high-level overview (if exists)
- `{{vaultFolder}}/Permanent Notes/Assisting-User-Context.md` for user's goals

**Check for active projects:**
- Count how many files have `status: active`

**If ZERO active projects found:**

Ask the user:
```
I don't see any active projects yet!

To create a daily plan, I need projects with next actions to prioritize.

Would you like to:
1. Run /process-inbox to create projects from your inbox captures
2. Manually create your first project in 01-Projects/
3. Skip planning for now (come back after you have projects)

What would you like to do?
```

If user selects option 1: Execute `/process-inbox` then continue to planning.
If user selects option 2 or 3: Exit gracefully.

**If projects exist, continue:**

**Scan for tasks across all locations:**

1. **Projects:** Read all files in `{{vaultFolder}}/01-Projects/` with `status: active`
   - Extract from "High Priority Next Actions" section (highest priority)
   - Extract from "Next Actions" section (regular priority)
   - Extract from "Waiting On" section
   - SKIP "Someday/Maybe" section

2. **Areas:** Read all area files in `{{vaultFolder}}/02-Areas/`
   - Extract from "High Priority Tasks" or "Critical Tasks" section (highest priority)
   - Extract from "Next Actions" or "Current Tasks" section (regular priority)
   - Extract from "Waiting On" section
   - SKIP "Someday/Maybe" section
   - SKIP "Recurring Responsibilities" unless overdue

3. **Relationships:** Read all person notes in `{{vaultFolder}}/02-Areas/Relationships/`
   - Extract from "High Priority" section (urgent people items)
   - Extract from "Next Actions → To Discuss" section (things to talk about)
   - Extract from "Waiting On" section (things you're waiting on from people)
   - SKIP "Someday/Maybe"

4. **Context:** Check `_Context.md` for flagged priorities

**Note:** You don't need to exhaustively scan every section. Focus on High Priority sections first, then sample Next Actions sections based on user's stated focus and available time.

### Step 2: Assess Context

Ask the user:
1. **What's your energy level today?** (High/Medium/Low)
2. **What contexts are available?** (Office, Computer, Phone, Home, Errands, Travel)
3. **How much time do you have?** (Rough blocks: morning, afternoon, evening)
4. **Any hard deadlines today?** (Things that MUST happen)

### Step 3: Generate Plan

Create a prioritized action list using these criteria:

**Priority Scoring:**
- High priority project = +3
- Medium priority project = +2
- Low priority project = +1
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

### Step 4: Create Daily Plan

Create today's daily plan file in the Daily Plans folder:

**File:** `{{vaultFolder}}/Daily Plans/{{YYYY-MM-DD}}.md`

**Check if file already exists:**
- If exists with `status: draft` (from last night's closeout):
  - Read the draft priorities
  - Keep the priorities but enhance with today's energy/context
  - Update status to `active`
  - Add note: "Enhanced from last night's draft based on your energy and context today"

- If exists with `status: active` (re-running plan during day):
  - Update with new plan
  - Note: "Plan updated at {{time}}"

- If doesn't exist:
  - Create new plan file

```markdown
## 🎯 Today's Plan (Generated {{time}})

**Energy:** 🔋🔋🔋 [User input]
**Context:** [User input]
**Available Time:** [User input]

### Must-Do Today (Top 3)
- [ ] [[Project A]] - Next: [Action] `#high #context/computer #energy/high #time/1h`
- [ ] [[Project B]] - Next: [Action] `#high #context/phone #energy/medium #time/15m`
- [ ] [[Project C]] - Next: [Action] `#medium #context/office #energy/low #time/30m`

### Should-Do (Next 5)
- [ ] [[Project D]] - Next: [Action] `#medium #context/computer #energy/medium #time/2h`
- [ ] [[Project E]] - Next: [Action] `#low #context/anywhere #energy/low #time/15m`
[...]

### ⏳ Waiting On (Check-ins)
- John's response (budget) - *Follow up if no response by EOD*
- API key from vendor - *Email if not received*

### ⚡ Quick Wins (Fill gaps)
- [ ] [5-min task]
- [ ] [10-min task]
- [ ] [15-min task]

---
*Plan generated by /daily-plan command at {{time}}*
*Based on [N] active projects with [N] next actions available*
```

### Step 5: Update Context File

If `_Context.md` exists, update it with today's priorities:

```markdown
# _Context.md

Last Updated: {{date:YYYY-MM-DD HH:mm}}

## Today's Focus ({{date:YYYY-MM-DD}})

**Top Priority:**
1. [[Project A]] - Next: [Action]
2. [[Project B]] - Next: [Action]
3. [[Project C]] - Next: [Action]

**Context:** [User's available contexts]
**Energy:** [User's energy level]

[... rest of context file ...]
```

If `_Context.md` doesn't exist, create it with this basic structure.

### Output Format

After generating the plan:

```
✅ DAILY PLAN GENERATED

📊 Intelligence Gathered:
- Active Projects: [N]
- Available Next Actions: [N]
- Waiting On: [N]

🎯 Plan Summary:
- Must-Do Today: 3 tasks
- Should-Do: 5 tasks
- Quick Wins: [N] tasks
- Waiting On Check-ins: [N]

📝 Files Updated:
- Daily Plan: {{vaultFolder}}/Daily Plans/{{date}}.md
- Context File: {{vaultFolder}}/_Context.md (if exists)

💡 Recommendation:
Start with: [[Project]] - [Next Action]
This is your highest priority based on context and energy.
```

## Important Notes

- Always consider user's actual available time
- Match energy to task complexity
- Respect context constraints (can't make phone calls in a meeting)
- Flag overcommitment (more than 8 hours of tasks)
- Suggest what to defer if plan is too packed

### Logging

After generating daily plan, create a log entry:

**Log File:** `.logs/daily-plan/YYYY-MM-DD.md`

**Log Content:**
```markdown
---
command: daily-plan
timestamp: YYYY-MM-DD HH:mm:ss
---

# Daily Plan Log

**Date:** YYYY-MM-DD
**Generated:** HH:mm:ss

## Context Assessment
- **Energy Level:** [High/Medium/Low]
- **Available Contexts:** [List]
- **Time Blocks:** [Morning/Afternoon/Evening]
- **Hard Deadlines:** [List or None]

## Intelligence Gathered
- Active Projects Analyzed: [N]
- Total Next Actions Found: [N]
- Waiting On Items: [N]

## Plan Generated
**Must-Do Today (Top 3):**
1. [[Project]] - [Action] (Score: X)
2. [[Project]] - [Action] (Score: X)
3. [[Project]] - [Action] (Score: X)

**Should-Do (Next 5):**
- [List with scores]

**Quick Wins:** [N] tasks
**Waiting On Check-ins:** [N] items

## Files Updated
- Daily Plan: {{vaultFolder}}/Daily Plans/YYYY-MM-DD.md
- Context File: {{vaultFolder}}/_Context.md

## Recommendations
**Top Priority:** [[Project]] - [Next Action]
**Reasoning:** [Why this is top priority]

## Status
✅ Daily plan generated successfully
```
