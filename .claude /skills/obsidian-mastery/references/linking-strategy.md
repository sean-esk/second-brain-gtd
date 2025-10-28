# Linking Strategy

> Comprehensive guide for creating meaningful connections between notes in the GTD + Second Brain system

---

## Philosophy

**"Links are the backbone of your Second Brain."**

- **Tags** categorize (WHAT type of thing is this?)
- **Folders** organize (WHERE does this go?)
- **Links** connect (HOW does this relate to other things?)

**Key Principles:**
1. **Link liberally** - More connections = more insights
2. **Explain relationships** - Don't just link, explain HOW they relate
3. **Bidirectional linking** - Related notes should link to each other
4. **No orphans** - Every permanent note needs 3+ links
5. **Progressive linking** - Add more links as connections emerge

---

## Link Types & Purposes

### 1. Hierarchical Links (Parent-Child)

**Purpose:** Show containment or ownership relationships

**Patterns:**

**Project → Tasks:**
```markdown
# Project Note
## Tasks
- [[Task - Draft proposal]]
- [[Task - Review with client]]
```

**Area → Projects:**
```markdown
# Area Note (YouTube Channel)
## Active Projects
- [[Project - Video Series on Second Brain]]
- [[Project - Channel Rebrand 2025]]
```

**MOC → Permanent Notes:**
```markdown
# MOC - Productivity Systems

## Core Concepts
- [[Time Blocking Reduces Decision Fatigue]]
- [[Context Switching Costs Focus Recovery]]
```

**Usage:**
- Establishes clear hierarchy
- Enables navigation up and down
- Shows scope and relationships

---

### 2. Associative Links (Related Concepts)

**Purpose:** Connect ideas that relate to each other

**Patterns:**

**Similar Concepts:**
```markdown
## Links

### Related Concepts
- [[Time Blocking Reduces Decision Fatigue]] - Related strategy: Both minimize mental overhead
- [[Deep Work Requires Uninterrupted Blocks]] - Explains why minimizing context switching matters
```

**Contrasting Views:**
```markdown
### Contrasts With
- [[Multitasking Increases Efficiency]] - Opposite view: Research shows this is false; context switching has costs
```

**Builds On:**
```markdown
### Builds On
- [[Attention Has Limited Capacity]] - Foundational concept this builds from
```

**Usage:**
- Creates knowledge network
- Enables serendipitous discovery
- Shows conceptual relationships

---

### 3. Source Links (Attribution)

**Purpose:** Connect knowledge notes to their sources

**Patterns:**

**Permanent Note → Reference Note:**
```markdown
## References
- [[Reference: Deep Work by Cal Newport]]
- [[Meeting Notes - 2025-10-15 - Productivity Discussion]]
```

**Reference Note → Permanent Notes:**
```markdown
## Permanent Notes Extracted
- [[Context Switching Costs Focus Recovery]]
- [[Deep Work Requires 90-Minute Blocks]]
- [[Shallow Work Should Be Batched]]
```

**Usage:**
- Maintains attribution
- Enables tracing ideas back to source
- Shows which sources are most valuable

---

### 4. Project Links (Work Context)

**Purpose:** Connect working documents to knowledge and resources

**Patterns:**

**Project → Permanent Notes (Resources):**
```markdown
# Project Note

## Resources & Context

### Key Concepts
- [[Time Blocking Reduces Decision Fatigue]] - Applying this to project scheduling
- [[Early User Feedback Reduces Post-Launch Changes]] - Strategy for beta testing
```

**Permanent Note → Projects (Application):**
```markdown
## Applications

**Used in:**
- [[Project - Client Website Redesign]] - Applied to planning workflow
- [[Area - YouTube Channel]] - Guides content scheduling
```

**Usage:**
- Links theory to practice
- Shows where knowledge is applied
- Enables learning from doing

---

### 5. MOC Links (Navigation)

**Purpose:** Connect notes to Maps of Content for discovery

**Patterns:**

