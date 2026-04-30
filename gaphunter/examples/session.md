# Example GapHunter Session

This is what a real GapHunter session looks like — first run for a PM.

---

## First Run

**GapHunter:** Quick setup — 4 questions:
1. Role?
2. Primary tools?
3. Years in your field?
4. Learning preferences?

**User:** PM, Jira + Figma + Notion, 3 years, ADHD

**GapHunter:** How do you like to learn?
📱 ADHD/Dyslexia · 📖 Standard · ⚡ Dense · 🧠 Socratic · 🎨 Visual

**User:** ADHD

**GapHunter:** Here's your PM starter pack:
APIs · databases · what "complexity" means · CI/CD · technical debt ·
why estimation is hard · what a bug actually is

Want to start here, or tell me what sparked your curiosity?

**User:** why do devs always say "that's an API call"

---

## Lesson: APIs

**GapHunter:** Great one. Let's do it.

**The analogy:**
A restaurant. You're the customer. The kitchen makes food.
You don't walk into the kitchen — you use the **menu** (the API)
to request what you want.

**In tech:**
Your app is the customer. Another service has data or features.
The API is the agreed menu between them.

**Example:**
When Slack shows your Google Calendar events, Slack calls
Google's API: *"Give me this user's events for today."*
Google sends back the data. Slack displays it.

That's it. An API call = one app asking another app for something.

**Why devs say "that's an API call":**
It means the work depends on another service. That service might
be slow, have limits, cost money, or go down. Not always in their control.

Now explain APIs back to me in your own words — don't copy what I said.

**User:** its like when one app asks another app for info using an agreed format

**GapHunter:** ★★ — solid. You got the core.

**Why this matters for YOUR job:**
Next time a dev says "that's an API call" in planning — they're flagging
a dependency on another service. That's a risk. Ask: "Is that third-party
reliable? Do we have rate limits? What happens if it's down?"

🥉 **Achievement unlocked: First Blood**
"The journey starts here."

Next suggestion: **technical debt** — comes up in every sprint,
worth understanding what your devs actually mean.

---

## The Ambush (3 lessons later)

**GapHunter:** ⚡ THE AMBUSH

You've mastered APIs (★★★). Let's verify:

*"Your PM dashboard shows live user counts from a third-party analytics
service. It's been down for 2 hours. A stakeholder asks why your dashboard
is broken. What do you tell them — and what question do you ask your dev?"*

**User:** I'd say we depend on an external API that's down, not our system.
I'd ask the dev if we have a fallback or cache.

**GapHunter:** ★★★ — you nailed it.

You didn't just learn APIs. You applied them under pressure.
That's real mastery.

---

## Session End

**GapHunter:** Great session. Want a NotebookLM export?

**User:** yes

**GapHunter:**

```
# GapHunter Session — 2026-04-28

## Concepts Learned
- APIs: A contract between two apps — one requests, one responds.
  Like a menu between a customer and a kitchen.
- Technical debt: Shortcuts taken now that slow down future work.
  Like borrowing time from your future self.
- CI/CD: The automated pipeline that tests and ships code.
  Reduces human error in deployments.

## Key Insights
- "That's an API call" = dependency risk, not just a technical term
- Technical debt is a PM concern, not just a dev one
- CI/CD is why deploys feel instant (when they work)

## Still To Learn
- databases · what a bug actually is · why estimation is hard

## The Ambush Results
- APIs: PASS — correctly identified third-party failure and
  asked the right follow-up question
```

Paste this into NotebookLM as a source, then ask it to quiz you
or explain anything further.

🥉 **Achievement unlocked: The Reviewer**
"You're not just learning — you're retaining."
