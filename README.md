# 🏛️ Architect Framework Seed Template

> **Intent-First, Decoupled-Milestone Architecture for Agentic IDEs** (Antigravity, Gemini, Cursor, Windsurf, Claude Code)

**Architect** is a deterministic software engineering framework for Agentic IDEs. It solves **Premature Code Generation Syndrome**—where AI agents jump straight to drafting UI files or backend boilerplate based on implicit, unverified assumptions—by enforcing a strict **5-State Machine lifecycle** across intent discovery, layer-decoupled roadmap mapping, granular feature specification, spec-bound execution, and automated verification.

---

## 🚀 Quick Start: Seeding a Project

### 1. Clone the Template
```bash
git clone https://github.com/EstebanDavilaA/architect-template.git my-new-project
cd my-new-project
```

### 2. Open in Antigravity
Open the `my-new-project` workspace in **Antigravity**. Antigravity automatically detects `.agents/AGENTS.md` and `GEMINI.md`.

### 3. Run Unified Onboarding
Type the following slash command in the chat:
```slash
/onboard
```

---

## 🔄 The 5-State Machine Lifecycle

```
                  [Workspace Onboarding: /onboard]
                                 │
                      ┌──────────┴──────────┐
                      ▼                     ▼
         [Option 1: New Project]   [Option 2: Existing Codebase]
                      │                     │
                      ▼                     ▼
         ┌──────────────────┐      ┌─────────────────┐
         │     /discover    │      │ codebase-mapper │
         │(State 0 Discovery│      │  (Audits Code)  │
         └────────┬─────────┘      └────────┬────────┘
                  │                         │
                  ▼                         │
         ┌──────────────────┐               │
         │       /map       │ ◄─────────────┘
         │ (State 1 Roadmap)│
         └────────┬─────────┘
                  │
                  ▼
         ┌──────────────────┐    Phase Specs
         │      /plan       │ ────────────────► [User Approves Spec: "SPEC_APPROVED"]
         │(State 2 Planning)│
         └────────┬─────────┘
                  │
                  ▼
         ┌──────────────────┐
         │     /execute     │ ──► [/verify] ──► [.gsd/VERIFICATION_REPORT.md]
         │(State 3 Build)   │
         └────────┬─────────┘
                  │
                  ▼
         ┌──────────────────┐
         │      /steer      │ ────────────────► Option A (Refine) / B (Next Phase) /
         │(State 4 Steering)│                  Option C (Pivot)  / D (Complete)
         └──────────────────┘
```

---

## 📖 Complete Step-by-Step Usage Guide with Examples

### Step 0: Onboarding (`/onboard`)
When you type `/onboard`, Architect asks:
> *"Welcome to Architect! How would you like to initialize this workspace?"*  
> - **Option 1 (New Project):** Routes to `/discover`.  
> - **Option 2 (Existing Codebase):** Spawns `codebase-mapper` to audit existing files/types/tests, map layer-decoupled milestones into `.gsd/ROADMAP.md`, initialize `.gsd/STATE.json`, and present `/steer`.

---

### Step 1: State 0 — Intent Discovery (`/discover`)
**Rule:** Zero code generation, zero technical stack proposals, zero file trees.

**User Input Example:**
> *"I want an audio app that helps users practice articulation for public speaking."*

**Architect Action:** Spawns `intent-discoverer` agent and generates `.gsd/DISCOVERY.md` with a maximum of 5 open, high-leverage questions across 3 buckets:

```markdown
# DISCOVERY: Articulation Trainer

## 1. Problem Taxonomy
- Core Problem Statement: Users lack real-time feedback on speaking clarity and speed.
- Intended Human Outcome: Measurable improvement in speech cadence and articulation clarity.

## 2. Open Domain Questions (Max 5)
### Value & Experience
1. What specific feedback metrics (WPM, pause frequency, filler word count) matter most to the user?

### Domain Mechanics
2. Should audio processing occur via real-time microphone stream or recorded file uploads?
3. How should articulation scoring be calculated?

### Constraints & Non-Goals
4. Is offline operation required, or are cloud API services permitted?
5. Is user account authentication out-of-scope for Milestone 1?

## 3. Answer Log
- [ ] Question 1: Pending user response
- [ ] Question 2: Pending user response
- [ ] Question 3: Pending user response
- [ ] Question 4: Pending user response
- [ ] Question 5: Pending user response
```

