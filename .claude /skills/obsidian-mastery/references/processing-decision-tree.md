# Processing Decision Tree

> Quick guide for choosing the right command when you have unprocessed content

---

## The Two Processing Systems

**GTD Processing** (`/process-inbox`) = For DOING (execution, task management)
**Zettelkasten Processing** (`/process-raw-notes`) = For THINKING (knowledge management)

**They complement each other. Often you'll use both on the same content.**

---

## Decision Tree

### Question 1: What type of content do you have?

```
┌─────────────────────────────────────────┐
│   What's in your unprocessed content?   │
└─────────────────────────────────────────┘
                    │
        ┌───────────┴───────────┐
        │                       │
        ▼                       ▼
   ACTIONABLE?            KNOWLEDGE?
   (Tasks, todos,      (Ideas, insights,
    projects)           research, learnings)
        │                       │
        ▼                       ▼
  /process-inbox        /process-raw-notes
   (GTD workflow)      (Zettelkasten workflow)
```

---

## Detailed Decision Path

### Path A: Actionable Content

**Use `/process-inbox`** when content is:

✅ **Tasks to do:**
- "Need to call John about proposal"
- "Schedule meeting with team"
- "Review client website"

✅ **Projects to start:**
- "Launch new product line"
- "Create YouTube video series"
- "Redesign website"

✅ **Mixed with actions:**
- Brain dump that includes "need to..." or "must..."
- Meeting notes with action items
- Ideas that require follow-up work

**Command applies GTD clarifying questions:**
1. What is it?
2. Is it actionable?
3. What's the desired outcome?
4. What's the next physical action?
5. Where does it belong?

**Creates:**
- Projects in `01-Projects/`
- Tasks added to project notes
- Areas in `02-Areas/`
- Reference material in `03-Resources/` (if not actionable)

---

### Path B: Knowledge Content

**Use `/process-raw-notes`** when content is:

✅ **Research findings:**
- "I learned that AI agents need feedback loops"
- Article highlights or notes
- Book notes or highlights

✅ **Insights and ideas:**
- "Interesting observation about productivity..."
- Concepts to remember
- Frameworks or mental models

✅ **Source material:**
- Imported Kindle highlights
- Web clippings
- Course notes

**Command extracts atomic knowledge:**
1. Reads content
2. Identifies distinct atomic ideas
3. Checks for duplicates
4. Creates permanent notes with template
5. Creates reference notes for sources
6. Links everything together
7. Links to MOCs

**Creates:**
- Permanent notes in `Permanent Notes/` or `03-Resources/`
- Reference notes for sources
- Links to related knowledge
- Connections to MOCs

---

### Path C: Mixed Content

**Use BOTH commands in sequence:**

**Step 1:** Run `/process-inbox` FIRST
- Extracts actionable items
- Creates projects and tasks
- Removes action-oriented content

**Step 2:** Run `/process-raw-notes` on what remains
- Extracts knowledge and insights
- Creates permanent notes
- Links to knowledge network

**Example:**

**Input:** Brain dump containing:
- "Need to call John about proposal"
- "Had idea for video about Second Brain"
- "Learned that context switching costs 20 minutes of focus recovery"

**Process:**
1. `/process-inbox`:
   - Extracts task: "Call John about proposal"
   - Suggests `/video-idea` for video concept
2. `/process-raw-notes`:
   - Creates permanent note: "Context Switching Costs Focus Recovery"
   - Links to [[MOC - Productivity Systems]]

---

## Quick Reference Guide

### When to Use Each Command

| Content Type | Command | Output |
|--------------|---------|--------|
| Tasks only | `/process-inbox` | Projects, tasks |
| Ideas only | `/process-raw-notes` | Permanent notes |
| Tasks + Ideas | Both (inbox first) | Projects + Permanent notes |
| Single quick thought | `/capture` (quick mode) | Quick note in inbox |
| Video concept | `/video-idea` | Structured video idea |
| Stream of consciousness | `/capture` (brain dump mode) | Archived + routed |
| Meeting notes | `/process-inbox` | Tasks + decisions |
| Book highlights | `/process-raw-notes` | Permanent + reference notes |
| Research session | `/process-raw-notes` | Permanent + reference notes |

---

## Common Scenarios

### Scenario 1: Brain Dump with Mixed Content

**Content:**
```
Need to schedule Level Method team call. Had idea for video about Second
Brain setup. John mentioned API launches next week. Interesting insight
about async communication requiring decision logs. Must review proposal
by Friday.
```

**Analysis:**
- 2 tasks ("schedule call", "review proposal")
- 1 video idea
- 1 reference info ("API launches")
- 1 knowledge insight ("async communication needs decision logs")

**Processing:**
1. `/capture [content]` - Archives raw input
2. `/process-inbox` - Extracts:
   - Task: Schedule Level Method call
   - Task: Review proposal by Friday
   - Reference: Note about API launch
3. `/video-idea` - For structured video capture
4. `/process-raw-notes` on insight:
   - Permanent note: "Async Communication Requires Decision Logs"

**Result:**
- 2 tasks added to projects
- 1 video idea structured
- 1 reference note created
- 1 permanent note created
- Brain dump archived

