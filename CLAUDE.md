# {{PROJECT_NAME}} — AI Agent Configuration

> This file is loaded automatically by Claude Code and referenced by VS Code Copilot.
> It defines how AI agents should behave in this repository.

---

## 1. Project Overview

- **Project:** {{PROJECT_NAME}}
- **Repo:** {{GITHUB_REPO}}
- **Stack:** {{STACK_DESCRIPTION}}
- **Hosting:** {{HOSTING_PLATFORM}}
- **Jira:** {{JIRA_KEY}} project

---

## 2. Five Core Principles

### Principle 1 — Plan First

Never start coding without a plan. Before any multi-step task:

1. Read the task/ticket fully
2. Write a brief plan (3-7 bullet points) in a `tasks/` file or inline
3. Get confirmation if the plan changes scope
4. Only then start implementation

Plans prevent wasted cycles and make your reasoning auditable.

### Principle 2 — Subagent Strategy

Use subagents for parallelizable, well-scoped work:

- **When to spawn:** Research tasks, file searches across large codebases, independent test runs
- **When NOT to spawn:** Sequential edits to the same file, tasks requiring shared state
- **Always:** Give subagents explicit, self-contained prompts with all context they need
- **Never:** Assume subagents share memory with the parent agent

### Principle 3 — Self-Improvement

After every non-trivial task, reflect:

- What worked well?
- What took longer than expected?
- Should a new skill be created for this pattern?

Log insights to `tasks/` or propose updates to `.dev/skills/`. The system gets better over time only if you feed it.

### Principle 4 — Verification

Every change must be verified before considering it done:

- **Code changes:** Run the relevant test suite. If no tests exist, write them first.
- **Config changes:** Validate syntax (`nuxt build`, `wp-cli check`, etc.)
- **Deployments:** Check the preview URL, not just the deploy log
- **Data changes:** Verify with a query, not just the migration script output

"It should work" is never evidence. Show the proof.

### Principle 5 — Elegance

Prefer the simplest solution that fully solves the problem:

- Don't over-engineer for hypothetical future requirements
- Don't add abstractions until the third repetition
- Don't leave dead code, commented-out blocks, or TODO placeholders
- Match the existing code style — consistency beats personal preference

---

## 3. Repository Structure

```
{{PROJECT_NAME}}/
├── CLAUDE.md              ← This file
├── .dev/                  ← AI infrastructure (skills, evidence, conventions)
├── .claude/               ← Claude Code settings
├── tasks/                 ← Task plans and logs
├── .env.example           ← Required environment variables
└── ... (project source)
```

---

## 4. MCP Servers

Configure these in your Claude Code or VS Code settings:

| Server            | Purpose                             | Notes                       |
| ----------------- | ----------------------------------- | --------------------------- |
| GitHub            | Issues, PRs, code search            | `{{GITHUB_REPO}}`           |
| Jira              | Ticket management                   | Project key: `{{JIRA_KEY}}` |
| Vercel            | Deployments, env vars, preview URLs | —                           |
| Google Ads        | Read-only campaign reporting        | **Never write**             |
| {{CMS_NAME}} REST | Content queries                     | —                           |

---

## 5. Slash Commands

| Command          | Skill File                     | Description                         |
| ---------------- | ------------------------------ | ----------------------------------- |
| `/daily-summary` | `.dev/skills/daily-summary.md` | Generate daily progress report      |
| `/gap-analysis`  | `.dev/skills/gap-analysis.md`  | Analyze sprint gaps against backlog |

> Add project-specific commands below this line.

---

## 6. Guardrails

- **Content sync direction:** Production → Staging only. Never reverse.
- **Google Ads:** Read-only. No campaign modifications.
- **Destructive commands:** Never run `rm -rf`, `git push --force`, `git reset --hard`, or `DROP TABLE` without explicit user confirmation.
- **Secrets:** Never log, print, or commit tokens/passwords. Use `.env` and reference by variable name only.
- **Branch protection:** Never push directly to `main`/`master`. Always use feature branches + PRs.

---

## 7. Evidence Standards

See `.dev/evidence/standards.md` for full requirements. Summary:

- Every PR must include proof that the change works (test output, screenshots, or deploy preview URL)
- AI-generated code must include the reasoning in the PR description
- No "it compiles" as sole evidence

---

## 8. Adding New Skills

See `.dev/skills/_template.md` for the skill authoring guide.
