# Process Inbox Workflow

Process all inbox items using GTD principles: clarify what each item means, organize into appropriate locations, and conduct a quick project review.

> **GTD Stages:** This workflow handles Clarify + Organize + Reflect (review)

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
- Respond: "Let's set up your Second Brain first so I know where to organize things."
- Run [setup workflow](setup.md)

**Use the vault path from Memory for all paths in this workflow.**

### Claude Code Fallback

**For Claude Code only:** If Memory is empty, also check `~/.second-brain/config.json` for legacy config.

---

**Then read these files:**
1. [GTD Methodology Reference](../references/gtd-methodology.md) - Core GTD principles
2. `{{vaultPath}}/_Context.md` - Current system state (if exists)
3. `{{vaultPath}}/Permanent Notes/Assisting-User-Context.md` - User's goals

---

## Process inbox items and review projects in TWO phases

---

## PHASE 1: CLARIFY INBOX ITEMS

### Step 1: Scan All Inbox Locations

**Scan these folders:**
- `{{vaultPath}}/00-Inbox/Daily/` - Daily captures
- `{{vaultPath}}/00-Inbox/Fleeting-Notes/` - Fleeting notes (if any)

**List all items found:**
- Count total captures across all files
- List each capture with its timestamp

---

### Step 2: Review and Ask Clarifying Questions

**Before processing anything, review ALL items first.**

For each capture, assess:
- **Is it clear?** Can you tell what action/outcome is needed?
- **Is it vague?** Does it need more info?

**If ANY items are vague or unclear:**

