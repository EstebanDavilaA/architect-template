---
name: planning
description: Feature specification authoring and phase planning skill.
---

# Feature Specification Planning Skill

## Operational Guidelines

1. **Atomic Phase Scope:**
   - Scope active milestone into focused, sequential/parallel phases.

2. **Feature Spec Authoring:**
   - Write `.gsd/specs/M{X}_P{Y}_feature_spec.md` containing 5 mandatory sections:
     - **Section 1:** Overview & Objective
     - **Section 2:** Data Schema & Contracts (interfaces, pre-conditions, invariants)
     - **Section 3:** Transformations & Pure Logic (deterministic input/output rules)
     - **Section 4:** Visual & Interface Expectations (layouts, events, states)
     - **Section 5:** Edge Cases & Failure Modes (limits, error recovery)
     - **Section 6:** Acceptance Criteria & Test Matrix (verifiable assertions)

3. **HALT Control:**
   - Never generate production code during planning. Wait for explicit user authorization `"SPEC_APPROVED"`.
