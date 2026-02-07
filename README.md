# Daniel's Kiro Coding Best Practices

A curated set of engineering standards and conventions for consistent, high-quality software development with [Kiro](https://kiro.dev). These steering files guide Kiro's AI agent to follow battle-tested practices around TDD, security, complexity management, testing workflows, and more.

## What's Included

### Core Engineering Rules

| Steering File | What It Covers |
|---------------|----------------|
| `rule-tdd` | Test-driven development workflow |
| `rule-small-changes` | Small, reversible, observable diffs |
| `rule-fail-fast` | No silent fallbacks, explicit error handling |
| `rule-minimize-complexity` | YAGNI, no premature optimization |
| `rule-dry-with-restraint` | Reusability vs. fit-for-purpose code |
| `rule-ask-dont-assume` | Clarify ambiguity, state assumptions |
| `rule-confidence-gated-autonomy` | Scale autonomy with confidence level |
| `rule-security-by-default` | Zero trust on input, least privilege |
| `rule-dont-break-contracts` | Preserve APIs, schemas, and contracts |
| `rule-risk-scaled-rigor` | Match rigor to risk level |

### Testing & Workflow

| Steering File | What It Covers |
|---------------|----------------|
| `property-tests` | Property-based testing guidelines, numRuns, when to prefer example-based tests |
| `test-execution` | Mandatory test workflow, Jest/Vitest commands, log analysis, cleanup patterns |

### Conventions

| Steering File | What It Covers |
|---------------|----------------|
| `spec-naming-convention` | `NNN-kebab-name` numbered spec naming pattern |
| `design-doc-diagrams` | Mermaid diagrams for all design docs |

## Installation

Add this power to your Kiro workspace from the GitHub repo:

```
https://github.com/kreuzhofer/danielkreuzhofer-kiro-coding-best-practices.git
```

1. Open Kiro
2. Open the Powers panel (click the Powers icon in the sidebar)
3. Click "Add Power" and select "From Git Repository"
4. Paste the repo URL above
5. The steering files will be active in all your conversations

## Credits

Some of the DRY and TDD rules were inspired by [Matthias Jung's article on coding best practices](https://www.linkedin.com/feed/update/urn:li:activity:7424837822479769600/).

## License

MIT — see [LICENSE.md](LICENSE.md)
