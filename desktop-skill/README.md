# Second Brain Skill for Claude Desktop

A personal knowledge management and productivity skill combining GTD (Getting Things Done), Zettelkasten note-taking, and PARA organization for Obsidian vaults.

## Features

- **Quick Capture** - Instantly capture thoughts, tasks, and ideas with natural language
- **Daily Planning** - AI-powered daily planning based on your projects and energy
- **Inbox Processing** - GTD-style clarification and organization
- **Daily Closeout** - End-of-day review and tomorrow preparation
- **Proactive Capture** - Claude offers to save valuable insights during conversations
- **Persistent Config** - Set up once, remembered forever

## Quick Start

### 1. Install the Skill

```bash
# Copy skill to Claude skills directory
cp -r second-brain ~/.claude/skills/
```

### 2. Start Using It

Just tell Claude:

> "Set up my Second Brain"

Claude will:
1. Ask for your Obsidian vault path
2. **Save it to `~/.second-brain/config.json`** (remembered forever)
3. Guide you through personalization (goals, people, first project)
4. Create your folder structure

**That's it!** No manual config needed.

## How Configuration Works

1. **First time**: Claude asks "Where is your vault?" → You provide the path
2. **Claude saves**: Creates `~/.second-brain/config.json` with your vault path
3. **Forever after**: Claude reads this file automatically - no more setup needed

```json
// ~/.second-brain/config.json (created automatically)
{
  "vaultPath": "/Users/you/Documents/MyVault",
  "setupComplete": true,
  "userName": "Your Name"
}
```

## Usage

Just talk naturally:

| Say | What Happens |
|-----|--------------|
| "Capture: call dentist tomorrow" | Saves to today's inbox |
| "Plan my day" | Creates prioritized daily plan |
| "Process my inbox" | Organizes captures into projects/areas |
| "Daily closeout" | Reviews day, preps tomorrow |
| "Set up my second brain" | First-time or reconfigure |

### Proactive Capture

When discussing topics, Claude will offer:

> "That's an interesting insight. Would you like me to capture this to your Second Brain?"

## Vault Structure

The skill creates/manages this structure:

```
YourVault/
├── 00-Inbox/
│   ├── Daily/              # Daily captures (YYYY-MM-DD.md)
│   └── Fleeting-Notes/     # Knowledge items
├── 01-Projects/            # Active projects
├── 02-Areas/               # Ongoing responsibilities
│   ├── Career-Development.md
│   ├── Health-Fitness.md
│   ├── Personal-Development.md
│   ├── Errands.md
│   ├── Personal-Todos.md
│   └── Relationships/      # People notes
├── 03-Resources/
│   └── Reference-Notes/
├── 04-Archives/            # Completed projects
├── Daily Plans/            # Generated plans
├── Meeting Notes/
├── Permanent Notes/        # Zettelkasten notes
│   └── Assisting-User-Context.md
└── Templates/
```

## Daily Workflow

| When | Action | Time |
|------|--------|------|
| Throughout day | "Capture: [thought]" | 30 sec |
| 3x per week | "Process my inbox" | 15 min |
| Every morning | "Plan my day" | 5 min |
| Every evening | "Daily closeout" | 5 min |

**Total: ~20-25 min/day + 45 min/week = Sustainable!**

## Skill Contents

```
second-brain/
├── SKILL.md                    # Main skill with triggers
├── config/
│   ├── config-template.json    # Config template
│   └── README.md               # Config docs
├── workflows/
│   ├── setup.md                # Interactive onboarding
│   ├── capture.md              # Quick capture
│   ├── process-inbox.md        # GTD clarify/organize
│   ├── daily-plan.md           # Morning planning
│   └── daily-closeout.md       # Evening review
├── references/
│   ├── gtd-methodology.md      # GTD principles
│   ├── para-zettelkasten.md    # Folder organization
│   ├── obsidian-mastery.md     # Obsidian conventions
│   └── tagging-strategy.md     # Tag taxonomy
└── templates/
    ├── project.md              # Multi-step outcomes
    ├── area.md                 # Ongoing responsibilities
    ├── permanent-note.md       # Zettelkasten notes
    ├── fleeting-note.md        # Quick knowledge capture
    ├── relationship.md         # People tracking
    ├── meeting-note.md         # Meeting documentation
    ├── daily-plan.md           # Daily execution plan
    ├── daily-inbox.md          # Daily capture file
    └── user-context.md         # User goals & preferences
```

## Troubleshooting

### Skill Not Activating

1. Verify skill is in `~/.claude/skills/second-brain/`
2. Check `SKILL.md` has valid YAML frontmatter
3. Try: "Use my Second Brain to capture..."

### Vault Path Issues

1. Check config: `cat ~/.second-brain/config.json`
2. Ensure path is absolute (starts with `/`)

### Reset Setup

```bash
rm ~/.second-brain/config.json
```
Then say "set up my second brain" to start fresh.

## Integration with Obsidian

Works with any Obsidian vault. Recommended plugins:

- **Core**: Backlinks, Tags, Search
- **Optional**: Dataview, Tasks

## Updates

```bash
cp -r second-brain ~/.claude/skills/
```

Config at `~/.second-brain/config.json` is preserved.

## License

MIT
