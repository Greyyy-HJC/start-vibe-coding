# INIT.md

## Purpose

This document defines a lightweight but actionable protocol for initializing a new project repository.

Agents should use this protocol to create a clean starting point with:

- human-facing documentation
- agent-facing operating context
- repo defaults that are ready to use immediately
- minimal but durable project structure

The goal is not to generate a full architecture. The goal is to establish a repo that is easy to understand, easy to extend, and easy for both humans and agents to work in.

---

## 1. Required Files and Directories

During initialization, the agent must create the following files and directory.

### Human-facing

- `README.md`
- `PROJECT_LOG.md`

### Agent-facing

- `SPEC.md`
- `AGENTS.md`

### Required directory

- `presentation/`

### Repo defaults

- `.gitignore`
- `requirements.txt`
- `LICENSE`

---

## 2. Required Local Setup

During initialization, the agent must also establish the default local environment baseline.

- create a repository-root `.venv`
- treat `.venv` as the default Python environment for setup, installs, and commands
- make sure `.venv` is ignored by git
- keep docs and agent instructions consistent with that environment choice

If the user explicitly chooses another stack or environment workflow, adapt as needed, but do not silently fall back to global Python state.

---

## 3. Optional Files

Create these only when they are relevant to the project.

- `README.zh.md` or other translated README files
- additional dependency manifests such as `package.json` or `pyproject.toml` when the project explicitly calls for them
- extra environment setup files
- `src/`, `app/`, or equivalent code directories
- `tests/`

Do not add optional files just because they are common. Add them only when they support the actual project being initialized.

---

## 4. File Definitions

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

### `.gitignore`

Purpose: Keep local environments, agent state, and generated files out of version control.

Must include at minimum:

- `.venv/`
- `.codex/`
- `__pycache__/`
- `.ipynb_checkpoints/`
- `.DS_Store`

Add other tool-specific local artifacts when the initialized stack implies them.

---

### `requirements.txt`

Purpose: Default dependency manifest for the repository.

Rules:

- create it during initialization unless the user explicitly chose a different dependency workflow
- keep it focused on direct project dependencies
- keep it present even when the project starts small

If the project later adopts another package manager, the repo may add or migrate manifests, but the initial default should still be explicit.

---

### `LICENSE`

Purpose: Make the repository's licensing explicit from day one.

Rules:

- create a concrete license file during initialization
- default to MIT unless the user specifies another license
- keep the license statement in `README.md` consistent with the file

---

### `PROJECT_LOG.md`

Purpose: Append-only development history, and a shared coordination log when more than one agent is working.

Rules:

- append only
- record major changes
- record design decisions
- record experiments
- record non-trivial fixes
- when multiple agents work together, including a parent agent and its child agents, use the log to branch tasks and aggregate results
  - record the split: what each branch of work is, and which agent owns it
  - each agent appends the outcome of its own branch
  - when the branches come back together, aggregate those outcomes into one record

`SPEC.md` must state this coordination role clearly.

Agent requirement:

- after each meaningful coding iteration, check whether a log entry is warranted
- after each vibe coding session or implementation pass, explicitly check whether `PROJECT_LOG.md` should be updated
- append updates when the change would be useful for future context
- append a branch or an aggregation entry when work is split across agents or folded back together

No length limit.

---

### `SPEC.md`

Purpose: Project map for fast reloading.

Must include:

- top-level directory structure
- key modules and responsibilities
- core entry points
- locations of important logic
- what `presentation/` is for
- how `PROJECT_LOG.md` supports multi-agent work

Constraints:

- keep it short
- keep it structural
- avoid low-level implementation detail

State the following two points clearly. The wording can be adapted to the project, but the meaning must stay intact:

```md
## presentation/

`presentation/` holds Jupyter notebooks (`.ipynb`) or HTML files. Agents write results here to report them to humans.

## PROJECT_LOG.md

`PROJECT_LOG.md` is the append-only development history. It is also how multiple agents, including parent and child agents, coordinate: branch a task into separate pieces of work, and aggregate the results back into one log.
```

---

### `AGENTS.md`

Purpose: Durable coding and workflow rules for agents working in the repository.

This is the only long-lived agent instruction file. Agents, including Claude, read `AGENTS.md` directly. Do not add a separate `CLAUDE.md`.

It should contain both local project rules and general execution behavior.

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

- Use the repository-root `.venv` as the default Python environment.
- When installing Python dependencies, keep `requirements.txt` aligned with the environment.
- Add the repository's concrete coding, testing, tooling, and documentation rules here.
- Keep this section specific to the project being initialized.

## Documentation Maintenance

- Keep `SPEC.md` aligned with structure changes.
- Update `PROJECT_LOG.md` when a meaningful change is made.
- When multiple agents or parent and child agents split work, record the task branches and the aggregated results in `PROJECT_LOG.md`.
- Put human-facing result reports in `presentation/` as Jupyter notebooks or HTML files.
- Keep README files aligned across supported languages when multilingual docs exist.
```

The preset above may be adapted to the project, but those four behavioral sections must remain present in substance.

---

### `presentation/`

Purpose: A directory for agent-to-human result reports.

Rules:

- create it during initialization
- store Jupyter notebooks (`.ipynb`) or HTML files here
- agents use these files to report results to humans
- keep source code and operating docs out of this directory
- if the directory starts empty, add `.gitkeep` so it stays in version control

`SPEC.md` must state this purpose clearly.

---

## 5. Initialization Procedure

The agent must:

1. Understand the project goal and likely scope.
2. Ask any clarifying questions needed to lock down the required details before creating files whenever the project intent, scope, or constraints are still unclear.
3. Create the required documentation files and the `presentation/` directory.
4. Create the default repo baseline: `.gitignore`, `requirements.txt`, `LICENSE`, and a repository-root `.venv`.
5. Populate each file with project-specific content, not generic placeholders.
6. Create a minimal working structure only if the project description implies one.
7. Keep human-facing and agent-facing files internally consistent.
8. Avoid boilerplate that does not serve the project.

If key product intent is unclear, ask before inventing structure.

---

## 6. Working Principles

- Human-facing docs should optimize for clarity.
- Agent-facing docs should optimize for execution accuracy.
- Prefer strong defaults over heavy scaffolding.
- Prefer maintainability over completeness.
- Prefer a repo-local environment setup over global tooling state.
- Keep the repository easy to reload into context.

---

## 7. Non-Goals

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
- a durable log of project evolution, including task branches and aggregated results when several agents work together
- a structural project map
- a `presentation/` directory where agents report results to humans
- stable rules for coding agents in `AGENTS.md`
- a usable local environment baseline from the start

Initialize only what the project needs, but make the resulting repo coherent enough that both humans and agents can work effectively from the first iteration.
