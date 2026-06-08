---
title: "The-y-coding-standard"
date: "2026-06-08"
tags: ["AI Engineering", "Claude Code", "Open Source", "Developer Tools", "Agentic AI", "Software Architecture"]
excerpt: "A deep dive into how I built an open-source Claude Code plugin that makes AI agents write code exactly the way I would - silently, consistently, across every project and every session."
---

# the_y_coding_standard: I Encoded My Entire Engineering Brain Into a Claude Code Plugin

I kept running into the same problem.

Every new AI session, I had to re-explain the same decisions. "Use the repository pattern." "No process.env outside lib/config.ts." "useReducer when state grows past three fields." "400 lines max per file, no exceptions."

Good engineers have strong opinions. The problem is that AI agents are stateless by default - they forget your opinions the moment the session ends.

So I built a fix. I encoded everything into a plugin.

---

## What is the_y_coding_standard?

It is a Claude Code plugin - a structured set of skills, commands, and reference files that any AI agent picks up automatically. Install it once and every session inherits my full engineering standard without me saying a word.

No lecture. No reminders. The agent just knows.

```
the_y_coding_standard/
  skills/the-y-coding-standard/
    SKILL.md                  - main entry point + trigger logic
    references/
      react-nextjs.md         - Next.js App Router standards
      python.md               - Python standards (uv, ruff, mypy)
      database-postgres.md    - Drizzle, schema design, indexing
      agentic-stack.md        - AGENTS.md format + folder layout
      governance.md           - security audit dimensions
      ... 5 more stacks
  commands/
    y-init.md                 - scaffold a full project in one command
    y-govern.md               - parallel security audit agents
    y-review.md, y-ship.md, y-retro.md ...
```

---

## The Core Idea: Standards That Travel With You

Most coding standards live in a repo's README that nobody reads. Or in a Notion doc that nobody updates. Or in a senior engineer's head that leaves when they leave.

Mine live in a plugin that loads automatically.

```mermaid
flowchart TD
    A[New AI Session] --> B{What stack?}
    B -->|Next.js / React| C[Load react-nextjs.md]
    B -->|Python| D[Load python.md]
    B -->|Postgres / SQL| E[Load database-postgres.md]
    B -->|Java / Spring| F[Load java-spring.md + oop.md]
    B -->|Agent governance| G[Load governance.md]
    C --> H[Apply rules silently while writing]
    D --> H
    E --> H
    F --> H
    G --> H
    H --> I[Code that matches my standard]
```

The key design choice: load only the relevant reference file for the current stack. Never all ten at once. This keeps the agent focused and the context window clean.

---

## The Universal Rules

Before any stack-specific rules, there are rules that apply everywhere. These override everything.

```mermaid
mindmap
  root((Universal Rules))
    File Length
      400 lines HARD cap
      300 preferred for services
      One file = one responsibility
    Naming
      Self-documenting names
      No abbreviations except id url db ctx
      Booleans is/has/can/should/did
    Design
      SOLID everywhere
      DRY on 3rd occurrence
      Centralized config only
      Middleware for cross-cutting concerns
    Yash Non-Negotiables
      No em dashes anywhere
      No emojis in code
      AGENTS.md in every repo
      Pre-commit hooks always
```

These are not preferences. They are hard rules. The word "opinionated" in the README is not a disclaimer - it is a feature.

---

## /y-init: One Command to Scaffold Everything

The most used command. Run `/y-init` in any new repo and it builds the full agentic engineering stack in the correct order.

```mermaid
sequenceDiagram
    participant Dev as Developer
    participant Agent as Claude Agent
    participant FS as Filesystem

    Dev->>Agent: /y-init
    Agent->>FS: Detect stack (package.json / pyproject.toml / Cargo.toml)
    Agent->>FS: Write README.md (if missing)
    Agent->>FS: Write AGENTS.md from template
    Agent->>FS: Write CLAUDE.md from template
    Agent->>FS: Write .gitignore
    Agent->>FS: Write .editorconfig
    Agent->>FS: Create .claude/commands/ .claude/hooks/
    Agent->>FS: Create .github/workflows/ci.yml
    Agent->>FS: Create .husky/pre-commit + commit-msg
    Agent->>FS: Create .devcontainer/devcontainer.json
    Agent->>FS: Create Docs/architecture.md
    Agent->>FS: Create Docs/decisions/0001-template.md
    Agent->>FS: Create plans/ findings/ progress/
    Agent-->>Dev: Summary table + next steps
```

