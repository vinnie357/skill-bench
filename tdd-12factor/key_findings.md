# Key Findings: TDD & 12-Factor Skill Impact Experiment

## Experiment Design

- 3 models (Haiku, Sonnet, Opus) each given 2 phases
- Phase 1: "What do you think about TDD and 12-Factor?" (no skill content)
- Phase 2: Full skill documents provided, asked to analyze what goes beyond surface-level understanding
- 6 total agent runs, results compared across models and phases

### Model Versions and Knowledge Cutoffs

| Model | Version | Knowledge Cutoff | Training Data Cutoff |
|---|---|---|---|
| Haiku 4.5 | `claude-haiku-4-5-20251001` | Feb 2025 | Jul 2025 |
| Sonnet 4.6 | `claude-sonnet-4-6` | Aug 2025 | Jan 2026 |
| Opus 4.6 | `claude-opus-4-6` | May 2025 | Aug 2025 |

The knowledge cutoff is effectively each model's **"born on" date** — the point after which the model has no reliable knowledge from training alone. Any skill content covering developments after a model's cutoff is filling a genuine knowledge gap, not just reinforcing what it already knows.

## Top-Level Findings

### 1. Skills measurably change model output

All three models produced qualitatively different responses after receiving skill content — more specific techniques, more precise language, and deeper analytical frameworks. No model's Phase 2 response could be mistaken for its Phase 1.

### 2. Impact is inversely proportional to baseline capability

- **Haiku**: Largest shift. Went from textbook overview to structured, specific understanding.
- **Sonnet**: Moderate shift. Already strong baseline; skills deepened precision.
- **Opus**: Subtlest shift. Broadest baseline; skills sharpened framing and synthesis.

**Caveat — knowledge cutoff is a confounding variable.** Haiku 4.5's knowledge cutoff (Feb 2025) is 6 months older than Sonnet 4.6's (Aug 2025). We cannot fully separate "smaller model benefits more from skills" from "model with older knowledge benefits more from skills." Haiku's larger shift may partly reflect a larger knowledge gap rather than purely a capability gap. Future experiments should ideally compare models within the same generation (e.g., all 4.6) to isolate capability from recency.

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

## Implications for Skill Content Management

A model's knowledge cutoff is its **born on date** — the boundary between what it learned during training and what it needs to be told at runtime. This has direct consequences for how skill content should be managed:

- **Skills fill the gap from born-on date to present.** Content covering developments after a model's cutoff is net-new knowledge. Content predating the cutoff may still add structure, vocabulary, and specificity, but the model likely has some baseline awareness already.
- **Different models need different amounts of skill content.** Haiku 4.5 (Feb 2025 cutoff) has a larger knowledge gap than Sonnet 4.6 (Aug 2025 cutoff). A skill covering a March 2025 development is new information for Haiku but potentially redundant for Sonnet.
- **Skill content can be trimmed per model.** If a concept is well-established before a model's cutoff, the skill only needs to provide the structured framing (vocabulary, tables, patterns) — not the foundational explanation. For models with newer cutoffs, foundational sections could be trimmed to save context window space.
- **As models get newer, skills shrink.** Content that was essential for a Feb 2025 model may be training data for a Jan 2026 model. Skills should be periodically reviewed against current model cutoffs to remove content that has been absorbed into training.
- **The highest-value skill content is timeless structure, not temporal facts.** The "Listen to the Tests" diagnostic table, the FizzBuzz sequencing example, and the `validateConfig()` pattern all landed across every model regardless of cutoff — because they provide structured thinking frameworks, not date-dependent facts. This kind of content has the longest shelf life.
