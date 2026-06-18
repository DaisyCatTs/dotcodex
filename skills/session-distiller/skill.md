---
name: session-distiller
description: Distill long or important Codex conversations into durable learning artifacts, project knowledge, decisions, reusable workflows, memory-update proposals, and candidate skills. Use when the user asks to summarize a long session,沉淀会话,复盘,提炼经验,整理精华,更新记忆, capture lessons learned, create a handoff, or turn repeated work into a reusable skill.
---

# Session Distiller

Transform a messy, high-context conversation into durable assets that help the user learn, resume work, and compound judgment over time.

## Core Contract

1. **Distill from evidence, not vibes.**
   Use conversation history, files, commands, diffs, screenshots, plans, tests, and explicit user decisions as source evidence. Mark unsupported claims as assumptions or omit them.

2. **Separate time horizons.**
   Classify outputs into immediate handoff, project knowledge, personal learning, reusable workflow, memory proposal, and skill candidate. Do not mix temporary debugging details with durable principles.

3. **Protect long-term memory quality.**
   Do not directly update memory unless the user explicitly asks for a memory update. When updating memory is useful, produce a concise proposal with evidence and scope.

4. **Prefer local artifacts for serious sessions.**
   When the user asks for a report, archive, handoff, or durable summary, write a local Markdown artifact in the confirmed artifact directory. For quick chat-only requests, answer inline.

5. **Preserve sharp lessons.**
   Capture mistakes, false starts, root causes, commands that actually worked, proxy/host/env details, review objections, and user preferences. These are often more valuable than the final happy path.

## Workflow

### 1. Scope the Distillation

Identify:

- **Session type**: debugging, feature delivery, architecture design, learning, workflow creation, review, or mixed.
- **Target audience**: future self, teammate, reviewer, onboarding reader, or Codex memory.
- **Durability level**:
  - `ephemeral`: useful only for today.
  - `project`: useful while working in this repo.
  - `personal`: useful across projects.
  - `skill-worthy`: repeated enough to become a Codex skill.
- **Evidence surface**: chat history, repo files, plan docs, terminal output, browser observations, images, external docs, memory files.

If the user asks for “精华/沉淀/复盘” without a target, default to `personal + project` and include both.

### 2. Build an Evidence Timeline

Create a concise timeline of:

1. User goal changes and clarified requirements.
2. Key hypotheses and why they were accepted or rejected.
3. Files, commands, configs, URLs, and tools that mattered.
4. Breakthroughs and root causes.
5. Final implementation or current state.
6. Remaining risks and follow-ups.

Keep only details that explain future decisions. Avoid raw chat replay.

### 3. Extract Knowledge Layers

Use the taxonomy in `references/distillation-taxonomy.md`.

Always separate:

- **Facts**: verified current state.
- **Decisions**: chosen direction and rejected alternatives.
- **Principles**: reusable reasoning.
- **Procedures**: commands, checklists, runbooks.
- **Preferences**: user-specific communication or workflow choices.
- **Open loops**: follow-ups, blockers, external dependencies.

### 4. Produce the Right Artifact

Use `references/artifact-templates.md` when writing a longer report.

Before writing a file, decide the artifact directory:

- If the user explicitly names a directory, write there.
- If the user has an established personal knowledge directory, use it when the request is personal, cross-project, or not clearly tied to the current repo.
- For this user, the established personal knowledge directory is `/Users/jerret/Places/work/kn`.
- If the destination is still unclear, ask one concise Chinese question to confirm where the artifact should be written before creating files.
- For project-bound handoffs or implementation plans, use the relevant project docs or plan directory only when the user clearly asks to keep the artifact with that project.

Default full artifact sections:

1. `# 会话沉淀：<topic>`
2. `## 一句话结论`
3. `## 背景和目标`
4. `## 关键时间线`
5. `## 已验证事实`
6. `## 决策和取舍`
7. `## 可复用方法`
8. `## 踩坑和排查顺序`
9. `## 后续待办`
10. `## 可转化资产`

For inline answers, keep the same logic but compress to the highest-signal sections.

### 5. Decide Whether to Propose Memory or Skill Updates

Propose a **memory update** only when all are true:

- The lesson is likely useful beyond the current thread.
- It is stable enough not to become misleading quickly.
- It has concrete evidence or a precise scope.
- It can be expressed in a short, searchable note.

Propose a **new skill or skill update** only when at least two are true:

- The workflow repeated across sessions or repos.
- The user explicitly wants repeatable behavior.
- The process has fragile steps worth encoding.
- The output format needs consistency.
- The task benefits from bundled references, scripts, or templates.

### 6. Verify the Distillation

Before finalizing, check:

- No private credential, token, cookie, or sensitive value is copied into the artifact.
- Claims are labeled as verified, inferred, or open.
- Commands and paths are exact.
- User preferences are not overgeneralized beyond evidence.
- Open loops are separated from completed work.
- If a file was written, links and referenced paths exist.

## Output Rules

- Use Chinese by default when the user uses Chinese.
- Keep final chat summaries concise; put detail into files when the session is large.
- Use exact paths and commands in code spans.
- Do not claim memory was updated unless a memory update file was actually written.
- Do not claim a skill is available in Codex unless visibility was verified.
- End with the concrete artifact path and the next action, not vague optional phrasing.
