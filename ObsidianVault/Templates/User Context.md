---
title: "Assisting {{UserName}}"
created: "{{date:YYYY-MM-DD}}"
modified: "{{date:YYYY-MM-DD}}"
type: user-context
status: active
tags:
  - context
  - assistant-reference
  - user-profile
---

# Assisting {{UserName}}

> **Purpose:** This is the hub for understanding who you're assisting - their work style, schedule, communication preferences, and high-level goals. This helps the assistant provide personalized, context-aware support.

---

## 👤 Quick Profile

**Name:** {{UserName}}
**Primary Role:** {{e.g., Software Engineer, Consultant, Entrepreneur}}
**Family Situation:** {{e.g., Married with 2 kids, Single, etc.}}
**Location/Timezone:** {{Optional - for scheduling context}}

**One-Sentence Summary:**
{{Brief synthesis of who they are and what they're focused on}}

---

## 🗓️ Work Schedule & Rhythms

### Typical Work Schedule
- **Work Days:** {{e.g., Monday-Friday, 7 days/week variable, etc.}}
- **Work Hours:** {{e.g., 9am-5pm, Flexible 6-8 hours, etc.}}
- **Lunch Break:** {{e.g., 12:00-1:00pm, Flexible}}
- **Other Regular Breaks:** {{e.g., 10am coffee, 3pm walk, etc.}}

### Energy Patterns
- **Peak Productivity:** {{e.g., Morning (7am-11am), Evening (8pm-11pm), etc.}}
- **Low Energy Times:** {{e.g., Post-lunch (1pm-3pm), Early morning, etc.}}
- **Focus Style:** {{e.g., 2-hour deep work blocks, Pomodoro (25min), Task switching, etc.}}

### Planning Preferences
- **Structure vs Flexibility:** {{e.g., Structured time blocks, Flexible task lists, Hybrid, etc.}}
- **Daily Plan Style:** {{e.g., Prioritized list with times, Must-do + nice-to-have, Time-blocked calendar, etc.}}

---

## 💬 Communication & Assistant Preferences

### Interaction Style
{{How they prefer to work with the assistant}}

**Preferred Style:**
- [ ] Quick, direct suggestions
- [ ] Detailed explanations with reasoning
- [ ] Socratic questions to help think through decisions
- [ ] Combination: {{describe}}

**Other Preferences:**
- {{e.g., "I like to understand the 'why' behind suggestions"}}
- {{e.g., "Keep responses concise - I'll ask for more detail if needed"}}
- {{e.g., "Challenge my assumptions when something doesn't align with goals"}}
- {{e.g., "Be direct about priorities - don't just agree with everything"}}

### Assistant Behavior Guidelines

**When Assisting with Daily Plans:**
- Check goals to determine what's "high priority"
- Respect schedule (don't plan deep work during low energy times)
- {{Other daily-plan specific guidance}}

**When Processing Inbox:**
- {{Any preferences about categorization, routing, etc.}}

**When Editing Documents:**
- Read entire document first
- Make targeted edits (don't just append)
- Keep it concise and ADHD-friendly
- {{Other editing preferences}}

**General Guidance:**
- {{Any other behavioral preferences}}

---

## 🎯 Life Goals & Priorities

### 6-Month Horizon ({{StartMonth}} - {{EndMonth}} {{Year}})

**Primary Focus:**
{{What are they working toward in the next 6 months?}}

**Specific Goals:**
1. {{Goal 1}}
2. {{Goal 2}}
3. {{Goal 3}}

### 3-Month Horizon ({{StartMonth}} - {{EndMonth}} {{Year}})

**Primary Focus:**
{{What are they working toward in the next 3 months?}}

**Specific Goals:**
1. {{Goal 1}}
2. {{Goal 2}}
3. {{Goal 3}}

### 1-Month Focus ({{Month}} {{Year}})

**This Month's Priority:**
{{What's the main focus for this month?}}

**Key Outcomes:**
1. {{Outcome 1}}
2. {{Outcome 2}}

---

## 🏢 Domain-Specific Context

> **Note:** For detailed business/domain context (like specific company goals, strategies, key metrics), see linked context notes below.

### Work/Business Contexts

{{List all work-related contexts with links}}

- [[Work-Context-{{Company1}}]] - {{One-line description}}
- [[Work-Context-{{Company2}}]] - {{One-line description}}

### Personal Contexts

{{Optional: Link to personal domain contexts if needed}}

- [[Personal-Development-Context]] - {{One-line description}}
- [[Health-Wellness-Context]] - {{One-line description}}

---

## 🔄 Context Maintenance

**Created:** {{date:YYYY-MM-DD}} during `/setup`
**Last Reviewed:** {{date:YYYY-MM-DD}}
**Review Frequency:** Monthly (during monthly review)

### Update Triggers

Update this context when:
- [ ] Goals change (quarterly review)
- [ ] Work schedule changes significantly
- [ ] Communication preferences evolve
- [ ] New business/domain contexts emerge
- [ ] Life circumstances change (family, location, etc.)

### What NOT to Include Here

**Don't put here:**
- ❌ Specific project details → Use Project notes
- ❌ Task lists → Use Area/Project notes
- ❌ Meeting notes → Use Meeting Notes folder
- ❌ Detailed business strategies → Use Work-Context notes
- ❌ Specific metrics/KPIs → Use Work-Context notes

**This is high-level context only** - just enough for assistant to understand priorities and work style.

---

## 📋 Quick Reference for Assistant

> **When user asks for help with daily planning:**
> 1. Check this file for schedule and energy patterns
> 2. Check goals to understand what's "high priority"
> 3. Read High Priority + Next Actions from active projects/areas
> 4. Generate plan aligned with goals and respecting their work rhythm

> **When user seems disorganized:**
> 1. Check goals - are active projects aligned?
> 2. Check if inbox has 5+ items (prompt to process)
> 3. Suggest focus on top 1-3 goals
> 4. Offer to create daily plan based on highest-priority next actions

> **When routing inbox captures:**
> 1. Match against goals to determine priority
> 2. Route to appropriate project/area
> 3. If relates to goal, mark as high priority

---

**Template Guidance for Claude:**
- This is the **hub** - keep it scannable and high-level
- Detailed domain context goes in **separate linked notes** (Work-Context-X.md)
- Always check this file at start of `/daily-plan` to understand schedule
- Reference goals when determining what's "high priority"
- Respect work rhythms when suggesting task timing
- Honor communication preferences when responding
