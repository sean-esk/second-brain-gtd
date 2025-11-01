# Atomic Note Template

> Streamlined template for creating permanent Zettelkasten notes in Obsidian

---

## Template Structure

```markdown
---
id: {{YYYYMMDDHHmmss}}
type: permanent-note
created: {{YYYY-MM-DD}}
updated: {{YYYY-MM-DD}}
tags:
  - permanent-note
source: []
project:
aliases: []
---

# {{Title}}

**Summary:** {{One-sentence TL;DR of the idea}}

## Idea

{{Write the idea in your own words so it stands alone in the future. Be concrete. Use examples.}}

## Why It Matters

{{Explain the implications, when to use this idea, constraints, real-world applications, or why this concept is valuable.}}

## Links

### Related Concepts
- [[{{Related Note 1}}]] - How they relate
- [[{{Related Note 2}}]] - How they relate

### Broader Context
- [[{{MOC or Hub Note}}]] - (Optional) Index/topic hub

## References

- [[{{Reference or Meeting Note}}]]
- {{URL or citation if applicable}}
```

---

## Field Explanations

### Frontmatter Properties

#### `id`
- **Format:** `YYYYMMDDHHmmss` (timestamp)
- **Purpose:** Unique identifier for the note
- **Example:** `20251020143052`
- **How to generate:** Use current date-time when creating note
- **Note:** Not required in filename, kept in frontmatter only

#### `type`
- **Value:** `permanent-note`
- **Purpose:** Distinguishes from fleeting, reference, project notes
- **Required:** Yes

#### `created`
- **Format:** `YYYY-MM-DD`
- **Purpose:** Original creation date
- **Example:** `2025-10-20`
- **Required:** Yes

#### `updated`
- **Format:** `YYYY-MM-DD`
- **Purpose:** Last modification date
- **Maintenance:** Update whenever note content changes significantly
- **Required:** Yes (initialize to same as `created`)

#### `tags`
- **Format:** YAML list
- **Philosophy:** Keep minimal - prefer links over tags
- **Required tags:**
  - `permanent-note` (always include)
- **Optional tags:**
  - Business tags if relevant: `youtube`, `level-method`, `eskerium`, `polar-gold`
  - Topic tags if helpful: `productivity`, `ai-tools`, `video-production`
- **Avoid:** Over-tagging (keep to 2-3 tags max)

**Example:**
```yaml
tags:
  - permanent-note
  - youtube
  - productivity
```

#### `source`
- **Format:** YAML list of links to reference notes or URLs
- **Purpose:** Attribution to original source material
- **Examples:**
  - `["[[Reference: Getting Things Done by David Allen]]"]`
  - `["https://example.com/article"]`
  - `["[[Meeting Notes - 2025-10-15 - Team Sync]]"]`
- **Can be empty:** `[]` if original thought

#### `project`
- **Format:** Plain text (single value, not a list)
- **Purpose:** Associate with business context
- **Values:** `YouTube | Level Method | Eskerium | Polar Gold | Consulting | Personal`
- **Can be empty:** Leave blank if not project-specific
- **Alternative:** Can use tag instead (pick one approach and stay consistent)

#### `aliases`
- **Format:** YAML list
- **Purpose:** Alternative titles for link matching
- **Use when:** The concept has multiple common names
- **Example:**
  ```yaml
  aliases:
    - "GTD Method"
    - "Getting Things Done System"
  ```
- **Can be empty:** `[]` if no aliases needed

---

### Content Sections

#### Title (H1)

**Guidelines:**
- Clear and descriptive
- Captures the core concept
- Noun phrase or statement
- 3-10 words ideal

**Examples:**
- ✅ Good: "Context Switching Costs 20 Minutes of Focus Recovery"
- ✅ Good: "Time Blocking Reduces Decision Fatigue"
- ✅ Good: "Early User Feedback Prevents Post-Launch Changes"
- ❌ Too vague: "Productivity Tips"
- ❌ Too long: "How Context Switching Between Multiple Tasks Throughout The Day Significantly Impacts Your Ability To Maintain Deep Focus And Complete Complex Work"

