# Gap Analysis

## Metadata

| Field             | Value           |
| ----------------- | --------------- |
| **Name**          | gap-analysis    |
| **Slash Command** | `/gap-analysis` |
| **Version**       | 1.0             |
| **Requires MCP**  | Jira, GitHub    |

---

## Purpose

Compare the current sprint's progress against the backlog to identify gaps, at-risk tickets, and scope creep for the **{{JIRA_KEY}}** project.

## Inputs

- **Required:** None (defaults to current active sprint)
- **Optional:** `--sprint [name/number]` (specific sprint), `--label [label]` (filter by Jira label)

## Steps

1. **Fetch sprint data** — Via Jira MCP, get all tickets in the current sprint for `{{JIRA_KEY}}`. Capture: ticket key, title, assignee, status, story points, labels.

2. **Calculate velocity snapshot** —
   - Total story points committed
   - Points completed (Done status)
   - Points in progress
   - Points not started
   - Percentage complete vs. sprint timeline percentage

3. **Identify at-risk tickets** — Flag tickets that are:
   - Not started and sprint is >50% elapsed
   - In progress for >3 days without status change
   - Unassigned
   - Missing story point estimates

4. **Check for scope creep** — Compare tickets added after sprint start vs. original commitment. List any additions.

5. **Cross-reference with PRs** — Via GitHub MCP, check if in-progress tickets have associated open PRs in `{{GITHUB_REPO}}`. Flag tickets with code work but no PR.

6. **Compile report** — Format using template below.

7. **Verify** — Confirm ticket counts match Jira board, point totals add up.

## Output Format

```markdown
## Gap Analysis — {{JIRA_KEY}} Sprint [Name] — [Date]

### Velocity Snapshot

- **Committed:** 34 points across 12 tickets
- **Completed:** 13 points (38%) — Sprint is 60% elapsed ⚠️
- **In Progress:** 13 points (5 tickets)
- **Not Started:** 8 points (3 tickets)

### At-Risk Tickets

| Ticket           | Title              | Risk                         | Assignee      |
| ---------------- | ------------------ | ---------------------------- | ------------- |
| {{JIRA_KEY}}-130 | API rate limiting  | Not started, sprint 60% done | @dev1         |
| {{JIRA_KEY}}-128 | Image optimization | In progress 4 days, no PR    | Unassigned ⚠️ |

### Scope Creep

- {{JIRA_KEY}}-135 added mid-sprint (3 points) — "Hotfix: broken checkout flow"
- Net change: +3 points over original commitment

### Missing PRs

- {{JIRA_KEY}}-128 (In Progress) — No associated PR found in {{GITHUB_REPO}}

### Recommendations

1. Reassign {{JIRA_KEY}}-128 or pair on it
2. Consider moving {{JIRA_KEY}}-130 to next sprint (8 points at risk)
3. Original commitment: 34 pts → Realistic forecast: 26 pts
```

## Guardrails

- Never modify tickets — this is a read-only analysis
- Never blame individuals — frame as team observations
- If velocity is on track, say so clearly (don't manufacture problems)
- If Jira MCP is unavailable, report from GitHub activity only and note the gap
