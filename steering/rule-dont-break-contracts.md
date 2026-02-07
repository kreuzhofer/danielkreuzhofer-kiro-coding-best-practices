# Don't Break Contracts

Preserve existing public APIs, schemas, and behavioral contracts unless explicitly instructed otherwise. If breaking changes are required, provide migration steps and compatibility tests.

## What Counts as a Contract

- **API endpoints:** URL paths, HTTP methods, request/response shapes, status codes
- **Database schemas:** Table/column names, types, constraints, indexes
- **Function signatures:** Public function names, parameter types, return types
- **Event schemas:** Message formats, topic names, payload structures
- **Config formats:** Environment variables, config file shapes, CLI flags
- **Behavioral expectations:** Side effects, ordering guarantees, error formats

## Rules

- ✅ Check for existing consumers before changing any public interface
- ✅ Use additive changes (new fields, new endpoints) over modifications
- ✅ When a breaking change is necessary, provide a migration path
- ✅ Add compatibility tests that verify the old contract still works
- ✅ Version APIs when breaking changes are unavoidable
- ❌ Never rename a public API field without a deprecation period or migration
- ❌ Never change a function's return type if other code depends on it
- ❌ Never remove a database column without verifying no code reads it

```typescript
// ❌ Breaking change — renames response field
// Before: { userName: "alice" }
// After:  { name: "alice" }

// ✅ Additive change — keeps backward compatibility
// After:  { userName: "alice", name: "alice" }
```

## Agentic Guidance

When working autonomously:
- Before modifying any exported function, type, or API endpoint, search for all callers/consumers.
- If you find consumers, ensure your change is backward-compatible or ask before proceeding.
- When adding fields to an API response, never remove existing fields in the same change.
- When modifying database schemas, prefer additive migrations (add column) over destructive ones (drop/rename column).
- If a breaking change is unavoidable, list the affected consumers and propose a migration plan before implementing.
- Use `grepSearch` to find all usages of a function/type/endpoint before changing its signature.