#### Summary Line

**Purpose:** One-sentence TL;DR that captures the essence

**Format:** `**Summary:** [One complete sentence]`

**Guidelines:**
- 1 sentence maximum
- Should be understandable without reading the note
- Captures the key insight
- Can be used in Dataview tables and quick scans

**Examples:**
- "Context switching between tasks costs approximately 20-30 minutes of focus recovery time."
- "Time blocking eliminates repeated decisions about what to work on next, reducing decision fatigue."
- "Gathering user feedback before feature completion reduces expensive post-launch changes."

#### Idea Section

**Purpose:** Explain the core concept in your own words

**Guidelines:**
- **Own words required** - Never copy-paste
- **Stand-alone** - Should make sense without context
- **Concrete** - Use specific examples
- **Focused** - One core idea only
- **Length:** 50-200 words typically

**Structure suggestions:**
1. State the concept clearly
2. Explain how/why it works
3. Provide a concrete example
4. Add relevant details

**Example:**

```markdown
## Idea

When you switch between different tasks or contexts (like checking email while
working on a report), your brain needs time to fully disengage from the first
task and fully engage with the second. Research shows this "switching cost" is
approximately 20-30 minutes of reduced focus and productivity.

The effect is cumulative. If you switch contexts 10 times in a day, you're
losing 3-5 hours of productive time, not to mention the quality reduction from
never reaching deep focus.

This is why time blocking (dedicating uninterrupted time to single tasks) is
so effective - it minimizes these switching costs.
```

#### Why It Matters Section

**Purpose:** Explain the implications, applications, and value

**Guidelines:**
- **Implications** - What does this mean?
- **When to use** - Practical applications
- **Constraints** - When does this NOT apply?
- **Examples** - Real-world scenarios
- **Length:** 50-150 words typically

**Structure suggestions:**
1. Explain why this is valuable
2. Describe when/how to apply it
3. Note any limitations or constraints
4. Provide real-world examples if helpful

**Example:**

```markdown
## Why It Matters

Understanding context switching costs helps optimize your work schedule. If you're
doing deep creative work (writing, coding, design), you should minimize interruptions
and batch similar tasks together.

**Applications:**
- Block 2-4 hour chunks for deep work without interruptions
- Batch email/Slack checking to specific times (e.g., 11am and 3pm)
- Turn off notifications during focus time
- Schedule meetings back-to-back rather than scattered

**Constraints:**
- Some roles require responsiveness (customer support, emergency response)
- Not all tasks require deep focus (admin work, quick responses)
- Must be balanced with collaboration needs
```

#### Links Section

**Purpose:** Connect this note to the broader knowledge network

**Philosophy:** **No orphans!** Every permanent note should have at least 3 links

##### Subsection: Related Concepts

**What to link:**
- Notes that explore similar or related ideas
- Notes that build on this concept
- Notes that contrast with this idea
- Notes that provide complementary perspectives

**Format:**
```markdown
### Related Concepts
- [[Note Title]] - Brief explanation of relationship
- [[Another Note]] - How they connect
```

**Examples:**
```markdown
### Related Concepts
- [[Time Blocking Reduces Decision Fatigue]] - Related strategy that leverages this insight
- [[Deep Work Requires Uninterrupted Focus]] - Why minimizing switching matters
- [[Multitasking Is Sequential Task Switching]] - Explains the mechanism behind the cost
```

##### Subsection: Broader Context (Optional)

**What to link:**
- MOCs (Maps of Content) for this topic area
- Hub notes that organize related concepts
- Project notes if this idea emerged from a project

**Format:**
```markdown
### Broader Context
- [[MOC - Productivity Systems]] - Part of broader productivity knowledge
- [[Project - YouTube Video Ideas]] - (If applicable)
```

**When to skip:** If note doesn't belong to a broader organized topic area yet (can add later)

#### References Section

**Purpose:** Cite sources and provide attribution

**What to include:**
- Link to reference note if derived from book/article/video
- URL to original source material
- Meeting note if idea came from discussion
- Course or training material

