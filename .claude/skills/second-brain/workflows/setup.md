# Setup Workflow

Interactive onboarding to configure your Second Brain system.

---

## Configuration Check

**CRITICAL FIRST STEP:** Check for existing configuration in Claude Memory.

### Check Memory for Configuration

1. Check Claude Memory for "Second Brain vault path"
2. Check Claude Memory for "Second Brain setup complete"

**If NOT found in Memory (or setup not complete):**
- This is FIRST-TIME SETUP
- Continue to **Step 1: Get Vault Path** below

**If found in Memory AND setup complete:**
- This is RE-RUN / UPDATE
- Continue to **FLOW B: Update Setup** below

### Claude Code Fallback

**For Claude Code only:** If Memory is empty, also check for legacy config at `~/.second-brain/config.json`. If found, migrate to Memory.

---

# FLOW A: Full Setup (First Time)

User is setting up for the first time.

---

## Step 1: Get Vault Path

```
Welcome to Second Brain setup!

First, I need to know where your Obsidian vault is located.

Please provide the full path to your Obsidian vault folder.

Examples:
- macOS: /Users/yourname/Documents/MyVault
- Windows: C:\Users\yourname\Documents\MyVault
- Linux: /home/yourname/Documents/MyVault

What's the path to your vault?
```

**Wait for response.**

**Validate the path:**
- Check if directory exists
- If not, ask: "That directory doesn't exist. Would you like me to create it, or did you mean a different path?"

**Store vault path for all remaining steps.**

---

## Step 1.5: Analyze Existing Vault (CRITICAL)

**After getting vault path, ALWAYS analyze what already exists.**

### Scan the Vault

Use Glob and Read to analyze:

```bash
# Check for existing folders
{{vaultPath}}/*/ (top-level folders)
{{vaultPath}}/**/*.md (all markdown files)
```

### Detect Existing Structure

Look for evidence of:

**Existing PARA-like structure:**
- Folders named: Projects, Areas, Resources, Archives (or similar)
- Folders with numbered prefixes (00-, 01-, 02-, etc.)

**Existing note-taking system:**
- Daily notes folder (Daily, Journal, Daily Notes)
- Templates folder
- Inbox or Capture folder
- Zettelkasten-style notes (with [[links]])

**Existing organization:**
- Count total .md files
- Identify main folders and their contents
- Check for existing frontmatter patterns

### Decision Point

**If vault is EMPTY or nearly empty (<5 files):**
- Continue to **Step 2: Welcome** (fresh setup)

**If vault has EXISTING content:**
- Continue to **FLOW C: Existing Vault Integration** below

---

# FLOW C: Existing Vault Integration

User has an existing Obsidian vault with content. We need to work WITH their existing structure, not against it.

---

## Step C1: Present Analysis

```
I've analyzed your vault at: {{vaultPath}}

**EXISTING CONTENT DETECTED**

📁 **Folder Structure Found:**
{{List all top-level folders with file counts}}

📄 **Total Notes:** {{count}} markdown files
📊 **Largest Folders:** {{top 3 by file count}}

---

**Good news:** I can set up the Second Brain system alongside your existing content without disrupting anything you already have.

I have two options:

**Option A: Additive Setup (Recommended)**
- Create the Second Brain folders (00-Inbox, 01-Projects, etc.) alongside your existing folders
- Your existing content stays exactly where it is
- You can gradually migrate content as you wish

**Option B: Migration Assistance**
- I'll analyze your content and suggest how it might map to the Second Brain structure
- We'll go through recommendations together
- You decide what to move (I won't move anything without explicit approval)

Which approach would you prefer? (A or B)
```

**Wait for response.**

---

## Step C2a: Additive Setup (Option A)

**Proceed with standard setup but:**

1. **DO NOT delete or modify any existing folders**
2. **Create Second Brain folders with prefixes to ensure sort order:**
   - `00-Inbox/` (captures)
   - `01-Projects/` (GTD projects)
   - `02-Areas/` (ongoing responsibilities)
   - `03-Resources/` (reference materials)
   - `04-Archives/` (completed items)
   - `Daily Plans/`
   - `Permanent Notes/`

3. **Check for conflicts:**
   - If a folder with same name exists, ASK before creating
   - Example: If they have "Projects/" already, ask:
     ```
     You already have a "Projects" folder with {{N}} files.

     I can either:
     1. Create "01-Projects/" (keeps yours separate)
     2. Use your existing "Projects/" folder

     Which would you prefer?
     ```

4. **Continue with Step 2 (Welcome and Introduction)**

---

## Step C2b: Migration Assistance (Option B)

### Analyze Content Categories

Read a sample of files from each major folder to understand content types.

