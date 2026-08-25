# EXT-302 — A Hook Instead of a Reminder (after EXT-110)

> Optional side quest · both tracks · not part of the main route
> Rules: [test task](../README.md) · Quest map: [side-quests/README.md](README.md)

**Why:** neither humans nor models follow rules consistently; a rule holds not through discipline but through automation — "make non-compliance impossible". Anything you ask an agent "not to forget" will, sooner or later, be forgotten.

**What it trains:** control through impossibility; turning a rule from a prompt into executable code.

**The real problem behind the quest:** "even the smartest model needs guardrails" is a field law of practitioners; in this very repository you have already seen how reminder-rules end up — `console.log` in production, nine of them.

**The task:** set up one hook in your agent that catches something you have already been burned by in this project. Examples: block a commit containing `console.log`; auto-run tests after a service file changes; warn on a diff larger than N lines.

**Definition of Done:**
- [ ] The hook configuration is committed
- [ ] The devlog records a case where it actually fired
- [ ] You wrote down which "reminder in the prompt" it replaced
