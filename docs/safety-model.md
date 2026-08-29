# Jarvis OS Safety Model

> **Model output is not authorization.**

The LLM can help plan or reason, but deterministic system policy decides whether an action is allowed.

## Core Safety Principles

### Explicit Autonomy Levels
Tasks are classified by what kind of action they require. Automatic execution is limited to bounded safe categories, while sensitive or external mutations require approval or remain unavailable.

### Deterministic Policy Gates
LLM planning and execution cannot weaken task ownership rules, autonomy constraints, approval requirements, agent capability checks, project isolation, or integration allowlists.

### Identity Validation
Before dispatch, the system validates consistency among task, execution attempt, assigned agent, actor, declared capabilities, and selected executor.

### Bounded LLM Context
LLM workflows receive bounded context rather than unrestricted database or filesystem access. Memory text is treated as untrusted, read-only context.

### Sensitive Data Handling
Sensitive or potentially unsafe context can be rejected before a model call. Sensitive and archived memories are excluded from normal retrieval.

### Verification Before Persistence
Successful execution alone is not enough for trusted memory write-back. Verification evidence is required before an execution can produce a memory proposal.

### External Tool Boundaries
The tool registry is empty by default. Explicitly configured adapters are capability-gated, autonomy-gated, bounded, and audited.

## GitHub Safety Example

### Read Access
- exact repository allowlist
- fixed GET-only operations
- rejected arbitrary URLs and redirects
- bounded normalized responses

### Write Access
- separate credentials
- persisted proposal before execution
- approval bound to exact operation and payload
- approval consumed before external request
- approval cannot be reused for retries or modified actions

## Production Boundary

Production LLM execution is intentionally narrower than the full executor framework and is restricted to safe read-only reasoning tasks.
