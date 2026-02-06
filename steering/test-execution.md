# Test Execution

## Mandatory Workflow

**1. Run tests → log file (ALWAYS):**
```bash
npm test -- --runInBand > /tmp/{SPEC_NUMBER}-test-output.log 2>&1
```

**2. Analyze log:**
```bash
grep "FAIL" /tmp/{SPEC_NUMBER}-test-output.log
grep "●" /tmp/{SPEC_NUMBER}-test-output.log | head -30
```

**3. Fix & verify individual files:**
```bash
npm test -- path/to/test.ts --runInBand
```

**4. Re-run full suite → log file**

## Commands

| Type | Command |
|------|---------|
| Backend (Jest) | `cd api && npm test -- --runInBand` |
| Frontend (Vitest) | `cd frontend && npm test` |
| Single file | `npm test -- path/to/file.test.ts --runInBand` |

## Rules

- ✅ Always `--runInBand` (prevents DB conflicts)
- ✅ Logs in `/tmp/` only
- ❌ Jest has no `--run` flag (Vitest only)
- ❌ Never `deleteMany({})` without `where` clause

## Test Cleanup

```typescript
// ✅ Correct
await db.account.deleteMany({ where: { id: testId } });

// ❌ Wrong - deletes ALL data
await db.account.deleteMany({});

// ✅ Best - use helper
import { cleanupTestDb } from '../helpers/testDb';
await cleanupTestDb();
```