**Format:**
```markdown
## References

- [[Reference: Deep Work by Cal Newport]]
- https://example.com/article-about-context-switching
- [[Meeting Notes - 2025-10-15 - Productivity Discussion]]
```

**Can be minimal or empty:**
- If original insight: Leave blank or put "Original thought"
- If fleeting note: Can reference the fleeting note or leave blank

---

## Usage Guidelines

### When to Use This Template

**Use for:**
- ✅ Atomic insights worth remembering
- ✅ Concepts that could apply to multiple contexts
- ✅ Ideas extracted from books, articles, courses
- ✅ Learnings from projects or experiences
- ✅ Frameworks or mental models

**Don't use for:**
- ❌ Project-specific documentation (use project note template)
- ❌ Procedural checklists (use workflow documentation)
- ❌ Meeting notes (use meeting note template)
- ❌ Daily journal entries (use daily note template)
- ❌ Reference material summaries (use reference note template)

### The Atomic Principle

**One idea per note. Always.**

**Test:** Can you explain this note's core concept in one sentence?
- **Yes** → Probably atomic ✅
- **No, it has multiple concepts** → Split into multiple notes ❌

**Example of non-atomic note to split:**

```markdown
# Productivity Tips  ❌ TOO BROAD

- Context switching costs time
- Time blocking helps focus
- Pomodoro technique for time management
- GTD for task management
```

**Should become 4 separate notes:**
1. "Context Switching Costs Focus Recovery Time"
2. "Time Blocking Reduces Decision Fatigue"
3. "Pomodoro Technique Uses Timed Intervals"
4. "GTD Clarifying Questions Transform Captures"

### Writing in Your Own Words

**Never copy-paste from sources into permanent notes.**

