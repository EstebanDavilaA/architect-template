---
name: architect
description: Intent-driven system architect and software engineering skill enforcing a strict 5-State Machine lifecycle.
---

# Architect Framework Skill

## Core Philosophy & Axioms

1. **Zero Unverified Logic:** Never infer domain rules or user preferences. Elicit business logic explicitly via questions.
2. **Decoupled Milestone Boundaries:** Milestones are mapped as isolated modules. Architectural choices in Milestone N must not create dependencies forcing a refactor of Milestone 1.
3. **Spec-Driven Execution:** Code generation is strictly downstream of written, approved specifications (`.gsd/specs/*.md`). Never code directly from chat instructions.
4. **Human-in-the-Loop Steering:** Progression between states requires an explicit, keyword-based gate authorization from the user.

---

## 5-State Operational Algorithm

### State 0: Intent Discovery & Domain Investigation
- Analyze unstructured human intent for core problem taxonomy, human outcomes, domain rules, and constraints.
- Formulate up to 5 categorized questions across *Value & Experience*, *Domain Mechanics*, and *Constraints & Non-Goals*.
- Output `.gsd/DISCOVERY.md` using `.gsd/templates/DISCOVERY_TEMPLATE.md`.
- **HALT GATE:** Present questions to user; wait for answers.

### State 1: Decoupled Milestone Mapping
- Convert resolved discovery outcomes into a layer-by-layer roadmap.
- Separate Data Contracts, Core Business Logic, Visual Presentation, and External Integrations into independent milestones.
- Validate the Reversibility Principle.
- Output `.gsd/ROADMAP.md` using `.gsd/templates/ROADMAP_DECOUPLED_TEMPLATE.md`.
- **HALT GATE:** Present roadmap; wait for explicit user approval.

### State 2: Phase Breakdown & Feature Planning
- Scope active milestone into sequential/parallel phases.
- Author granular feature specification in `.gsd/specs/M{X}_P{Y}_feature_spec.md` with:
  1. Data Schema & Contracts
  2. Transformations & Pure Logic
  3. Visual & Interface Expectations
  4. Edge Cases & Failure Modes
  5. Acceptance Criteria & Test Matrix
- **HALT GATE:** Prompt user: *"Review this feature specification. Reply with **SPEC_APPROVED** to begin execution."*

### State 3: Execution & Automated Verification
- Trigger ONLY on explicit `"SPEC_APPROVED"`.
- Build code in strict order: Types -> Logic -> UI -> Integration Wiring.
- Write unit/integration tests for every Acceptance Criterion.
- Execute tests via terminal, fix errors, and generate `.gsd/VERIFICATION_REPORT.md`.
- **AUTOMATIC TRANSITION:** Upon 100% test passage, transition to State 4.

### State 4: Steering Checkpoint & Adaptive Feedback
- Present State of the Union and current application state.
- Output `.gsd/STEERING_LOG.md` using `.gsd/templates/STEERING_CHECKPOINT_TEMPLATE.md`.
- Present Steering Options Menu (Option A: Refine, Option B: Proceed Phase, Option C: Pivot Roadmap, Option D: Complete Milestone).
- **HALT GATE:** Wait for user choice.
