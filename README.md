# Second Brain Starter Kit

A complete Getting Things Done (GTD) + Zettelkasten knowledge management system powered by Obsidian and Claude AI.

**Version:** 3.0
**Last Updated:** 2025-10-25
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

## Requirements

Before you begin, you'll need to install a few tools. Follow these steps IN ORDER for the best experience!

### Required Tools

1. **VS Code** - Your command center (includes terminal for running commands)
2. **Git** - For downloading this repository
3. **Claude CLI** - AI-powered assistant
4. **Obsidian** - Note-taking app

---

## Installation Guide

**IMPORTANT:** Follow these steps in this exact order!

### Step 1: Install VS Code (Your Command Center)

VS Code is where you'll run all the commands. It has a built-in terminal that makes everything easier.

**Why VS Code first?**
- Built-in terminal (no need to find your system terminal)
- Easy to navigate folders
- Can edit configuration files if needed
- Beginner-friendly interface

**Download for your platform:**
- **macOS:** https://code.visualstudio.com/Download (choose "Mac")
- **Windows:** https://code.visualstudio.com/Download (choose "Windows")
- **Linux:** https://code.visualstudio.com/Download (choose "Linux")

**Install:**
1. Download the appropriate version
2. Run the installer
3. Complete installation with default settings

**Verify it works:**
1. Open VS Code
2. Go to Terminal → New Terminal (or press Ctrl+` / Cmd+`)
3. You should see a command prompt

**Alternative:** If you're already comfortable with terminals, you can use your system terminal instead. But we recommend VS Code for beginners!

---

### Step 2: Install Git

Git lets you download and manage this repository.

**macOS:**
```bash
# Check if Git is already installed
git --version

# If not installed, install via Homebrew
brew install git

# Or download from: https://git-scm.com/download/mac
```

