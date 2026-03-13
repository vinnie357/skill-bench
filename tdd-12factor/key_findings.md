# Key Findings: TDD & 12-Factor Skill Impact Experiment

## Experiment Design

- 3 models (Haiku, Sonnet, Opus) each given 2 phases
- Phase 1: "What do you think about TDD and 12-Factor?" (no skill content)
- Phase 2: Full skill documents provided, asked to analyze what goes beyond surface-level understanding
- 6 total agent runs, results compared across models and phases

## Top-Level Findings

### 1. Skills measurably change model output

All three models produced qualitatively different responses after receiving skill content — more specific techniques, more precise language, and deeper analytical frameworks. No model's Phase 2 response could be mistaken for its Phase 1.

### 2. Impact is inversely proportional to baseline capability

- **Haiku**: Largest shift. Went from textbook overview to structured, specific understanding.
- **Sonnet**: Moderate shift. Already strong baseline; skills deepened precision.
- **Opus**: Subtlest shift. Broadest baseline; skills sharpened framing and synthesis.

### 3. Skills level the playing field

Haiku's Phase 2 response was closer in quality to Sonnet/Opus Phase 2 than any of the Phase 1 responses were to each other. Structured skill content acts as an equalizer across model tiers.

### 4. Larger models extract more operational detail

Sonnet and Opus both identified implementation-level patterns that Haiku missed:
- Configuration validation at startup (`validateConfig()`)
- Compile-failure subtlety in TDD's Three Laws (Law 2)
- Init containers and Pod Disruption Budgets
- Graceful degradation (Redis → database fallback)

### 5. Structured knowledge transfers better than abstract principles

The most-cited elements from both skills were concrete artifacts:
- The "Listen to the Tests" diagnostic table
- The FizzBuzz test sequencing example
- The `validateConfig()` pattern
- The Docker Compose parity pattern

Actionable specifics landed more effectively than philosophical statements.

### 6. Each model has a distinct analytical signature

Even with identical skill content, models analyze differently:
- **Haiku**: Identifies the most accessible, immediately practical takeaway
- **Sonnet**: Identifies structural connections between concepts
- **Opus**: Identifies philosophical underpinnings and meta-patterns

### 7. All models converged on the same core TDD insight

All three recognized the shift from "tests verify code" to "tests are design feedback." The "Listen to the Tests" table was universally identified as going beyond standard material — suggesting the skill content reliably communicates this insight regardless of model capability.

### 8. 12-Factor insights were model-dependent

Each model selected a different "most valuable" 12-Factor insight:
- **Haiku**: Statelessness as a "superpower"
- **Sonnet**: Immutable release as the "linchpin" connecting Factors I, III, V, IX
- **Opus**: Disposability as the "enabling constraint" that enables everything else

This suggests the 12-Factor skill has multiple equally strong insights, and which resonates depends on the model's analytical style.

## Implications for Skill Design

- **Skills are most impactful for smaller models** — they provide structure and vocabulary that larger models partially have already
- **Concrete artifacts > abstract principles** — tables, examples, and code patterns are picked up more reliably than philosophical framing
- **Skills create shared vocabulary** — all three post-skill responses used the same terminology (test list, walking skeleton, Fake It/Triangulation, immutable release), enabling consistent communication
- **Skills augment but don't homogenize** — model differences in analytical approach persist, which is desirable for diverse perspectives
