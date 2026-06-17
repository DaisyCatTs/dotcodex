# BDD Specifications for Session Distiller Skill

## Feature: Long Session Distillation

### Scenario: Create a durable session summary

Given a user asks to summarize or沉淀 a long session
When the skill is used
Then the agent classifies the session type and durability level
And produces a structured artifact with conclusion, timeline, verified facts, decisions, reusable methods, pitfalls, follow-ups, and convertible assets.

### Scenario: Protect memory quality

Given a session includes temporary debugging details and unverified assumptions
When the agent extracts reusable knowledge
Then it separates verified facts from assumptions
And does not claim memory was updated unless an actual memory update file was written
And proposes memory updates only when the lesson is stable, scoped, and evidence-backed.

### Scenario: Preserve project-specific procedures

Given a session contains exact commands, paths, proxy rules, or environment setup
When the agent writes the distillation
Then it records exact commands and paths
And includes expected success signals and common failure signals
And avoids generalizing one machine-specific condition into a universal rule.

### Scenario: Identify skill candidates

Given a workflow repeats across sessions or is fragile enough to encode
When the agent reviews the session
Then it records a skill candidate with trigger phrases, workflow, required references, and validation signals.

### Scenario: Inline quick summary

Given the user asks for a quick summary only
When the skill is used
Then the agent returns a concise inline summary
And still separates completed work from follow-ups
And avoids writing files unless the user requested durable output.

## Testing Strategy

- Validate skill structure through the dotcodex release tests.
- Validate `npm run build:skills` mirrors source skills into the public layer.
- Validate installer tests prove `session-distiller` is copied or linked like other stable skills.
- Manually inspect `SKILL.md` for concise trigger description and no TODO placeholders.
