---
description: Process inbox items using GTD methodology - clarify, organize, and review projects
---

# Process Inbox Command

Process all inbox items using GTD principles: clarify what each item means, organize into appropriate locations, and conduct a quick project review.

> **GTD Stages:** This command handles Clarify + Organize + Reflect (review)

---

## Context

**CRITICAL FIRST STEP:** Read `.claude/vault-config.json` to get the vault folder name.

**If vault-config.json doesn't exist:**
- User hasn't run `/setup` yet
- Respond: "Please run `/setup` first to configure your Second Brain!"
- Do not proceed

**Extract `vaultFolder` value and use it for all paths in this command.**

---

**Then read these files:**
1. `.claude/skills/gtd-workflow/SKILL.md` - GTD methodology
2. `.claude/skills/gtd-workflow/references/gtd-methodology.md` - Core GTD principles
3. `.claude/skills/obsidian-mastery/SKILL.md` - Obsidian conventions
4. `{{vaultFolder}}/_Context.md` - Current system state (if exists)
5. `{{vaultFolder}}/Permanent Notes/Assisting-User-Context.md` - User's goals

---

## Your Task

Process inbox items and review projects in TWO phases.

---

## PHASE 1: CLARIFY INBOX ITEMS

### Step 1: Scan All Inbox Locations

**Scan these folders:**
- `{{vaultFolder}}/00-Inbox/Daily/` - Daily captures
- `{{vaultFolder}}/00-Inbox/Fleeting-Notes/` - Fleeting notes (if any)

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

**Before routing, determine priority level using GTD skill guidance:**

**Reference:** `.claude/skills/gtd-workflow/SKILL.md` section "Determining Task Priority"

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
   - About a specific person? → See "For Relationship Items" below

2. **Add to appropriate section based on priority (from Step 4):**
   - Priority: HIGH → "High Priority" or "High Priority Tasks" section
   - Priority: NEXT ACTION → "Next Actions" or "Current Tasks" section
   - Priority: SOMEDAY → "Someday/Maybe" section

3. **Format:** `- [ ] {{Action}} #context/X #energy/X #time/Xm`

**Example routing:**
- "Call John ASAP about budget" + relates to top goal → Personal-Todos → High Priority section
- "Buy groceries this week" → Errands → Next Actions section
- "Eventually learn Spanish" → Personal-Development → Someday/Maybe section

**For Projects (multi-step outcomes):**
1. Create new project note in `{{vaultFolder}}/01-Projects/`
2. Use Project Template
3. **Determine project priority:**
   - Relates to user's top 1-3 goals? → priority: high
   - Has deadline <30 days? → priority: high
   - Otherwise → priority: medium
4. Fill out:
   - Desired Outcome (GTD: what does done look like?)
   - Next Actions section: Add at least one concrete action (determine priority using Step 4 logic)
   - Status: active, priority: (from step 3), area: (if applicable)
5. Move original capture content into project notes section

**For Knowledge/Insights:**
1. Create fleeting note in `{{vaultFolder}}/00-Inbox/Fleeting-Notes/`
2. Use Fleeting Note template
3. Capture the core thought
4. Mark for later development into permanent note
5. **Don't try to create permanent notes now** - that's deep work for later

**For Reference Information:**
1. Determine topic
2. Search for existing related notes using Grep
3. If exists: Add info to existing note
4. If not: Create new in `{{vaultFolder}}/03-Resources/Reference-Notes/`

**For Relationship Items (About Specific People):**

**Detect if capture mentions a specific person:**
- "Talk to John about..."
- "Ask Sarah for..."
- "Follow up with Mom on..."
- "Discuss with [business partner name]..."

**If person mentioned:**
1. Check if relationship note exists: `{{vaultFolder}}/02-Areas/Relationships/{{Person-Name}}.md`
2. **If exists:**
   - Determine priority (use Step 4 logic)
   - Add to appropriate section based on priority:
     - Priority: HIGH → "High Priority" section
     - Priority: NEXT ACTION → "Next Actions → To Discuss" subsection
     - Priority: SOMEDAY → "Someday/Maybe" section
   - If waiting on them → "Waiting On" section
