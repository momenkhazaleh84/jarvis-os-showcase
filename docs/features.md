# Jarvis OS Feature Overview

## Goal and Task Management
- Root-goal creation and progress tracking
- Goal decomposition into sequenced tasks
- Task actors and dependency graphs
- Deterministic ready-task selection
- Bounded root-goal runner

## Approvals and Autonomy
- Explicit autonomy levels
- Approval gates for sensitive actions
- One-time approval consumption for approval-bound external operations
- Rejection propagation and safe downstream blocking

## Agents
- Persistent Jarvis and specialist agent profiles
- Declared capabilities per agent
- Agent enable/disable controls
- Compatible task-to-agent routing
- Agent identity persisted in execution records

## LLM Planning and Execution
- Optional structured LLM planning
- Pydantic-validated structured outputs
- Deterministic fallback when providers fail or plans are invalid
- Guarded LLM execution for safe read-only reasoning
- Bounded project and goal context

## Execution and Auditability
- Numbered execution attempts
- Started, succeeded, and failed execution states
- Output summaries and verification evidence
- Append-only orchestration events
- Task execution history APIs

## Memory
- Global user facts and preferences
- Project-scoped facts, decisions, summaries, and notes
- Project isolation during search
- Sensitive and archived memory exclusion
- Verified memory write-back proposals

## Scheduling and Notifications
- One-time and interval schedules
- Persistent run history
- Background scheduler worker
- Project-scoped notification center
- Deduplicated notification generation

## Authentication and Dashboard
- Optional API-key authentication
- Operator and viewer roles
- Production fail-closed behavior
- React/Vite dashboard
- Exact-origin CORS allowlist

## GitHub Integrations
- Exact repository allowlists
- Bounded read operations
- Approval-bound write proposals
- One-time approval consumption
