# INIT.md

## Purpose
This document defines a minimal protocol for initializing a new project repository.

Agents must follow this protocol to create a consistent, maintainable project structure with both human-facing and agent-facing documentation.

---

## 1. Required Files

The following files must be created during initialization:

### Human-facing
- README.md
- PROJECT_LOG.md

### Agent-facing
- SPEC.md
- AGENTS.md
- CLAUDE.md

---

## 2. File Definitions

### README.md
Purpose: Entry point for users.

Must include:
- Project description
- Installation / environment requirements
- Usage instructions
- Optional structure overview
- License

Constraints:
- Keep concise
- Avoid internal development details

---

### PROJECT_LOG.md
Purpose: Development history.

Rules:
- Append-only
- Record:
  - Major changes
  - Design decisions
  - Experiments
  - Non-trivial fixes

Agent requirement:
- After each coding iteration, check whether an update is needed
- Append new entries when appropriate

No length limit.

---

### SPEC.md
Purpose: Project map.

Must include:
- Directory structure
- Key modules and responsibilities
- Locations of core logic and entry points

Constraints:
- Keep short
- No implementation details

---

### AGENTS.md
Purpose: Define coding and workflow rules.

Must include:

#### Coding principles
- Prefer simplicity
- Avoid unnecessary abstraction
- Limit deep call chains
- Keep logic locally understandable

#### Style
- Clear naming
- Minimal comments

#### Workflow
- Update PROJECT_LOG when needed
- Keep SPEC consistent with structure
- Avoid unnecessary dependencies

---

### CLAUDE.md
Purpose: Entry point for agent instructions.

Rules:
- Reference AGENTS.md
- Stay consistent with AGENTS.md
- Keep minimal

---

## 3. Initialization Procedure

Agent must:

1. Understand the project goal
2. Create all required files
3. Populate them according to this protocol
4. Create minimal working structure if applicable
5. Ensure consistency across agent-facing files

---

## 4. Principles

- Human-facing → clarity
- Agent-facing → structure
- Keep everything minimal
- Prefer maintainability over completeness

---

## 5. Optional Additions

Include only if relevant:
- Dependency files (e.g. requirements.txt)
- Environment setup instructions
- src/ or app/ directories
- tests/

---

## 6. Non-Goals

- No over-engineering
- No premature optimization
- No excessive boilerplate

---

## Summary

INIT.md serves as a single source of truth for project initialization.

Agents should strictly follow it when bootstrapping new repositories.
