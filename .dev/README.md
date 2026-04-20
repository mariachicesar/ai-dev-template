# AI Development Infrastructure

This directory contains shared AI agent conventions, skills, and evidence standards for **{{PROJECT_NAME}}**.

## Structure

```
.dev/
├── README.md              ← You are here
├── skills/                ← Reusable skill definitions for AI agents
│   ├── _template.md       ← Guide for writing new skills
│   ├── daily-summary.md   ← Daily progress summary
│   └── gap-analysis.md    ← Sprint/backlog gap analysis
└── evidence/
    └── standards.md       ← Evidence requirements for AI-generated work
```

## Quick Start

1. Copy this `.dev/` folder + `CLAUDE.md` + `.claude/` into your project root
2. Replace all `{{PROJECT_NAME}}` placeholders with your project name
3. Replace `{{JIRA_KEY}}` with your Jira project key (e.g., `METH`)
4. Replace `{{GITHUB_REPO}}` with your GitHub repo (e.g., `org/repo-name`)
5. Copy `.env.example` to `.env` and fill in your MCP tokens
6. Add project-specific skills to `.dev/skills/`

## Conventions

- All skills follow the format defined in `skills/_template.md`
- Evidence standards apply to every AI-generated PR
- Skills are referenced from `CLAUDE.md` slash commands
