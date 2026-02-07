# DRY with Restraint — Reusability vs. Fit

Apply DRY only to real, stable duplication. Avoid abstractions that increase cognitive load without clear benefit. Prefer fit-for-purpose code unless a second use case is concrete.

## Principles

- **Real duplication:** Two pieces of code that look similar but serve different domains are not duplication — they're coincidence.
- **Stable duplication:** Only extract when the duplicated logic is unlikely to diverge.
- **Cognitive cost:** Every abstraction adds a layer of indirection. The cost must be justified.

## When to Extract

| Situation | Action |
|-----------|--------|
| Same logic, same domain, 3+ occurrences | Extract |
| Same logic, different domains | Keep separate — they'll likely diverge |
| 2 occurrences, stable logic | Consider extracting, but don't force it |
| 2 occurrences, evolving logic | Keep separate until patterns stabilize |

## Rules

- ✅ Tolerate some duplication if it keeps code simple and readable
- ✅ Extract only when the shared logic is stable and well-understood
- ✅ Name extracted functions/modules by what they do, not where they came from
- ❌ Never extract a "shared utility" from two slightly different implementations
- ❌ Never create a base class just because two classes have one similar method
- ❌ Never add parameters/flags to a function to handle "both cases" — split instead

```typescript
// ❌ Forced DRY — one function doing two things via flags
function processEntity(entity: User | Order, type: 'user' | 'order') {
  if (type === 'user') { /* user-specific logic */ }
  else { /* order-specific logic */ }
}

// ✅ Separate, clear, fit-for-purpose
function processUser(user: User) { /* user logic */ }
function processOrder(order: Order) { /* order logic */ }
```

## Agentic Guidance

When working autonomously:
- Don't extract shared code unless you see 3+ identical usages in the same domain.
- If you notice duplication across two files, leave it unless the user asks you to consolidate.
- When creating new code, write it inline first. Extract only if a second caller appears during the same task.
- Never create a `utils/` or `helpers/` file proactively — only when extraction is justified.
- If you're unsure whether to extract, err on the side of duplication. It's easier to extract later than to untangle a bad abstraction.
