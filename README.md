# ai-agentic-workflows

Repository for GitHub Agentic Workflows (`gh-aw`) that run on the Copilot engine. Add skills under `.github/skills/` and workflows as Markdown under `.github/workflows/`. The Copilot agent and dispatcher skill created by `gh aw init` author and compile those workflows.

## Layout

- `.github/skills/` — skills the Copilot engine can load
- `.github/agents/agentic-workflows.md` — Copilot custom agent for creating and debugging workflows
- `.github/workflows/` — agentic workflow sources (`.md`) and compiled GitHub Actions files (`.lock.yml`)
- `.github/mcp.json` — local `gh aw mcp-server` tools for compile, audit, logs, inspect, and status

## Add a workflow

From this repository, with the [gh-aw extension](https://github.com/github/gh-aw) installed:

```bash
gh aw new my-workflow --engine copilot
gh aw compile
```

Or ask Copilot to use the `agentic-workflows` skill and describe the workflow. Personal repositories need a `COPILOT_GITHUB_TOKEN` secret (a fine-grained PAT with Copilot Requests set to Read) before a Copilot-engine workflow can run.
