# Security-by-Default

Treat all external input as untrusted. Use safe defaults and least privilege. Never weaken auth, authorization, crypto, or injection defenses without explicit instruction.

## Principles

- **Zero trust on input:** All data from users, APIs, files, and environment variables is untrusted until validated.
- **Least privilege:** Grant the minimum permissions needed. Default to deny.
- **Safe defaults:** Secure configuration out of the box. Insecure options require explicit opt-in.
- **Defense in depth:** Don't rely on a single layer of protection.

## Rules

- ✅ Validate and sanitize all external input at the boundary
- ✅ Use parameterized queries — never string-concatenate SQL or NoSQL queries
- ✅ Use established crypto libraries — never roll your own
- ✅ Default to the most restrictive permission/role
- ✅ Store secrets in environment variables or secret managers, never in code
- ❌ Never disable CSRF, CORS, or auth middleware without explicit instruction
- ❌ Never log sensitive data (passwords, tokens, PII)
- ❌ Never commit secrets, API keys, or credentials to the repository
- ❌ Never use `eval()`, `dangerouslySetInnerHTML`, or equivalent without explicit justification

```typescript
// ❌ SQL injection risk
const user = await db.$queryRaw(`SELECT * FROM users WHERE id = '${id}'`);

// ✅ Parameterized query
const user = await db.$queryRaw`SELECT * FROM users WHERE id = ${id}`;
```

## Agentic Guidance

When working autonomously:
- Never introduce a secret or credential in code — use environment variables and note it.
- When writing database queries, always use parameterized queries or the ORM's built-in methods.
- When adding API endpoints, include input validation and auth checks by default.
- If a user asks you to disable security features (CORS, auth, etc.), confirm the intent before proceeding.
- When reviewing code, flag any raw SQL, `eval()`, or unvalidated input as a security concern.
- If you're unsure whether something is a security risk, treat it as one and ask.