**Permanent Note → MOC:**
```markdown
## Links

### Broader Context
- [[MOC - Productivity Systems]]
- [[MOC - AI Technology]]
```

**MOC → Notes:**
```markdown
# MOC - Productivity Systems

## Core Concepts
- [[Time Blocking Reduces Decision Fatigue]]
- [[Context Switching Costs Focus Recovery]]
- [[Deep Work Requires Uninterrupted Blocks]]

## Applications
- [[Project Planning Workflow]]
- [[Daily Execution Framework]]
```

**MOC → MOC:**
```markdown
# MOC - Productivity Systems

## Related Maps
- [[MOC - Time Management]] - Overlaps with scheduling concepts
- [[MOC - ADHD Strategies]] - Applications for neurodivergent productivity
```

**Usage:**
- Provides navigation hubs
- Organizes knowledge by domain
- Enables topic exploration

---

## Linking Standards

### Standard 1: No Orphan Permanent Notes

**Rule:** Every permanent note must have at least 3 links

**Link count breakdown:**
- 1-2 links to related concepts
- 1 link to MOC (broader context)
- 1 link to source (reference note or URL)
- Optional: Links to projects where applied

**Minimum viable:**
```markdown
## Links

### Related Concepts
- [[Related Note 1]]
- [[Related Note 2]]

### Broader Context
- [[MOC - Topic]]

## References
- [[Reference: Source]]
```

**Exception:** Brand new topic areas may start with fewer links temporarily, but add more during reviews.

---

### Standard 2: Explain Relationships

**Don't just link - explain HOW they relate**

**❌ Bad (no explanation):**
```markdown
## Links
- [[Time Blocking]]
- [[Deep Work]]
- [[Productivity]]
```

**✅ Good (relationship explained):**
```markdown
## Links

### Related Concepts
- [[Time Blocking Reduces Decision Fatigue]] - Complementary strategy: Time blocking reduces context switching opportunities
- [[Deep Work Requires Uninterrupted Blocks]] - Explains why minimizing context switching enables deep work
- [[MOC - Productivity Systems]] - Part of broader productivity knowledge
```

**Why:** Explanations make connections explicit and useful

---

### Standard 3: Bidirectional Linking

**When creating strong relationships, link both directions**

**Example:**

**Note A: "Context Switching Costs Focus Recovery"**
```markdown
## Links
- [[Time Blocking Reduces Decision Fatigue]] - Complementary strategy
```

**Note B: "Time Blocking Reduces Decision Fatigue"**
```markdown
## Links
- [[Context Switching Costs Focus Recovery]] - Problem this strategy solves
```

**When to use:**
- Strong conceptual relationships
- Builds-on / Built-by relationships
- Complementary strategies
- Problem-solution pairs

**When NOT to use:**
- Weak or tangential connections
- Every single link (too much maintenance)
- MOC links (MOCs link to many notes, notes link back to MOC)

---

### Standard 4: Link Placement

**Where to put links in different note types:**

**Permanent Notes:**
- In "## Links" section
- Organized by relationship type (Related Concepts, Broader Context, Contrasts With)

**Project Notes:**
- In "Resources & Context" section
- In "Related Projects" section

**Reference Notes:**
- In "Related" section
- In "Permanent Notes Extracted" section

**MOCs:**
- Throughout the body (organized by category)
- In "Related MOCs" section

---

## Linking Workflows

### Workflow 1: Creating a New Permanent Note

**When creating permanent note:**

1. **Before finishing the note, search for related notes:**
   - Use Grep to search keywords
   - Search for related concepts
   - Check relevant MOCs

2. **Add minimum 3 links:**
   - 1-2 related concept links
   - 1 MOC link (broader context)
   - 1 source link (if applicable)

3. **Explain each relationship:**
   - Don't just list links
   - Add brief "how they relate" text

4. **Optional: Add backlinks:**
   - For strong relationships, add link in related note back to this one

