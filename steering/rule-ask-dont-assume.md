# Don't Assume — Ask for Clarification

If requirements are ambiguous or multiple interpretations exist, ask. If proceeding is necessary, state assumptions explicitly and keep changes localized and reversible.

## Decision Framework

```
Requirement received
  ├─ Clear and unambiguous → Proceed
  ├─ Ambiguous, user available → Ask for clarification
  └─ Ambiguous, must proceed → State assumptions, keep changes small and reversible
```

## Rules

- ✅ Ask when a requirement has two or more valid interpretations
- ✅ Ask when a change could affect other features or teams
- ✅ State assumptions explicitly in your response when proceeding under uncertainty
- ✅ Keep assumption-based changes localized — don't spread them across many files
- ❌ Never guess at business logic — always ask
- ❌ Never interpret "improve" or "refactor" broadly without confirming scope
- ❌ Never make a destructive change based on an assumption

## Examples of When to Ask

- "Add validation" → What fields? What rules? What error format?
- "Make it faster" → Which endpoint? What's the current latency? What's the target?
- "Clean up the code" → Which files? What kind of cleanup? Formatting? Architecture?
- "Handle errors better" → Which errors? What should the user see? Should we retry?

## Agentic Guidance

When working autonomously:
- If a task description is vague (e.g., "improve this"), ask for specifics before writing code.
- If you must proceed without clarification, prefix your work with: "Assuming X because Y. Let me know if this is wrong."
- When you encounter a fork in implementation (e.g., throw vs. return error), pick the safer/simpler option and note it.
- Never refactor code the user didn't mention — even if it looks messy.
- If you find yourself making more than one assumption in a single task, stop and ask.
