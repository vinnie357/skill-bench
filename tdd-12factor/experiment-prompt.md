# Experiment Prompt: TDD & 12-Factor Skill Impact

## Overview

This experiment measures how structured skill content changes an LLM's understanding of TDD and 12-Factor methodology. Each model runs two phases.

---

## Phase 1 Prompt (Without Skills)

```
Without external research, what do you think about TDD (Test-Driven Development) and 12-Factor App methodology?

Share your understanding, opinions, and any critiques. Cover:
- Core concepts and principles
- Where each methodology shines and where it falls short
- Common mistakes or misconceptions
- How they relate to modern software development

Be thorough and honest about what you know and what you're less certain about.
```

**Instructions to agent:** Write the full response to `without-skills.md` in your assigned directory.

---

## Phase 2 Prompt (With Skills)

```
Below are two structured skill documents covering TDD and 12-Factor methodology. Read them carefully.

[SKILL CONTENT: tdd-skill.md is inserted here]

[SKILL CONTENT: twelve-factor-skill.md is inserted here]

---

Given this material, share your understanding of TDD and 12-Factor. How does this structured knowledge compare to general understanding? Specifically:

- What concepts or frameworks does this material introduce that go beyond surface-level understanding?
- What practical techniques or patterns are included that you wouldn't typically see in a general overview?
- Are there areas where the material challenges common assumptions?
- What's the most valuable insight from each skill document?

Be specific — reference particular sections, examples, or frameworks from the skill content.
```

**Instructions to agent:** Write the full response to `with-skills.md` in your assigned directory.

---

## Skill Sources

- `skills/tdd-skill.md` — Full TDD skill content from `core:tdd` (vinnie357/core v0.1.17)
- `skills/twelve-factor-skill.md` — Full 12-Factor skill content from `core:twelve-factor` (vinnie357/core v0.1.17)