**Example process:**
```
Creating note: "Context Switching Costs Focus Recovery"

1. Search for related:
   - Grep "productivity", "focus", "context"
   - Find: [[Time Blocking]], [[Deep Work]], [[Multitasking]]
   - Check: [[MOC - Productivity Systems]]

2. Add links with explanations:
   - [[Time Blocking]] - Strategy that minimizes context switching
   - [[Deep Work Requires Uninterrupted Blocks]] - Explains why
   - [[MOC - Productivity Systems]] - Topic hub

3. Consider backlinks:
   - Update [[Time Blocking]] to mention context switching cost
```

---

### Workflow 2: Processing Raw Notes

**When running `/process-raw-notes`:**

**For each permanent note created:**

1. **Search phase:**
   - Use Grep to find notes with similar keywords
   - Search for existing MOCs on the topic
   - Check if source reference note exists

2. **Link creation:**
   - Add links to related permanent notes found
   - Add link to MOC
   - Create or link to source reference note

3. **Suggest additional connections:**
   - "Found 5 related notes on productivity. Should I link them?"
   - "Create [[MOC - Productivity Systems]] to organize these?"

---

### Workflow 3: Refining Notes

**When running `/refine-notes`:**

**Quality check includes:**

1. **Link count:**
   - Count outbound links
   - Flag notes with < 3 links

2. **Link quality:**
   - Are relationships explained?
   - Are links meaningful (not forced)?
   - Any MOC connections?

3. **Suggest additions:**
   - Search for related notes not yet linked
   - Suggest MOC connections
   - Identify topic clusters needing MOCs

---

### Workflow 4: Updating MOCs

**When running `/update-moc`:**

1. **Scan vault:**
   - Find all permanent notes related to MOC topic
   - Identify notes not yet in MOC

2. **Suggest additions:**
   - "Found 3 new productivity notes not in [[MOC - Productivity Systems]]"
   - Present list for approval

3. **Add to MOC:**
   - Add links in appropriate section
   - Update note count
   - Update last review date

---

## Link Discovery Strategies

### Strategy 1: Keyword Search

**Use Grep to search for related keywords:**

```
When creating note about "context switching":
1. Grep search: "context", "switching", "focus", "productivity"
2. Review results
3. Identify relevant notes
4. Add links with explanations
```

**Multiple keyword searches:**
- Core concept keywords
- Related concept keywords
- Problem keywords (if solution note)
- Solution keywords (if problem note)

---

### Strategy 2: MOC Browsing

**Check relevant MOCs for related notes:**

```
Creating productivity note:
1. Open [[MOC - Productivity Systems]]
2. Browse sections for related concepts
3. Identify 2-3 to link
4. Add links with relationship explanations
```

---

### Strategy 3: Recent Notes Review

**Check recently created notes:**

```
1. Query last 20 permanent notes created
2. Scan titles for related topics
3. Read 2-3 that seem related
4. Link if connection found
```

**Dataview query for recent notes:**
```dataview
TABLE created
FROM "Permanent Notes" OR "03-Resources"
WHERE type = "permanent-note"
SORT created DESC
LIMIT 20
```

---

### Strategy 4: Backlink Analysis

**Use Obsidian's backlinks pane:**

```
When viewing a note:
1. Check "Linked Mentions" pane
2. See what notes already link here
3. Consider if bidirectional link makes sense
4. Add link back if strong relationship
```

---

### Strategy 5: Graph View Exploration

**Use Obsidian's graph view:**

```
1. Open graph view
2. Select a note
3. See what's nearby (connected notes)
4. Identify clusters
5. Consider if connections should exist
```

**Useful for:**
- Finding knowledge gaps
- Identifying disconnected clusters
- Seeing topic relationships visually

---

## Linking Between System Types

### GTD ↔ Zettelkasten Links

**Projects → Permanent Notes:**

**Purpose:** Link to knowledge that supports execution

```markdown
# Project Note: Client Website Redesign

## Resources & Context

### Key Concepts to Apply
- [[User Research Prevents Waste]] - Doing user interviews before design
- [[Mobile-First Reduces Desktop Complexity]] - Designing mobile-first approach
- [[Early Feedback Reduces Post-Launch Changes]] - Beta testing strategy
```