**Windows:**
1. Download Git from: https://git-scm.com/download/win
2. Run the installer
3. Use default settings (just keep clicking "Next")

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get update
sudo apt-get install git
```

**Verify installation in VS Code:**
1. Open VS Code
2. Open Terminal (Terminal → New Terminal)
3. Type: `git --version`
4. Should show: `git version 2.x.x`

---

### Step 3: Download This Repository

Now let's get the Second Brain files.

**Option A: Download ZIP (Recommended)**

1. Go to: https://github.com/[YOUR-USERNAME]/second-brain-starter
2. Click the green "Code" button
3. Click "Download ZIP"
4. Extract to your Documents folder:
   - macOS: `/Users/YourName/Documents/SecondBrain/`
   - Windows: `C:\Users\YourName\Documents\SecondBrain\`

**Option B: Git Clone (In VS Code Terminal)**

1. Open VS Code
2. Open Terminal (Terminal → New Terminal)
3. Navigate to Documents:
   ```bash
   cd ~/Documents              # macOS/Linux
   cd C:\Users\YourName\Documents  # Windows
   ```
4. Clone the repository:
   ```bash
   git clone https://github.com/[YOUR-USERNAME]/second-brain-starter.git
   mv second-brain-starter SecondBrain
   ```

**Important:** Remember this folder location!

---

### Step 4: Install Claude CLI

Claude CLI is the AI assistant that powers the smart commands.

**Installation:**

Visit: https://docs.claude.com/en/docs/claude-code/getting-started

Follow the installation instructions for your operating system.

**Quick install (macOS/Linux):**
```bash
curl -fsSL https://claude.ai/install.sh | sh
```

**Windows:**
Download the installer from the Claude Code website and run it.

**Verify installation:**
```bash
claude --version
# Should show the Claude CLI version
```

**First-time setup:**
```bash
# Claude CLI will walk you through authentication
claude auth login
```

---

### Step 5: Run the Setup Command

Now let's configure your Second Brain using VS Code!

**Open the folder in VS Code:**

1. Launch VS Code
2. Go to File → Open Folder
3. Navigate to and select the `SecondBrain` folder you downloaded
4. Click "Select Folder" / "Open"

**Open the terminal in VS Code:**

1. Go to Terminal → New Terminal (or press Ctrl+` on Windows / Cmd+` on Mac)
2. The terminal opens at the bottom of VS Code
3. You should be in the SecondBrain folder automatically

**Verify you're in the right place:**

```bash
ls -la      # macOS/Linux
dir         # Windows
```

You should see: `.claude` folder, `ObsidianVault` folder, `README.md`, `CLAUDE.md`

**Run the setup:**

In the VS Code terminal, type:

```bash
claude
```

Then type:
```
/setup
```

**The setup will ask you questions like:**
- What are your personal goals?
- What do you want to accomplish in 6 months?
- What are your main areas of responsibility?

**Answer thoughtfully** - this helps the AI understand how to prioritize your work!

**What `/setup` creates:**
- Your personalized context file with goals
- Complete PARA folder structure
- Initial configuration files
- Welcome documentation

**Time needed:** 5-10 minutes

---

### Step 6: Install Obsidian

Obsidian is where you'll interact with your Second Brain.

**Download Obsidian:**
- Website: https://obsidian.md
- macOS: https://obsidian.md/download (Mac Intel or Apple Silicon)
- Windows: https://obsidian.md/download (Windows)
- Linux: https://obsidian.md/download (AppImage, .deb, or Snap)

**Install:**
1. Download the appropriate version
2. Run the installer
3. Complete the installation

**Don't open Obsidian yet!** We'll do that in the next step.

---

### Step 7: Open Your Vault in Obsidian

Now let's connect Obsidian to your Second Brain files.

**Launch Obsidian:**

**First-time launch:**
1. Obsidian will ask: "Create a new vault or open existing?"
2. Click: **"Open folder as vault"**
3. Navigate to: `SecondBrain/ObsidianVault`
   - macOS: `/Users/YourName/Documents/SecondBrain/ObsidianVault`
   - Windows: `C:\Users\YourName\Documents\SecondBrain\ObsidianVault`
4. Click "Open"

**You're in!** 🎉

You should now see:
- Folder structure in the left sidebar
- README.md file open in the main area
- Your Assisting-User-Context file in Permanent Notes

---

## Syncing Your Vault (Optional)

Want to access your Second Brain on multiple devices? Here are your options:

### Option 1: Obsidian Sync (Paid, Official)

**Best for:** People who want seamless sync with zero setup

**Cost:** $10/month (includes version history and mobile app sync)

**Setup:**
1. In Obsidian, go to Settings → Core Plugins
2. Enable "Sync"
3. Sign up for Obsidian Sync
4. Follow the prompts to connect your vault

**Website:** https://obsidian.md/sync

---

### Option 2: iCloud Drive (Free, Mac/iOS Only)

**Best for:** Apple users who want free syncing

**Setup:**

1. **Move your vault to iCloud:**
   ```bash
   # Create Obsidian folder in iCloud Drive
   mkdir -p ~/Library/Mobile\ Documents/com~apple~CloudDocs/Obsidian

   # Move your vault
   mv ~/Documents/SecondBrain/ObsidianVault ~/Library/Mobile\ Documents/com~apple~CloudDocs/Obsidian/
   ```

2. **Update your Claude Code working directory:**
   - Close Claude Code
   - Navigate to the new location:
     ```bash
     cd ~/Library/Mobile\ Documents/com~apple~CloudDocs/Obsidian
     ```
   - Open Claude Code from here

3. **Re-open vault in Obsidian:**
   - In Obsidian: Settings → Files and Links
   - Close current vault
   - Open folder: `~/Library/Mobile Documents/com~apple~CloudDocs/Obsidian/ObsidianVault`

4. **On iOS:**
   - Install Obsidian from App Store
   - Open vault at: iCloud Drive → Obsidian → ObsidianVault

**Syncing happens automatically!**

---

### Option 3: Git (Free, Advanced Users)

**Best for:** Developers comfortable with version control

**Setup:**
1. Initialize Git in the ObsidianVault folder:
   ```bash
   cd ObsidianVault
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. Create a private GitHub repository
3. Push your vault:
   ```bash
   git remote add origin https://github.com/yourusername/your-vault.git
   git push -u origin main
   ```

4. On other devices:
   ```bash
   git clone https://github.com/yourusername/your-vault.git
   ```

**Note:** Be careful not to commit sensitive information!

---

### Option 4: Dropbox, Google Drive, OneDrive

**Best for:** People already using these services

**Setup:**
1. Move `ObsidianVault` folder to your sync folder
2. Update paths in Claude Code (same as iCloud process above)
3. Open vault from sync folder in Obsidian

**Important:** Some sync services can cause conflicts. Obsidian Sync is most reliable.

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

### "Command not found" when running `/setup`

**Cause:** Claude CLI not in the correct directory

**Fix:**
```bash
# Navigate to the 0-claude folder (parent of ObsidianVault)
cd ~/Documents/SecondBrain  # Or wherever you put it

# Verify you see .claude folder
ls -la

# Now run Claude
claude
```

---

### "Can't find ObsidianVault folder"

**Cause:** Commands expect vault in specific location

**Fix:**
Make sure:
1. Your terminal is in the `SecondBrain` folder (parent of ObsidianVault)
2. The folder is named `ObsidianVault` exactly (case-sensitive)
3. Run `/setup` if you haven't yet

---

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
4. Open it

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
**Last Updated:** 2025-10-25
**Status:** Production Ready

**Ready to build your Second Brain?** 🧠

Run `/setup` to begin!