3. **If doesn't exist AND person is important (business partner, family, key colleague):**
   - Create new relationship note using Relationship Note template
   - Fill in relationship type (business-partner, family, colleague, etc.)
   - Determine priority and add to appropriate section
   - Inform user: "Created relationship note for {{Person}}"
4. **If person is not important/one-off:** Just add as regular task to relevant area

**Example routing with priority:**
- "Need to discuss Q4 budget with John ASAP" → `Relationships/John.md` → High Priority (ASAP keyword)
- "Ask Mom about Thanksgiving plans" → `Relationships/Mom.md` → Next Actions (no urgency)
- "Might talk to Sarah about new tool eventually" → `Relationships/Sarah.md` → Someday/Maybe
- "Call dentist office tomorrow" → `Health-Fitness.md` → Next Actions (not a relationship note)

**For Trash:**
1. Delete the capture

---

## PHASE 2: PROJECT REVIEW

After processing inbox, do a quick project health check.

### Step 5: Scan All Active Projects

**Read all files in:**
- `{{vaultFolder}}/01-Projects/`

**Check frontmatter for:** `status: active`

---

### Step 6: Quick Health Check (Max 10 Minutes)

For each active project, check:

1. **Has clear next action?**
   - YES → Good, move on
   - NO → Flag for user: "{{Project}} needs a next action defined"

2. **Status current?**
   - Check last-modified date
   - If >7 days: Flag as stalled

3. **Actually completed?**
   - If status says "done" → Move to `{{vaultFolder}}/04-Archives/`
   - Celebrate: "{{Project}} completed!"

4. **Should be someday/maybe?**
   - If stalled >30 days, suggest: "Move to someday status?"

---

### Step 7: Update System State

**Update `{{vaultFolder}}/_Context.md`:**
- List of active projects
- Count of active projects
- Top 3 priorities
- Waiting-on items

**If _Context.md doesn't exist, create it with basic structure.**

---

## Output Format

```
📥 INBOX PROCESSING & REVIEW COMPLETE

## Inbox Processing

**Items Found:** {{N}}
**Items Processed:** {{N}}

{{For each item processed:}}
✓ "{{Capture}}" → {{Task added to Project X / New project created / Fleeting note created / etc.}}

**Summary:**
- ✅ Projects Created: {{N}}
- ✅ Tasks Added to Projects: {{N}}
- ✅ Fleeting Notes Created: {{N}}
- ✅ Reference Notes Created: {{N}}
- 🗑️ Items Deleted: {{N}}

**Inbox Status:** ✅ ZERO

---

## Project Review

**Active Projects:** {{N}}

{{If any updates:}}
**Updates:**
- [[Project X]] - Added next action
- [[Project Y]] - Archived (completed!)
- [[Project Z]] - Flagged as stalled (no update in {{N}} days)

{{If projects need attention:}}
**⚠️ Attention Needed:**
- [[Project A]] - No next action defined
- [[Project B]] - Stalled {{N}} days - consider moving to someday?

**Projects Archived:** {{N}}

---

✅ Processing complete!
✅ Inbox at zero
✅ All active projects reviewed

💡 Next: Run `/daily-plan` to prioritize your work for today.
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
- User can deep-dive specific projects later

**Skill coordination:**
- Use **gtd-workflow skill** for actionable items (apply clarifying questions, understand next actions)
- Use **obsidian-mastery skill** for note structure (fleeting notes, reference notes, linking)

---

## Tools Available

- **Read** - Read inbox files, project files, context files
- **Write** - Create new project notes, fleeting notes, reference notes
- **Edit** - Add tasks to existing projects, update _Context.md
- **Grep** - Search for existing related notes
- **Glob** - Find all project files

---

Now process the inbox!
