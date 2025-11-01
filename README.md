# Second Brain Starter Kit

A complete Getting Things Done (GTD) + Zettelkasten knowledge management system powered by Obsidian and Claude AI.

**Version:** 3.0
**Last Updated:** 2025-11-01
**Compatible With:** Obsidian + Claude Code

---

## What Is This?

This is a **ready-to-use productivity and knowledge management system** that helps you:

- ✅ **Capture** thoughts instantly without friction
- ✅ **Organize** projects and tasks using the GTD methodology
- ✅ **Build** a connected network of knowledge with Zettelkasten
- ✅ **Plan** your day based on energy and context
- ✅ **Review** regularly to keep everything on track

**Perfect for:**
- Knowledge workers who juggle multiple projects
- Content creators managing ideas and production
- Anyone who wants to "get things done" with less stress
- People with ADHD looking for a structured but flexible system

---

## What You'll Get

### Productivity System (GTD)
- Daily planning based on context and energy
- Weekly review process
- Project and task management
- Inbox processing workflows

### Knowledge System (Zettelkasten)
- Atomic note-taking for connected knowledge
- Progressive elaboration over time
- Maps of Content for organization
- Quality maintenance workflows

### AI-Powered Commands
- `/setup` - Interactive onboarding
- `/capture` - Quick thought and task capture
- `/process-inbox` - Organize captured items
- `/daily-plan` - Generate today's execution plan
- `/daily-closeout` - Review and plan tomorrow

**That's it!** Simple and focused.

---

## Quick Start

### New to Development?

If you don't have Git, Node.js, or Claude Code installed yet, start here:

**[Complete Beginner Setup Guide](SETUP-GUIDE.md)** - Start from zero, we'll walk you through everything!

This guide assumes you have no development environment set up. It covers:
- Installing VS Code, Git, Node.js, and Claude Code
- Downloading this repository
- Running the `/setup` command
- Configuring Obsidian
- Optional sync setup

**Estimated time:** 30-45 minutes for complete setup

---

### Already Have Prerequisites?

If you already have Git, Node.js 18+, Claude Code, and Obsidian installed, continue below.

#### Prerequisites

Before you begin, make sure you have:

- **Git** installed
- **Node.js 18+** installed
- **Claude Code** installed and authenticated
- **Obsidian** installed

**Not sure?** Run these commands:

```bash
git --version
node --version
claude --version
```

If all three show version numbers, you're ready! If not, see the [Setup Guide](SETUP-GUIDE.md).

#### Quick Start Steps

**1. Clone this repository:**

```bash
git clone https://github.com/[YOUR-USERNAME]/second-brain-starter.git
cd second-brain-starter
```

**2. Run the setup command:**

```bash
claude
```

Then type:

```
/setup
```

The setup will ask about your goals, priorities, and areas of responsibility. Answer thoughtfully - this helps the AI prioritize your work!

**3. Open the vault in Obsidian:**

1. Launch Obsidian
2. Click **"Open folder as vault"**
3. Navigate to the `ObsidianVault` folder inside this repository
4. Click **"Open"**

**4. Start using your Second Brain:**

```
/capture Your first thought or task
/daily-plan
```

**Next:** Check out the [First Week Guide](ObsidianVault/START%20HERE%20-%20First%20Week%20Guide.md) in your vault.

---

## Getting Started

Now that everything is installed, here's how to use your Second Brain!

### The Core Loop

```
CAPTURE → PROCESS → PLAN → CLOSEOUT → (repeat)
```

1. **Capture** (`/capture`) - Get thoughts out of your head
2. **Process** (`/process-inbox`) - Clarify and organize (3x/week)
3. **Plan** (`/daily-plan`) - Choose what to work on (every morning)
4. **Closeout** (`/daily-closeout`) - Review and prep tomorrow (every evening)

**That's the entire system!**

### First Week Guide

**New users:** See `ObsidianVault/START HERE - First Week Guide.md` for day-by-day checklist!