Ask the user for clarification ON ALL VAGUE ITEMS AT ONCE (don't ask one at a time):

```
I found {{N}} items to process. A few need clarification:

1. "{{Vague item 1}}" - Could you clarify: {{What's unclear - is this a task? A project? What's the desired outcome?}}

2. "{{Vague item 2}}" - Could you clarify: {{What's unclear}}

3. "{{Vague item 3}}" - Could you clarify: {{What's unclear}}

Please provide any additional context that will help me organize these properly.
```

**Wait for user response** before continuing to Step 3.

**If all items are clear:** Skip to Step 3.

---

### Step 3: Process Each Item Using GTD

For EACH capture, apply the GTD clarifying questions:

**Question 1: What is it?**
- Understand the capture

**Question 2: Is it actionable?**
- **YES** → Continue to Q3
- **NO** → Route to reference/trash (Q5)

**Question 3: What's the desired outcome?**
- **Multiple steps needed?** → It's a PROJECT
- **Single action?** → It's a TASK

**Question 4: What's the next physical action?**
- Must be concrete and doable
- Example: "Call John at 555-1234" NOT "Contact John"

**Question 5: Where does it belong?**
- Related to existing project? → Add task to that project
- New multi-step outcome? → Create new project
- Ongoing area responsibility? → Add to area note
- Knowledge/insight? → Create fleeting note
- Reference information? → Create reference note
- Not needed? → Delete

---

### Step 4: Determine Priority FIRST

**For each task, check:**

1. **Check for SOMEDAY indicators:**
   - Contains "someday", "eventually", "when I have time"?
   - Exploratory language: "might", "could", "interesting to"?
   - If YES → Priority: SOMEDAY

2. **Check for HIGH PRIORITY indicators:**
   - Urgency keywords: "urgent", "ASAP", "critical", "important"?
   - Deadline <7 days: "today", "tomorrow", "by Friday"?
   - Relates to user's top 1-3 goals (check Assisting-User-Context.md)?
   - Time-sensitive: "sale ends", "offer expires"?
   - If YES to any → Priority: HIGH

3. **Default:**
   - Otherwise → Priority: NEXT ACTION (regular)

**Remember:** When unclear, default to NEXT ACTION.

---

### Step 5: Route to Appropriate Location with Priority

**For Tasks (single actions):**

1. **Identify destination:**
   - Related to existing project? → That project
   - Home/house task? → `02-Areas/Personal-Todos.md`
   - Health-related? → `02-Areas/Health-Fitness.md`
   - Errand/shopping? → `02-Areas/Errands.md`
   - Work/career? → `02-Areas/Career-Development.md`
   - Learning? → `02-Areas/Personal-Development.md`
   - About a specific person? → `02-Areas/Relationships/{{Person}}.md`

2. **Add to appropriate section based on priority:**
   - Priority: HIGH → "High Priority" section
   - Priority: NEXT ACTION → "Next Actions" section
   - Priority: SOMEDAY → "Someday/Maybe" section

3. **Format:** `- [ ] {{Action}} #context/X #energy/X #time/Xm`

**For Projects (multi-step outcomes):**
1. Create new project note in `{{vaultPath}}/01-Projects/`
2. Fill out:
   - Desired Outcome (GTD: what does done look like?)
   - Next Actions section: Add at least one concrete action
   - Status: active
   - Priority: high (if relates to goals) or medium

**For Knowledge/Insights:**
1. Create fleeting note in `{{vaultPath}}/00-Inbox/Fleeting-Notes/`
2. Capture the core thought
3. Mark for later development into permanent note

**For Reference Information:**
1. Create/update in `{{vaultPath}}/03-Resources/Reference-Notes/`

**For Relationship Items:**
- Check if relationship note exists: `{{vaultPath}}/02-Areas/Relationships/{{Person}}.md`
- If exists, add to appropriate priority section
- If doesn't exist and person is important, create relationship note

---

## PHASE 2: PROJECT REVIEW

After processing inbox, do a quick project health check.

### Step 6: Scan All Active Projects

**Read all files in:** `{{vaultPath}}/01-Projects/`

**Check frontmatter for:** `status: active`

---

### Step 7: Quick Health Check (Max 10 Minutes)

For each active project, check:

1. **Has clear next action?**
   - YES → Good, move on
   - NO → Flag for user: "{{Project}} needs a next action defined"

2. **Status current?**
   - Check last-modified date
   - If >7 days: Flag as stalled

3. **Actually completed?**
   - If all tasks done → Move to `{{vaultPath}}/04-Archives/`
   - Celebrate: "{{Project}} completed!"

4. **Should be someday/maybe?**
   - If stalled >30 days, suggest: "Move to someday status?"

---

### Step 8: Update System State

**Update `{{vaultPath}}/_Context.md`:**
- List of active projects
- Count of active projects
- Top 3 priorities
- Waiting-on items

---

## Output Format

```
INBOX PROCESSING & REVIEW COMPLETE

## Inbox Processing

**Items Found:** {{N}}
**Items Processed:** {{N}}

{{For each item processed:}}
- "{{Capture}}" → {{Task added to Project X / New project created / etc.}}

**Summary:**
- Projects Created: {{N}}
- Tasks Added to Projects: {{N}}
- Fleeting Notes Created: {{N}}
- Reference Notes Created: {{N}}
- Items Deleted: {{N}}

**Inbox Status:** ZERO

---

## Project Review

**Active Projects:** {{N}}

{{If any updates:}}
**Updates:**
- [[Project X]] - Added next action
- [[Project Y]] - Archived (completed!)
- [[Project Z]] - Flagged as stalled

{{If projects need attention:}}
**Attention Needed:**
- [[Project A]] - No next action defined
- [[Project B]] - Stalled {{N}} days

---

Processing complete! Your inbox is at zero.

Want to plan your day next?
```

---

## Important Guidelines

**Processing mindset:**
- Be quick and mechanical
- Don't overthink
- When in doubt, create a fleeting note and clarify later
- If item takes <2 min to action, suggest doing it now (GTD two-minute rule)

**Project review mindset:**
- Quick health check, not deep analysis
- Flag issues, don't try to solve them all now
- Time-box this: max 10 minutes total for project scan

---

## Tools Available

- **Read** - Read inbox files, project files, context files
- **Write** - Create new project notes, fleeting notes, reference notes
- **Edit** - Add tasks to existing projects, update _Context.md
- **Grep** - Search for existing related notes
- **Glob** - Find all project files
