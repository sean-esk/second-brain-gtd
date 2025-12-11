# Second Brain Starter Kit

A complete Getting Things Done (GTD) + Zettelkasten knowledge management system powered by Obsidian and Claude AI.

**Version:** 4.0
**Last Updated:** 2025-12-11
**Compatible With:** Claude Code + Claude Desktop + Obsidian

---

## What Is This?

This is a **ready-to-use productivity and knowledge management system** that helps you:

- **Capture** thoughts instantly without friction
- **Organize** projects and tasks using the GTD methodology
- **Build** a connected network of knowledge with Zettelkasten
- **Plan** your day based on energy and context
- **Review** regularly to keep everything on track

**Perfect for:**
- Knowledge workers who juggle multiple projects
- Content creators managing ideas and production
- Anyone who wants to "get things done" with less stress
- People with ADHD looking for a structured but flexible system

---

## What's New in v4.0

- **Natural Language Triggers** - Just talk naturally instead of slash commands
- **Unified Skill** - One skill does everything (replaces multiple skills + commands)
- **Works Everywhere** - Same skill for Claude Code AND Claude Desktop
- **Existing Vault Support** - Setup intelligently handles existing Obsidian vaults
- **Persistent Config** - Your settings persist across sessions

---

## Installation

### Option 1: Claude Code (Recommended for Power Users)

**Prerequisites:** Git, Node.js 18+, Claude Code, Obsidian

```bash
# Clone the repository
git clone https://github.com/[YOUR-USERNAME]/second-brain-gtd.git
cd second-brain-gtd

# Start Claude Code
claude
```

Then just say: **"Set up my second brain"**

The skill is automatically available from the `.claude/skills/second-brain/` folder.

---

### Option 2: Claude Desktop (Easiest)

1. **Download the skill:**
   - Download or clone this repository
   - Navigate to `.claude/skills/second-brain/`
   - Zip the entire `second-brain` folder

2. **Install in Claude Desktop:**
   - Open Claude Desktop
   - Go to Settings → Skills (or Features)
   - Click "Add Skill" or "Import"
   - Select the `second-brain.zip` file

3. **Start using it:**
   - Just say: **"Set up my second brain"**
   - Claude will ask for your Obsidian vault path and guide you through setup

---

### New to Development?

If you don't have Git, Node.js, or Claude Code installed yet:

**[Complete Beginner Setup Guide](SETUP-GUIDE.md)** - Start from zero!

---

## How to Use

### Just Talk Naturally!

No commands to memorize. Just tell Claude what you want:

| What You Want | What to Say |
|---------------|-------------|
| **First-time setup** | "Set up my second brain" or "Configure my vault" |
| **Capture a thought** | "Capture: [your thought]" or "Remember this: [idea]" |
| **Plan your day** | "Plan my day" or "What should I work on today?" |
| **Process captures** | "Process my inbox" or "Organize my captures" |
| **End of day review** | "Daily closeout" or "Review my day" |

**Proactive Capture:** When you're researching or discussing topics, Claude will offer to save valuable insights to your Second Brain!

---

## The Core Workflow

```
CAPTURE → PROCESS → PLAN → CLOSEOUT → (repeat)
```

### Throughout the Day: Capture
> "Capture: Need to call dentist about appointment"
> "Remember this: Great idea for the project..."

- Get thoughts out of your head instantly
- Everything goes to your daily inbox
- No organizing - just capture!

### Morning (5 min): Plan
> "Plan my day"

- Reviews your projects and areas
- Asks about your energy, time, and context
- Creates a prioritized task list

### Evening (5 min): Closeout
> "Daily closeout"

- Review what you accomplished
- Mark tasks complete
- Create tomorrow's draft plan

### 3x Per Week (15 min): Process
> "Process my inbox"

- Clarify what each capture means
- Organize into projects/tasks/notes
- Review active projects
- Archive completed items

---

## What Gets Created

### Your Vault Structure

```
YourVault/
├── 00-Inbox/                  # Unprocessed captures
│   ├── Daily/                 # Quick captures
│   └── Fleeting-Notes/        # Knowledge items
├── 01-Projects/               # Active projects
├── 02-Areas/                  # Ongoing responsibilities
│   ├── Career-Development.md
│   ├── Health-Fitness.md
│   ├── Personal-Development.md
│   ├── Errands.md
│   ├── Personal-Todos.md
│   └── Relationships/         # Notes per person
├── 03-Resources/              # Reference materials
├── 04-Archives/               # Completed projects
├── Daily Plans/               # Your daily plans
├── Meeting Notes/             # Meeting documentation
└── Permanent Notes/           # Your insights (Zettelkasten)
```

