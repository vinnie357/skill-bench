# skill-bench

A framework for measuring how structured skill content impacts LLM understanding.

## What This Is

skill-bench runs controlled experiments to answer: **do structured skill documents actually change what an LLM knows?**

Each experiment presents the same prompt to multiple models in two phases:
1. **Without skills** — the model responds from its training data alone
2. **With skills** — the model receives structured skill content inline and responds again

Comparing the two phases across model tiers (Haiku, Sonnet, Opus) reveals whether skills measurably change output quality, specificity, and depth.

## Directory Layout

```
skill-bench/
├── README.md              # This file
├── RUNBOOK.md             # Phased guide for running new experiments
└── tdd-12factor/          # First experiment
    ├── experiment-prompt.md
    ├── conversation-record.md
    ├── comparison.md
    ├── key_findings.md
    ├── skills/
    │   ├── tdd-skill.md
    │   └── twelve-factor-skill.md
    ├── haiku/
    │   ├── without-skills.md
    │   └── with-skills.md
    ├── sonnet/
    │   ├── without-skills.md
    │   └── with-skills.md
    └── opus/
        ├── without-skills.md
        └── with-skills.md
```

Each experiment lives in its own topic directory following the same structure.

## Running a New Experiment

See [RUNBOOK.md](RUNBOOK.md) for a step-by-step phased guide. The runbook is written so a Claude agent can follow it using TaskCreate/TaskUpdate to track progress.

## First Experiment: TDD & 12-Factor

The [tdd-12factor/](tdd-12factor/) experiment measured skill impact across three Claude model tiers using TDD and 12-Factor methodology skills.

**Key findings:**
- Skills measurably change model output across all tiers
- Impact is inversely proportional to baseline capability (Haiku benefits most)
- Structured knowledge levels the playing field between model tiers
- Concrete artifacts (tables, examples, code patterns) transfer better than abstract principles

Full results: [comparison.md](tdd-12factor/comparison.md) | [key_findings.md](tdd-12factor/key_findings.md)