### Daily Workflow

**Throughout the Day:**
```
/capture Your thought or task here
```
- Get it out of your head (GTD Capture stage)
- Everything appends to today's inbox file
- No organizing - just capture!

**Morning (5 minutes):**
```
/daily-plan
```
- Choose what to work on today (GTD Engage stage)
- Matches tasks to your energy and context
- Creates must-do, should-do, and quick-win lists
- Enhances draft plan from last night if it exists

**Evening (5 minutes):**
```
/daily-closeout
```
- Review what you accomplished (GTD Reflect stage)
- Mark completed tasks
- Create tomorrow's DRAFT plan (refined in morning)

---

### Weekly Workflow

**3x Per Week (15 min each):**
```
/process-inbox
```
- Clarify what each capture means (GTD Clarify stage)
- Organize into projects/tasks/notes (GTD Organize stage)
- Review all active projects (GTD Reflect stage)
- Archive completed projects
- Get inbox to zero
- **This combines processing AND weekly review!**

---

## All Available Commands

| Command | Purpose | When to Use |
|---------|---------|-------------|
| `/setup` | Configure your system | First time setup |
| `/capture` | Quick capture | Anytime you have a thought |
| `/process-inbox` | Organize captures | 3x per week |
| `/daily-plan` | Plan your day | Every morning |
| `/daily-closeout` | Review and prep tomorrow | Every evening |

**That's all you need!** Simple workflow, powerful results.

---

## Folder Structure

After setup, your ObsidianVault will look like this:

```
ObsidianVault/
├── 00-Inbox/                  # Unprocessed captures
│   ├── Daily/                 # ALL captures from /capture
│   └── Fleeting-Notes/        # Knowledge items from /process-inbox
├── 01-Projects/               # Active projects (GTD multi-step outcomes)
├── 02-Areas/                  # Ongoing responsibilities (no end date)
│   ├── Career-Development.md
│   ├── Health-Fitness.md
│   ├── Personal-Development.md
│   ├── Errands.md
│   ├── Personal-Todos.md
│   └── Relationships/         # Individual notes per person
├── 03-Resources/              # Reference materials
│   └── Reference-Notes/       # Summaries of external sources
├── 04-Archives/               # Completed projects
├── Daily Plans/               # Generated plans
├── Meeting Notes/             # Meeting documentation
├── Permanent Notes/           # Your insights (Zettelkasten)
└── Templates/                 # Reusable templates
```

**Simple and Clean!**