### Configuration

Your settings are saved to `~/.second-brain/config.json`:

```json
{
  "vaultPath": "/path/to/your/vault",
  "setupComplete": true,
  "userName": "Your Name",
  "preferences": {
    "proactiveCapture": true,
    "inboxThreshold": 5
  }
}
```

This persists across sessions - no need to reconfigure!

---

## Existing Vault Support

**Already have an Obsidian vault?** No problem!

During setup, Claude will:
1. Analyze your existing folder structure
2. Show you what's already there
3. Offer two approaches:
   - **Additive:** Create Second Brain folders alongside your content
   - **Migration:** Help categorize and move existing files (with your approval)

**Your existing content is never deleted or modified without explicit permission.**

---

## Example Conversations

### Quick Capture
```
You: Capture: Call mom about birthday plans
Claude: Captured to your inbox! Added to 2025-12-11.md
```

### Morning Planning
```
You: Plan my day
Claude: Good morning! Let me check your projects...

I found 12 tasks across 4 projects.

How's your energy today?
1. High - Ready for deep work
2. Medium - Normal productivity
3. Low - Administrative tasks only

You: 2

Claude: And how much time do you have?

You: About 4 hours of focused time

Claude: Here's your plan for today:

**Must Do:**
- [ ] Review quarterly report (Project: Q4 Planning)
- [ ] Send follow-up email to client (Project: Client Work)

**Should Do:**
- [ ] Draft blog post outline (Area: Content)
- [ ] Schedule dentist appointment (Area: Health)

**Quick Wins (under 5 min):**
- [ ] Reply to John's message (Relationship: John)

I've saved this to Daily Plans/2025-12-11.md
```

### Proactive Capture
```
You: What are the best practices for API design?

Claude: [Provides detailed answer about API design...]

That's a valuable insight about versioning strategies.
Would you like me to capture this to your Second Brain?

You: Yes please

Claude: Captured to your inbox! You can develop this into
a permanent note during your next inbox processing.
```

---

## Learning Path

### Week 1: Foundation
- Say "Set up my second brain" and complete setup
- Use "Capture: [thought]" throughout the day
- Say "Plan my day" each morning

### Week 2: Build the Habit
- "Plan my day" every morning
- "Daily closeout" every evening
- "Process my inbox" on Mon/Wed/Fri

### Week 3: Refine Your Process
- Notice patterns in what you capture
- Start creating project notes
- Link related notes together

### Week 4: System Mastery
- The workflow becomes natural
- Customize to your preferences
- The system adapts to you

---

## Troubleshooting

### "Config not found" error
Run setup first: Say "Set up my second brain"

### Captures not appearing
Check your vault path in `~/.second-brain/config.json`

### Want to change vault location
Say "Set up my second brain" again and provide the new path

### Obsidian shows empty vault
Make sure Obsidian is pointing to the correct vault folder (the one you specified during setup)

---

## Technical Details

### Skill Location

```
.claude/skills/second-brain/
├── SKILL.md              # Main skill definition
├── config/               # Configuration templates
├── workflows/            # Setup, capture, planning, etc.
├── references/           # GTD, PARA, Zettelkasten docs
└── templates/            # Note templates
```

### How It Works

1. **Claude** (Code or Desktop) loads the second-brain skill
2. **Natural language** triggers the appropriate workflow
3. **Files** are created/updated in your Obsidian vault
4. **Obsidian** displays and links your notes beautifully
5. **Config** persists at `~/.second-brain/config.json`

---

## FAQ

**Q: Do I need both Claude Code AND Claude Desktop?**
A: No! Use whichever you prefer. The skill works with both.

**Q: Is my data stored in the cloud?**
A: No. Everything is stored locally in your Obsidian vault. Claude just helps you manage it.

**Q: Can I use this with an existing Obsidian vault?**
A: Yes! Setup intelligently handles existing vaults without destroying your content.

**Q: What if I forget the commands?**
A: There are no commands to memorize. Just talk naturally: "capture this", "plan my day", etc.

**Q: Is this free?**
A: The skill is free. Obsidian is free. Claude requires a subscription for extended use.

---

## Credits

**Methodologies:**
- GTD - David Allen
- Zettelkasten - Niklas Luhmann
- PARA - Tiago Forte

**Built with:**
- Claude (Anthropic)
- Obsidian (Obsidian.md)

---

**Version:** 4.0
**Last Updated:** 2025-12-11
**Status:** Production Ready

---

**Ready to build your Second Brain?**

Just say: **"Set up my second brain"**
