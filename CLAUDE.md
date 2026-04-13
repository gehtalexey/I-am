# CLAUDE.md

Guidance for Claude Code (and other AI assistants) working in this repository.

## Repository overview

- **Name:** I-am Sourcer
- **GitHub:** `gehtalexey/i-am`
- **Owner:** `gehtalexey`
- **Purpose:** Personal sandbox. No production code lives here yet.
- **Current state:** Effectively empty. The only tracked content is `README.md` and this file.

Because the repo has no application code, build system, tests, or CI, most sections below are intentionally short and forward-looking. **Update this file as soon as real code lands** so future sessions have accurate guidance.

## Current structure

```
.
├── CLAUDE.md   # This file
└── README.md   # One-line description of the sandbox
```

There are no packages, modules, services, scripts, or configuration files to document yet.

## When adding new code

1. Before assuming a language, framework, or layout, check whether the user has already chosen one. If not, ask.
2. Once a stack is chosen, immediately update this file with:
   - The language / framework / runtime version
   - How to install dependencies
   - How to build, run, test, lint, and format
   - The directory layout and where new code should go
3. Prefer editing existing files over creating new ones. Do not create README, docs, or scaffolding files unless the user asks for them.
4. Do not add speculative tooling (linters, formatters, CI, frameworks, dependency managers) without being asked.

## Development workflow

- **Never commit directly to `main`.** Always work on a feature branch.
- **Branch naming for AI-driven work:** `claude/<short-description>-<suffix>` — e.g. the current branch `claude/add-claude-documentation-RR0LY`.
- **Commits:** short imperative subject line; body (when present) should explain the *why*, not the *what*.
- **Do not create commits unless the user explicitly asks for them.**
- **Do not push to `main`** without explicit permission.

## Git & GitHub conventions

- The only in-scope remote repository is `gehtalexey/i-am`. Do not touch any other repo.
- First push of a new branch: `git push -u origin <branch-name>`.
- On transient network failures, retry push/fetch up to 4 times with exponential backoff (2s, 4s, 8s, 16s). Do not retry on non-network errors — diagnose instead.
- **Do not open pull requests unless the user explicitly asks.**
- Use the GitHub MCP tools (prefixed `mcp__github__`) for any GitHub interaction; there is no `gh` CLI available.

## Housekeeping rules for Claude

- Keep this file accurate. When the repository gains real structure, replace the placeholder sections above with concrete commands and paths.
- Do not introduce emojis in files unless the user asks.
- Do not add error handling, abstractions, or "future-proofing" beyond what the task requires.
- Treat this repo as a sandbox: the user may experiment freely, so avoid heavy-handed refactors unless asked.

## Open questions to clarify when real work begins

- What language / stack should the sandbox use (or is it multi-language)?
- Is there an intended first project or theme for the sandbox?
- Should a license be added?
- Are there preferences for formatters, linters, or test frameworks?
