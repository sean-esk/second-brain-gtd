---
title: "{{date:YYYY-MM-DD}} - {{Meeting topic}}"
date: "{{date:YYYY-MM-DD}}"
time: "{{HH:MM}}"
type: meeting-note
status: active
tags:
  - meeting-note
area: "{{Which area or project this relates to}}"
attendees: []
---

# {{date:YYYY-MM-DD}} - {{Meeting Topic}}

**Date:** {{date:dddd, MMMM DD, YYYY}}
**Time:** {{Start time}} - {{End time}}
**Duration:** {{Length}}
**Location/Platform:** {{In-person, Zoom, Teams, etc.}}

---

## 👥 Attendees

- {{Your name}}
- {{Person 2}}
- {{Person 3}}

---

## 📋 Agenda

{{What was planned to be discussed}}

1. {{Topic 1}}
2. {{Topic 2}}
3. {{Topic 3}}

---

## 📝 Discussion Notes

### {{Topic 1}}

{{Notes from this discussion point}}

### {{Topic 2}}

{{Notes from this discussion point}}

### {{Topic 3}}

{{Notes from this discussion point}}

---

## 🎯 Key Decisions

{{Important decisions made - these might become permanent notes or project updates}}

- {{Decision 1}} → *Consider creating permanent note about this*
- {{Decision 2}} → *Update relevant project*

---

## ✅ Action Items

> **Guidance:** Extract these during /process-inbox to add to relevant projects

### Assigned to Me
- [ ] {{Action 1}} - Due: {{date:YYYY-MM-DD}} `#context/X #time/Xm`
- [ ] {{Action 2}} - Due: {{date:YYYY-MM-DD}} `#context/X #time/Xm`

### Assigned to Others (Waiting On)
- [ ] @{{Person}} - {{Action}} - Due: {{date:YYYY-MM-DD}}

---

## 💡 Ideas & Insights

{{Any interesting thoughts or potential fleeting notes}}

- {{Idea 1}} - *Consider creating fleeting note*
- {{Idea 2}}

---

## 🔗 Related

**Project:**
- [[{{Main project this meeting was about}}]]

**Area:**
- [[{{Relevant area of responsibility}}]]

**Resources:**
- [[{{Referenced documents or notes}}]]

---

## 📅 Follow-Up

**Next Meeting:** {{date:YYYY-MM-DD}}

**Topics for Next Time:**
- {{Topic to revisit}}
- {{Question to address}}

---

**Template Guidance for Claude:**
- **Action Items** = Extract these and add to relevant projects during /process-inbox
- **Key Decisions** = Might warrant permanent notes if significant insights
- **Ideas & Insights** = Create fleeting notes for interesting thoughts
- **Attendees** = Track who was there for future reference
- Meeting notes stay in Meeting Notes/ folder for archival
