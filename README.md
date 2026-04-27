# start-vibe-coding

Bootstrap a new repo with documentation that works for both humans and coding agents from day one.

English | [简体中文](README.zh.md)

---

## What This Is

`start-vibe-coding` is a lightweight repository bootstrap protocol centered around a single file: `INIT.md`.

Instead of re-explaining your conventions every time you start a project, you drop in one protocol file and let the agent initialize a clean, repeatable working setup.

The result is a repo that is:

- readable for humans
- structured for agents
- consistent across new projects
- minimal without feeling under-specified

---

## How To Use It

### 1. Add `INIT.md` to your new repository

Copy the protocol into the root of the project you want to bootstrap.

### 2. Tell the agent what you want to build

Describe the product, tool, app, script, or library in plain language.

### 3. Ask the agent to initialize the repo from the protocol

Example prompt:

```text
I want to start a project for a personal expense tracker web app.
Initialize this project following INIT.md.
```

The agent should then:

- create the required files
- populate them with project-specific content
- establish a minimal working structure
- keep the human-facing and agent-facing docs consistent

---

## The Problem It Solves

Starting a new project usually means repeating the same setup loop:

- write a `README`
- create a project log
- explain structure and conventions
- restate coding rules to the agent
- rebuild the same initialization context from scratch

That repetition is small, but it compounds. `start-vibe-coding` turns it into a reusable protocol.

---

## Why It Works Well

This protocol creates a clean split between documents for people and documents for agents.

| Audience | Files | Job |
| --- | --- | --- |
| Humans | `README.md`, `PROJECT_LOG.md` | Explain the project, setup, usage, and progress |
| Agents | `SPEC.md`, `AGENTS.md`, `CLAUDE.md` | Define structure, rules, and execution expectations |

That separation makes collaboration smoother:

- humans get a familiar project surface
- agents get explicit operating instructions
- both stay aligned as the repo evolves

---

## What `INIT.md` Creates

The initialization protocol defines a compact starter set:

- `README.md` for the project overview and usage
- `PROJECT_LOG.md` for append-only development history
- `SPEC.md` for the project map
- `AGENTS.md` for durable coding and workflow rules
- `CLAUDE.md` as a lightweight agent entry point

It can also support multilingual docs when needed, such as `README.zh.md`.

---

## Design Principles

- Minimal, but not vague
- Strong defaults over heavy scaffolding
- Clear separation of concerns
- Agent-readable structure
- Low ongoing maintenance cost

---

## Why The Agent Files Matter

Most projects already have a `README`. Fewer have durable instructions for coding agents.

`start-vibe-coding` treats agent-facing files as first-class project infrastructure:

- `AGENTS.md` holds the durable working rules
- `CLAUDE.md` stays minimal and points the agent at those rules
- `SPEC.md` keeps the repo map easy to reload

This gives the agent a stable operating context instead of relying on repeated chat prompts.

---

## License

MIT License
