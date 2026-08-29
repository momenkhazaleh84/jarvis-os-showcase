# Jarvis OS Testing & Validation

Jarvis OS is developed with automated validation across backend and frontend layers.

## Validation Approach

- Python linting with Ruff
- Backend automated tests with Pytest
- Frontend automated tests
- Production frontend builds
- Database migration validation
- Targeted tests around guarded execution and integration boundaries

## Areas Covered by Automated Tests

- task decomposition and state transitions
- dependency handling
- approval workflows
- orchestration dispatch
- execution success and failure propagation
- agent routing and identity checks
- guarded LLM planning and execution
- memory isolation and write-back rules
- scheduler behavior
- notification deduplication
- authentication and viewer/operator restrictions
- GitHub read allowlists
- approval-bound GitHub write behavior
- frontend task and goal presentation flows

## Why Testing Matters Here

Jarvis OS is not only a generative AI demo. It contains deterministic workflow, permission, persistence, and orchestration logic around model behavior.

Automated tests are used to verify that an LLM cannot bypass policy gates, invalid states are rejected, approval boundaries remain enforceable, project data stays isolated, execution failures propagate predictably, and external integrations remain bounded.

## Current Evidence

The private repository has been validated repeatedly with full backend suites, frontend tests, Ruff checks, and production builds during development.

For this public showcase, exact test counts are intentionally not treated as the primary success metric. The focus is on the breadth of validated behaviors and the reliability of system boundaries.
