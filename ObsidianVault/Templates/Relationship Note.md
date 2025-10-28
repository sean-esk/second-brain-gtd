---
title: "{{Person Name}}"
created: "{{date:YYYY-MM-DD}}"
modified: "{{date:YYYY-MM-DD}}"
type: relationship
status: active
tags:
  - relationship
  - person
relationship-type: "{{business-partner/family/colleague/friend/etc.}}"
---

# {{Person Name}}

> **Guidance:** This is a relationship note for tracking an important person in your life - business partner, family member, key colleague, etc. Track things to discuss, commitments, and interactions.

---

## 👤 About

**Relationship:** {{Business partner / Family / Colleague / Friend / etc.}}
**Context:** {{How you know them, what you work on together}}
**Contact:** {{Email, phone, preferred contact method}}

---

## 🚨 High Priority

> Critical items to discuss or actions related to this person

- [ ] {{Urgent topic to discuss}} `#context/phone #time/15m`
- [ ] {{Important action}} `#context/X #time/Xm`

---

## 📋 Next Actions

> Things to discuss, tasks related to this person

### To Discuss
- [ ] {{Topic 1 to bring up}} `#context/phone #time/10m`
- [ ] {{Topic 2 to bring up}} `#context/meeting #time/30m`

### To Do (Related to Them)
- [ ] {{Action for/with them}} `#context/X #time/Xm`

---

## 💭 Someday/Maybe

> Topics or ideas for future discussion

- [ ] {{Might discuss eventually}}

---

## ⏳ Waiting On

> Items you're waiting on from this person

- [ ] {{What you're waiting for}} - Asked: {{date:YYYY-MM-DD}} - *Follow up: {{date}}*

---

## 🤝 Commitments & Agreements

{{Track what you've committed to each other}}

**I committed to:**
- {{Item 1}}
- {{Item 2}}

**They committed to:**
- {{Item 1}}
- {{Item 2}}

---

## 📅 Interaction Log

### {{date:YYYY-MM-DD}} - {{Type: Meeting/Call/Email}}

{{Notes from interaction}}

**Discussed:**
- {{Topic 1}}
- {{Topic 2}}

**Decided:**
- {{Decision or outcome}}

**Next Steps:**
- {{Action items}}

---

## 🔗 Related

**Projects:**
- [[{{Shared project}}]]

**Areas:**
- [[{{Relevant area - e.g., if family member, link to Family area}}]]

**Meeting Notes:**
- [[{{date}} - Meeting with {{name}}]]

---

## 📝 Context Notes

{{Important background, preferences, working style, personal notes}}

**Communication Preferences:**
- {{How they prefer to communicate}}

**Important Dates:**
- {{Birthdays, anniversaries, etc.}}

**Interests/Topics:**
- {{Things they care about}}

---

**Template Guidance for Claude:**
- **Relationship Type** = business-partner, family, colleague, friend, mentor, client
- **High Priority** = Urgent things to discuss or do (scan in daily-plan)
- **To Discuss** = Topics to bring up when you meet/talk
- **Waiting On** = Track what you're waiting for from them
- **Commitments** = Mutual agreements and promises
- **Interaction Log** = Running history of conversations
- Use same task structure as projects/areas for consistency
- When processing captures that mention a person's name, route here or create new relationship note