**Look for:**
- Project-like content (tasks, action items, deadlines)
- Area-like content (ongoing topics, recurring themes)
- Reference-like content (information, research, notes from sources)
- Daily notes or journal entries
- Templates

### Present Migration Recommendations

```
Based on my analysis, here's how your content might map to the Second Brain structure:

**PROJECTS (Multi-step outcomes with end dates)**
Candidates from your vault:
- {{folder/file}} - Looks like: {{reason}}
- {{folder/file}} - Looks like: {{reason}}

**AREAS (Ongoing responsibilities, no end date)**
Candidates from your vault:
- {{folder/file}} - Looks like: {{reason}}
- {{folder/file}} - Looks like: {{reason}}

**RESOURCES (Reference materials)**
Candidates from your vault:
- {{folder/file}} - Looks like: {{reason}}

**DAILY NOTES**
{{Found/Not found}} - {{location if found}}

**UNKNOWN / NEEDS REVIEW**
- {{folder/file}} - Not sure, you should decide

---

**IMPORTANT:** I won't move anything automatically.

Would you like to:
1. Accept these recommendations and I'll help you move files
2. Review each recommendation one by one
3. Skip migration for now and just create the new structure (you can migrate later)
```

**Wait for response.**

### If User Wants to Migrate

For EACH recommended move:

```
Move "{{filename}}" from {{current location}} to {{suggested location}}?

**Why:** {{reason this fits the category}}

[Yes / No / Skip all remaining]
```

**NEVER move files without explicit "Yes" for that specific file.**

### After Migration Review

```
Migration summary:
- Moved {{N}} files to Projects
- Moved {{N}} files to Areas
- Moved {{N}} files to Resources
- Kept {{N}} files in original locations

Your existing folders are still intact. You can continue migrating manually anytime.
```

**Continue to Step 2: Welcome and Introduction**

---

## Step C3: Handle Existing Daily Notes

**If user has existing daily notes system:**

```
I noticed you have daily notes in: {{location}}

The Second Brain uses:
- `00-Inbox/Daily/` for captures (quick thoughts throughout the day)
- `Daily Plans/` for daily planning (morning planning, evening review)

Options:
1. Keep your existing daily notes where they are (I'll use separate folders)
2. Use your existing folder for captures instead of 00-Inbox/Daily/
3. Help me understand your current system so I can adapt

Which would you prefer?
```

**Adapt folder structure based on their choice.**

---

## Step C4: Handle Existing Templates

**If user has existing templates:**

```
You have existing templates in: {{location}}

I have templates for:
- Projects, Areas, Permanent Notes
- Daily plans, Meeting notes
- Relationships, Fleeting notes

Options:
1. Add my templates alongside yours (in your existing Templates folder)
2. Create a separate "Second-Brain-Templates/" folder
3. Skip templates (you'll use your existing ones)

Which would you prefer?
```

**Adapt template handling based on their choice.**

---

## Step C5: Resume Standard Setup

After handling existing vault integration, continue with:
- **Step 2: Welcome and Introduction** (adapted for existing vault)
- Remaining steps as normal

**Key adaptations for existing vault:**
- Skip creating folders that already exist (and user chose to use)
- Respect user's existing organization
- Offer to link existing content to new system
- Be explicit about what's being created vs. what exists

---

## Step 2: Welcome and Introduction

```
Vault location confirmed: {{vaultPath}}

This setup will take about 10 minutes. I'll ask you a few questions to understand your needs, then set up everything automatically.

We'll cover:
- Your goals and what you're working toward (1-2 min)
- Important people you interact with (2-3 min)
- Your first project (2-3 min)

Then I'll create your personalized system and you'll be ready to start!

Sound good? Ready to begin?
```

**Wait for confirmation.**

---

## Step 3: Get to Know Them (Two-Part Questions)

### Step 3a: Who They Are

```
To set up the system and assist you properly, I need to know a bit about you.

Tell me about yourself - your name, what you do, family situation, and what you're working toward.

For example:
- "I'm John, a software engineer, married with two kids. I'm trying to grow my freelance business while staying healthy and being present with family."

- "I'm Sarah, running a small consulting firm, single, focused on scaling my business and learning new skills. I'm trying to get things more organized."

Just share whatever feels relevant - the more you can share the better context I will have.
```

**Wait for response.**

**Extract:**
- Name
- Career/work context
- Family situation
- Goals and what they're working toward

---

### Step 3b: How They Work