**Why link:**
- Brings relevant knowledge to execution context
- Shows where theory applies to practice
- Enables learning while doing

---

**Permanent Notes → Projects:**

**Purpose:** Show where knowledge was applied or tested

```markdown
# Permanent Note: Early Feedback Reduces Post-Launch Changes

## Applications

**Applied in:**
- [[Project - Client Website Redesign]] - Used beta testing approach
- [[Project - Product Launch 2025]] - Implemented user feedback loops
```

**Why link:**
- Shows real-world application
- Validates knowledge with experience
- Enables retrieval when working on similar projects

---

**Areas → Permanent Notes:**

**Purpose:** Link to ongoing knowledge relevant to area

```markdown
# Area Note: YouTube Channel

## Knowledge Resources
- [[Hook in First 3 Seconds Increases Retention]]
- [[B-Roll Covers Jump Cuts]]
- [[Thumbnail CTR Matters More Than View Count]]
```

---

### GTD ↔ GTD Links

**Projects → Projects:**

**Purpose:** Show dependencies or relationships

```markdown
# Project A

## Related Projects
- [[Project B]] - Dependency: Waiting on API from this project
- [[Project C]] - Collaboration: Sharing resources with this team
```

**Projects → Areas:**

**Purpose:** Show which area project belongs to

```markdown
# Project Note

**Belongs to:** [[Area - YouTube Channel]]
```

---

### Zettelkasten ↔ Zettelkasten Links

**Permanent Notes → Permanent Notes:**

**Purpose:** Build knowledge network

```markdown
## Links

### Related Concepts
- [[Time Blocking Reduces Decision Fatigue]] - Complementary productivity strategy
- [[Deep Work Requires Uninterrupted Blocks]] - Explains the mechanism
- [[Multitasking Is Sequential Task Switching]] - Related: Same underlying problem

### Contrasts With
- [[Reactive Work Requires Availability]] - Tension: Some work needs responsiveness

### Builds On
- [[Attention Has Limited Capacity]] - Foundational concept
```

**Permanent Notes → Reference Notes:**

**Purpose:** Source attribution

```markdown
## References
- [[Reference: Deep Work by Cal Newport]]
- From conversation: [[Meeting Notes - 2025-10-15]]
```

**MOCs → Permanent Notes:**

**Purpose:** Organize knowledge domain

```markdown
# MOC - Productivity Systems

## Focus & Attention
- [[Context Switching Costs Focus Recovery]]
- [[Deep Work Requires Uninterrupted Blocks]]
- [[Flow State Requires 15-Minute Warm-Up]]

## Time Management
- [[Time Blocking Reduces Decision Fatigue]]
- [[Energy Levels Vary Throughout Day]]
```

---

## Link Placement Guidelines

### In Permanent Notes

**Required sections:**

```markdown
## Links

### Related Concepts
- [[Note 1]] - Relationship explanation
- [[Note 2]] - Relationship explanation

### Broader Context
- [[MOC - Topic]]

## References
- [[Source Note or URL]]
```

**Optional sections:**

```markdown
### Contrasts With
- [[Opposing View]] - Key difference

### Builds On
- [[Prerequisite Concept]]

### Applications
- [[Project where applied]]
```

---

### In Project Notes

**Recommended sections:**

```markdown
## Resources & Context

### Key Concepts
- [[Permanent Note 1]] - How it applies to this project
- [[Permanent Note 2]] - Relevant knowledge

### Reference Material
- [[Reference Note]]
- External URL

## Related Projects
- [[Other Project]] - How they relate
```

---

### In Reference Notes

**Required sections:**

```markdown
## Permanent Notes Extracted
- [[Permanent Note 1]]
- [[Permanent Note 2]]

## Related References
- [[Reference: Related Book]]
- [[Reference: Related Article]]
```

---

### In MOCs

**Structure:**

