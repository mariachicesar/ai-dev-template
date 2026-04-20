# Daily Summary

## Metadata

| Field             | Value            |
| ----------------- | ---------------- |
| **Name**          | daily-summary    |
| **Slash Command** | `/daily-summary` |
| **Version**       | 1.0              |
| **Requires MCP**  | GitHub, Jira     |

---

## Purpose

Generate a concise daily progress report covering commits, PRs, Jira ticket movement, and blockers for **{{GITHUB_REPO}}**.

## Inputs

- **Required:** None (defaults to today)
- **Optional:** `--date YYYY-MM-DD` (specific date), `--team @handle,@handle` (filter by team members)

## Steps

1. **Gather Git activity** — Via GitHub MCP, fetch all commits to `main`/`develop` in the last 24 hours for `{{GITHUB_REPO}}`. Include commit message, author, and files changed count.

2. **Gather PR activity** — Fetch PRs opened, merged, or closed in the last 24 hours. Note review status and any blocking reviews.

3. **Gather Jira movement** — Via Jira MCP, fetch all `{{JIRA_KEY}}` tickets that changed status today. Group by: Started, In Review, Done, Blocked.

4. **Identify blockers** — Flag any:
   - PRs open > 48 hours without review
   - Tickets marked Blocked
   - Failed CI runs on open PRs

5. **Compile report** — Format using the output template below.

6. **Verify** — Confirm commit counts match GitHub, ticket counts match Jira board.

## Output Format

```markdown
## Daily Summary — {{PROJECT_NAME}} — [Date]

### Commits (last 24h)

| Author | Message                 | Files Changed |
| ------ | ----------------------- | ------------- |
| @dev1  | Fix hero section layout | 3             |

### Pull Requests

- **Opened:** #42 — Add contact form validation (@dev1)
- **Merged:** #39 — Update API caching layer (@dev2)
- **Awaiting Review:** #40 — Refactor nav component (48h+) ⚠️

### Jira Tickets ({{JIRA_KEY}})

| Ticket           | Title             | Status Change           |
| ---------------- | ----------------- | ----------------------- |
| {{JIRA_KEY}}-123 | Homepage redesign | In Progress → In Review |

### Blockers

- ⚠️ PR #40 has no reviewers assigned (48h+)
- 🚫 {{JIRA_KEY}}-125 blocked on third-party API access

### Tomorrow

- [ ] Review PR #40
- [ ] Unblock {{JIRA_KEY}}-125
```

## Guardrails

- Never include commit diffs — summaries only
- Never expose secrets or environment variable values from commits
- If GitHub or Jira MCP is unavailable, report what you can and note the gap