The output is not just files. It is a complete workflow scaffold: CI runs on every push, pre-commit hooks block bad commits, the `Docs/` folder enforces architecture documentation, and `plans/findings/progress/` give every AI session structured places to put its work.

---

## /y-govern: Parallel Security Audit Agents

Before shipping anything significant, `/y-govern` dispatches three parallel sub-agents:

```mermaid
graph LR
    Trigger["/y-govern"] --> SA[Security Agent]
    Trigger --> AA[Audit Agent]
    Trigger --> PA[Permissions Agent]

    SA -->|scan_secrets.py| S1[Regex + entropy secret scanning]
    SA -->|audit_deps.py| S2[npm/pip vulnerability scan]

    AA -->|check_agents_md.py| A1[AGENTS.md completeness check]
    AA --> A2[Lockfile freshness check]

    PA --> P1[Agent permissions matrix review]
    PA --> P2[Deny-list enforcement check]

    S1 & S2 & A1 & A2 & P1 & P2 --> Findings[findings/YYYY-MM-DD-governance.md]
    Findings -->|P0 found| BLOCK[Ship blocked]
    Findings -->|P1-P3 only| PASS[Ship allowed]
```

Severity is explicit:
- **P0 (Critical):** blocks ship - hardcoded secrets, unsafe eval on untrusted input
- **P1 (High):** fix before release - missing pre-commit hooks, unverified dependencies
- **P2 (Medium):** queue for backlog
- **P3 (Low):** track, non-blocking

This runs in parallel so all three audits complete in the time the slowest one takes.

---

## The AGENTS.md Contract

Every repo that uses this standard gets an `AGENTS.md` file. This is the universal agent contract - a machine-readable document that tells any AI agent everything it needs to know about the project before writing a single line.

```mermaid
classDiagram
    class AGENTS_MD {
        +Project Overview
        +Stack and Versions
        +Folder Layout
        +Branching Convention
        +Workflow: Issue to Ship
        +Agent Permissions Matrix
        +Hard Constraints
        +Resolver Routing Table
        +Skill Inventory
        +Governance Checklist
    }

    class PermissionsMatrix {
        +Allowed: Read Write Edit Bash-git
        +Denied: rm-rf force-push sudo
    }

    class ResolverTable {
        +user phrase -> skill invocation
        +"/y-init" -> scaffold command
        +"/y-govern" -> audit command
        +"review this" -> /y-review
    }

    AGENTS_MD --> PermissionsMatrix
    AGENTS_MD --> ResolverTable
```

"If it is not on disk, it did not happen." Every agent action produces a named artifact. Plans go in `plans/`. Investigation outputs go in `findings/`. Session journals go in `progress/`.

---

## Stack-Specific Standards: Next.js

The `react-nextjs.md` reference is where I spend the most time. These are the rules that Next.js App Router projects follow automatically:

```mermaid
flowchart TD
    A[Next.js Component] --> B{Needs browser API / hooks / events?}
    B -->|No| C[Server Component - default]
    B -->|Yes| D["'use client' - leaf only"]

    C --> E{Has 3+ related useState?}
    D --> E
    E -->|Yes| F[useReducer required]
    E -->|No| G[useState allowed]

    A --> H{Reads process.env?}
    H -->|Yes| I[VIOLATION - move to lib/config.ts]
    H -->|No| J[OK]

    A --> K{File length}
    K -->|Over 400 lines| L[VIOLATION - split the file]
    K -->|Under 400 lines| M[OK]
```

The state management hierarchy is strict: URL state first, then server state, then local state with `useReducer`, then Context, then Zustand as a last resort. `useEffect + setState` for data fetching is banned - Server Components use direct async/await.