```markdown
## [Category Section]
- [[Note 1]] - Brief description
- [[Note 2]] - Brief description

## Related MOCs
- [[MOC - Related Topic]]
```

---

## Link Maintenance

### Weekly Link Review

**During `/weekly-review` or `/refine-notes`:**

1. **Check for orphans:**
   - Query notes with 0 outbound links
   - Add minimum 3 links

2. **Check link quality:**
   - Are relationships explained?
   - Are links meaningful?
   - Any broken links?

3. **Add new connections:**
   - Review recent notes for new link opportunities
   - Link to newly created MOCs

**Dataview query for orphans:**
```dataview
TABLE length(file.outlinks) as "Links"
FROM "Permanent Notes" OR "03-Resources"
WHERE type = "permanent-note"
WHERE length(file.outlinks) < 3
SORT length(file.outlinks) ASC
```

---

### Monthly Link Audit

**Once per month:**

1. **Review most-linked notes:**
   - Are they actually central concepts?
   - Update if they've become hubs

2. **Review least-linked notes:**
   - Are they actually valuable?
   - Add more links or consider deleting

3. **Check for link clusters:**
   - Do related notes link to each other?
   - Create MOC if cluster detected

**Dataview query for most-linked:**
```dataview
TABLE length(file.inlinks) as "Backlinks"
FROM "Permanent Notes"
SORT length(file.inlinks) DESC
LIMIT 20
```

---

## Command Integration

### How Commands Handle Linking

**`/process-raw-notes`:**

**Linking workflow:**
1. After creating permanent note, search for related notes
2. Use Grep with keywords from note title and content
3. Find 3+ related notes
4. Add links with relationship explanations
5. Check for existing MOCs on topic
6. Link to MOC if found
7. Suggest creating MOC if 3+ related notes exist

**Implementation:**
```markdown
### Step X: Link Discovery

For permanent note "{{Title}}":
1. Grep search: {{key concepts}}
2. Found related: [[Note A]], [[Note B]], [[Note C]]
3. Check MOC: [[MOC - {{Topic}}]] (exists/create?)
4. Add links to note with explanations
```

---

**`/refine-notes`:**

**Linking analysis:**
1. Count outbound links per note
2. Flag orphans (< 3 links)
3. Check if linked to MOC
4. Search for additional related notes
5. Suggest link additions with reasoning

**Quality report:**
```markdown
## Link Analysis

**Orphan Notes (0-2 links):**
1. [[Note Title]] - Currently 1 link
   - Suggested additions:
     - [[Related 1]] - Both discuss productivity
     - [[Related 2]] - Contrasting perspective
     - [[MOC - Productivity]] - Topic hub
```

---

**`/create-moc`:**

**Auto-linking workflow:**
1. Search vault for notes matching MOC topic
2. Group by subtopic
3. Add links in appropriate sections
4. Link MOC to related MOCs

---

**`/update-moc`:**

**Link refresh workflow:**
1. Read existing MOC
2. Search for new notes on topic (created since last update)
3. Suggest additions
4. Update note count
5. Refresh last review date

---

## Link Quality Criteria

### High-Quality Link

**Characteristics:**
- ✅ Relationship is explained
- ✅ Connection is meaningful (not forced)
- ✅ Adds value to both notes
- ✅ Enables new insights or understanding

**Example:**
```markdown
- [[Time Blocking Reduces Decision Fatigue]] - Complementary strategy: By pre-deciding when to work on what, time blocking eliminates the context switching decisions that add up to decision fatigue
```

---

### Low-Quality Link

**Characteristics:**
- ❌ No explanation of relationship
- ❌ Connection is tenuous or forced
- ❌ Added just to hit link count
- ❌ Doesn't add value

**Example:**
```markdown
- [[Productivity]]  # Too vague, no explanation
```

---

## Progressive Linking

**Links improve over time - don't aim for perfection on first pass**

**Version 1 (During creation):**
```markdown
## Links
- [[Related Note 1]]
- [[Related Note 2]]
- [[MOC - Topic]]
```

