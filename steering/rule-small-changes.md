# Small, Reversible, Observable Changes

Prefer small diffs and scoped changes. Make changes visible and user-testable before moving to backend work. Keep changes reversible and maintain separation of concerns.

## Principles

- **Small diffs:** One logical change per commit/step. Avoid mixing unrelated changes.
- **Observable first:** Implement UI or user-facing changes before backend plumbing when feasible.
- **Reversible:** Prefer additive changes (new files, new functions) over destructive edits to existing code.
- **Separation of concerns:** Don't mix orchestration, domain logic, and I/O in the same function unless the logic is trivial.

## Rules

- ✅ Break large features into small, independently testable steps
- ✅ Each step should leave the codebase in a working state
- ✅ Prefer adding new code over modifying existing code when possible
- ✅ Keep orchestration (controllers/handlers) thin — delegate to domain and I/O layers
- ❌ Never combine a refactor with a behavior change in the same step
- ❌ Never make a change that requires multiple other changes to avoid breaking the build

## Agentic Guidance

When working autonomously:
- Plan multi-file changes as a sequence of small steps, not one large batch.
- After each step, verify the project still builds/passes tests before continuing.
- If a task requires touching more than 3-4 files, pause and outline the plan before starting.
- When modifying existing functions, prefer wrapping or extending over rewriting.
- If you realize a change is growing large, stop and ask the user whether to continue or split it up.