**Process:**
1. Read the source material
2. Close the source (don't look at it)
3. Write the idea as if explaining to a friend
4. Add your own examples and interpretation
5. Then add citation to reference section

**Why:** This ensures you actually understand the concept and makes it easier to remember.

### Progressive Elaboration

**Don't aim for perfection on first pass.**

**Mindset:**
- Rough is better than missing
- Notes improve over time
- Add links as connections emerge
- Refine during weekly reviews

**Evolution:**
1. **V1:** Quick capture during processing (50-100 words)
2. **V2:** Add examples and refine during review (100-200 words)
3. **V3:** Add more links as you discover connections (ongoing)
4. **V4:** Enhance with new insights from later learning (ongoing)

---

## Examples

### Example 1: Complete Permanent Note

```markdown
---
id: 20251020143500
type: permanent-note
created: 2025-10-20
updated: 2025-10-20
tags:
  - permanent-note
  - productivity
source: ["[[Reference: Deep Work by Cal Newport]]"]
project:
aliases:
  - "Task switching cost"
  - "Context switching penalty"
---

# Context Switching Costs 20 Minutes of Focus Recovery

**Summary:** Switching between tasks or contexts costs approximately 20-30 minutes of focus recovery time per switch.

## Idea

When you switch between different tasks or contexts (like checking email while working on a report), your brain needs time to fully disengage from the first task and fully engage with the second. Research by Gloria Mark at UC Irvine shows this "switching cost" is approximately 23 minutes on average.

The effect is cumulative. If you switch contexts 10 times in a day, you're losing 3-4 hours of productive time, not to mention the quality reduction from never reaching deep focus.

This happens because your brain maintains "attention residue" from the previous task. Part of your attention is still thinking about what you were doing before, which reduces your capacity for the current task.

## Why It Matters

Understanding context switching costs helps optimize your work schedule. If you're doing deep creative work (writing, coding, design, video editing), you should minimize interruptions and batch similar tasks together.

**Applications:**
- Block 2-4 hour chunks for deep work without interruptions
- Batch email/Slack checking to specific times (11am and 3pm only)
- Turn off notifications during focus time
- Schedule meetings back-to-back rather than scattered throughout the day
- Use "office hours" for reactive work instead of constant availability

**Constraints:**
- Some roles require responsiveness (customer support, emergency response)
- Not all tasks require deep focus (admin work, quick email responses)
- Must balance with collaboration and team communication needs

## Links

### Related Concepts
- [[Time Blocking Reduces Decision Fatigue]] - Strategy that leverages this insight
- [[Deep Work Requires 90-Minute Uninterrupted Blocks]] - Why long focus sessions matter
- [[Multitasking Is Sequential Task Switching]] - Explains the mechanism
- [[Notification Fragmentation Prevents Flow State]] - Related interruption source

### Broader Context
- [[MOC - Productivity and Focus Systems]]

## References

- [[Reference: Deep Work by Cal Newport]]
- Study: Gloria Mark, UC Irvine - "The Cost of Interrupted Work"
```

### Example 2: Minimal Permanent Note (Still Valid)

```markdown
---
id: 20251020145000
type: permanent-note
created: 2025-10-20
updated: 2025-10-20
tags:
  - permanent-note
  - video-production
source: []
project: YouTube
aliases: []
---

# B-Roll Covers Jump Cuts in Video Editing

**Summary:** Overlaying B-roll footage over jump cuts creates smooth transitions and maintains visual continuity.

## Idea

When editing video, you often need to cut out dead air, mistakes, or filler words. These cuts create jarring "jump cuts" where the subject suddenly shifts position.

B-roll (secondary footage showing what you're talking about) can be overlaid during these cuts. The viewer sees the B-roll instead of the jump, creating a smooth transition while adding visual interest.

## Why It Matters

This is a fundamental video editing technique that:
- Makes rough edits feel professional
- Adds visual variety to talking-head footage
- Provides context for what's being discussed
- Keeps viewer attention through visual change

Standard practice for YouTube, documentaries, and tutorials.

## Links

### Related Concepts
- [[Visual Variety Maintains Viewer Attention]] - Why this technique works psychologically
- [[Shoot 3x B-Roll as Scripted Duration]] - Planning for adequate coverage

### Broader Context
- [[MOC - Video Production Techniques]]

## References

Original insight from video editing practice
```

---

## Template Variations by Business Context

### For YouTube Content Creation

```yaml
tags:
  - permanent-note
  - youtube
  - content-strategy
project: YouTube
```

### For Business Strategy (Level Method, Eskerium, etc.)

```yaml
tags:
  - permanent-note
  - business-strategy
project: Level Method
```

### For Technical/Development Notes

```yaml
tags:
  - permanent-note
  - development
  - technical
project:
```

---

## Common Mistakes

### Mistake 1: Too Much Detail
**Problem:** Note becomes 800+ words with multiple concepts
**Solution:** Split into multiple atomic notes

### Mistake 2: Copy-Pasting Content
**Problem:** Note is just quotes from source
**Solution:** Read → Close → Write in your own words

### Mistake 3: No Links
**Problem:** Orphan note with zero connections
**Solution:** Force yourself to add 3+ links before considering note complete

### Mistake 4: Vague Title
**Problem:** "Productivity Note #5"
**Solution:** Specific, descriptive title that captures the core idea

### Mistake 5: No Summary
**Problem:** Can't scan notes quickly
**Solution:** Always include one-sentence summary at top

---

## Related Templates

- **Reference Note Template:** For source summaries (books, articles, videos)
- **Project Note Template:** For active projects with deadlines
- **Fleeting Note Template:** For quick temporary captures
- **Meeting Note Template:** For meetings and discussions

---

## Obsidian-Specific Features

### Dataview Integration

Permanent notes can be queried with Dataview:

```dataview
TABLE summary as Summary, created, tags
FROM "Permanent Notes"
WHERE type = "permanent-note"
SORT created DESC
LIMIT 10
```

### Bases Integration

Permanent notes work well in Bases dashboards:

```yaml
views:
  Recent Permanent Notes:
    filters:
      and:
        - file.inFolder("Permanent Notes")
        - 'type == "permanent-note"'
    sorts:
      - field: created
        order: desc
```

### Graph View

Atomic notes with good linking create a rich graph visualization showing knowledge clusters.

---

**Remember:** The template is a guide, not a prison. Adapt as needed, but always preserve the atomic principle and quality linking.

---

**Tags:** #template #zettelkasten #permanent-note #atomic-note
