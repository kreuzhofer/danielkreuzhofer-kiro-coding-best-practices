# Fail Fast, No Silent Fallbacks

Validate inputs at boundaries. Surface errors early and explicitly. Assume dependencies may fail. Any fallback behavior must be explicit, tested, and observable.

## Principles

- **Boundary validation:** Validate all inputs where they enter the system (API handlers, CLI args, config loaders, message consumers).
- **Explicit errors:** Throw or return typed errors. Never swallow exceptions silently.
- **Dependency distrust:** Assume external calls (DB, HTTP, file I/O) can fail. Handle failures explicitly.
- **Observable fallbacks:** If a fallback exists, it must be logged, tested, and documented.

## Rules

- ✅ Validate inputs at the boundary, not deep inside business logic
- ✅ Use typed error classes or result types instead of generic `Error`
- ✅ Log or surface every caught exception — even if handled gracefully
- ✅ Write tests for error paths, not just happy paths
- ❌ Never use empty `catch {}` blocks
- ❌ Never return a default value on error without logging or signaling the failure
- ❌ Never assume an external service call will succeed

```typescript
// ❌ Silent fallback
function getUser(id: string) {
  try {
    return db.user.findUnique({ where: { id } });
  } catch {
    return null; // caller has no idea this failed
  }
}

// ✅ Explicit error surfacing
function getUser(id: string) {
  try {
    return db.user.findUnique({ where: { id } });
  } catch (error) {
    logger.error('Failed to fetch user', { id, error });
    throw new DatabaseError('User lookup failed', { cause: error });
  }
}
```

## Agentic Guidance

When working autonomously:
- When writing new functions, always consider: what happens if this input is null/undefined/malformed?
- When calling external services or DB, always wrap in error handling with explicit logging.
- Never add a `catch` block that swallows errors — always log or re-throw.
- When reviewing existing code, flag any empty catch blocks or silent fallbacks.
- If you're unsure whether a fallback is acceptable, ask rather than silently adding one.
