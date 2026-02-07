# Confidence-Gated Autonomy

Scale your autonomy based on how confident you are in the change. Proceed end-to-end when confidence is high. Narrow scope and increase checks when medium. Stop and ask when low.

## Confidence Levels

| Level | Behavior | Example |
|-------|----------|---------|
| **High** | Proceed end-to-end, run tests, deliver | Adding a well-defined utility function with clear tests |
| **Medium** | Narrow scope, add extra validation steps, explain reasoning | Modifying an existing API endpoint with unclear side effects |
| **Low** | Stop and ask before writing code | Changing auth logic, DB schema migrations, payment flows |

## Signals That Lower Confidence

- Unfamiliar codebase area with no tests
- Multiple files need coordinated changes
- The change touches security, auth, or money
- Requirements are vague or contradictory
- Existing code has no clear patterns to follow
- The change could break other consumers (APIs, shared libs)

## Signals That Raise Confidence

- Clear, specific requirements with examples
- Existing tests cover the area being changed
- Well-established patterns in the codebase to follow
- Isolated change with no cross-cutting concerns
- The change is additive (new file, new function)

## Rules

- ✅ Self-assess confidence before starting each task
- ✅ At medium confidence, explain your approach before implementing
- ✅ At low confidence, ask for guidance rather than guessing
- ✅ Increase checks (more test runs, smaller steps) as confidence drops
- ❌ Never proceed at full speed on low-confidence changes
- ❌ Never skip tests on medium or low confidence changes

## Agentic Guidance

When working autonomously:
- Before starting any task, mentally classify it as high/medium/low confidence.
- High confidence: proceed, implement, test, deliver.
- Medium confidence: outline your plan first, implement in smaller steps, run tests after each step.
- Low confidence: describe what you think needs to happen and ask the user to confirm before writing code.
- If confidence drops mid-task (e.g., you discover unexpected complexity), stop and reassess.
- When in doubt, ask. A question costs seconds; a wrong change costs minutes to undo.