---

### Scenario 2: Book Highlights (Pure Knowledge)

**Content:** 50 highlights from "Deep Work" by Cal Newport

**Analysis:**
- Pure knowledge, no actions
- External source with attribution
- Multiple related ideas to extract

**Processing:**
1. Skip `/process-inbox` (no actions)
2. `/process-raw-notes` only:
   - Groups highlights by theme
   - Creates 5-8 permanent notes
   - Creates "Reference: Deep Work by Cal Newport"
   - Links permanent notes to reference
   - Links all to [[MOC - Productivity Systems]]

**Result:**
- 5-8 permanent notes created
- 1 reference note
- All linked together and to MOC

---

### Scenario 3: Project Brainstorm (Pure Actions)

**Content:**
```
Project ideas for Q4:
1. Website redesign for client
2. Internal tool for Level Method
3. YouTube series on AI agents
```

**Analysis:**
- All actionable projects
- No knowledge to extract (just project ideas)

**Processing:**
1. `/process-inbox` only:
   - Creates 3 project notes
   - Assigns to appropriate businesses
   - Defines initial next actions
2. Skip `/process-raw-notes` (no atomic knowledge to extract)

**Result:**
- 3 projects in `01-Projects/`
- Each with next action defined

---

### Scenario 4: Research Session Results

**Content:**
```
Researched AI agents today. Found that:
- Feedback loops are essential for autonomous agents
- Multi-agent coordination is complex
- Need to build prototype to test these concepts
```

**Analysis:**
- 2 knowledge insights
- 1 action item ("build prototype")

**Processing:**
1. `/process-raw-notes`:
   - Permanent note: "AI Agents Require Feedback Loops"
   - Permanent note: "Multi-Agent Coordination Complexity"
   - Links to [[MOC - AI Technology]]
2. `/process-inbox`:
   - Project: "AI Agent Prototype"
   - Links to the permanent notes created

**Result:**
- 2 permanent notes (knowledge)
- 1 project (execution)
- Project links to knowledge for context

---

### Scenario 5: Meeting Notes

**Content:** Meeting notes with discussion, decisions, and action items

**Analysis:**
- Action items to extract
- Decisions to document
- Possibly insights to capture as knowledge

**Processing:**
1. `/process-inbox`:
   - Extracts action items as tasks
   - Documents decisions in project notes
2. `/process-raw-notes` (if valuable insights):
   - Extracts learnings as permanent notes
   - Links to meeting note as source

**Result:**
- Tasks added to projects
- Decisions documented
- Insights captured as permanent notes
- Meeting note becomes reference

---

## Workflow Flowchart

```
┌──────────────────────────────────┐
│     Content in Inbox             │
│  (brain dump, notes, imports)    │
└────────────┬─────────────────────┘
             │
             ▼
┌──────────────────────────────────┐
│   Analyze Content Type           │
│   - Actions?                     │
│   - Knowledge?                   │
│   - Both?                        │
└────────────┬─────────────────────┘
             │
      ───────┴────────
     │                │
     ▼                ▼
┌─────────┐     ┌──────────────┐
│ Actions │     │  Knowledge   │
└────┬────┘     └──────┬───────┘
     │                 │
     ▼                 ▼
┌─────────────────────────────────┐
│   /process-inbox                │
│   (GTD clarification)           │
│                                 │
│   Asks:                         │
│   - Is it actionable?           │
│   - What's the outcome?         │
│   - Next physical action?       │
│                                 │
│   Creates:                      │
│   - Projects                    │
│   - Tasks                       │
│   - Areas                       │
└─────────────────────────────────┘

┌─────────────────────────────────┐
│   /process-raw-notes            │
│   (Zettelkasten extraction)     │
│                                 │
│   Extracts:                     │
│   - Atomic ideas                │
│   - Insights                    │
│   - Learnings                   │
│                                 │
│   Creates:                      │
│   - Permanent notes             │
│   - Reference notes             │
│   - Links to MOCs               │
└─────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│   Result: Organized System      │
│   - Projects for execution      │
│   - Knowledge for reference     │
│   - All properly linked         │
└─────────────────────────────────┘
```

---

## Special Cases

### Case 1: Fleeting Note (Single Quick Thought)

**Content:** Single sentence or paragraph

**Processing:**
- If actionable → `/capture` (quick mode) or `/process-inbox`
- If knowledge → Keep as fleeting note, process in batch later with `/process-raw-notes`
- Don't overthink single thoughts

---

### Case 2: Video Idea

**Content:** Concept for YouTube video

**Processing:**
- Use `/video-idea` specifically (not `/process-inbox` or `/process-raw-notes`)
- Has specialized RICE scoring and structure

---

### Case 3: Conversation or Discussion

**Content:** Notes from conversation with someone

**Processing:**
1. `/process-inbox` for action items and decisions
2. `/process-raw-notes` for insights shared
3. Meeting note becomes reference material

---

### Case 4: Daily Note with Captures

**Content:** Daily journal with mixed thoughts

**Processing:**
- Scan daily note for action items → `/process-inbox`
- Scan for insights/learnings → `/process-raw-notes`
- Keep daily note as-is (historical log)