**Default Areas (Created During Setup):**
- **Career-Development** - Professional growth, skills, networking
- **Health-Fitness** - Physical health, mental wellness
- **Personal-Development** - Learning, hobbies, growth
- **Errands** - Shopping, errands, things to buy
- **Personal-Todos** - Miscellaneous one-off tasks
- **Relationships/** - Folder for important people (business partners, family, colleagues)

**What goes where:**
- **All captures** → 00-Inbox/Daily
- **Projects** → 01-Projects
- **One-off tasks** → Appropriate Area (Errands, Personal-Todos, etc.)
- **People items** → Relationships/Person-Name.md
- **Your insights** → Permanent Notes
- **Source summaries** → 03-Resources/Reference-Notes

**During `/setup`, you'll define your specific areas and create your first projects!**

---

## Customization

### Your Areas and Projects

The folder structure is **customized to you** during `/setup`. Examples:

**Projects might be:**
- Work/Website-Redesign
- Personal/Home-Renovation
- Side-Business/Product-Launch

**Areas might be:**
- Career-Development
- Health-Fitness
- Content-Creation
- Financial-Planning

### Your Tags

Tags are also customized during setup. Common examples:
- `#work`, `#personal`, `#side-business`
- `#status/active`, `#status/waiting`
- `#priority/high`, `#priority/medium`

### Templates

All templates are in `ObsidianVault/Templates/` and can be customized:
- Atomic Note.md
- Meeting Note.md
- Project Template.md
- MOC Template.md

---

## Troubleshooting

### Changes Not Syncing

**iCloud:**
- Check Settings → iCloud → iCloud Drive is enabled
- Verify Obsidian has access to iCloud
- Wait 1-2 minutes for sync to process

**Obsidian Sync:**
- Check sync icon in bottom-right of Obsidian
- Click to see sync status and logs

**Git:**
- Remember to commit and push changes:
  ```bash
  git add .
  git commit -m "Update notes"
  git push
  ```

---

### Obsidian Shows Empty Vault

**Cause:** Opened wrong folder

**Fix:**
1. In Obsidian: Settings → General
2. Click "Open another vault"
3. Navigate to correct `ObsidianVault` folder
4. Make sure you're opening `ObsidianVault`, not the repository root

---

### Installation Issues

For problems with installing Git, Node.js, Claude Code, or Obsidian, see the [Setup Guide Troubleshooting](SETUP-GUIDE.md#troubleshooting) section.

---

## Learning Path

### Week 1: Foundation
- Run `/setup` and answer questions thoughtfully
- Use `/capture` throughout the day
- Run `/daily-plan` each morning
- Get comfortable with basic capture

### Week 2: Build the Habit
- Run `/daily-plan` every morning
- Run `/daily-closeout` every evening
- Run `/process-inbox` 3x this week (Mon/Wed/Fri)
- Start seeing the system work for you

### Week 3: Refine Your Process
- Notice patterns in what you capture
- Adjust your daily rhythm
- Start creating project notes in `01-Projects/`
- Link related notes together

### Week 4: System Mastery
- The workflow becomes natural
- Customize templates if desired
- Add more projects and areas
- The system adapts to you

---

## Need Help?

### Documentation

- **CLAUDE.md** - Complete system reference (in this folder)
- **Skill References** - In `.claude/skills/` folders
- **Templates** - In `ObsidianVault/Templates/`

### Common Questions

**Q: Do I need to use all the commands every day?**
A: No! Use `/capture` anytime, `/daily-plan` in mornings, `/daily-closeout` in evenings, and `/process-inbox` 3x per week.

**Q: Can I modify the system?**
A: Yes! The templates and folder structure are yours to customize.

**Q: What if I don't want to use Git/Claude/Obsidian?**
A: This system is designed to work with all three. Individual pieces may not work alone.

**Q: Is this free?**
A: The system is free. Obsidian is free. Claude Code requires a Claude account (free tier available). Obsidian Sync is optional ($10/month).

**Q: How do I backup my vault?**
A: Use Obsidian Sync, iCloud, or Git. The vault is just markdown files - easy to backup!

---

## What's Next?

Once you're set up:

1. **Run `/setup`** if you haven't already
2. **Capture something** with `/capture`
3. **Plan your day** with `/daily-plan`
4. **Use it daily** for 2 weeks to build the habit
5. **Customize** as you learn what works for you

**The system gets better the more you use it!**

---

## Technical Details

### File Structure

```
SecondBrain/
├── .claude/                   # Claude Code configuration
│   ├── commands/              # Slash commands
│   └── skills/                # AI skills
├── ObsidianVault/             # Your actual vault
│   └── [all your notes]
├── README.md                  # This file
└── CLAUDE.md                  # System reference
```

### How It Works

1. **Claude Code** provides AI-powered commands
2. **Commands** read/write markdown files in ObsidianVault
3. **Obsidian** displays and links the files beautifully
4. **You** capture, organize, and get things done!

---

## License

This system is provided as-is for personal use. Customize freely!

**Attribution appreciated but not required.**

---

## Credits

**Methodologies:**
- GTD - David Allen
- Zettelkasten - Niklas Luhmann
- PARA - Tiago Forte

**Built with:**
- Claude Code (Anthropic)
- Obsidian (Obsidian.md)

---

**Version:** 3.0
**Last Updated:** 2025-11-01
**Status:** Production Ready

**Ready to build your Second Brain?** 🧠

Run `/setup` to begin!
