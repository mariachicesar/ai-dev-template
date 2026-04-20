# Skill Template

> Copy this file and rename it to create a new skill.
> Replace all content below the `---` line.

## Metadata

| Field             | Value                                  |
| ----------------- | -------------------------------------- |
| **Name**          | skill-name                             |
| **Slash Command** | `/skill-name`                          |
| **Author**        | Your Name                              |
| **Version**       | 1.0                                    |
| **Requires MCP**  | (list required MCP servers, or "None") |

---

## Purpose

One sentence: what does this skill do and when should it be used?

## Inputs

List what the agent needs before running this skill:

- **Required:** (e.g., sprint number, date range, repo name)
- **Optional:** (e.g., specific team filter, output format)

## Steps

Number each step. Be explicit about what the agent should do:

1. **Gather context** — Describe what to read/fetch
2. **Analyze** — Describe the analysis or transformation
3. **Output** — Describe the expected output format
4. **Verify** — Describe how to confirm the output is correct

## Output Format

Describe or show a template of the expected output:

```markdown
## [Skill Name] — [Date/Context]

### Section 1

- Bullet points of findings

### Section 2

- More findings

### Action Items

- [ ] Item 1
- [ ] Item 2
```

## Guardrails

List constraints and safety rules for this skill:

- Never do X
- Always verify Y before Z
- If [condition], stop and ask the user

## Examples

### Example 1: [Scenario]

**Input:** `/skill-name --param value`
**Output:** (brief description or snippet)

---

## Changelog

| Version | Date       | Change          |
| ------- | ---------- | --------------- |
| 1.0     | YYYY-MM-DD | Initial version |
