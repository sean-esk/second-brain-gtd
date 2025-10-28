---
description: Capture thoughts, tasks, ideas, and notes quickly - everything goes to your daily inbox
---

# Capture Command

Get it out of your head and into the system. Fast, frictionless capture.

> **GTD Principle:** "Capture first, clarify later." Don't organize or categorize during capture - just get it down.

---

## Context

**CRITICAL FIRST STEP:** Read `.claude/vault-config.json` to get the vault folder name.

```json
{
  "vaultFolder": "ObsidianVault"  // or "General" or whatever user named it
}
```

**If vault-config.json doesn't exist:**
- User hasn't run `/setup` yet
- Respond: "Please run `/setup` first to configure your Second Brain!"
- Do not proceed

**Extract `vaultFolder` value and use it for all paths in this command.**

---

## Your Task

Capture the user's input to today's inbox file in their vault. That's it!

---

## How It Works

### Step 1: Determine Today's Inbox File

**File:** `{{vaultFolder}}/00-Inbox/Daily/{{YYYY-MM-DD}}.md`

(Use the vault folder from vault-config.json)

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

> Captures from today. Process with `/process-inbox` command.

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
✅ Captured at {{HH:mm}}

📝 Added to: {{vaultFolder}}/00-Inbox/Daily/{{YYYY-MM-DD}}.md

{{Count total captures in today's file}}

💡 Run `/process-inbox` to organize your captures (recommended 3x/week).
```

---

## Important Principles

**From GTD:**
- Capture = Get it out of your head
- Clarify = Figure out what it means (happens during `/process-inbox`)
- **Don't mix them!**

**What NOT to do:**
- ❌ Don't categorize during capture
- ❌ Don't route to destinations
- ❌ Don't try to be smart about it
- ❌ Don't ask clarifying questions

**What to do:**
- ✅ Take input exactly as given
- ✅ Add timestamp
- ✅ Append to today's inbox
- ✅ Confirm and move on

---

## Handling Different Input Types

**Single thought:**
```
/capture Call dentist tomorrow
```
→ Append as-is with timestamp

**Multiple thoughts (brain dump):**
```
/capture Need to call dentist. Also should research new CRM options. Had idea about improving onboarding process.
```
→ Append as-is with timestamp

**Long paragraphs:**
```
/capture [Multiple paragraphs of stream-of-consciousness]
```
→ Append as-is with timestamp

**The key:** Whatever the user captures, it ALL goes to the same place - today's inbox. No special handling, no categorization.

---

## Output Examples

**Quick capture:**
```
✅ Captured at 14:32

📝 Added to: {{vaultFolder}}/00-Inbox/Daily/2025-10-25.md

You have 3 captures today.

💡 Run `/process-inbox` to organize (recommended 3x/week).
```

**Brain dump:**
```
✅ Captured at 09:15

📝 Added to: {{vaultFolder}}/00-Inbox/Daily/2025-10-25.md

You have 1 capture today (this was your first).

💡 Run `/process-inbox` when ready to organize your captures.
```

---

## Integration with Workflow

**Capture feeds into:**
- `/process-inbox` - Reads these files and processes each capture using GTD clarifying questions

**User workflow:**
1. Throughout the day: `/capture` whenever something comes to mind
2. 3x per week: `/process-inbox` to organize everything

**Benefits of this approach:**
- **Fast capture** - No thinking required
- **Batch processing** - More efficient than one-at-a-time
- **GTD compliant** - Respects capture/clarify separation
- **Simple** - Just get it out of your head!

---

## Tools Available

- **Read** - Check if today's inbox file exists
- **Write** - Create new inbox file if needed
- **Edit** - Append to existing inbox file

**That's all you need!**

---

Now capture the user's input!
