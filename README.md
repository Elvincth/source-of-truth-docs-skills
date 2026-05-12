# Source of Truth Docs Skills

`source-of-truth-docs-skills` helps agents create and maintain repository documentation that acts as the project's source of truth.

It is inspired by OpenAI's Harness Engineering post and Karpathy-style coding guidelines. The combined idea is simple: put durable project knowledge in the repo, make it easy to navigate, and edit docs with restraint.

## Install

Install from GitHub:

```bash
npx skills add elvincth/source-of-truth-docs-skills --skill source-of-truth-docs-skills
```

List skills in the repository before installing:

```bash
npx skills add elvincth/source-of-truth-docs-skills --list
```

Install from a local checkout:

```bash
npx skills add . --skill source-of-truth-docs-skills
```

## The Problems

Karpathy-style guidelines call out a few recurring agent failure modes:

- Agents make wrong assumptions and keep going instead of checking.
- They hide confusion, miss inconsistencies, and fail to surface tradeoffs.
- They overcomplicate code, APIs, and abstractions.
- They touch nearby comments or code they do not understand, even when it is unrelated to the task.

Documentation work has the same failure modes. Agents can invent architecture, duplicate stale facts, create giant instruction files, or rewrite unrelated docs while trying to be helpful.

## The Solution

This skill applies four principles to documentation work:

| Principle | Addresses |
| --- | --- |
| Think Before Editing | Wrong assumptions, hidden confusion, missing tradeoffs |
| Simplicity First | Overcomplicated docs, giant instruction files, duplicated sources |
| Surgical Changes | Orthogonal edits, rewritten sections, touching docs outside the request |
| Goal-Driven Verification | Source-backed claims, checkable links, resumable handoffs |

The Harness Engineering inspiration is to keep project knowledge inside the repository. `AGENTS.md` becomes the compact map, while deeper docs hold the actual source of truth.

## Why this is useful

Agent-heavy projects do not need one huge instruction file. They need a small map and a reliable knowledge base.

This approach is good because:

- Important knowledge lives in versioned files.
- Future work becomes resumable through active and completed execution plans.
- Generated facts are separated from human-authored guidance.
- External references can be converted into local agent-readable files.
- Documentation changes stay small, reviewable, and verifiable.

## Recommended documentation map

This is a general pattern. Rename or remove parts that do not fit your project.

```text
AGENTS.md
ARCHITECTURE.md
docs/
|-- design-docs/
|   |-- index.md
|   |-- core-beliefs.md
|   `-- ...
|-- exec-plans/
|   |-- active/
|   |-- completed/
|   `-- tech-debt-tracker.md
|-- generated/
|   `-- db-schema.md
|-- product-specs/
|   |-- index.md
|   |-- new-user-onboarding.md
|   `-- ...
|-- references/
|   |-- design-system-reference-llms.txt
|   |-- nixpacks-llms.txt
|   |-- uv-llms.txt
|   `-- ...
|-- DESIGN.md
|-- FRONTEND.md
|-- PLANS.md
|-- PRODUCT_SENSE.md
|-- QUALITY_SCORE.md
|-- RELIABILITY.md
`-- SECURITY.md
```

## What each part is for

- `AGENTS.md`: Short agent map with repo rules, common commands, constraints, and links to deeper docs.
- `ARCHITECTURE.md`: System map, boundaries, layers, dependency direction, runtime shape, and invariants.
- `docs/design-docs/`: Design history, decisions, tradeoffs, and core beliefs.
- `docs/exec-plans/`: Active and completed plans plus tech debt that should not be forgotten.
- `docs/generated/`: Generated facts such as schema snapshots or API references.
- `docs/product-specs/`: Product behavior, acceptance criteria, user flows, permissions, and edge cases.
- `docs/references/`: Local agent-readable copies or summaries of external documentation.
- `docs/DESIGN.md`: Cross-cutting visual and interaction design rules.
- `docs/FRONTEND.md`: Frontend architecture, UI state, components, routing, and testing expectations.
- `docs/PLANS.md`: Planning conventions and links to important active or completed plans.
- `docs/PRODUCT_SENSE.md`: Product principles, audience assumptions, and UX priorities.
- `docs/QUALITY_SCORE.md`: Quality rubric and known gaps by area.
- `docs/RELIABILITY.md`: Operational expectations, observability, failure modes, and performance budgets.
- `docs/SECURITY.md`: Auth, secrets, sensitive boundaries, threat notes, and review expectations.

## Skill

The skill lives at:

```text
source-of-truth-docs-skills/SKILL.md
```

It was initialized with:

```bash
npx skills init source-of-truth-docs-skills
```

## Sources

- OpenAI Harness Engineering: https://openai.com/index/harness-engineering/
- Karpathy-inspired guidelines: https://github.com/forrestchang/andrej-karpathy-skills
- Skills CLI reference: https://github.com/vercel-labs/skills
