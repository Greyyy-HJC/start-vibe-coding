# INIT.md

## Purpose

This document defines a lightweight but actionable protocol for initializing a new project repository.

Agents should use this protocol to create a clean starting point with:

- human-facing documentation
- agent-facing operating context
- minimal but durable project structure

The goal is not to generate a full architecture. The goal is to establish a repo that is easy to understand, easy to extend, and easy for both humans and agents to work in.

---

## 1. Required Files

During initialization, the agent must create the following files.

### Human-facing

- `README.md`
- `PROJECT_LOG.md`

### Agent-facing

- `SPEC.md`
- `AGENTS.md`
- `CLAUDE.md`

---

## 2. Optional Files

Create these only when they are relevant to the project.

- `README.zh.md` or other translated README files
- dependency manifests such as `requirements.txt`, `package.json`, or `pyproject.toml`
- environment setup files
- `src/`, `app/`, or equivalent code directories
- `tests/`

Do not add optional files just because they are common. Add them only when they support the actual project being initialized.

---

## 3. File Definitions

### `README.md`

Purpose: The main entry point for humans.

Must include:

- what the project is
- why it exists
- how to install or run it when applicable
- how to use it at a high level
- license information

Constraints:

- keep it concise
- prefer clarity over completeness
- avoid internal implementation details

If multilingual support is needed:

- keep `README.md` as the primary default entry point
- add `README.zh.md` or other language files as peers
- add language switch links near the top of each README
- keep structure aligned across languages

---

### `PROJECT_LOG.md`

Purpose: Append-only development history.

Rules:

- append only
- record major changes
- record design decisions
- record experiments
- record non-trivial fixes

Agent requirement:

- after each meaningful coding iteration, check whether a log entry is warranted
- after each vibe coding session or implementation pass, explicitly check whether `PROJECT_LOG.md` should be updated
- append updates when the change would be useful for future context

No length limit.

---

### `SPEC.md`

Purpose: Project map for fast reloading.

Must include:

- top-level directory structure
- key modules and responsibilities
- core entry points
- locations of important logic

Constraints:

- keep it short
- keep it structural
- avoid low-level implementation detail

---

### `AGENTS.md`

Purpose: Durable coding and workflow rules for agents working in the repository.

This should be the main long-lived instruction file. It should contain both local project rules and general execution behavior.

Must include:

- project-specific coding conventions
- workflow expectations
- maintenance expectations for docs and tests
- a behavioral baseline for how the agent should reason and edit

At minimum, initialize `AGENTS.md` with a preset in this shape:

```md
# AGENTS.md

Project-specific instructions for coding agents working in this repository.

## Think Before Coding

Don't assume. Don't hide confusion. Surface tradeoffs.

- State assumptions explicitly.
- If multiple interpretations exist, present them instead of picking silently.
- If something is unclear, ask before implementing.
- If a simpler approach exists, say so.

## Simplicity First

Write the minimum code that solves the requested problem.

- No features beyond what was asked.
- No speculative abstractions.
- No unnecessary configurability.
- Prefer locally understandable logic.

Ask: would a strong engineer consider this overcomplicated? If yes, simplify it.

## Surgical Changes

Touch only what is required for the task.

- Do not refactor unrelated code unless asked.
- Do not rewrite adjacent comments, formatting, or structure without need.
- Match the existing style of the repository.
- Clean up only the unused code created by your own changes.

Every changed line should trace back to the task.

## Goal-Driven Execution

Turn tasks into verifiable outcomes.

- Define what success looks like before changing code.
- Prefer tests or checks when they are appropriate.
- For multi-step work, keep a short plan and verify each step.
- Do not stop at implementation; verify the result.

## Workflow Hygiene

- Before each `git add` and `git commit`, check whether `.gitignore` needs to be updated.
- After each vibe coding session or meaningful implementation pass, check whether `PROJECT_LOG.md` should be updated.

## Project-Specific Rules

- Add the repository's concrete coding, testing, tooling, and documentation rules here.
- Keep this section specific to the project being initialized.

## Documentation Maintenance

- Keep `SPEC.md` aligned with structure changes.
- Update `PROJECT_LOG.md` when a meaningful change is made.
- Keep README files aligned across supported languages when multilingual docs exist.
```

The preset above may be adapted to the project, but those four behavioral sections must remain present in substance.

---

### `CLAUDE.md`

Purpose: Lightweight entry point for agent instructions.

`CLAUDE.md` should not duplicate the full operating rules if `AGENTS.md` already contains them. Its job is to direct the agent to the durable rules and add only minimal agent-entry context.

Initialize it with a structure like:

```md
# CLAUDE.md

Start here when working in this repository.

Read `AGENTS.md` first and follow it as the primary source of coding and workflow rules.

Use `SPEC.md` for the project map.
Use `PROJECT_LOG.md` for recent development history when relevant.
```

Rules:

- reference `AGENTS.md`
- stay consistent with `AGENTS.md`
- keep it minimal
- avoid duplicating long rule blocks unless the environment requires it

---

## 4. Initialization Procedure

The agent must:

1. Understand the project goal and likely scope.
2. Ask any clarifying questions needed to lock down the required details before creating files whenever the project intent, scope, or constraints are still unclear.
3. Create the required documentation files.
4. Populate each file with project-specific content, not generic placeholders.
5. Create a minimal working structure only if the project description implies one.
6. Keep human-facing and agent-facing files internally consistent.
7. Avoid boilerplate that does not serve the project.

If key product intent is unclear, ask before inventing structure.

---

## 5. Working Principles

- Human-facing docs should optimize for clarity.
- Agent-facing docs should optimize for execution accuracy.
- Prefer strong defaults over heavy scaffolding.
- Prefer maintainability over completeness.
- Keep the repository easy to reload into context.

---

## 6. Non-Goals

- No over-engineering
- No speculative architecture
- No premature optimization
- No mandatory framework choices
- No unnecessary files

---

## Summary

`INIT.md` is the single source of truth for bootstrapping a new repository.

Use it to establish:

- a clear `README`
- a durable log of project evolution
- a structural project map
- stable rules for coding agents

Initialize only what the project needs, but make the resulting repo coherent enough that both humans and agents can work effectively from the first iteration.
