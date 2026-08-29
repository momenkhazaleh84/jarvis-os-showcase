# Jarvis OS Architecture

## Product Boundary

Jarvis OS is the personal command center. Independent projects and specialist systems can connect to Jarvis, but they are not embedded inside Jarvis Core.

## Target Request Flow

```text
User request
  -> Jarvis Leader
  -> Intent analysis
  -> Project context retrieval
  -> Task graph builder
  -> Dependency resolver
  -> Risk and permission classification
  -> Specialist agent dispatch
  -> Guarded execution
  -> Verification gate
  -> Memory and audit update
  -> Final report
```

## Main Architectural Layers

### 1. API Layer
FastAPI exposes project, task, orchestration, memory, scheduling, notification, approval, agent, and integration endpoints.

### 2. Task Engine
Goals are decomposed into structured tasks with actors, dependencies, autonomy levels, explicit state transitions, and downstream release or blocking behavior.

### 3. Orchestration Runtime
The runtime identifies the next ready task, transitions safe work into execution, records execution attempts, verifies completion, and propagates success, failure, or blocking state.

### 4. Agent Registry and Routing
Jarvis and specialist agents have stable identities, declared capabilities, enabled/disabled state, actor compatibility, and executor configuration.

### 5. Guarded Execution
Executor behavior is constrained by explicit policy boundaries. The optional LLM execution path is intentionally narrower than the general executor framework and is limited to safe read-only reasoning tasks in production configuration.

### 6. Persistence
PostgreSQL stores long-lived system state. SQLAlchemy is used for ORM/repository work and Alembic manages migrations.

### 7. Memory
Memory is project-isolated, bounded, and treated as untrusted context before being supplied to LLM workflows.

### 8. Scheduling and Background Work
One-time and interval schedules invoke the same bounded goal runner rather than bypassing safety controls.

### 9. Frontend
A React/Vite dashboard communicates with the backend through an exact-origin CORS allowlist and role-aware API authentication.

### 10. External Integrations
GitHub integrations are separated into guarded read access and approval-bound write operations.
