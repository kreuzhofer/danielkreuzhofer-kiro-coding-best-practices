---
name: "danielkreuzhofer-kiro-coding-best-practices"
displayName: "Daniel Kreuzhofer's Kiro Coding Best Practices"
description: "Team coding standards covering TDD, property-based testing, test execution workflows, spec naming conventions, and design document guidelines."
keywords: ["coding-standards", "tdd", "property-based-testing", "spec-naming", "mermaid-diagrams"]
author: "Daniel Kreuzhofer"
---

# Daniel Kreuzhofer's Kiro Coding Best Practices

## Overview

A curated set of engineering standards and conventions for consistent, high-quality software development. Covers core project rules (TDD, YAGNI, fail-fast), property-based testing guidelines, test execution workflows, spec naming conventions, and design document formatting.

These practices are opinionated and battle-tested — designed to keep codebases clean, tests meaningful, and teams aligned.

## Available Steering Files

- **project-rules** — Core engineering principles: TDD, small reversible changes, fail fast, YAGNI, security-by-default, and more
- **property-tests** — When to use property-based tests, numRuns guidelines, random data rules, and when to prefer example-based tests
- **test-execution** — Mandatory test workflow, commands for Jest/Vitest, log analysis, and test cleanup patterns
- **spec-naming-convention** — Numbered kebab-case spec naming pattern with rules for finding the next number
- **design-doc-diagrams** — Mermaid diagram requirements for design documents

## Quick Reference

| Topic | Key Rule |
|-------|----------|
| Testing | Write tests first. Don't claim done unless tests pass. |
| Changes | Small, reversible, observable diffs. |
| Errors | Fail fast. No silent fallbacks. |
| Complexity | Simplest solution that meets current requirements. |
| Security | All external input is untrusted. Safe defaults. |
| Property tests | Default `numRuns: 3`. Prefer example-based when possible. |
| Spec naming | `NNN-kebab-name` (three-digit prefix). |
| Diagrams | Mermaid only. No ASCII art. |
