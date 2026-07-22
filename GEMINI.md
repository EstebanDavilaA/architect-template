# Architect — Antigravity CLI Operating Context

> **Antigravity CLI** reads `GEMINI.md` automatically for project context and loads workspace directives from `.agents/AGENTS.md`.

This context provides Antigravity with the operating instructions for **Architect**, an intent-driven system architect and software engineering framework enforcing a strict **5-State Machine lifecycle**.

## Core 5-State Machine Lifecycle

Work progresses through 5 explicit states with HALT exit gates:
0. **ONBOARDING (`/onboard`):** Prompts user to determine if workspace is greenfield (`/discover`) or existing codebase (`codebase-mapper` -> `/steer`).
1. **STATE 0 (Intent Discovery & Domain Investigation):** Sub-agent: `intent-discoverer` | Workflow: `/discover` | Skill: `skills/discovery`. Creates `.gsd/DISCOVERY.md` with max 5 open questions, zero code/tech stack selection, HALT.
2. **STATE 1 (Decoupled Milestone Mapping):** Sub-agent: `roadmapper` | Workflow: `/map` | Skill: `skills/roadmap`. Structures layer-isolated roadmap in `.gsd/ROADMAP.md`, HALT.
3. **STATE 2 (Phase Breakdown & Feature Planning):** Sub-agent: `planner` | Workflow: `/plan` | Skill: `skills/planning`. Generates binding feature specifications in `.gsd/specs/M{X}_P{Y}_feature_spec.md`, HALT for `"SPEC_APPROVED"`.
4. **STATE 3 (Execution & Automated Verification):** Sub-agents: `executor` & `verifier` | Workflows: `/execute`, `/verify` | Skill: `skills/verification`. Builds code strictly bound to approved specs, runs automated test suites, outputs `.gsd/VERIFICATION_REPORT.md`, auto-transitions to State 4 upon 100% test passage.
5. **STATE 4 (Steering Checkpoint):** Sub-agent: `verifier` | Workflow: `/steer` | Skill: `skills/verification`. Presents State of the Union, provides Steering Options Menu in `.gsd/STEERING_LOG.md`, HALT.

## Antigravity Customization Structure

- `.agents/AGENTS.md` — Workspace System Directive (Rules)
- `.agents/agents/` — Sub-Agent Cards (`intent-discoverer`, `roadmapper`, `planner`, `executor`, `verifier`, `codebase-mapper`)
- `.agents/workflows/` — Easy-to-Call Action Workflows (`onboard`, `discover`, `map`, `plan`, `execute`, `verify`, `steer`)
- `.agents/skills/` — Skills (`onboard`, `architect`, `discovery`, `roadmap`, `planning`, `verification`)
- `.gsd/STATE.json` — Persistent State Engine
