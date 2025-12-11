# Capture Workflow

Get it out of your head and into the system. Fast, frictionless capture.

> **GTD Principle:** "Capture first, clarify later." Don't organize or categorize during capture - just get it down.

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
- Respond: "I'd love to help you capture that! But first, let's set up your Second Brain. Would you like me to guide you through a quick setup?"
- If yes, run [setup workflow](setup.md)
- If no, offer to save in a temporary location

**Use the vault path from Memory for all paths in this workflow.**

### Claude Code Fallback

**For Claude Code only:** If Memory is empty, also check `~/.second-brain/config.json` for legacy config.

---

## Your Task

Capture the user's input to today's inbox file in their vault. That's it!

---

## How It Works

### Step 1: Determine Today's Inbox File

**File:** `{{vaultPath}}/00-Inbox/Daily/{{YYYY-MM-DD}}.md`

**If file doesn't exist, create it:**

```markdown
---
title: "Daily Inbox - {{YYYY-MM-DD}}"
created: "{{YYYY-MM-DD}}"
type: inbox
status: inbox
tags:
  - inbox
  - daily-capture
---

# Daily Inbox - {{Day}}, {{Month DD, YYYY}}

> Captures from today. Use "process my inbox" to organize.

---

## Captures

```

---

### Step 2: Add the Capture

**Append to the file:**

```markdown
### {{HH:mm}} Capture

{{User's input exactly as provided}}

---
```

**That's it!** No categorization, no routing, no intelligence. Just capture with timestamp.

---

### Step 3: Confirm

Provide simple confirmation:

```
Captured at {{HH:mm}}

Added to: {{vaultPath}}/00-Inbox/Daily/{{YYYY-MM-DD}}.md

You have {{N}} captures today.

Process your inbox when ready to organize (recommended 3x/week).
```

---

## Important Principles

**From GTD:**
- Capture = Get it out of your head
- Clarify = Figure out what it means (happens during inbox processing)
- **Don't mix them!**

**What NOT to do:**
- Don't categorize during capture
- Don't route to destinations
- Don't try to be smart about it
- Don't ask clarifying questions

**What to do:**
- Take input exactly as given
- Add timestamp
- Append to today's inbox
- Confirm and move on

---

## Handling Different Input Types

**Single thought:**
```
Capture: Call dentist tomorrow
```
Append as-is with timestamp

**Multiple thoughts (brain dump):**
```
Capture: Need to call dentist. Also should research new CRM options. Had idea about improving onboarding process.
```
Append as-is with timestamp (all together, will separate during processing)

**Long paragraphs:**
```
Remember this: [Multiple paragraphs of stream-of-consciousness]
```
Append as-is with timestamp

**The key:** Whatever the user captures, it ALL goes to the same place - today's inbox. No special handling, no categorization.

---

## Trigger Phrases

This workflow activates when user says things like:
- "Capture: [thought]"
- "Capture this: [thought]"
- "Save this thought: [thought]"
- "Remember this: [thought]"
- "Note this down: [thought]"
- "Add to my inbox: [thought]"
- "Quick capture: [thought]"

Also activate when user shares something worth preserving during conversation and you ask if they want to capture it.

---

## Proactive Capture

During conversations, if you notice:
- An interesting insight
- A task the user should remember
- An idea worth preserving
- Something they want to follow up on

**Offer:**
```
That's worth remembering. Would you like me to capture "[brief summary]" to your inbox?
```

If they agree, run this workflow with the content.

---

## Output Examples

**Quick capture:**
```
Captured at 14:32

Added to: /Users/sean/Vault/00-Inbox/Daily/2025-12-10.md

You have 3 captures today.
```

**Brain dump:**
```
Captured at 09:15

Added to: /Users/sean/Vault/00-Inbox/Daily/2025-12-10.md

You have 1 capture today (this was your first).

Process your inbox when ready to organize your captures.
```

---

## Tools Available

- **Read** - Check if today's inbox file exists
- **Write** - Create new inbox file if needed
- **Edit** - Append to existing inbox file
