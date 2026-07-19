# Weekly Trending Log

Newest entries on top. Anything logged here in the last 8 weeks should not
be re-suggested unless something materially changed.

---

## 2026-07-19

Scanned `github.com/trending?since=weekly` and `github.com/trending/python?since=weekly`.
`hallmark` re-appeared (now ~8,834 stars, up from ~2,274) — already logged
2026-07-15, not re-listed. Skipped as not relevant (no concrete
Kalamata/SourcingX tie): `OpenCut`, `Vibe-Trading`, `DeepTutor`, `OfficeCLI`
(seen before), `cangjie-skill`, `DesktopCommanderMCP` (redundant with
Claude Code's own terminal access), `openai/codex` (already the reviewer
agent, not a new tool to adopt), `openinterpreter`, `abseil-cpp` (seen
before), `orca` (agent-fleet orchestration, but Kalamata's own
`cappedParallel` Workflow pattern already covers this), `ui-skills`,
`nanobot`, `ai-hedge-fund`, `claude-video` (seen before), `QwenPaw`,
`ossie`, `zapret`, `lingbot-map`, `public-apis`, `grok-1`, `posthog`
(too broad a platform for the actual gap here).

1. **prefect** (~480 stars this week / mature project) — a Python workflow
   orchestration framework with built-in retries, scheduling, and
   observability. Relevant because: Kalamata's reliability layer
   (`error_handling.py`'s circuit breaker, `api_helpers.py`'s token-bucket
   rate limiting) and its Claude Code Dynamic Workflow orchestration
   (`daily-routine.js`'s hand-rolled `cappedParallel`) solve exactly what
   Prefect ships out of the box.
   Next step: not a wholesale replacement (the Workflow's agent fan-out is
   too custom to port) — but worth comparing Prefect's retry/observability
   primitives against `error_handling.py` for the plain-Python steps.
2. **claude-code-templates** (~864 stars) — a CLI for configuring and
   monitoring Claude Code setups. Relevant because: Kalamata alone runs 50+
   skills, several hooks, and multiple Dynamic Workflows under `.claude/` —
   exactly the kind of sprawl this tool is meant to audit/configure.
   Next step: point it at Kalamata's `.claude/` directory and see if it
   flags stale or unused skills/hooks worth cleaning up.
3. **graphify** (~8,611 stars) — turns a codebase into a queryable
   knowledge graph for AI coding assistants. Relevant because: SourcingX's
   `dashboard.py` is a single ~7,300-line file, and both projects have two
   AI agents (Claude + Codex) working the same large codebase — a
   persistent semantic map could sharpen how fast either agent locates the
   right call site.
   Next step: try it on SourcingX's `dashboard.py` and see if it
   meaningfully speeds up context-gathering before a change, vs. plain grep.

Honorable mention: **spec-kit** (~2,724 stars) — a spec-driven-development
toolkit. Kalamata already writes extensive `PLAN-*.md` docs
(`PLAN-adaptive-search-v3.md`, `PLAN-learn-from-winners.md`, etc.) before
big changes — spec-kit might formalize a pattern that's already informally
in use. Not in the top 3 only because the informal version is already
working.

---

## 2026-07-15

Scanned `github.com/trending?since=weekly`. Most of this week's list is
generic AI-agent/design tooling with no clear tie to sourcing — skipped
`abseil-cpp`, `OfficeCLI`, `CubeSandbox`, `claude-video`, `impeccable`,
`astryx`, `bun`, `argo-cd`, `pentagi`, `meetily`, `archify` (no concrete
Kalamata/SourcingX pain point).

1. **codex-plugin-cc** (~2,063 stars) — lets Codex run directly inside
   Claude Code for code review, instead of round-tripping through GitHub PR
   comments. Relevant because: SourcingX's `CLAUDE.md` already documents
   exactly this loop by hand ("Claude opens a PR → Codex reviews on GitHub →
   Claude reads PR comments and fixes"). This plugin could collapse that
   into one session instead of a GitHub round-trip.
   Next step: try it on one SourcingX PR and see if it saves the
   context-switch without losing review quality.
2. **hallmark** (~2,274 stars) — a skill that flags AI-generated-content
   "tells" (patterns, tone) in Claude/Cursor output. Relevant because: both
   projects generate candidate-facing outreach text — `email_generator.py`,
   `opener-writer` (Kalamata), `email-subject-line` /
   `email-personal-note` (SourcingX) — where sounding like generic AI slop
   directly hurts reply rates.
   Next step: run it over a batch of recent generated openers/emails and
   see what patterns it flags before shipping the next batch.
3. **TencentDB-Agent-Memory** (~1,790 stars) — a local long-term memory
   system for AI agents with no external dependencies. Relevant because:
   Kalamata already built a bespoke cross-run memory system
   (`sourcer_memory.py` / "sourcer's brain"), and SourcingX explicitly does
   NOT persist screening results today ("each JD gets a fresh evaluation").
   Worth comparing against the homegrown system, or as a lighter-weight
   option for giving SourcingX itself a screening-memory layer.
   Next step: skim its memory model against `sourcer_memory.py`'s — worth
   adopting only if it's genuinely simpler, not just different.

Honorable mention (didn't make top 3): **OmniRoute** (~4,297 stars) — AI
gateway with multi-provider routing + token-cost optimization. Both
projects juggle OpenAI + Claude + several paid data APIs and track usage by
hand (`usage_tracker.py`) — worth a second look if the top 3 don't pan out.
