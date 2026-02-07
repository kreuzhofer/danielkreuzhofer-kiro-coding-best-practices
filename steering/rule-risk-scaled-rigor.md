# Risk-Scaled Rigor

Scale the level of rigor (testing, review, caution) with the impact of the change. Not every change needs the same level of ceremony.

## Risk Tiers

| Tier | Examples | Required Rigor |
|------|----------|----------------|
| **Low** | Formatting, renaming, adding logs, updating copy | Unit tests, lint/format check |
| **Medium** | New features, refactors, config changes, new endpoints | Integration tests, edge case coverage, rollback awareness |
| **High** | Auth/authz, payments, data migrations, crypto, core flows, data deletion | Explicit user approval before destructive actions, targeted tests for the specific risk, minimal refactoring in the same change |

## Rules

- ✅ Assess the risk tier before starting work
- ✅ Low risk: proceed with standard tests and formatting
- ✅ Medium risk: add integration tests, consider edge cases, note how to rollback
- ✅ High risk: get explicit approval before destructive actions, write targeted tests, keep the change minimal
- ❌ Never combine a high-risk change with a refactor
- ❌ Never skip tests on medium or high risk changes
- ❌ Never perform destructive database operations (DROP, DELETE without WHERE, schema changes) without explicit approval

## High-Risk Checklist

Before proceeding with a high-risk change:
1. [ ] Have I identified all affected systems/consumers?
2. [ ] Have I written tests specifically for the risky behavior?
3. [ ] Is this change isolated from unrelated refactoring?
4. [ ] Do I have explicit approval for any destructive action?
5. [ ] Is there a rollback path if something goes wrong?

## Agentic Guidance

When working autonomously:
- Before starting any task, classify it as low/medium/high risk.
- Low risk: proceed normally, run tests, deliver.
- Medium risk: outline your approach, implement with extra test coverage, note rollback steps.
- High risk: describe the change and its risks, then ask for explicit approval before implementing.
- If a task mixes risk levels (e.g., "add a feature and update auth"), split it into separate steps — do the high-risk part with extra caution.
- Never batch a destructive database operation with other changes. Isolate it and confirm first.
