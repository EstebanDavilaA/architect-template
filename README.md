# Architect Project Seed Template

> **Intent-First, Decoupled-Milestone Architecture for Antigravity IDE**

This repository serves as a **lean seed template** for starting new software projects or onboarding existing codebases using the **Architect** framework in Antigravity. Architect prevents premature code generation by enforcing a strict 5-State Machine lifecycle across intent discovery, roadmap decomposition, specification writing, and automated verification.

---

## 🚀 How to Use This Seed Template

1. **Seed Workspace:** Copy the contents of this repository into your project directory:
   ```bash
   cp -r . /path/to/my-project/
   ```
2. **Run Unified Onboarding (`/onboard`):** Open your Agentic IDE in the new workspace and call **`/onboard`**.
3. **Select Project Context:**
   - **Option 1 (New Greenfield Project):** Routes to **`/discover`** to elicit domain mechanics and formulate State 0 questions.
   - **Option 2 (Existing Codebase):** Spawns `codebase-mapper` to audit existing files/types/tests, map layer-decoupled milestones into `.gsd/ROADMAP.md`, initialize `.gsd/STATE.json`, and present **`/steer`**.

---

## 🔄 The 5-State Machine Lifecycle

```
 [Workspace Onboarding: /onboard]
                │
     ┌──────────┴──────────┐
     ▼                     ▼
[New Project]      [Existing Codebase]
     │                     │
     ▼                     ▼
┌───────────┐      ┌───────────────┐
│  STATE 0  │      │Codebase Mapper│
│ Discovery │      │ (Audits Code) │
└─────┬─────┘      └───────┬───────┘
      │                    │
      ▼                    │
┌───────────┐              │
│  STATE 1  │ ◄────────────┘
│ Roadmap   │
└─────┬─────┘
      │
      ▼
┌───────────┐    Phase Specs
│  STATE 2  │ ─────────────────► [User Approves Spec: "SPEC_APPROVED"]
│ Planning  │
└─────┬─────┘
      │
      ▼
┌───────────┐
│  STATE 3  │ ──► [Build] ──► [Test / Verify] ──► [Verification Report]
│ Execution │
└─────┬─────┘
      │
      ▼
┌───────────┐
│  STATE 4  │ ─────────────────► Pivot Logic / Adjust Roadmap / Next Phase
│ Steering  │
└───────────┘
```

### Actionable Workflows & Slash Commands

| Command Call | Operational Focus | Primary Sub-Agent | Key Output Artifact |
|--------------|-------------------|-------------------|---------------------|
| **`/onboard`** | **Unified Project Onboarding & Context Elicitation** | `intent-discoverer` or `codebase-mapper` | `.gsd/STATE.json` |
| **`/discover`** | State 0: Intent Discovery & Domain Elicitation | `intent-discoverer` | `.gsd/DISCOVERY.md` |
| **`/map`** | State 1: Decoupled Milestone Mapping | `roadmapper` | `.gsd/ROADMAP.md` |
| **`/plan`** | State 2: Phase Breakdown & Feature Spec Authoring | `planner` | `.gsd/specs/M{X}_P{Y}_feature_spec.md` |
| **`/execute`** | State 3: Spec-Bound Code Implementation | `executor` | Source Code & Test Suite |
| **`/verify`** | Codebase Verification & Audit Pass | `verifier` | `.gsd/VERIFICATION_REPORT.md` |
| **`/steer`** | State 4: Steering Checkpoint & Adaptive Feedback | `verifier` | `.gsd/STEERING_LOG.md` |

---

## 📁 Antigravity Standard Repository Layout

```
purpose-gsd/
├── .agents/                                # Antigravity Workspace Customization Root
│   ├── AGENTS.md                          # Workspace System Directive (Rules)
│   ├── agents/                            # Dedicated State Sub-Agent Cards
│   │   ├── onboard.md                     # Onboarding Sub-Agent Card
│   │   ├── codebase-mapper.md             # Codebase Audit Sub-Agent Card
│   │   ├── intent-discoverer.md           # [STATE 0] Intent Discovery Agent
│   │   ├── roadmapper.md                  # [STATE 1] Decoupled Roadmapper Agent
│   │   ├── planner.md                     # [STATE 2] Feature Specification Planner Agent
│   │   ├── executor.md                    # [STATE 3] Spec-Bound Execution Agent
│   │   └── verifier.md                    # [STATE 3/4] Verification & Steering Agent
│   ├── skills/                            # Agent Skills
│   │   ├── onboard/SKILL.md               # Unified Onboarding & Audit Skill
│   │   ├── architect/SKILL.md             # Master Architect Framework Skill
│   │   ├── discovery/SKILL.md             # Intent Discovery Skill
│   │   ├── roadmap/SKILL.md               # Decoupled Roadmap Skill
│   │   ├── planning/SKILL.md              # Feature Spec Planning Skill
│   │   └── verification/SKILL.md          # Automated Verification Skill
│   └── workflows/                         # Easy-to-Call Action Workflows
│       ├── onboard.md                     # Unified Project Onboarding Workflow (/onboard)
│       ├── discover.md                    # State 0 Intent Discovery Workflow (/discover)
│       ├── map.md                         # State 1 Decoupled Roadmap Workflow (/map)
│       ├── plan.md                        # State 2 Feature Planning Workflow (/plan)
│       ├── execute.md                     # State 3 Code Execution Workflow (/execute)
│       ├── verify.md                      # Automated Verification Workflow (/verify)
│       └── steer.md                       # State 4 Steering Checkpoint Workflow (/steer)
├── .gsd/                                  # Framework Runtime Directory
│   ├── STATE.json                         # Persistent state machine engine (State 0)
│   ├── DISCOVERY.md                       # Active State 0 Discovery document
│   └── templates/                         # Framework templates
│       ├── DISCOVERY_TEMPLATE.md
│       ├── ROADMAP_DECOUPLED_TEMPLATE.md
│       ├── FEATURE_SPEC_TEMPLATE.md
│       ├── STEERING_CHECKPOINT_TEMPLATE.md
│       └── STATE_SCHEMA_TEMPLATE.json
├── GEMINI.md                              # Antigravity Operating Context
└── README.md                              # Lean seed template usage guide
```