**Version 2 (During weekly review):**
```markdown
## Links

### Related Concepts
- [[Related Note 1]] - How they relate
- [[Related Note 2]] - Connection
- [[New Note Found]] - Just discovered this connection

### Broader Context
- [[MOC - Topic]]
```

**Version 3 (After applying knowledge):**
```markdown
## Links

### Related Concepts
- [[Related Note 1]] - How they relate
- [[Related Note 2]] - Connection
- [[New Note Found]] - Just discovered this connection

### Applications
- [[Project Alpha]] - Applied here successfully
```

**Philosophy:** Start with basic links, enhance over time as understanding deepens.

---

## Integration with Obsidian Features

### Graph View

**Links create visual knowledge graph:**
- Nodes = Notes
- Edges = Links
- Clusters = Related topics
- Hubs = Highly-connected notes (often MOCs)

**Use graph to:**
- Identify disconnected notes
- Find knowledge clusters
- Visualize topic relationships
- Discover unexpected connections

---

### Backlinks Pane

**Shows who links to this note:**
- See incoming connections
- Discover related contexts
- Find applications of knowledge
- Identify potential bidirectional links

**Use for:**
- Understanding note importance
- Finding usage contexts
- Adding reciprocal links

---

### Linked Mentions

**Shows unlinked mentions:**
- Notes that mention this note's title
- Potential links not yet created

**Use for:**
- Finding implicit connections
- Suggesting explicit links
- Discovering related content

---

## Link Metrics

### Healthy Linking Indicators

**Permanent Notes:**
- Average 3-7 outbound links per note
- < 10% orphan notes
- 90%+ linked to at least one MOC
- Bidirectional linking on strong relationships

**Projects:**
- Links to 2-5 relevant permanent notes (resources)
- Links to parent area
- Links to related projects

**MOCs:**
- Links to 10+ permanent notes minimum
- Links to 2-5 related MOCs
- Updated monthly with new notes

---

## Common Linking Mistakes

### Mistake 1: Link Hoarding

**Problem:** Linking to 20+ notes because "might be related"

**Solution:** Be selective. Link to truly related notes only.

**Quality > Quantity**

---

### Mistake 2: No Relationship Explanation

**Problem:** Just listing links without context

**Solution:** Always add "- How they relate" after link

---

### Mistake 3: One-Way Streets

**Problem:** Note A links to Note B, but B doesn't link back (when relationship is strong)

**Solution:** For strong relationships, add bidirectional links

---

### Mistake 4: Orphan Tolerance

**Problem:** Letting notes exist with 0 links

**Solution:** No permanent note should be an orphan. Minimum 3 links required.

---

### Mistake 5: Forced Linking

**Problem:** Adding links just to hit link count

**Solution:** Only link when connection is meaningful. If can't find 3 meaningful links, note might not be valuable enough to keep.

---

## Quick Reference

### Minimum Links by Note Type

| Note Type | Minimum Links | Where |
|-----------|---------------|-------|
| Permanent Note | 3+ | Related Concepts (2) + MOC (1) |
| Reference Note | 2+ | Permanent notes extracted |
| Project Note | 2+ | Parent area + resources |
| Area Note | 1+ | Active projects list |
| MOC | 10+ | Permanent notes in domain |
| Task | 1 | Parent project |

### Link Relationship Types

| Type | Purpose | Example |
|------|---------|---------|
| Related | Similar concepts | "Both productivity strategies" |
| Contrasts | Opposing views | "Different approach to same problem" |
| Builds On | Prerequisite | "Foundational concept" |
| Leads To | Consequence | "Enables this insight" |
| Application | Used in | "Applied in this project" |
| Source | Attribution | "Learned from this source" |
| Parent | Hierarchy | "Part of this larger concept" |
| Example | Instance | "Specific instance of general principle" |

---

**Remember:** Links are what make your Second Brain "brain-like." The value isn't in individual notes, but in the connections between them.

---

**Last Updated:** 2025-10-20
**Version:** 2.0
