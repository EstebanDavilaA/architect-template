# Architect Framework — Claude Code Port

Ported from the Antigravity-native `architect-template`, with two customizations:
1. A two-speed entry point (prototype-first, not spec-first-always).
2. Vertical-slice milestones (not layer-based) and independent critic verification.

## Entry point
Start with `/onboard`. It routes to:
- **`/prototype`** — raw, unvalidated idea. Minimal ceremony, fast walking skeleton.
- **`/discover`** — idea is already validated/clear enough to spec directly.
- **Existing codebase audit** — formalizes what's already there via `codebase-mapper`.

## The full lifecycle
```
/onboard → /prototype → (user validates) → /promote ─┐
                                                        │
/onboard → /discover ─────────────────────────────────┼─→ /map → /plan →
                                                                  [SPEC_APPROVED] →
                                                        /execute → /verify →
                                                        (pass) → /steer
                                                        (fail) → /diagnose → back to
                                                                 /execute, /plan, or /discover
```

## Hard rules (non-negotiable regardless of track)
1. No implementation code before either a prototype's validation target is explicit, or a spec is approved with the literal string `SPEC_APPROVED`.
2. Milestones must be **vertical slices** — a user-visible outcome — never a horizontal layer (types-only, backend-only, UI-only). See `.claude/agents/roadmapper.md`.
3. `/verify` never trusts the executor's own tests as proof of correctness. It runs three layers: executor's tests, an independent `critic` audit against the approved spec, and a regression pass across all prior milestones.
4. Any verification failure routes through `/diagnose` before any fix is attempted — implementation bug, spec error, and misunderstood intent are fixed at different layers (`/execute`, `/plan`, `/discover` respectively), and patching at the wrong layer tends to reproduce the same class of bug later.
5. `/steer` is a mandatory halt. Never auto-advance past it, even when the next step seems obvious.

## Directory reference
```
.claude/
├── skills/
│   ├── onboard/SKILL.md
│   ├── prototype/SKILL.md      ← fast track
│   ├── promote/SKILL.md        ← prototype → structured handoff
│   ├── discover/SKILL.md       ← State 0
│   ├── plan/SKILL.md           ← State 2
│   ├── execute/SKILL.md        ← State 3
│   ├── verify/SKILL.md         ← 3-layer check
│   ├── diagnose/SKILL.md       ← root-cause routing
│   └── steer/SKILL.md          ← State 4
└── agents/
    ├── codebase-mapper.md
    ├── intent-discoverer.md
    ├── prototyper.md
    ├── roadmapper.md            ← vertical-slice enforcement
    ├── planner.md
    ├── executor.md
    ├── critic.md                ← independent correctness audit
    └── verifier.md              ← steering-log summarizer

.gsd/                            ← runtime state, unchanged across IDEs
├── STATE.json
├── DISCOVERY.md
├── ROADMAP.md
├── specs/
├── CRITIC_REPORT.md
├── VERIFICATION_REPORT.md
└── STEERING_LOG.md
```

## Project-specific context
<!-- Add build commands, test commands, package manager, and any conventions below. -->