```
Great! Now let me understand how you like to work so I can assist you better.

Tell me about your typical schedule and work preferences:

- What's your normal work schedule? (days per week, typical hours)
- Do you have regular breaks? (lunch time, other breaks)
- How do you prefer to interact with an assistant?
  - Quick, direct suggestions?
  - Detailed explanations?
  - Questions to help you think through decisions?
- Any other preferences about how you like to work?
  - Deep focus blocks vs. task switching?
  - Morning vs. evening productivity?
  - Prefer structured plans or flexible lists?

Share whatever helps me understand your rhythm and preferences!
```

**Wait for response.**

**Extract:**
- Work schedule
- Break times
- Communication preferences
- Energy patterns
- Planning preferences

---

## Step 4: Create Personal Context File

**File:** `{{vaultPath}}/Permanent Notes/Assisting-User-Context.md`

**Create with content:**

```markdown
---
title: "Assisting User Context"
created: "{{YYYY-MM-DD}}"
type: permanent-note
status: active
tags:
  - context
  - personal
  - system
---

# Assisting User Context

## About {{Name}}

{{Summary from Step 3a - who they are, what they do, family situation}}

## Goals

### 6-Month Goals
{{Extract from their response}}

### 3-Month Goals
{{Extract from their response}}

### 1-Month Goals
{{Extract from their response}}

## Work Style

### Schedule
{{From Step 3b}}

### Energy Patterns
{{From Step 3b}}

### Communication Preferences
{{From Step 3b}}

### Planning Preferences
{{From Step 3b}}

## Assistant Guidelines

Based on your preferences:
- {{Guideline 1}}
- {{Guideline 2}}
- {{Guideline 3}}

---

*Last updated: {{YYYY-MM-DD}}*
```

**Inform user:**
```
Created your personal context file!

This helps me:
- Respect your schedule when planning
- Align suggestions with your goals
- Match your communication preferences
- Understand what's "high priority" for you

(You can review/update it anytime at: Permanent Notes/Assisting-User-Context.md)
```

---

## Step 5: Create Default Areas