---

## Command Capabilities Comparison

### `/process-inbox` (GTD)

**Primary Question:** "What do I need to DO about this?"

**Analyzes for:**
- Actionability
- Next actions
- Project vs task
- Urgency and priority

**Creates:**
- Project notes with GTD frontmatter
- Task checkboxes in projects
- Area notes
- Reference material (if not actionable)

**Frontmatter applied:**
```yaml
status: [inbox|next|active|waiting|...]
next-action: "Specific action"
priority: [high|medium|low]
context: [office|computer|phone|...]
energy: [high|medium|low]
time-needed: [5m|15m|30m|...]
```

---

### `/process-raw-notes` (Zettelkasten)

**Primary Question:** "What knowledge should I CAPTURE from this?"

**Analyzes for:**
- Atomic ideas
- Distinct concepts
- Source attribution
- Topic clustering

**Creates:**
- Permanent notes with Zettelkasten frontmatter
- Reference notes for sources
- Links between knowledge
- Connections to MOCs

**Frontmatter applied:**
```yaml
id: YYYYMMDDHHmmss
type: permanent-note
source: ["[[Reference]]"]
aliases: []
related: ["[[Note]]"]
```

---

## When Commands Overlap

**Both commands can:**
- Read inbox folders
- Create reference material
- Generate processing reports

**Key difference:**
- `/process-inbox` asks "Is it actionable?" (GTD mindset)
- `/process-raw-notes` asks "What ideas are here?" (Knowledge mindset)

**They're complementary, not competing.**

---

## Best Practices

### 1. Start with `/capture` (brain dump mode)

**For stream-of-consciousness captures:**
1. Use `/capture` (brain dump mode) to archive raw input
2. Then decide which processing command(s) to use

### 2. Batch Process Similar Content

**For efficiency:**
- Process all tasks together with `/process-inbox`
- Process all knowledge together with `/process-raw-notes`
- Don't switch between commands repeatedly

### 3. Weekly Inbox Zero

**During weekly review:**
1. Run `/process-inbox` on action-oriented items
2. Run `/process-raw-notes` on knowledge items
3. Use `/video-idea` for video concepts
4. Archive processed sources

### 4. Separate Concerns

**GTD for execution:**
- Projects, tasks, areas
- Status tracking
- Next actions
- Context and energy matching

**Zettelkasten for learning:**
- Permanent notes
- Knowledge connections
- MOC organization
- Progressive elaboration

**Link them together:**
- Projects link to relevant permanent notes (resources)
- Permanent notes link to projects where applied (applications)

---

## Still Confused?

**Ask yourself:**

**"Do I need to DO something about this?"**
- **Yes** → `/process-inbox`
- **No** → Continue...

**"Do I want to REMEMBER something from this?"**
- **Yes** → `/process-raw-notes`
- **No** → Maybe just reference material or can be deleted

**"Is it a YouTube video idea?"**
- **Yes** → `/video-idea`

**"Is it just a quick single thought?"**
- **Yes** → `/capture` (quick mode)

**"Is it a messy stream of consciousness?"**
- **Yes** → `/capture` (brain dump mode) (then process later)

---

## Examples by Content Type

| Content Source | Primary Command | Secondary Command | Reasoning |
|----------------|-----------------|-------------------|-----------|
| Brain dump | `/capture` (brain dump mode) | Then `/process-inbox` + `/process-raw-notes` | Archive first, then separate actions from knowledge |
| Book highlights | `/process-raw-notes` | None | Pure knowledge extraction |
| Meeting notes | `/process-inbox` | `/process-raw-notes` if insights | Extract actions first, then learnings |
| Research session | `/process-raw-notes` | `/process-inbox` if follow-ups | Knowledge first, actions second |
| Task list | `/process-inbox` | None | Pure execution |
| Article summary | `/process-raw-notes` | None | Pure knowledge |
| Video idea | `/video-idea` | None | Specialized structure |
| Project ideas | `/process-inbox` | None | Creating projects |
| Daily note review | `/process-inbox` | `/process-raw-notes` | Scan for both actions and insights |
| Fleeting notes | `/process-raw-notes` | None | Convert to permanent notes |

---

## Integration with Broader Workflow

```
CAPTURE (Low Friction)
    ↓
/capture or /capture
    ↓
PROCESS (Transform)
    ↓
    ├─→ /process-inbox (for actions) → Projects, Tasks
    │
    └─→ /process-raw-notes (for knowledge) → Permanent Notes
            ↓
            └─→ Links to MOCs automatically
    ↓
REFINE (Improve Quality)
    ↓
/refine-notes (quarterly on permanent notes)
    ↓
REVIEW (Maintain)
    ↓
    ├─→ /daily-plan (daily execution)
    └─→ /weekly-review (weekly maintenance)
    ↓
EXECUTE (Get Work Done)
    ↓
GTD Dashboard, what-next command
```

---

**Remember:** When in doubt, you can run both commands on the same content. They serve different purposes and won't conflict.

---

**Last Updated:** 2025-10-20
**Version:** 1.0
