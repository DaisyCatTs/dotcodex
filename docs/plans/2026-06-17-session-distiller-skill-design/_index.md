# Design: Session Distiller Skill

## Context

The user described this as an unusually long, high-value conversation and wanted a skill that can control, summarize, and distill session content into reusable essence for later learning, growth, and work accumulation.

The existing dotcodex repository already maintains workflow skills under `.agents/skills/`, publishes stable skills under `skills/`, and controls public installation through `release/skills.json`.

## Discovery Results

- `.agents/skills/<name>/SKILL.md` is the development source-of-truth.
- `skills/<name>/skill.md` is generated from the source layer by `npm run build:skills`.
- `release/skills.json` controls which skills are stable and installed.
- Tests assert the manifest, source layer, public layer, and installer behavior.
- Historical local guidance says skill visibility must be verified, not assumed from file presence.

## Requirements

1. Create a reusable skill for long-session distillation.
2. Support Chinese-first summaries when the user uses Chinese.
3. Separate verified facts, decisions, reusable principles, procedures, preferences, and open loops.
4. Avoid polluting long-term memory with unsupported or temporary details.
5. Produce local durable artifacts when a session is large or important.
6. Propose memory or skill updates only when evidence supports them.
7. Integrate with dotcodex stable skill release flow.
8. Keep the skill concise and use references for detailed taxonomy/templates.

## Rationale

The chosen design is a workflow skill named `session-distiller`.

It is intentionally not a generic summarizer. A generic summarizer would compress the conversation but lose the most valuable parts: root causes, user preferences, commands that worked, false starts, and decisions that should shape future work. `session-distiller` instead acts as a knowledge asset gatekeeper with explicit evidence and durability rules.

## Detailed Design

The skill has:

- A concise `SKILL.md` with the core contract and workflow.
- `references/distillation-taxonomy.md` for classifying extracted knowledge.
- `references/artifact-templates.md` for durable Markdown outputs.
- `agents/openai.yaml` metadata for UI use.
- Stable release manifest inclusion so it can be installed with the existing dotcodex pipeline.

## Design Documents

- [BDD Specifications](./bdd-specs.md) - Behavior scenarios and testing strategy
- [Architecture](./architecture.md) - Repository integration and skill structure
- [Best Practices](./best-practices.md) - Quality, privacy, and memory-safety rules
