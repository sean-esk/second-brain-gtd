# Configuration

The Second Brain skill stores its configuration in **Claude's Memory feature**, which persists across all sessions automatically.

## How Configuration Works

### Primary: Claude Memory (Recommended)

Claude Memory stores your configuration and persists it across all sessions. This works in:
- Claude Desktop (including sandboxed skills)
- Claude Code
- Any Claude interface with Memory enabled

**What gets stored in Memory:**
- Second Brain vault path
- User name
- Setup completion status
- User preferences (proactive capture, inbox threshold)

### Setup

Just ask Claude: **"Set up my Second Brain"** and it will:
1. Ask for your Obsidian vault path
2. Guide you through configuration
3. Save everything to Memory automatically

That's it! Claude will remember your configuration in all future sessions.

---

## Legacy: Config File (Claude Code Only)

**For Claude Code users:** A config file at `~/.second-brain/config.json` can be used as a fallback if Memory is empty.

**Important:** This does NOT work in Claude Desktop because skills run in a sandboxed environment without file system access.

### Creating the Config File (Optional)

```bash
mkdir -p ~/.second-brain
cp config-template.json ~/.second-brain/config.json
```

Then edit `~/.second-brain/config.json` with your vault path.

### Config File Format

```json
{
  "vaultPath": "/absolute/path/to/vault",
  "setupComplete": true,
  "userName": "Your Name",
  "userContext": "Permanent Notes/Assisting-User-Context.md",
  "preferences": {
    "defaultCaptureType": "inbox",
    "proactiveCapture": true,
    "inboxThreshold": 5
  }
}
```

### Fields

| Field | Description |
|-------|-------------|
| `vaultPath` | **Required.** Absolute path to your Obsidian vault |
| `setupComplete` | Whether initial setup has been completed |
| `userName` | Your name (used for personalization) |
| `userContext` | Path within vault to your context file |
| `preferences.defaultCaptureType` | Where to capture by default ("inbox") |
| `preferences.proactiveCapture` | Enable proactive capture suggestions |
| `preferences.inboxThreshold` | Items in inbox before prompting to process |

---

## Environment Variable Override

You can override the vault path with an environment variable (useful for testing):

```bash
export SECOND_BRAIN_VAULT_PATH="/path/to/your/obsidian/vault"
```

Add to your shell profile (`~/.bashrc`, `~/.zshrc`, etc.) for persistence.

**Priority order:**
1. Environment variable (if set)
2. Claude Memory
3. Config file (Claude Code only)

---

## Vault Requirements

Your Obsidian vault should have this structure (created during setup):

```
YourVault/
├── 00-Inbox/
│   ├── Daily/
│   └── Fleeting-Notes/
├── 01-Projects/
├── 02-Areas/
│   └── Relationships/
├── 03-Resources/
│   └── Reference-Notes/
├── 04-Archives/
├── Daily Plans/
├── Meeting Notes/
├── Permanent Notes/
└── Templates/
```

If these folders don't exist, the setup workflow will create them.

---

## Troubleshooting

### Claude doesn't remember my vault path

1. Make sure you completed the full setup ("set up my second brain")
2. Check Claude Memory: Settings > Capabilities > View and edit memory
3. Look for "Second Brain vault path" entry
4. If missing, run setup again

### Memory not available

If Claude Memory isn't available in your region yet:
- Use Claude Code with the config file fallback
- Or set the environment variable

### Changing vault location

Tell Claude: "My Second Brain vault moved to /new/path/here" and it will update Memory.
