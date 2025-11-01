# Second Brain Setup Guide for Beginners

**Version:** 3.0
**Last Updated:** 2025-11-01
**Estimated Time:** 30-45 minutes

---

## Who Is This Guide For?

This guide is for **complete beginners** who are starting from zero. If you don't have Git, Node.js, VS Code, or Claude Code installed yet - you're in the right place!

**We'll walk you through:**
- Installing every prerequisite tool
- Downloading the Second Brain repository
- Configuring your personalized system
- Getting Obsidian set up
- Optional: Setting up sync across devices

**Already have the prerequisites installed?** Skip to the [main README](README.md) for a quick start guide.

---

## Table of Contents

1. [Prerequisites Overview](#prerequisites-overview)
2. [System Requirements](#system-requirements)
3. [Step-by-Step Installation](#step-by-step-installation)
   - [Step 1: Install VS Code](#step-1-install-vs-code)
   - [Step 2: Install Git](#step-2-install-git)
   - [Step 3: Install Node.js](#step-3-install-nodejs)
   - [Step 4: Download This Repository](#step-4-download-this-repository)
   - [Step 5: Install Claude Code](#step-5-install-claude-code)
   - [Step 6: Run the `/setup` Command](#step-6-run-the-setup-command)
   - [Step 7: Install and Configure Obsidian](#step-7-install-and-configure-obsidian)
4. [Optional: Sync Setup](#optional-sync-setup)
5. [Troubleshooting](#troubleshooting)
6. [What's Next](#whats-next)

---

## Prerequisites Overview

Before you can use the Second Brain system, you'll need to install several tools. Don't worry - we'll guide you through each one!

### What You'll Install

✅ **VS Code** - A code editor with a built-in terminal (your command center)
✅ **Git** - Version control tool for downloading the repository
✅ **Node.js 18+** - JavaScript runtime required by Claude Code
✅ **Claude Code** - AI assistant that powers the smart commands
✅ **Obsidian** - Beautiful note-taking app for your vault

### Already Have These?

If you already have Git, Node.js 18+, and Claude Code installed, you can skip to the [Quick Start section in the main README](README.md#quick-start).

**Not sure if you have them?** Open a terminal and run:

```bash
git --version
node --version
claude --version
```

If all three commands show version numbers, you're ready for the quick start!

---

## System Requirements

Make sure your computer meets these requirements:

### Operating System

- **macOS:** 10.15 (Catalina) or later
- **Windows:** 10 or later with WSL (Windows Subsystem for Linux)
- **Linux:** Ubuntu 20.04+ or equivalent

### Hardware

- **RAM:** 4GB minimum (8GB recommended)
- **Disk Space:** At least 2GB free
- **Internet:** Required for installation and Claude Code authentication

### Other Requirements

- Administrator/sudo access to install software
- An active internet connection
- A Claude account (free tier available at https://claude.ai)

---

## Step-by-Step Installation

Follow these steps **in order** for the smoothest experience!

---

### Step 1: Install VS Code

VS Code is where you'll run all the commands. It has a built-in terminal that makes everything easier.

#### Why VS Code First?

- Built-in terminal (no need to find your system terminal)
- Easy to navigate folders
- Can edit configuration files if needed
- Beginner-friendly interface

#### Download VS Code

Choose your platform:

- **macOS:** https://code.visualstudio.com/Download (choose "Mac")
- **Windows:** https://code.visualstudio.com/Download (choose "Windows")
- **Linux:** https://code.visualstudio.com/Download (choose "Linux")

#### Install

1. Download the appropriate version for your operating system
2. Run the installer
3. Complete installation with default settings (just keep clicking "Next")
4. Launch VS Code when installation completes

#### Verify It Works

1. Open VS Code
2. Go to **Terminal → New Terminal** (or press `Ctrl+\`` on Windows / `Cmd+\`` on Mac)
3. You should see a command prompt at the bottom of the window

**Success!** If you see a terminal, you're ready to move on.

#### Troubleshooting

**Terminal won't open:**
- Try restarting VS Code
- On Windows: Make sure you selected "Add to PATH" during installation
- On macOS: Grant terminal permissions if prompted

**Alternative:** If you're already comfortable with terminals, you can use your system terminal instead. But we recommend VS Code for beginners!

---

### Step 2: Install Git

Git lets you download and manage this repository.

#### macOS

**Check if Git is already installed:**

```bash
git --version
```

If you see a version number (like `git version 2.x.x`), Git is already installed! **Skip to Step 3.**

**If not installed, install via Homebrew:**

First, install Homebrew (if you don't have it):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install Git:

```bash
brew install git
```

**Or download directly:** https://git-scm.com/download/mac

#### Windows

1. Download Git from: https://git-scm.com/download/win
2. Run the installer
3. Use default settings (just keep clicking "Next")
4. **Important:** Make sure "Git from the command line and also from 3rd-party software" is selected

**Windows users:** You may also need WSL (Windows Subsystem for Linux) for Claude Code. See [Windows-specific notes](#windows-wsl-setup).

#### Linux (Ubuntu/Debian)

```bash
sudo apt-get update
sudo apt-get install git
```

**Other distributions:**
- **Fedora:** `sudo dnf install git`
- **Arch:** `sudo pacman -S git`

#### Verify Installation

In VS Code, open the terminal (Terminal → New Terminal) and run:

```bash
git --version
```

You should see something like: `git version 2.x.x`

#### Troubleshooting

**"git: command not found":**
- Restart VS Code
- On Windows: Make sure Git was added to PATH during installation
- On macOS/Linux: Try opening a new terminal window

---

### Step 3: Install Node.js

Node.js is a JavaScript runtime required by Claude Code. You need version 18 or higher.

#### Check if Node.js is Already Installed

```bash
node --version
npm --version
```

If both commands show version numbers **and Node.js is 18 or higher**, you're good! **Skip to Step 4.**

#### macOS

**Option A: Using Homebrew (Recommended)**

```bash
brew install node
```

**Option B: Download directly**

Download the LTS version from: https://nodejs.org/

Run the installer and use default settings.

#### Windows

1. Download the LTS version from: https://nodejs.org/
2. Run the installer
3. Use default settings (keep clicking "Next")
4. **Important:** Check "Automatically install necessary tools" if prompted

#### Linux (Ubuntu/Debian)

```bash
# Install Node.js 18+ from NodeSource
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**Other distributions:**
- See https://nodejs.org/en/download/package-manager for your specific distribution

#### Verify Installation

```bash
node --version
npm --version
```

You should see:
- Node.js version 18.x or higher
- npm version 9.x or higher

#### Troubleshooting

**Version too old (below 18):**
- Uninstall the old version and install the latest LTS
- On macOS: `brew upgrade node`
- On Windows/Linux: Download and install the latest from nodejs.org

**"node: command not found":**
- Restart VS Code
- Restart your computer if needed
- Verify the installer completed successfully

---

### Step 4: Download This Repository

Now let's get the Second Brain files onto your computer.

#### Choose Your Download Method

**Option A: Download ZIP (Recommended for Beginners)**

1. Go to: https://github.com/[YOUR-USERNAME]/second-brain-starter
2. Click the green **"Code"** button
3. Click **"Download ZIP"**
4. Extract the ZIP file to your Documents folder:
   - **macOS:** `/Users/YourName/Documents/SecondBrain/`
   - **Windows:** `C:\Users\YourName\Documents\SecondBrain\`
   - **Linux:** `/home/yourname/Documents/SecondBrain/`

**Option B: Git Clone (In VS Code Terminal)**

1. Open VS Code
2. Open Terminal (Terminal → New Terminal)
3. Navigate to your Documents folder:

   **macOS/Linux:**
   ```bash
   cd ~/Documents
   ```

   **Windows:**
   ```bash
   cd C:\Users\YourName\Documents
   ```

4. Clone the repository:
   ```bash
   git clone https://github.com/[YOUR-USERNAME]/second-brain-starter.git
   mv second-brain-starter SecondBrain
   ```

#### Verify the Download

In VS Code:
1. Go to **File → Open Folder**
2. Navigate to and select the `SecondBrain` folder
3. Click **"Select Folder"** / **"Open"**

You should see in the left sidebar:
- `.claude` folder
- `ObsidianVault` folder
- `README.md`
- `CLAUDE.md`

#### Troubleshooting

**Can't find the folder:**
- Make sure you extracted the ZIP completely
- Remember where you saved it (check Downloads folder)
- Try searching for "SecondBrain" in Finder/Explorer

---

### Step 5: Install Claude Code

Claude Code is the AI assistant that powers the smart commands like `/capture` and `/daily-plan`.

#### Before You Begin

**You'll need:**
- A Claude account (sign up at https://claude.ai)
- An active subscription or free tier access
- **Note:** Claude Code requires an API key or Pro subscription

#### Installation

**macOS/Linux (Quick Install):**

```bash
curl -fsSL https://claude.ai/install.sh | sh
```

**Windows:**

Download the installer from: https://docs.claude.com/en/docs/claude-code/getting-started

Run the installer and follow the prompts.

**Manual installation (all platforms):**

Visit the official documentation: https://docs.claude.com/en/docs/claude-code/setup

#### Verify Installation

```bash
claude --version
```

You should see the Claude CLI version number.

#### Authenticate Claude Code

**First-time setup:**

```bash
claude auth login
```

This will:
1. Open a browser window
2. Ask you to log in to your Claude account
3. Generate an authentication token
4. Save it securely on your system

**Follow the prompts to complete authentication.**

#### Windows: WSL Setup

**Windows users:** Claude Code requires WSL (Windows Subsystem for Linux).

If you haven't installed WSL yet:

1. Open PowerShell as Administrator
2. Run:
   ```powershell
   wsl --install
   ```
3. Restart your computer
4. After restart, complete Ubuntu setup
5. Install Claude Code inside WSL (using the Linux instructions above)

**More info:** https://docs.microsoft.com/en-us/windows/wsl/install

#### Troubleshooting

**"claude: command not found":**
- Restart your terminal/VS Code
- On macOS/Linux: Check if `~/.local/bin` is in your PATH
- On Windows: Make sure you're running inside WSL

**Authentication fails:**
- Verify you have a valid Claude account
- Check your internet connection
- Try logging out and back in: `claude auth logout` then `claude auth login`

**Billing/subscription errors:**
- Claude Code may require a paid subscription or API access
- Visit https://claude.ai/settings to check your account status

---

### Step 6: Run the `/setup` Command

Now let's configure your Second Brain to match your goals and workflow!

#### Open the Folder in VS Code

1. Launch VS Code
2. Go to **File → Open Folder**
3. Navigate to and select the `SecondBrain` folder you downloaded
4. Click **"Select Folder"** / **"Open"**

#### Open the Terminal in VS Code

1. Go to **Terminal → New Terminal** (or press `Ctrl+\`` / `Cmd+\``)
2. The terminal opens at the bottom of VS Code
3. You should be in the SecondBrain folder automatically

#### Verify You're in the Right Place

**macOS/Linux:**
```bash
ls -la
```

**Windows:**
```bash
dir
```

You should see: `.claude` folder, `ObsidianVault` folder, `README.md`, `CLAUDE.md`

#### Run the Setup

In the VS Code terminal, type:

```bash
claude
```

Then type:

```
/setup
```

#### What to Expect

The `/setup` command will ask you questions like:

- **What are your personal goals?**
- **What do you want to accomplish in 6 months?**
- **What are your main areas of responsibility?**
- **What projects are you working on?**

**Answer thoughtfully!** This helps the AI understand how to prioritize your work and suggest tasks.

#### What `/setup` Creates

- Your personalized context file (`Assisting-User-Context.md`) with your goals
- Complete PARA folder structure (Projects, Areas, Resources, Archives)
- Initial configuration files
- Welcome documentation
- Your first project and area templates

#### Time Needed

5-10 minutes (depending on how detailed your responses are)

#### Troubleshooting

**"Command not found":**
- Make sure you're in the `SecondBrain` folder (parent of ObsidianVault)
- Run `pwd` (macOS/Linux) or `cd` (Windows) to verify location
- Try running `ls -la` to see if `.claude` folder exists

**Setup fails midway:**
- Check your internet connection
- Verify Claude authentication is working: `claude auth status`
- Try running `/setup` again - it can resume from where it left off

**Can't access `/setup` command:**
- Make sure Claude Code is properly authenticated
- Verify `.claude/commands/` folder exists
- Try restarting VS Code

---

### Step 7: Install and Configure Obsidian

Obsidian is where you'll interact with your Second Brain - capturing thoughts, viewing notes, and navigating your knowledge graph.

#### Download Obsidian

- **Website:** https://obsidian.md
- **macOS:** https://obsidian.md/download (Mac Intel or Apple Silicon)
- **Windows:** https://obsidian.md/download (Windows)
- **Linux:** https://obsidian.md/download (AppImage, .deb, or Snap)

#### Install

1. Download the appropriate version for your operating system
2. Run the installer
3. Complete the installation with default settings

#### Launch Obsidian

**First-time launch:**

When you open Obsidian for the first time, it will ask: **"Create a new vault or open existing?"**

1. Click: **"Open folder as vault"**
2. Navigate to the `ObsidianVault` folder inside your `SecondBrain` directory:
   - **macOS:** `/Users/YourName/Documents/SecondBrain/ObsidianVault`
   - **Windows:** `C:\Users\YourName\Documents\SecondBrain\ObsidianVault`
   - **Linux:** `/home/yourname/Documents/SecondBrain/ObsidianVault`
3. Click **"Open"**

#### You're In!

You should now see:
- Folder structure in the left sidebar
- Files and notes in the main area
- Your `Assisting-User-Context.md` file in Permanent Notes
- The First Week Guide in the vault root

**Congratulations!** Your Second Brain is now set up and ready to use!

#### Troubleshooting

**Vault appears empty:**
- Verify you opened the `ObsidianVault` folder (not the `SecondBrain` folder)
- In Obsidian: Settings → General → Check vault location
- Make sure `/setup` completed successfully first

**Can't find the ObsidianVault folder:**
- Navigate to your Documents folder
- Look for `SecondBrain/ObsidianVault`
- Double-check the folder name is spelled correctly (case-sensitive)

**Files aren't showing:**
- Click the folder icon in the left sidebar to expand folders
- Check if `.obsidian` folder exists (hidden folder with settings)
- Try closing and reopening the vault

---

## Optional: Sync Setup

Want to access your Second Brain on multiple devices? Here are your options.

**Important:** Set up sync ONLY after your system is working locally. Don't try to sync during initial setup!

---

### Option 1: Obsidian Sync (Paid, Official)

**Best for:** People who want seamless sync with zero setup

**Cost:** $10/month (includes version history and mobile app sync)

**Pros:**
- Official Obsidian service
- Automatic syncing
- Version history
- End-to-end encryption
- Works on mobile (iOS/Android)

**Setup:**

1. In Obsidian, go to **Settings → Core Plugins**
2. Enable **"Sync"**
3. Sign up for Obsidian Sync at https://obsidian.md/sync
4. Follow the prompts to connect your vault
5. Install Obsidian mobile app and sign in to sync

**Website:** https://obsidian.md/sync

---

### Option 2: iCloud Drive (Free, Mac/iOS Only)

**Best for:** Apple users who want free syncing

**Pros:**
- Free
- Automatic syncing
- Works with iOS Obsidian app

**Cons:**
- Mac/iOS only
- Can be slow sometimes
- Occasional sync conflicts

**Setup:**

1. **Move your vault to iCloud:**

   ```bash
   # Create Obsidian folder in iCloud Drive
   mkdir -p ~/Library/Mobile\ Documents/com~apple~CloudDocs/Obsidian

   # Move your vault
   mv ~/Documents/SecondBrain/ObsidianVault ~/Library/Mobile\ Documents/com~apple~CloudDocs/Obsidian/
   ```

2. **Update your working directory:**

   ```bash
   # Move the entire SecondBrain folder
   mv ~/Documents/SecondBrain ~/Library/Mobile\ Documents/com~apple~CloudDocs/SecondBrain
   ```

3. **Re-open vault in Obsidian:**

   - In Obsidian: **Settings → Files and Links**
   - Click **"Open another vault"**
   - Navigate to: `~/Library/Mobile Documents/com~apple~CloudDocs/SecondBrain/ObsidianVault`
   - Open it

4. **Update VS Code working directory:**

   - In VS Code: **File → Open Folder**
   - Navigate to: `~/Library/Mobile Documents/com~apple~CloudDocs/SecondBrain`
   - Open it

5. **On iOS:**

   - Install Obsidian from App Store
   - Open vault at: **iCloud Drive → SecondBrain → ObsidianVault**

**Syncing happens automatically!**

---

### Option 3: Git (Free, Advanced Users)

**Best for:** Developers comfortable with version control

**Pros:**
- Free
- Version history
- Full control
- Works on any device

**Cons:**
- Requires manual commits/pushes
- More technical
- Risk of merge conflicts

**Setup:**

1. **Initialize Git in the ObsidianVault folder:**

   ```bash
   cd ObsidianVault
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Create a private GitHub repository:**

   - Go to https://github.com/new
   - Create a **private** repository (don't share personal notes publicly!)
   - Name it something like `my-second-brain-vault`

3. **Push your vault:**

   ```bash
   git remote add origin https://github.com/yourusername/my-second-brain-vault.git
   git branch -M main
   git push -u origin main
   ```

4. **On other devices:**

   ```bash
   git clone https://github.com/yourusername/my-second-brain-vault.git
   ```

5. **Daily workflow:**

   ```bash
   # Pull changes from other devices
   git pull

   # After making changes, push them
   git add .
   git commit -m "Daily update"
   git push
   ```

**Important:** Be careful not to commit sensitive information! Consider using a `.gitignore` file.

---

### Option 4: Dropbox, Google Drive, OneDrive

**Best for:** People already using these services

**Pros:**
- May already have subscription
- Automatic syncing
- Large storage

**Cons:**
- Can cause sync conflicts
- Slower than Obsidian Sync
- May have file locking issues

**Setup:**

1. **Move vault to sync folder:**

   **Dropbox:**
   ```bash
   mv ~/Documents/SecondBrain ~/Dropbox/SecondBrain
   ```

   **Google Drive:**
   ```bash
   mv ~/Documents/SecondBrain ~/Google\ Drive/SecondBrain
   ```

   **OneDrive:**
   ```bash
   mv ~/Documents/SecondBrain ~/OneDrive/SecondBrain
   ```

2. **Update paths:**

   - In Obsidian: Open vault from new location
   - In VS Code: Open folder from new location

3. **Wait for sync:**

   - Let the service sync the folder completely before opening on other devices

**Warning:** Some sync services can cause conflicts with Obsidian. Obsidian Sync is the most reliable option.

---

## Troubleshooting

Common issues and how to fix them.

---

### Installation Issues

#### "git: command not found"

**Cause:** Git not installed or not in PATH

**Fix:**
- Verify Git is installed: Try the installation steps again
- Restart your terminal/VS Code
- On Windows: Re-run Git installer and ensure "Add to PATH" is checked
- On macOS/Linux: Try `which git` to see if it's installed but not in PATH

---

#### "node: command not found"

**Cause:** Node.js not installed or not in PATH

**Fix:**
- Verify Node.js is installed: Try the installation steps again
- Restart your terminal/VS Code
- On macOS: `brew install node`
- On Windows/Linux: Reinstall from nodejs.org
- Try `which node` (macOS/Linux) to verify location

---

#### "claude: command not found"

**Cause:** Claude Code not installed or not in PATH

**Fix:**
- Verify Claude Code is installed: Try the installation steps again
- Restart your terminal/VS Code
- On macOS/Linux: Check if `~/.local/bin` is in your PATH
- On Windows: Make sure you're inside WSL, not PowerShell
- Try reinstalling Claude Code

---

### Windows: WSL Setup

#### WSL not installed

**Fix:**
1. Open PowerShell as Administrator
2. Run: `wsl --install`
3. Restart your computer
4. Complete Ubuntu setup after restart
5. Install Claude Code inside WSL (not Windows)

#### Can't access files in WSL

**Fix:**
- Access Windows files from WSL: `/mnt/c/Users/YourName/Documents/`
- Access WSL files from Windows: `\\wsl$\Ubuntu\home\yourname\`

---

### Authentication Issues

#### Claude authentication fails

**Cause:** Network issue or invalid credentials

**Fix:**
- Check your internet connection
- Verify you have a Claude account at https://claude.ai
- Try logging out and back in:
  ```bash
  claude auth logout
  claude auth login
  ```
- Check account status at https://claude.ai/settings

#### "Permission denied" errors

**Cause:** File permissions or sudo required

**Fix:**
- On macOS/Linux: Try with `sudo` for system-wide installations
- Don't use `sudo` for Claude Code authentication (should be user-level)
- Check folder permissions: `ls -la`

---

### Path and Directory Issues

#### Can't find ObsidianVault folder

**Cause:** Wrong directory or folder not created

**Fix:**
1. Verify you're in the right place:
   ```bash
   pwd  # macOS/Linux
   cd   # Windows
   ```
2. Look for the folder:
   ```bash
   ls -la  # macOS/Linux
   dir     # Windows
   ```
3. Make sure `/setup` completed successfully
4. The folder name is case-sensitive: `ObsidianVault` (not `obsidianvault`)

---

### Setup Command Issues

#### `/setup` command doesn't work

**Cause:** Wrong directory or Claude not running

**Fix:**
1. Make sure you're in the `SecondBrain` folder (parent of ObsidianVault)
2. Verify `.claude` folder exists: `ls -la`
3. Make sure you ran `claude` first (not just `/setup`)
4. Try restarting VS Code

#### Setup fails midway

**Cause:** Network interruption or authentication issue

**Fix:**
- Check internet connection
- Verify Claude authentication: `claude auth status`
- Try running `/setup` again (it may resume)
- Check Claude Code logs for errors

---

### Obsidian Issues

#### Vault appears empty

**Cause:** Opened wrong folder

**Fix:**
1. In Obsidian: **Settings → General**
2. Check vault location
3. Click **"Open another vault"**
4. Navigate to correct `ObsidianVault` folder
5. Make sure you're opening `ObsidianVault`, not `SecondBrain`

#### Can't open vault

**Cause:** Folder doesn't exist or wrong path

**Fix:**
- Verify the folder exists: Navigate to it in Finder/Explorer
- Make sure `/setup` was run first
- Try creating a new vault and pointing to the folder again

---

### Network and Firewall Issues

#### Installation downloads fail

**Cause:** Firewall or network restrictions

**Fix:**
- Check internet connection
- Try disabling VPN temporarily
- Check corporate firewall settings
- Try downloading installers directly from official websites

---

### Still Stuck?

If you're still having issues after trying these troubleshooting steps:

1. **Check the documentation:**
   - Claude Code docs: https://docs.claude.com/en/docs/claude-code
   - Obsidian docs: https://help.obsidian.md

2. **Verify all prerequisites:**
   - Run `git --version`, `node --version`, `claude --version`
   - Make sure all show version numbers

3. **Start fresh:**
   - Sometimes it's easier to start over
   - Delete the `SecondBrain` folder
   - Follow the guide again from Step 4

4. **Search for specific error messages:**
   - Copy the exact error message
   - Search online for solutions
   - Many errors have been solved by others

5. **Ask for help:**
   - Create an issue on the GitHub repository
   - Include your operating system, error messages, and steps you've tried

---

## What's Next?

**Congratulations!** You've successfully set up your Second Brain system!

### Start Using Your System

Now that everything is installed, here's how to use it:

1. **Open Claude in VS Code:**
   - Open VS Code
   - Open the `SecondBrain` folder
   - Open Terminal
   - Run `claude`

2. **Capture your first thought:**
   ```
   /capture Buy milk and eggs
   ```

3. **Plan your day:**
   ```
   /daily-plan
   ```

4. **Open Obsidian:**
   - Launch Obsidian
   - Open your vault
   - See your notes appear!

### Learn the Workflow

The Second Brain has a simple daily workflow:

**Throughout the day:**
- `/capture` - Get thoughts out of your head (30 seconds each)

**Every morning (5 minutes):**
- `/daily-plan` - Choose what to work on today

**Every evening (5 minutes):**
- `/daily-closeout` - Review accomplishments and plan tomorrow

**3x per week (15 minutes):**
- `/process-inbox` - Organize captured items into projects/tasks

### Read the Documentation

For more details on how to use the system:

- **[Main README](README.md)** - Complete system overview and usage guide
- **[First Week Guide](ObsidianVault/START%20HERE%20-%20First%20Week%20Guide.md)** - Day-by-day checklist in your vault
- **[CLAUDE.md](CLAUDE.md)** - Complete system reference and methodology

### Build the Habit

**Week 1:** Use `/capture` and `/daily-plan` every day
**Week 2:** Add `/daily-closeout` in the evenings
**Week 3:** Start running `/process-inbox` 3x per week
**Week 4:** The system becomes natural!

### Customize Your System

After a week or two, you can:
- Customize templates in `ObsidianVault/Templates/`
- Add your own project areas
- Adjust the workflows to match your style
- Create your own tags and organization

**The system adapts to you, not the other way around!**

---

## Ready to Build Your Second Brain?

You've got everything set up. Now it's time to start using it!

**Next step:** Open VS Code, run `claude`, and type `/capture` to capture your first thought.

**Happy capturing!**
