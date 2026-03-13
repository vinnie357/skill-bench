# Comparison: Skill Impact Across Models

How structured skill content changes understanding of TDD and 12-Factor across Haiku, Sonnet, and Opus.

---

## Phase 1: Baseline Understanding (Without Skills)

### Depth and Sophistication

| Dimension | Haiku | Sonnet | Opus |
|---|---|---|---|
| TDD framing | Testing technique with design benefits | Design technique (not just testing) | Design technique + test pyramid concept |
| 12-Factor framing | List of 12 principles | Operational methodology with historical context | Architecture + operations philosophy |
| Historical attribution | "Emerged from Heroku" | Kent Beck, Adam Wiggins, XP origins, circa 2011 | Kent Beck, Adam Wiggins, ~2011-2012 |
| Critique quality | Generic (cost vs. benefit) | Nuanced ("frequently oversold," env vars limiting) | Balanced (mixed empirical evidence, age of methodology) |
| Connections drawn | TDD + 12-Factor are complementary | Shared "separation of concerns" + cargo cult risk | CI/CD, containers/K8s, DevOps/SRE, serverless |
| Honest uncertainties | Adoption rates, niche domains | Gap between textbook and real-world TDD | Empirical evidence, newer paradigms, "Beyond 12-Factor" |

**Key finding**: Sonnet already identified TDD as "primarily a design technique" in Phase 1 -- an insight the other models only surfaced after receiving the skill content. Opus provided the broadest initial coverage, connecting both methodologies to CI/CD, containers, and DevOps trends. Haiku delivered a solid but textbook-level overview.

### Writing Quality

- **Haiku**: Clear, well-organized, but descriptive rather than analytical. Reads like a competent summary.
- **Sonnet**: Most structurally sophisticated Phase 1 response. Included a comparison table, separated opinions from facts, and explicitly labeled misconceptions vs. mistakes.
- **Opus**: Most comprehensive. Covered every factor individually, drew the most external connections, and was most transparent about uncertainty.

---

## Phase 2: With Skill Content

### What Each Model Picked Up

| Concept from Skills | Haiku | Sonnet | Opus |
|---|---|---|---|
| Test List as planning artifact | Yes -- called it "most practically valuable" | Yes -- formal artifact with sequencing discipline | Yes -- elevated to "first-class step" in the cycle |
| Three strategies (Fake It, Obvious, Triangulation) | Yes -- "conscious choice, not dogma" | Yes -- with decision rules and fallback logic | Yes -- with risk-management framing |
| Test sequencing / FizzBuzz example | Yes -- "driving toward generic code" | Yes -- FizzBuzz as illustration of generalization | Yes -- "controlling the pace of generalization" |
| Listen to the Tests diagnostic table | Yes -- "canary in the coal mine" | Yes -- "diagnostic tool" with specific remedies | Yes -- "actionable diagnostic framework" |
| Double-Loop TDD / Walking Skeleton | Yes -- "two-level strategy" | Yes -- "fractal structure" at two scales | Yes -- "fundamentally different starting point" |
| Outside-In / Ports and Adapters | Yes -- "discovering architecture" | Yes -- concrete motivation for hexagonal architecture | Yes -- "discovery process" for interfaces |
| Modern Extensions (XIII-XV) | Yes -- "completing the picture" | Yes -- acknowledging pre-K8s, pre-microservices gaps | Yes -- "foundational, not optional extras" |
| Configuration validation at startup | No | Yes -- converts runtime to startup failure | Yes -- "small but critical operational detail" |
| Graceful degradation pattern | No | Yes -- resilience beyond Factor IV | Yes -- "real-world operational complexity" |
| Three Laws (compile-failure subtlety) | No | Yes -- Law 2's precision that compile failure counts | Yes -- "this subtlety is lost in most presentations" |
| Init containers / Pod Disruption Budgets | No | Yes -- Kubernetes-native Factor IX | Yes -- "deployment resilience technique" |

**Key finding**: Sonnet and Opus picked up on operational details (configuration validation, graceful degradation, compile-failure subtlety in Law 2, init containers) that Haiku did not mention. Haiku focused on the conceptual shifts while Sonnet and Opus engaged with both conceptual and implementation-level content.

### Most Valuable Insight Selected

| | TDD | 12-Factor |
|---|---|---|
| **Haiku** | Test List as a planning tool | Statelessness as a "superpower" |
| **Sonnet** | "Listen to the Tests" diagnostic table | Immutable release as the "linchpin" connecting Factors I, III, V, IX |
| **Opus** | Test list + sequencing as "controlling the pace of generalization" | Disposability as the "enabling constraint" that makes all other factors work |

