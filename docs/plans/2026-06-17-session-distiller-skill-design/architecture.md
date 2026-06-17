# Architecture for Session Distiller Skill

## System Overview

`session-distiller` is a dotcodex workflow skill. It lives in the source layer and is published through the existing stable skill pipeline.

```text
dotcodex/
├── .agents/skills/session-distiller/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/
│       ├── artifact-templates.md
│       └── distillation-taxonomy.md
├── skills/session-distiller/
│   └── skill.md
└── release/skills.json
```

## Components

### SKILL.md

Contains the trigger description, core contract, workflow, and output rules. It stays concise so it can be loaded frequently without wasting context.

### distillation-taxonomy.md

Defines the knowledge types:

- Fact
- Decision
- Principle
- Procedure
- Preference
- Open Loop
- Skill Candidate

### artifact-templates.md

Provides durable Markdown templates for:

- Full session distillation
- Memory proposal
- Skill candidate

### release/skills.json

Adds `session-distiller` to the stable whitelist so the existing installer can publish it.

## Integration Points

- `npm run build:skills` copies `.agents/skills/session-distiller/SKILL.md` to `skills/session-distiller/skill.md`.
- `npm test` verifies source and public layers remain synchronized.
- `install.sh` and `scripts/install.mjs` install it into a Codex profile as `SKILL.md`.

## Technology Choices

No runtime script is needed in v1. The skill is procedural and template-driven; deterministic automation can be added later if repeated artifacts need machine parsing.
