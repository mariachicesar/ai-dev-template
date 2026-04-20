# Evidence Standards

> Every AI-generated change must include proof that it works.
> "It should work" is never acceptable evidence.

---

## Required Evidence by Change Type

### Code Changes (features, bug fixes, refactors)

| Evidence               | Required        | Example                                       |
| ---------------------- | --------------- | --------------------------------------------- |
| Tests pass             | ✅ Always       | `npm test` output showing green suite         |
| New tests for new code | ✅ Always       | Test file covering the added/changed behavior |
| Build succeeds         | ✅ Always       | `npm run build` exits 0                       |
| Lint passes            | ✅ Always       | No new warnings/errors from linter            |
| Manual verification    | When UI changes | Screenshot or preview URL                     |

**Minimum PR description:**

```markdown
## What

One sentence describing the change.

## Why

Link to ticket or brief rationale.

## Evidence

- [ ] Tests pass: (paste output or CI link)
- [ ] Build succeeds: (paste output or CI link)
- [ ] Preview URL: (link if applicable)

## Reasoning

Brief explanation of approach chosen and alternatives considered.
```

### Configuration Changes (env vars, build config, hosting)

| Evidence              | Required                      | Example                                      |
| --------------------- | ----------------------------- | -------------------------------------------- |
| Syntax validation     | ✅ Always                     | Config file parses without errors            |
| Build with new config | ✅ Always                     | Build succeeds with the change               |
| Preview deployment    | ✅ For hosting/deploy changes | Preview URL loads correctly                  |
| Rollback plan         | ✅ For production config      | "Revert commit X" or "Set env var back to Y" |

### Content / CMS Changes

| Evidence                  | Required                      | Example                                           |
| ------------------------- | ----------------------------- | ------------------------------------------------- |
| Content renders correctly | ✅ Always                     | Screenshot or preview URL showing the page        |
| No broken links           | ✅ For navigation/URL changes | Link checker output                               |
| SEO metadata present      | ✅ For new pages              | `<title>`, `<meta description>` visible in source |

### Database / Migration Changes

| Evidence               | Required          | Example                                  |
| ---------------------- | ----------------- | ---------------------------------------- |
| Migration runs forward | ✅ Always         | Migration command output                 |
| Migration rolls back   | ✅ Always         | Rollback command output                  |
| Data integrity check   | ✅ Always         | Query showing expected row counts/values |
| Backup taken           | ✅ For production | Backup timestamp and location            |

---

## Evidence Anti-Patterns

These do **not** count as evidence:

- ❌ "It compiles" — Compilation is necessary but not sufficient
- ❌ "It works on my machine" — Must work in CI/preview environment
- ❌ "I tested it manually" without proof — Include a screenshot or recording
- ❌ "The tests should pass" — Run them and show the output
- ❌ Empty PR description — Always include What/Why/Evidence/Reasoning

---

## AI-Specific Requirements

When an AI agent generates code:

1. **Reasoning must be explicit** — The PR description must explain _why_ this approach was chosen, not just what was done
2. **Alternatives considered** — Briefly note what other approaches were evaluated
3. **Confidence level** — If the agent is uncertain about an approach, flag it for human review
4. **Test coverage** — AI-generated code must have equal or better test coverage than human-written code in the same area
