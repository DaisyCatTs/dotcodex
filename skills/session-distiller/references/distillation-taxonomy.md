# Distillation Taxonomy

Use this taxonomy to prevent long-session summaries from collapsing into a vague recap.

## Fact

A verified current-state statement.

Good examples:

- `client/app/.local/nginx/nginx.conf` is the local wpsweb nginx config.
- The verified Cowork plugin id was `APPa407e056af`.

Rules:

- Cite the source surface in prose when practical: file, command, browser observation, user statement, or test.
- Avoid converting a one-time condition into a universal rule.

## Decision

A choice made during the session, including rejected alternatives.

Capture:

- Chosen option.
- Alternatives considered.
- Why the chosen option won.
- What would make the decision change later.

## Principle

A reusable reasoning rule.

Good examples:

- For plugin no-log failures, verify the proxy chain before changing business code.
- Keep personal automation outside product repos.

Rules:

- Generalize only one level above the evidence.
- Preserve the constraint that made the principle true.

## Procedure

A repeatable sequence of steps.

Capture:

- Exact commands.
- Required working directory.
- Environment variables.
- Expected success signal.
- Common failure signal.

## Preference

A user-specific working style or communication preference.

Capture only when stable and repeatedly demonstrated:

- Chinese-first communication.
- Minimal product-repo churn.
- Prefer local durable artifacts for serious summaries.

## Open Loop

A follow-up that remains incomplete.

Classify as:

- `blocked`: needs user or external system.
- `todo`: can be done later by Codex.
- `watch`: may change over time.

## Skill Candidate

A workflow that may deserve a dedicated skill.

Record:

- Trigger phrases.
- Repeatable procedure.
- Failure modes.
- Required references or scripts.
- Validation command or observable success signal.
