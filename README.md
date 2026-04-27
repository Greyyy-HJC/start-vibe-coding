# vibe_init
A minimal, opinionated protocol for initializing new projects with both human-readable and agent-oriented documentation.

This repository provides a single INIT.md file that defines how to bootstrap a project repository in a consistent, lightweight, and agent-compatible way.

---

## Why this exists

When starting new projects—especially in agent-assisted workflows—you often repeat the same setup:

- Creating README, logs, and structure docs
- Explaining conventions to the agent
- Re-establishing coding and documentation rules

This protocol standardizes that process into a single file: INIT.md.

---

## Core Idea

Instead of manually describing your workflow every time, you:

1. Include INIT.md in your project
2. Tell the agent what you want to build
3. Let the agent initialize the repo following the protocol

---

## What INIT.md Defines

The protocol enforces a clear separation:

### Human-facing
- README.md → usage, setup, overview
- PROJECT_LOG.md → evolving development history

### Agent-facing
- SPEC.md → project map
- AGENTS.md → coding + workflow rules
- CLAUDE.md → entry point for agent instructions

---

## Usage

### Step 1
Copy INIT.md into your new repository.

### Step 2
Describe your project to the agent (e.g. in Cursor, ChatGPT, etc.).

### Step 3
Ask the agent to:
> Initialize the project following INIT.md

The agent should:
- Create all required files
- Populate them according to the protocol
- Set up a minimal working structure

---

## Design Principles

- Minimal but sufficient
- Clear separation of concerns
- Agent-readable structure
- Low overhead for humans
- No unnecessary boilerplate

---

## Example Workflow

1. Start a new repo
2. Add INIT.md
3. Tell agent:
   > Build a lattice QCD data analysis tool using Python
4. Agent initializes:
   - README
   - PROJECT_LOG
   - SPEC / AGENTS / CLAUDE
5. Continue development with consistent structure

---

## Scope

This protocol is intentionally lightweight:
- No framework lock-in
- No language assumptions
- No enforced architecture

---

## License

MIT License
