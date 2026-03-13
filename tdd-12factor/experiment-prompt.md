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

## Model Versions

Experiment run on 2026-03-13 using Claude Code CLI v2.1.63 with default alias resolution:

| Alias | Resolved Model ID | Family |
|---|---|---|
| `haiku` | `claude-haiku-4-5-20251001` | Claude Haiku 4.5 |
| `sonnet` | `claude-sonnet-4-6` | Claude Sonnet 4.6 |
| `opus` | `claude-opus-4-6` | Claude Opus 4.6 |

The orchestrating agent (which ran analysis and wrote comparison/findings) was also `claude-opus-4-6`.

**Note:** Claude Code's `--model` flag accepts shorthand aliases (e.g., `haiku`) that resolve to the latest available version at runtime. Future runs with the same aliases may use different model versions. Always record the resolved model IDs for reproducibility.

---

## Skill Sources

- `skills/tdd-skill.md` — Full TDD skill content from `core:tdd` (vinnie357/core v0.1.17)
- `skills/twelve-factor-skill.md` — Full 12-Factor skill content from `core:twelve-factor` (vinnie357/core v0.1.17)
