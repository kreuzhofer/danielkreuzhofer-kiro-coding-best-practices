# Minimize Complexity (YAGNI)

Implement the simplest solution that meets current requirements and tests. Do not design for speculative future use cases. Optimize only with evidence.

## Principles

- **YAGNI:** If there's no test or requirement for it, don't build it.
- **No premature optimization:** Write clear code first. Optimize only when profiling shows a bottleneck.
- **No speculative abstractions:** Don't add interfaces, factories, or strategy patterns "just in case."

## Rules

- ✅ Solve the stated problem, nothing more
- ✅ Prefer inline logic over indirection when there's only one use case
- ✅ Use concrete types until a second consumer requires an abstraction
- ✅ Optimize only after measuring — with benchmarks or profiling data
- ❌ Never add configuration options nobody asked for
- ❌ Never introduce a design pattern without a concrete second use case
- ❌ Never pre-build pagination, caching, or retry logic unless the requirement calls for it

```typescript
// ❌ Over-engineered for one use case
interface DataFetcher<T> { fetch(id: string): Promise<T>; }
class UserFetcher implements DataFetcher<User> { /* ... */ }
class UserFetcherFactory { create(): DataFetcher<User> { /* ... */ } }

// ✅ Simple and direct
async function getUser(id: string): Promise<User> {
  return db.user.findUniqueOrThrow({ where: { id } });
}
```

## Agentic Guidance

When working autonomously:
- Before adding any abstraction, ask: is there a second use case right now? If no, keep it concrete.
- Don't add helper functions, utility classes, or shared modules unless they're needed by the current task.
- If the user asks for a feature, implement exactly that feature — don't anticipate extensions.
- When you feel the urge to "make it generic," resist unless explicitly asked.
- If you spot existing over-engineering, mention it but don't refactor it unless asked.