Each model chose a different facet of each methodology:
- **Haiku** picked the most accessible insight -- practically useful, easy to apply immediately.
- **Sonnet** picked the most architecturally connective insight -- the immutable release as the concept that unifies multiple factors into a coherent system.
- **Opus** picked the most philosophically deep insight -- disposability not as a nice-to-have but as the prerequisite that enables everything else.

---

## Magnitude of Shift (Phase 1 to Phase 2)

### Haiku: Largest Shift

Haiku showed the most dramatic transformation. Its Phase 1 was a competent but generic overview -- the kind you'd find in any introductory blog post. Phase 2 demonstrated specific, structured understanding: test lists as roadmaps, sequencing as a generalization driver, the diagnostic table, walking skeletons. The skill content gave Haiku a framework it clearly lacked in Phase 1.

**Before**: "TDD is about writing tests before code, which leads to better design."
**After**: "TDD is a design discipline where test sequencing drives incremental generalization, and testing difficulty is a diagnostic for design problems."

### Sonnet: Precision Deepened

Sonnet's shift was less dramatic because it already had strong baseline understanding (identifying TDD as a design technique in Phase 1). The skill content sharpened its specificity: it gained the Three Laws' compile-failure subtlety, the explicit connection between Outside-In TDD and hexagonal architecture's motivation being testability, and the immutable release as a unifying concept. The shift was from "good understanding" to "precise, actionable understanding."

**Before**: "TDD is primarily a design technique, not a testing strategy."
**After**: "TDD is a design methodology where 'Listen to the Tests' provides a diagnostic table mapping specific testing difficulties to specific structural problems with specific refactoring remedies."

### Opus: Framing Sharpened

Opus had the most comprehensive Phase 1 but still shifted meaningfully. The change was less about learning new concepts (Opus already knew about walking skeletons and outside-in development in general terms) and more about sharper framing. The test list became a "design instrument for controlling generalization pace." Disposability became an "enabling constraint." The synthesis -- "constraints drive design" as the shared philosophy -- was new.

**Before**: "Both represent distilled practitioner wisdom -- patterns that emerged from real experience building and operating software at scale."
**After**: "In TDD, the constraint 'never write production code without a failing test' drives the discovery of clean interfaces. In 12-Factor, 'processes must be stateless and disposable' drives externalization of state. Constraints drive design."

---

## Cross-Model Patterns

### 1. Skill Content Levels the Playing Field

Haiku's Phase 2 response was closer in quality to Sonnet and Opus's Phase 2 responses than their Phase 1 responses were to each other. The structured skill content provided a common framework that all three models could engage with, reducing the gap between models. Skills act as an equalizer.

### 2. Larger Models Extract More Operational Detail

Sonnet and Opus both identified implementation-level patterns (configuration validation, init containers, Pod Disruption Budgets, compile-failure edge case in Law 2) that Haiku missed. Larger models appear better at extracting and synthesizing specific operational details from the skill content.

### 3. Each Model Has a Different Analytical Signature

- **Haiku**: Identifies the most accessible, immediately practical takeaway. Good at distilling "what should I do differently?"
- **Sonnet**: Identifies structural connections between concepts. Good at "how do these pieces fit together?"
- **Opus**: Identifies philosophical underpinnings and meta-patterns. Good at "what is the deeper principle at work?"

### 4. All Models Shifted on the Same Core Insight

All three models recognized the same fundamental shift in TDD understanding: from "tests verify code" to "tests are design feedback." The skill content's "Listen to the Tests" table was universally identified as going beyond standard TDD material. This suggests the skill content is effective at communicating this particular insight regardless of model capability.

### 5. 12-Factor Insights Were More Varied

For 12-Factor, the three models selected three different "most valuable insights" (statelessness, immutable release, disposability). This suggests the 12-Factor skill content has multiple equally strong insights, and which one resonates most depends on the model's analytical style.

---

## Conclusions

1. **Skills measurably change model output.** All three models produced qualitatively different responses after receiving skill content, with more specific techniques, more precise language, and deeper analytical frameworks.

2. **The impact is inversely proportional to baseline capability.** Haiku benefited most; Opus benefited in subtler ways. This suggests skills are most valuable for augmenting less capable models.

3. **Skills provide shared vocabulary.** All three post-skill responses used the same terminology (test list, walking skeleton, Fake It/Triangulation, disposability, immutable release), creating a common language across model tiers.

4. **Structured knowledge transfers better than abstract principles.** The most-cited elements from both skills were concrete artifacts: the diagnostic table, the FizzBuzz sequencing example, the `validateConfig()` pattern, the Docker Compose parity pattern. Actionable specifics landed more effectively than philosophical statements.

5. **Model differences persist even with skills.** Despite the leveling effect, each model's analytical signature remained distinct. Skills augment thinking -- they don't homogenize it.
