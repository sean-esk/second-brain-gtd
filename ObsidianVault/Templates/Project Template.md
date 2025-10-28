---
title: "{{title}}"
created: "{{date:YYYY-MM-DD}}"
modified: "{{date:YYYY-MM-DD}}"
type: project
status: active
priority: medium
area: "{{Which area does this support?}}"
due-date: "{{YYYY-MM-DD or leave empty}}"
tags:
  - project
  - status/active
---

# {{title}}

> **Guidance:** A GTD project is any desired outcome requiring more than one action step. Can be small ("clean shed this weekend") or large ("launch new business").

---

## 🎯 Desired Outcome

{{What does "done" look like? Be specific about the end state.}}

**Example:** "Shed is organized with all tools accessible, floor is clear, seasonal items stored."

---

## 📋 Why This Matters

{{How does this align with your goals or support an area of responsibility?}}

**Connects to Area:** [[{{Area name if applicable}}]]

---

## 🚨 High Priority Next Actions

> `/daily-plan` scans these FIRST - most urgent/important tasks

- [ ] {{Critical action 1}} `#context/{{computer/phone/office/home}} #energy/{{high/medium/low}} #time/{{Xm or Xh}}`
- [ ] {{Critical action 2}} `#context/X #energy/X #time/Xm`

---

## 📋 Next Actions

> Regular priority tasks - `/daily-plan` scans these after high priority

- [ ] {{Action 1}} `#context/X #energy/X #time/Xm`
- [ ] {{Action 2}} `#context/X #energy/X #time/Xm`
- [ ] {{Action 3}} `#context/X #energy/X #time/Xm`

**Task Format:**
- Physical and concrete (not "think about" or "plan")
- Specific enough to know exactly what to do
- Tagged with context, energy, and time estimate
- Example: "Call John at 555-1234 to discuss timeline" `#context/phone #energy/medium #time/15m`

---

## 💭 Someday/Maybe

> Lower priority - `/daily-plan` SKIPS these (keeps plan focused)

- [ ] {{Nice to have but not urgent}}
- [ ] {{Could do eventually}}

---

## ⏳ Waiting On

> Blocked by external dependencies - shown separately in daily plan

- [ ] {{Person}} - {{What you're waiting for}} - Asked: {{date:YYYY-MM-DD}} - *Follow up: {{date}}*

---

## ✅ Completed

{{Move finished tasks here to track progress}}

- [x] {{Completed task}} - {{date:YYYY-MM-DD}}

---

## 📝 Project Notes

{{Background, context, decisions, important information}}

---

## 🔗 Related

**Projects:** [[{{Related project}}]]
**Areas:** [[{{Supported area}}]]
**Resources:** [[{{Helpful permanent note or reference}}]]

---

## 📊 Progress Log

### {{date:YYYY-MM-DD}}
{{Updates, decisions, progress}}

---

**Template Guidance for Claude:**
- **Desired Outcome** = GTD "what does done look like?"
- **High Priority** = Urgent/important tasks (scan first in daily-plan)
- **Next Actions** = Regular priority (scan second)
- **Someday/Maybe** = Skip in daily planning
- **Waiting On** = Track blocked items
- All tasks tagged with #context, #energy, #time for filtering