**Create these 5 areas automatically (if don't exist):**

1. `{{vaultPath}}/02-Areas/Career-Development.md`
2. `{{vaultPath}}/02-Areas/Health-Fitness.md`
3. `{{vaultPath}}/02-Areas/Personal-Development.md`
4. `{{vaultPath}}/02-Areas/Errands.md`
5. `{{vaultPath}}/02-Areas/Personal-Todos.md`

**Use Area Template for each:**

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

> {{Brief description of this area}}

---

## High Priority Tasks

<!-- Urgent/important items - scanned FIRST by daily planning -->

## Next Actions / Current Tasks

<!-- Regular priority items -->

## Someday/Maybe

<!-- Lower priority/exploratory - skipped by daily planning -->

## Waiting On

<!-- Blocked by external dependencies -->

## Completed

<!-- Finished tasks with dates -->
```

**Inform:**
```
Created your default areas for organizing tasks:

- Career & Work
- Health & Fitness
- Personal Growth
- Errands & Shopping
- Personal Todos

These give you organized places for one-off tasks.
```

---

## Step 6: Important People

```
Now let's set up relationship tracking for important people in your life.

Who are some people you interact with regularly and want to track conversations/tasks with?

Think about:
- Business partners or co-founders
- Key colleagues or team members
- Family members you coordinate with often
- Mentors, advisors, or clients

List 2-5 people (first name or "John Smith" format), or say "skip":
```

**Wait for response.**

**If they provide names:**

For EACH person:
```
For {{Person}}:

What's your relationship?
- business-partner
- colleague
- family
- mentor
- client
- friend
```

**Create:** `{{vaultPath}}/02-Areas/Relationships/{{Person-Name}}.md`

**After all created:**
```
Created relationship notes for:
- {{Person 1}} ({{type}})
- {{Person 2}} ({{type}})

When you capture "Discuss budget with {{Person}}", it will route to their note!
```

**If "skip":**
```
No problem! You can add relationship notes later.
```

---

## Step 7: Create First Project

```
Let's create your first project so you can start using the daily planner.

A "project" in GTD is anything that takes more than one step.

Examples:
- Small: "Organize garage" (5-6 steps)
- Large: "Launch website" (20+ steps)

What's ONE thing you're working on right now that has multiple steps?
```

**Wait for response.**

**Ask:**
```
For "{{Their project}}":

1. What does "done" look like?
```

**Wait.**

```
2. What's the very next action you could take?
```

**Wait.**

**Create:** `{{vaultPath}}/01-Projects/{{Project-Name}}.md`

**Fill in:**
- Desired Outcome
- First next action in High Priority section
- Status: active
- Priority: high (if aligns with goals) or medium

**Offer:**
```
Created: [[{{Project Name}}]]

Want to add another project?
1. Yes - add another
2. No - let's finish up
```

**Allow multiple projects.**

---

## Step 8: Ensure Folder Structure

Create any missing folders:
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

**Create directories silently using Bash mkdir -p**

---

## Step 9: Create _Context.md

**File:** `{{vaultPath}}/_Context.md`

**Structure:**
```markdown
---
title: "_Context"
created: "{{YYYY-MM-DD}}"
modified: "{{YYYY-MM-DD}}"
type: meta
status: active
tags:
  - context
  - system
---

# _Context

**Last Updated:** {{YYYY-MM-DD}}

## Active Projects
- [[{{Project 1}}]] - {{Outcome}}

## Key Relationships
- [[{{Person 1}}]] ({{type}})

## Top Priorities
1. {{Priority from user goals}}
2. {{Priority 2}}
3. {{Priority 3}}

## Notes for Assistant
**User Focus:** {{Goals brief}}
**Setup Date:** {{YYYY-MM-DD}}
```

---

## Step 10: Save Configuration to Memory

**Save the following to Claude Memory:**

Tell the user: "I'll save your Second Brain configuration to my memory so I remember it in future sessions."

**What to remember:**

1. **Second Brain vault path**: `{{ActualVaultPath}}`
2. **Second Brain user name**: `{{From Step 3}}`
3. **Second Brain setup complete**: `true`
4. **Second Brain setup date**: `{{YYYY-MM-DD}}`
5. **Second Brain preferences**:
   - Proactive capture: enabled
   - Inbox threshold: 5 items

**Example memory entries:**
- "User's Second Brain Obsidian vault is located at /Users/sean/Documents/MyVault"
- "User's name for Second Brain is Sean"
- "Second Brain setup was completed on 2025-12-11"
- "Second Brain preferences: proactive capture enabled, process inbox when 5+ items"

**This marks setup as complete. Claude will remember this across all future sessions.**

### Claude Code Additional Step (Optional)

**For Claude Code users:** You may also write a backup config file at `~/.second-brain/config.json` for compatibility with scripts or other tools that might need it. This is optional and not required for the skill to function.

---

## Step 11: Completion Summary

```
SETUP COMPLETE!

I've created your personalized Second Brain system:

**Folder Structure**
- Full PARA organization (Projects, Areas, Resources, Archives)
- Inbox for captures
- Daily Plans folder

**Your Personal Context**
- Saved your goals in: Permanent Notes/Assisting-User-Context.md

**{{N}} Projects**
- [[{{Project 1}}]] - {{Outcome}}
- [[{{Project 2}}]] - {{Outcome}}

**{{N}} Relationship Notes**
- {{Person 1}} ({{type}})
- {{Person 2}} ({{type}})

**5 Default Areas**
- Career, Health, Personal Dev, Errands, Personal Todos

---

## How to Use Your Second Brain

Throughout your day, just ask me to:

**Capture:** "Capture: [thought/task/idea]" or "Remember this: [...]"
**Plan:** "Plan my day" or "What should I work on?"
**Process:** "Process my inbox" or "Organize my captures"
**Review:** "Daily closeout" or "Review my day"

I'll also offer to capture interesting insights when we're discussing topics!

---

Your Second Brain is ready. Let's get things done!
```

---

# FLOW B: Update Setup (setupComplete = true)

User has already completed setup and is re-running.

---

## Step 1: Load Existing Configuration

**Recall from Claude Memory:**
- Second Brain vault path
- Second Brain user name
- Second Brain setup date

**Read user context:** `{{vaultPath}}/Permanent Notes/Assisting-User-Context.md`

**Scan existing setup:**
- Count area files in `{{vaultPath}}/02-Areas/`
- Count relationship notes in `{{vaultPath}}/02-Areas/Relationships/`
- Count active projects in `{{vaultPath}}/01-Projects/` (status: active)

---

## Step 2: Show Summary and Ask What to Update

```
EXISTING SETUP DETECTED

Your Second Brain is already configured!

**Vault:** {{vaultPath}}
**Setup Date:** {{setupDate}}
**User:** {{userName}}

**Current Configuration:**
- {{N}} Active Projects: {{list project names}}
- {{N}} Relationship Notes: {{list people names}}
- 5 Default Areas

**Your Current Goals (from Assisting-User-Context.md):**
- 6-month: {{goal}}
- 3-month: {{goal}}
- 1-month: {{goal}}

---

Would you like to update anything?

1. Update personal information (goals, work style, preferences)
2. Add more relationship notes
3. Add more projects
4. Change vault location
5. No changes needed (exit)

What would you like to do?
```

**Wait for user selection and handle accordingly.**

---

## Tools Available

- **Read** - Check config, read existing files
- **Write** - Create new files
- **Edit** - Update existing files
- **Bash** - Create directories
- **Glob** - Find existing files
