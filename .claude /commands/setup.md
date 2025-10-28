---
description: Interactive step-by-step setup to configure your Second Brain system
---

# Second Brain Setup

Welcome! I'm your assistant. Let me help you set up your Second Brain system with a few quick questions.

---

## Your Task

Guide the user through a conversational, step-by-step setup. **Ask ONE question at a time. Wait for response. Then next question.**

**Total time:** ~10 minutes
**Approach:** Progressive, not overwhelming

---

## Setup Flow

### Step 0: Detect Vault Folder (CRITICAL - DO THIS FIRST!)

> **CRITICAL:** Commands need to know which folder is your Obsidian vault. Detect it before anything else.

**Scan for vault folders:**

Use Glob to find folders that contain:
- `.obsidian` subfolder (Obsidian vault marker)
- OR `Templates/` subfolder (our vault structure)

**Count results:**

**If exactly 1 vault found:**
```
✓ Found your vault folder: {{FolderName}}

I'll configure all commands to work with this vault.
```
- Store vault name for later steps
- No user interaction needed

**If 0 vaults found:**
```
I'm looking for your Obsidian vault folder, but I don't see one yet.

The vault folder should be named something like:
- ObsidianVault
- General
- MyVault
- SecondBrain

What would you like to name your vault folder?
```
- Wait for user response
- Use their provided name
- Will create the folder in later steps

**If multiple vaults found:**
```
I found multiple potential vault folders:

{{List each folder name}}

Which one should I use for your Second Brain?
```
- Wait for user selection
- Use selected folder name

**Store the vault folder name in a variable for all subsequent steps.**

---

### Step 0b: Update Command Files with Vault Name

**If vault name is NOT "ObsidianVault":**

Need to update all command files to use the correct vault name.

**Update these files:**
1. `.claude/commands/capture.md`
2. `.claude/commands/process-inbox.md`
3. `.claude/commands/daily-plan.md`
4. `.claude/commands/daily-closeout.md`

**For each file:**
1. Read the file
2. Replace ALL instances of `ObsidianVault/` with `{{ActualVaultName}}/`
3. Write back

**Also create/update:** `.claude/vault-config.json`

```json
{
  "vaultFolder": "{{ActualVaultName}}",
  "setupDate": "{{YYYY-MM-DD}}",
  "setupComplete": true,
  "userName": "{{Will be filled in Step 2}}"
}
```

**Inform user:**
```
✓ Configured all commands to work with your vault: {{VaultName}}

All files will be saved in the correct location!
```

**If vault name IS "ObsidianVault":**
- No command updates needed (already correct)
- Still create/update vault-config.json with vault name
- Inform user configuration is complete

---

### Step 1: Welcome and Introduction

Greet the user warmly:

```
Welcome to your Second Brain setup! 🧠

This will take about 10 minutes. I'll ask you a few questions to understand your needs, then set up everything automatically.

We'll cover:
✓ Your goals and what you're working toward (1-2 min)
✓ Important people you interact with (2-3 min)
✓ Your first project (2-3 min)

Then I'll create your personalized system and you'll be ready to start!

Sound good? Ready to begin?
```

**Wait for user confirmation (y/n or any positive response).**

---

### Step 2: Get to Know Them (ONE Holistic Question)

**Ask about them as a person - name, career, family, goals:**

```
To set up the system and assist you properly, I need to know a bit about you.

Tell me about yourself - your name, what you do, family situation, and what you're working toward.

For example:
- "I'm John, a software engineer, married with two kids. I'm trying to grow my freelance business while staying healthy and being present with family."
- "I'm Sarah, running a small consulting firm, single, focused on scaling my business and learning new skills."

Just share whatever feels relevant - 3-5 sentences is perfect!
```

**Wait for their response.**

**Extract from their response:**
- Name (for personalization!)
- Career/work context
- Family situation
- Goals and what they're working toward
- Priorities and focus areas

**This becomes the foundation for:**
- Creating Assisting-User-Context.md
- Determining their priorities
- Personalizing future interactions
- Understanding what's "high priority" for them

**Also update vault-config.json with their name:**

Read `.claude/vault-config.json`, update `userName` field with their name, write back.

---

### Step 3: Create Their Personal Context File

