# Jarvis OS

**A safety-first multi-agent AI assistant and automation platform for structured project and task execution.**

Jarvis OS is a personal AI operating system designed to turn high-level goals into structured, auditable workflows. The user interacts with a Jarvis leader, which plans work, separates agent-executable tasks from user-owned tasks, delegates safe work to specialist agents, requests approval for sensitive actions, verifies results, and records execution evidence.

> This repository is a public showcase of the project architecture, engineering decisions, and selected evidence. The full source repository remains private.

## Why Jarvis OS Exists

Many AI assistants can generate answers, but real work requires more than generation: task state, permissions, approvals, verification, persistence, memory, scheduling, and auditability.

Jarvis OS explores that system layer around AI agents.

## Core Capabilities

- Multi-agent task orchestration
- Goal decomposition and dependency-aware task graphs
- Specialist agent assignment and capability routing
- Explicit autonomy levels and approval gates
- Persistent execution attempts and audit events
- Project-scoped memory
- Guarded LLM planning and execution
- Scheduled goal runtime and background worker
- Project notifications
- Operator/viewer API authentication
- React/Vite dashboard integration
- Guarded GitHub read integration
- Approval-bound GitHub write proposals

## Architecture at a Glance

```text
User request
    |
    v
Jarvis Leader
    |
    v
Planning / Task Graph
    |
    v
Risk + Permission Classification
    |
    v
Agent Assignment
    |
    v
Guarded Executor / Tool Adapter
    |
    v
Verification
    |
    +--> Execution & Audit Records
    +--> Project Memory
    +--> Notifications / Scheduling
```

See [Architecture](docs/architecture.md) for more detail.

## Technology Stack

| Area | Technologies |
|---|---|
| Backend | Python, FastAPI, Pydantic |
| Agent orchestration | LangGraph, structured LLM workflows |
| Database | PostgreSQL, SQLAlchemy, Alembic |
| Frontend | React, Vite |
| Infrastructure | Docker, Docker Compose |
| Validation | Pytest, Ruff, frontend tests, production builds |
| Integrations | GitHub read/write adapters with explicit policy boundaries |

## Safety-First Design

Jarvis OS does not treat an LLM response as permission to act.

The runtime uses explicit policy boundaries. Sensitive or external actions require dedicated authorization paths, approval-bound execution, or remain unavailable. The LLM layer cannot weaken deterministic permission checks.

See [Safety Model](docs/safety-model.md).

## Selected Engineering Areas

### Task Engine
Goals are decomposed into sequenced tasks with actors, dependencies, autonomy levels, and explicit state transitions.

### Orchestration Runtime
The runtime deterministically selects ready work, dispatches safe tasks, records execution attempts, verifies results, and propagates success, failure, or blocking state.

### Agent Runtime
Tasks are routed to compatible agents using declared capabilities, enabled/disabled state, actor compatibility, and executor configuration.

### Persistent Memory
The system supports global and project-scoped memories while excluding sensitive and archived entries from normal retrieval. Memory cannot expand an executor's permissions.

### Scheduling
Persistent one-time and interval schedules can resume bounded root-goal execution through the same guarded orchestration path.

### GitHub Integration
Read access is allowlisted and GET-only. Write operations are separately opt-in and approval-bound, with one-time approval consumption before external requests.

## Project Status

Jarvis OS is an actively developed private project. The implementation includes a FastAPI backend, PostgreSQL persistence, multi-agent orchestration, approval and audit systems, memory, scheduling, notifications, a React/Vite dashboard, and guarded GitHub integrations.

See [Testing & Validation](docs/testing.md).

## Public Showcase Contents

- [Architecture](docs/architecture.md)
- [Feature Overview](docs/features.md)
- [Safety Model](docs/safety-model.md)
- [Testing & Validation](docs/testing.md)

Planned additions:

- Architecture diagram image
- Selected dashboard screenshots
- Short product walkthrough video
- Selected API examples with sensitive details removed

## About the Developer

Built by **Mo'men Khazaleh**, an Artificial Intelligence student at Jordan University of Science and Technology focused on Applied AI, LLM agents, backend systems, and multi-agent applications.

- GitHub: https://github.com/momenkhazaleh84
- Email: Momenkhazaleh84@gmail.com

## Source Availability

The full source repository is private. Technical discussion, architecture walkthroughs, and selected code review access can be provided when appropriate.
