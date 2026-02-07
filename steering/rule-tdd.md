# Test-Driven Development

Write or update tests before implementing production code. Never claim a task is complete unless tests run and pass.

## Workflow

1. Write a failing test that captures the requirement
2. Implement the minimal code to make it pass
3. Refactor if needed, re-run tests
4. If tests cannot be run, explicitly state why in your response

## Rules

- ✅ Always run the relevant test suite after making changes
- ✅ Update existing tests when modifying behavior
- ✅ Add new tests when adding new functionality
- ✅ Treat a red test suite as a blocker — do not move on
- ❌ Never mark a task as done with failing or skipped tests
- ❌ Never delete a failing test to make the suite green
- ❌ Never write production code without a corresponding test

## Agentic Guidance

When working autonomously:
- Before editing any source file, check if a test file exists for it. If yes, read it first.
- After every code change, run the test command and inspect the output before proceeding.
- If a test fails unexpectedly, fix the test or the code — do not skip it.
- If you cannot run tests (missing deps, environment issues), say so explicitly and stop.
- Prefer running a single test file over the full suite for faster feedback during iteration.