**Behind the scenes** (don't overwhelm user with details):

**File:** `{{VaultFolder}}/Permanent Notes/Assisting-User-Context.md`

**Note:** Use the vault folder name detected in Step 0. Throughout all remaining steps, use `{{VaultFolder}}/` instead of hardcoding "ObsidianVault/".

**Fill out:**
- **Summary:** One-sentence synthesis of their primary focus
- **Current Focus:** Extract goals and priorities from Step 2 response
- **Identity/Roles:** Synthesize from what they shared (name, career, family)
- **Why It Matters:** How this context helps with prioritization
- **Assistant Behavior:** Standard guidance about ADHD-friendly editing, prioritization, checking goals for priority determination

**Don't show them the file contents** - just confirm it was created.

---

### Step 4: Create Default Areas (Inform, Don't Ask)

**Create these 5 default areas automatically:**

1. **File:** `ObsidianVault/02-Areas/Career-Development.md`
   - Use Area Template
   - Purpose: "Professional growth, skills, networking, career advancement"
   - Leave task sections empty

2. **File:** `ObsidianVault/02-Areas/Health-Fitness.md`
   - Use Area Template
   - Purpose: "Physical health, mental wellness, fitness, and self-care"
   - Leave task sections empty

3. **File:** `ObsidianVault/02-Areas/Personal-Development.md`
   - Use Area Template
   - Purpose: "Learning, hobbies, personal growth, and development"
   - Leave task sections empty

4. **File:** `ObsidianVault/02-Areas/Errands.md`
   - Use Area Template
   - Purpose: "Shopping, errands, things to buy or pick up"
   - Leave task sections empty

5. **File:** `ObsidianVault/02-Areas/Personal-Todos.md`
   - Use Area Template
   - Purpose: "Miscellaneous one-off personal tasks and to-dos"
   - Leave task sections empty

**Then inform user:**

```
✅ Created your default areas for organizing tasks:

- Career & Work - Professional stuff
- Health & Fitness - Health, exercise, wellness
- Personal Growth - Learning, hobbies
- Errands & Shopping - Things to buy
- Personal Todos - Random one-off tasks

These give you organized places for all those one-off tasks like "call dentist" or "order replacement filter."

(You can customize these later if needed!)
```

**Don't wait for response - just inform and move on.**

---

### Step 5: Important People (CRITICAL for Relationships)

**Now ask about people:**

```
Now let's set up relationship tracking for important people in your life.

Who are some people you interact with regularly and want to track conversations/tasks with?

Think about:
- Business partners or co-founders
- Key colleagues or team members
- Family members you coordinate with often
- Mentors, advisors, or clients

List 2-5 people (first name or "John Smith" format, one per line):
```

**Wait for their list.**

**If they provide names:**

For EACH person they listed, ask:

```
For {{Person 1 from their list}}:

What's your relationship?
- business-partner
- colleague
- family
- mentor
- client
- friend
```

**Wait for response.**

**Then create relationship note:**

1. **File:** `ObsidianVault/02-Areas/Relationships/{{Person-Name}}.md`
2. Use Relationship Note template
3. Fill in:
   - Title: Person's name
   - Relationship type: from their response
   - Leave task sections empty (user will add as they capture)

**Repeat for each person.**

**After all created:**

```
✅ Created relationship notes for:
- {{Person 1}} ({{relationship type}})
- {{Person 2}} ({{relationship type}})
- {{Person 3}} ({{relationship type}})

When you capture something like "Need to discuss budget with {{Person 1}}", it will automatically route to their relationship note!
```

**If they say "none" or "skip":**

```
No problem! You can add relationship notes later when you need them.

The Relationships folder is ready whenever you want to track important people.
```

---

### Step 6: Create Their First Project

**Ask for one project:**

```
Let's create your first project so you can start using the daily planner.

A "project" in GTD is anything that takes more than one step.

Examples:
- Small: "Organize garage this weekend" (5-6 steps)
- Large: "Launch new website" (20+ steps)

What's ONE thing you're working on right now that has multiple steps?

(Just one for now - you can add more anytime!)
```

**Wait for their response.**

**Then ask clarifying questions:**

```
Great! For "{{Their project}}":

1. What does "done" look like?

(Describe the finished state - be specific!)
```

**Wait for response.**

```
2. What's the very next action you could take on this?

(Must be concrete and doable - like "Call John at 555-1234" not just "Contact John")
```

**Wait for response.**

**Determine priority based on their goals:**

If project relates to their stated 3-6 month goals → priority: high
Otherwise → priority: medium

**Create the project:**

1. **File:** `ObsidianVault/01-Projects/{{Project-Name}}.md`
2. Use Project Template
3. Fill in:
   - Title
   - Desired Outcome (from their answer to Q1)
   - High Priority Next Actions section: Add their first next action (from Q2)
   - Status: active
   - Priority: high or medium (based on goal alignment)
   - Why It Matters: Connect to their 3-6 month goals

**Then offer option:**

```
✅ Created: [[{{Project Name}}]]

Want to add one more project, or is this good to start?

1. Add one more project
2. That's good - let's move on
```

**If Option 1:** Repeat questions for second project (max 2 projects total)
**If Option 2:** Move to Step 7

---

### Step 7: Create Folder Structure (Behind Scenes)

Verify all folders exist. Create any missing:

```
ObsidianVault/
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

**Don't mention this to user** - just do it.

---

### Step 8: Create _Context.md File

**File:** `ObsidianVault/_Context.md`

**Content:**

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

> System state and current priorities

---

## Active Projects

{{List projects created}}

- [[{{Project 1}}]] - {{Desired outcome}}
- [[{{Project 2}}]] - {{Desired outcome}} (if created)

---

## Key Relationships

{{List people created}}

- [[{{Person 1}}]] ({{relationship type}})
- [[{{Person 2}}]] ({{relationship type}})

---

## Top Priorities

{{From their goals response}}

1. {{Priority 1 from their 3-6 month goals}}
2. {{Priority 2}}
3. {{Priority 3}}

---

## Notes for Assistant

**User Focus:** {{Their 3-6 month goals in brief}}
**Setup Date:** {{YYYY-MM-DD}}
```

**Don't show user** - just create it.

---

### Step 9: Create Welcome README

**File:** `ObsidianVault/README.md`

```markdown
# Welcome to Your Second Brain! 🧠

Setup completed {{YYYY-MM-DD}}

## What You Have

✅ **5 Default Areas** - Organized places for one-off tasks
✅ **{{N}} Relationship Notes** - Track important people
✅ **{{N}} Projects** - Ready to work on
✅ **Personal Context** - Your goals captured in `Permanent Notes/Assisting-User-Context.md`
✅ **Complete folder structure** - Everything organized

---

## Quick Start

See: `START HERE - First Week Guide.md` for your first week checklist!

### The Core Loop

1. **Capture:** `/capture` - Get thoughts out of your head (anytime)
2. **Process:** `/process-inbox` - Organize captures (3x/week)
3. **Plan:** `/daily-plan` - Choose what to work on (every morning)
4. **Closeout:** `/daily-closeout` - Review and prep tomorrow (every evening)

---

## Your Setup

**Projects:**
- [[{{Project 1}}]] - {{One-line description}}
- [[{{Project 2}}]] - {{One-line description}}

**Areas:**
- Career-Development
- Health-Fitness
- Personal-Development
- Errands
- Personal-Todos

**Relationships:**
- {{Person 1}} ({{type}})
- {{Person 2}} ({{type}})

---

## Next Steps

1. Start capturing: `/capture [your first thought]`
2. Tomorrow morning: `/daily-plan`
3. Open in Obsidian (download from obsidian.md)

You're all set! Let's build your Second Brain. 🚀
```

---

### Step 10: Completion Summary

Provide encouraging summary:

```
✅ SETUP COMPLETE!

I've created your personalized Second Brain system:

📁 **Folder Structure**
- Full PARA organization (Projects, Areas, Resources, Archives)
- Inbox for captures
- Daily Plans folder
- Templates ready to use

📝 **Your Personal Context**
- Saved your goals in: `Permanent Notes/Assisting-User-Context.md`
- I'll reference this to help prioritize your work

📋 **Your First {{N}} Projects**
- [[{{Project 1}}]] - {{Desired outcome}}
- [[{{Project 2}}]] - {{Desired outcome}}
- Each has a clear outcome and first next action

🤝 **{{N}} Relationship Notes Created**
- {{Person 1}} ({{type}})
- {{Person 2}} ({{type}})
- Track conversations and commitments

🗂️ **5 Default Areas for One-Off Tasks**
- Career-Development
- Health-Fitness
- Personal-Development
- Errands
- Personal-Todos

---

## What's Next?

**Right now:**
1. Start capturing your thoughts:
   ```
   /capture [anything on your mind]
   ```

**Tomorrow morning:**
2. Plan your day:
   ```
   /daily-plan
   ```
   You already have projects and areas, so this will generate a real plan!

**This week:**
3. Process your captures (3x this week):
   ```
   /process-inbox
   ```

**Every evening:**
4. Review your day:
   ```
   /daily-closeout
   ```

---

📖 **New User?** Check out: `START HERE - First Week Guide.md` in your vault for a day-by-day checklist!

🎯 **Ready to open in Obsidian?**
- Download Obsidian from https://obsidian.md
- Open the `ObsidianVault` folder as a vault
- See your system come to life!

---

Your Second Brain is ready. Let's get things done! 🚀
```

---

## Important Implementation Notes

**Question pacing:**
- ONE question at a time
- Wait for response before next question
- Keep questions simple and concrete
- Provide examples for clarity
- Don't ask about things you can auto-create (like default areas)

**What to auto-create:**
- Default 5 areas (Career, Health, Personal Dev, Errands, Personal Todos)
- Folder structure
- _Context.md
- README

**What to ask about:**
- Their 3-6 month goals (ONE combined question)
- Important people (2-5 names + relationship types)
- First project (ONE project, with outcome + next action)
- Optional second project

**Behind the scenes:**
- Use their goals response to create Assisting-User-Context.md
- Use their people list to create relationship notes
- Use their project response to create first project(s)
- Connect everything (_Context.md tracks it all)

---

Now run the guided setup process!