**HALT GATE:** Agent presents `.gsd/DISCOVERY.md` and waits for your answers before proceeding.

---

### Step 2: State 1 — Decoupled Milestone Mapping (`/map`)
**Rule:** Milestones are strictly decoupled by architectural layer. Decisions in Milestone 2 must never force a refactor of Milestone 1.

**Architect Action:** Spawns `roadmapper` agent and converts your answered discovery questions into `.gsd/ROADMAP.md`:

```markdown
# ROADMAP: Articulation Trainer

## Decoupled Milestones

### Milestone 1: Data Contracts & Pure Interfaces
- Objective: Define audio frame schemas, scoring types, and state structures.
- Verification Threshold: 100% type safety & contract test pass.

### Milestone 2: Core Logic Engine & Audio Calculations
- Objective: Build deterministic WPM calculator, pause analyzer, and articulation scoring engine.
- Verification Threshold: 100% unit test passage for logic engine (0% UI coupling).

### Milestone 3: Visual Presentation & Component Binding
- Objective: Render real-time audio visualizers, feedback dials, and controls.
- Verification Threshold: UI component integration tests pass.

### Milestone 4: External Integrations & Storage
- Objective: Wire microphone WebAudio API drivers and local session persistence.
- Verification Threshold: End-to-end integration suite pass.
```

**HALT GATE:** Agent prompts: *"Does this milestone sequence capture your vision?"* Wait for explicit authorization.

---

### Step 3: State 2 — Feature Planning (`/plan`)
**Rule:** Atomic planning for active phase. Code generation is strictly forbidden until `"SPEC_APPROVED"` is received.

**Architect Action:** Spawns `planner` agent to draft `.gsd/specs/M1_P1_feature_spec.md`:

```markdown
# FEATURE SPECIFICATION: M1_P1 - Audio Frame & Score Data Contracts

## 1. Data Schema & Contracts
export interface AudioFrame {
  timestamp: number;
  pcmData: Float32Array;
  sampleRate: number;
}

export interface ArticulationScore {
  wpm: number;
  pauseRatio: number;
  clarityScore: number;
}

## 2. Transformations & Pure Logic
- `calculateWpm(frames: AudioFrame[]): number`
- `detectPauses(frames: AudioFrame[], thresholdMs: number): PauseInterval[]`

## 3. Acceptance Criteria & Test Matrix
| ID | Requirement | Test Type | Expected Outcome |
|----|-------------|-----------|------------------|
| AC-1 | WPM Calculation | Unit Test | Returns accurate WPM within +/- 2% error |
| AC-2 | Pause Detection | Unit Test | Detects silent intervals > 500ms |
```

**HALT GATE:** Agent prompts: *"Review this feature specification. Reply with **SPEC_APPROVED** to begin execution."*

---

### Step 4: State 3 — Execution & Verification (`/execute` & `/verify`)
**Rule:** Code generation is strictly bound to approved feature specs in layered construction order: Types → Logic → UI → Wiring.

**User Input:**
```text
SPEC_APPROVED
```

**Architect Action:**
1. `executor` agent builds production source files cleanly in order:
   - Step 1: Types (`src/types/audio.ts`)
   - Step 2: Core Logic (`src/engine/scoring.ts`)
   - Step 3: Automated Unit Tests (`tests/scoring.test.ts`)
2. `verifier` agent executes `/verify` via terminal tooling.
3. Compiles `.gsd/VERIFICATION_REPORT.md`:

```markdown
# VERIFICATION REPORT: M1_P1

## Test Suite Results
- `tests/scoring.test.ts`: 12/12 PASS (100%)
- Build Compilation: SUCCESS (0 errors)

## Acceptance Criteria Audit
- AC-1 (WPM Calculation): VERIFIED
- AC-2 (Pause Detection): VERIFIED
```

**AUTOMATIC TRANSITION:** Upon 100% test passage, automatically transitions to State 4 (`/steer`).

---

### Step 5: State 4 — Steering Checkpoint (`/steer`)
**Rule:** Do not close context or advance automatically. Present State of the Union and Steering Options Menu.

**Architect Action:** Spawns `verifier` to generate `.gsd/STEERING_LOG.md` and present options:

```text
[STATE 4: Steering Checkpoint]

State of the Union: Milestone 1 Phase 1 (Data Contracts & Scoring Engine) is built and 100% verified.

Please choose one of the following steering options:

- Option A (Refine): Submit comments/adjustments on current phase.
- Option B (Proceed Phase): Advance to next Phase (P2) in active Milestone.
- Option C (Pivot Roadmap): Adjust future Milestones based on insights gained.
- Option D (Complete): Mark Milestone complete & move to next Milestone.
```

**HALT GATE:** Agent halts and waits for your selection (`Option A`, `Option B`, `Option C`, or `Option D`).

---

## 🛠️ Atomic Git Commit Protocol

Architect commits changes atomically at every state boundary and construction layer:

| Operational State | Trigger | Git Commit Message Example |
|-------------------|---------|----------------------------|
| **State 0 (Discovery)** | `.gsd/DISCOVERY.md` created | `docs(discovery): initialize State 0 questions (.gsd/DISCOVERY.md)` |
| **State 1 (Roadmap)** | `.gsd/ROADMAP.md` approved | `docs(roadmap): lock State 1 decoupled roadmap (.gsd/ROADMAP.md)` |
| **State 2 (Planning)** | Feature Spec written | `docs(spec): draft feature spec M1_P1` |
| **State 3 (Types)** | Data schemas built | `feat(M1_P1): implement data schemas & state types` |
| **State 3 (Logic)** | Business logic built | `feat(M1_P1): implement core logic engine & pure state transformations` |
| **State 3 (UI)** | UI components bound | `feat(M1_P1): bind UI components to state engine` |
| **State 3 (Verify)** | 100% test pass | `test(M1_P1): 100% test suite pass - .gsd/VERIFICATION_REPORT.md` |
| **State 4 (Steering)** | Steering decision logged | `docs(steering): log user steering decision Option B` |

---

## 📁 Repository Customization Structure (`.agents/`)

```
purpose-gsd/
├── .agents/                                # Antigravity Customization Root
│   ├── AGENTS.md                          # [RULES] Workspace Master Directive
│   ├── workflows/                         # [WORKFLOWS] Easy-to-Call Action Workflows
│   │   ├── onboard.md                     # Unified Project Onboarding (/onboard)
│   │   ├── discover.md                    # State 0 Intent Discovery (/discover)
│   │   ├── map.md                         # State 1 Decoupled Milestone Mapping (/map)
│   │   ├── plan.md                        # State 2 Phase Feature Planning (/plan)
│   │   ├── execute.md                     # State 3 Spec-Bound Execution (/execute)
│   │   ├── verify.md                      # Codebase Verification Audit (/verify)
│   │   └── steer.md                       # State 4 Steering Checkpoint (/steer)
│   ├── skills/                            # [SKILLS] Actionable Skill Packages
│   │   ├── onboard/SKILL.md               # Unified Onboarding & Audit Skill
│   │   ├── architect/SKILL.md             # Master Architect Framework Skill
│   │   ├── discovery/SKILL.md             # Intent Discovery Skill
│   │   ├── roadmap/SKILL.md               # Decoupled Roadmap Skill
│   │   ├── planning/SKILL.md              # Feature Spec Planning Skill
│   │   └── verification/SKILL.md          # Automated Verification Skill
│   └── agents/                            # [SUB-AGENTS] Dedicated State Agent Cards
│       ├── codebase-mapper.md             # Codebase Audit Agent
│       ├── intent-discoverer.md           # [STATE 0] Intent Discoverer Agent
│       ├── roadmapper.md                  # [STATE 1] Decoupled Roadmapper Agent
│       ├── planner.md                     # [STATE 2] Feature Spec Planner Agent
│       ├── executor.md                    # [STATE 3] Spec-Bound Executor Agent
│       └── verifier.md                    # [STATE 3/4] Verifier & Steering Agent
├── .gsd/                                  # Framework Runtime Engine Directory
│   ├── STATE.json                         # Persistent State Engine (current_state: 0)
│   ├── DISCOVERY.md                       # Active State 0 Discovery Document
│   └── templates/                         # Framework Templates
│       ├── DISCOVERY_TEMPLATE.md
│       ├── ROADMAP_DECOUPLED_TEMPLATE.md
│       ├── FEATURE_SPEC_TEMPLATE.md
│       ├── STEERING_CHECKPOINT_TEMPLATE.md
│       └── STATE_SCHEMA_TEMPLATE.json
├── GEMINI.md                              # Antigravity Operating Context
└── README.md                              # Seed Template Documentation
```
