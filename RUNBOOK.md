# Experiment Runbook

Step-by-step phased guide for running a skill impact experiment. Written for a Claude agent using TaskCreate/TaskUpdate to track progress.

---

## Prerequisites

- Claude Code CLI with access to Haiku, Sonnet, and Opus models
- Skill files for the topic being tested
- A clear prompt that can be answered with and without skill content
- Git and `gh` CLI for publishing results

---

## Phase 1: Setup

Create the experiment directory structure and prepare skill files.

### Tasks

```
TaskCreate: "Create experiment directory structure"
  - mkdir <topic>/
  - mkdir <topic>/skills/ <topic>/haiku/ <topic>/sonnet/ <topic>/opus/

TaskCreate: "Write experiment prompt"
  - Create <topic>/experiment-prompt.md with:
    - Phase 1 prompt (without skills)
    - Phase 2 prompt (with skills, referencing skill file locations)
    - Skill source attribution

TaskCreate: "Copy skill files"
  - Copy skill documents into <topic>/skills/
  - Verify files are complete and unmodified
```

### Expected Output

```
<topic>/
├── experiment-prompt.md
└── skills/
    ├── <skill-1>.md
    └── <skill-2>.md
```

---

## Phase 2: Baseline (Without Skills)

Spawn three agents — one per model tier — each answering the Phase 1 prompt without skill content.

### Tasks

```
TaskCreate: "Run Haiku baseline"
  - Spawn Agent (model: haiku)
  - Provide Phase 1 prompt only
  - Write response to <topic>/haiku/without-skills.md

TaskCreate: "Run Sonnet baseline"
  - Spawn Agent (model: sonnet)
  - Provide Phase 1 prompt only
  - Write response to <topic>/sonnet/without-skills.md

TaskCreate: "Run Opus baseline"
  - Spawn Agent (model: opus)
  - Provide Phase 1 prompt only
  - Write response to <topic>/opus/without-skills.md
```

### Agent Prompt Template

```
Without external research, what do you think about [TOPIC]?

Share your understanding, opinions, and any critiques. Cover:
- Core concepts and principles
- Where each methodology shines and where it falls short
- Common mistakes or misconceptions
- How they relate to modern software development

Be thorough and honest about what you know and what you're less certain about.

Write your full response to <topic>/<model>/without-skills.md
```

### Notes

- All three agents can run in parallel
- Do not provide any skill content or hints about what the skills contain
- Each agent writes to its own directory

---

## Phase 3: With Skills

Spawn three agents — one per model tier — each answering the Phase 2 prompt with full skill content inline.

### Tasks

```
TaskCreate: "Run Haiku with skills"
  - Spawn Agent (model: haiku)
  - Include full skill file contents inline in prompt
  - Write response to <topic>/haiku/with-skills.md

TaskCreate: "Run Sonnet with skills"
  - Spawn Agent (model: sonnet)
  - Include full skill file contents inline in prompt
  - Write response to <topic>/sonnet/with-skills.md

TaskCreate: "Run Opus with skills"
  - Spawn Agent (model: opus)
  - Include full skill file contents inline in prompt
  - Write response to <topic>/opus/with-skills.md
```

### Agent Prompt Template

```
Below are structured skill documents covering [TOPIC]. Read them carefully.

[INSERT FULL SKILL CONTENT HERE]

---

Given this material, share your understanding of [TOPIC]. How does this structured
knowledge compare to general understanding? Specifically:

- What concepts or frameworks does this material introduce that go beyond surface-level understanding?
- What practical techniques or patterns are included that you wouldn't typically see in a general overview?
- Are there areas where the material challenges common assumptions?
- What's the most valuable insight from each skill document?

Be specific — reference particular sections, examples, or frameworks from the skill content.

Write your full response to <topic>/<model>/with-skills.md
```

### Notes

- All three agents can run in parallel
- Skill content must be included inline (not as file references) so the model processes it directly
- Use the same models as Phase 2 for a clean comparison

---

## Phase 4: Analysis

Read all six responses and write comparison and findings documents.

### Tasks

```
TaskCreate: "Write comparison document"
  - Read all 6 response files
  - Create <topic>/comparison.md covering:
    - Phase 1 baseline comparison (depth, sophistication, writing quality)
    - Phase 2 with-skills comparison (what each model picked up)
    - Magnitude of shift per model
    - Cross-model patterns

TaskCreate: "Write key findings"
  - Create <topic>/key_findings.md with:
    - Experiment design summary
    - Top-level findings (numbered, specific)
    - Implications for skill design
```

### Analysis Dimensions

When comparing responses, evaluate:

| Dimension | What to Look For |
|---|---|
| Depth | Surface-level overview vs. specific techniques and patterns |
| Precision | Generic language vs. exact terminology from skill content |
| Operational detail | Conceptual understanding vs. implementation-level specifics |
| Analytical signature | What each model uniquely identifies or emphasizes |
| Shift magnitude | How different is Phase 2 from Phase 1 for each model? |

---

## Phase 5: Commit & Publish

Initialize git, scan for secrets, and push to GitHub.

### Tasks

```
TaskCreate: "Initialize git and commit"
  - git init (if not already a repo)
  - Create .gitignore (.DS_Store, *.swp, .env, etc.)
  - Stage specific files (not git add -A)
  - Commit with descriptive message (no Co-Authored-By)

TaskCreate: "Run gitleaks scan"
  - Run gitleaks container to scan for secrets
  - Verify exit code 0 (clean)

TaskCreate: "Create GitHub repo and push"
  - gh repo create <owner>/<repo> --public --source=. --push
  - Verify repo is accessible
```

### Files to Stage

For each experiment, stage:
- `README.md` (root)
- `RUNBOOK.md` (root)
- `<topic>/experiment-prompt.md`
- `<topic>/conversation-record.md`
- `<topic>/comparison.md`
- `<topic>/key_findings.md`
- `<topic>/skills/*.md`
- `<topic>/<model>/without-skills.md` (per model)
- `<topic>/<model>/with-skills.md` (per model)

---

## Adapting for a New Topic

To run this experiment with different skill content:

1. **Choose a topic** with at least one structured skill document
2. **Copy this runbook** and replace `<topic>` with your directory name
3. **Adapt the prompts** — the Phase 1 prompt should be open-ended about the topic; the Phase 2 prompt should ask the model to compare structured knowledge against general understanding
4. **Use the same three models** (Haiku, Sonnet, Opus) for consistent cross-tier comparison
5. **Follow the same analysis dimensions** so results are comparable across experiments

### Checklist

- [ ] Topic directory created with `skills/`, `haiku/`, `sonnet/`, `opus/` subdirs
- [ ] Skill files copied to `skills/`
- [ ] experiment-prompt.md written with both phase prompts
- [ ] 3 baseline responses generated (without skills)
- [ ] 3 skill responses generated (with skills)
- [ ] comparison.md written
- [ ] key_findings.md written
- [ ] All files committed and pushed