---

## Stack-Specific Standards: Python

Python projects follow an equally strict set of rules:

| Rule | Standard |
|------|----------|
| Package manager | `uv` only. Poetry as fallback. `pipenv` banned. |
| Linting + formatting | `ruff` replaces black, isort, and flake8 |
| Type checking | `mypy --strict` in CI. No `any` without a comment. |
| Config | `pydantic-settings.BaseSettings`. Never `os.environ.get` scattered in code. |
| Project structure | Feature-based vertical slices: `features/users/`, `features/billing/` |
| FastAPI routers | 5-line body max. No SQL or business logic in routers. |
| Domain models | `@dataclass(frozen=True, slots=True)` for internal models. |
| Exceptions | Custom hierarchy in `exceptions.py`. Never bare `except:`. |
| Python version | Always the latest stable release - looked up at runtime, never hardcoded. |

The CI gate requires 90% test coverage. `uv sync --frozen`, `ruff check`, `ruff format --check`, `mypy --strict`, `pytest --cov` in that order.

---

## How I Built It

The plugin follows the Claude Code skill format: a directory with a `SKILL.md` entry point, reference files loaded on demand, and command definitions as markdown files.

The key architectural decision was the **Reference Index** - a routing table in `SKILL.md` that maps code contexts to reference files. This prevents the agent from loading all 10 reference files into context for a simple Python script fix.

```mermaid
flowchart LR
    Prompt[User Prompt] --> Detect[Detect Stack]
    Detect --> Route{Reference Index}
    Route -->|React/Next.js| R1[react-nextjs.md]
    Route -->|Python| R2[python.md]
    Route -->|Non-React TS| R3[javascript-typescript.md]
    Route -->|Postgres/SQL| R4[database-postgres.md]
    Route -->|Java/Spring| R5[java-spring.md + oop.md]
    Route -->|C++| R6[cpp.md]
    Route -->|Agent structure| R7[agentic-stack.md]
    Route -->|Security/audit| R8[governance.md]
    R1 & R2 & R3 & R4 & R5 & R6 & R7 & R8 --> Apply[Apply rules silently]
```

The 37 eval cases in `evals/triggers.md` verify the routing is correct. Each case defines an input prompt and the expected positive or negative trigger behavior. This makes the skill testable.

---

## Why Open Source?

I built this for myself. But the problems it solves are not personal.

Every engineer who works with AI coding agents faces the same friction: the agent does not know your preferences, your architecture decisions, your hard constraints. You repeat yourself every session. The agent makes the same mistakes on the same patterns.

A shared standard - one that the community contributes to and extends - is more valuable than a personal one. If you have strong opinions about how Go services should be structured, or how Rails apps should handle config, or how Rust projects should enforce safety patterns - that knowledge belongs in a reference file that any agent can load.

The goal is a **universal standard for AI-assisted engineering** where the community's collective hard opinions become the agent's default behavior.

---

## Get Involved

The repo is at **github.com/yashs33244/the_y_coding_standard**.

The places where contributions matter most right now:
- New reference files for stacks not yet covered (Go, Rust, Ruby on Rails, .NET)
- Additional eval cases in `evals/triggers.md`
- Governance scripts in `skills/the-y-coding-standard/scripts/`
- Battle-testing the existing references against real production codebases

If you have opinions about how code should be written - and you have enough scars to back them up - they belong here.

---

## Summary

```mermaid
journey
    title From "AI forgets my standards" to "AI knows my standards"
    section Before
      Explain rules every session: 1: Developer
      Agent ignores architecture decisions: 1: Developer
      Same mistakes repeated: 1: Developer
    section After
      Install plugin once: 5: Developer
      Agent loads correct reference: 5: Claude Agent
      Rules applied silently: 5: Claude Agent
      Standards travel across every project: 5: Developer, Claude Agent
```

The best tools disappear into your workflow. You stop thinking about them and just build.

That is what this standard is trying to be.

---

*Star it. Fork it. Contribute a reference file. github.com/yashs33244/the_y_coding_standard*