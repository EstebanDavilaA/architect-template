# Plan Workflow

**Command Trigger:** `/plan`  
**Operational State:** `STATE 2: Phase Breakdown & Feature Planning`  
**Assigned Agent:** `planner`  
**Skill:** `skills/planning`

---

## Workflow Action Sequence

1. **Verify Preconditions:**
   - Ensure roadmap is authorized and active milestone is selected.

2. **Phase Breakdown & Feature Spec Authoring:**
   - Scope active milestone into sequential/parallel phases.
   - Write feature specification in `.gsd/specs/M{X}_P{Y}_feature_spec.md` with:
     - Data Schema & Contracts
     - Transformations & Pure Logic
     - Visual & Interface Expectations
     - Edge Cases & Failure Modes
     - Acceptance Criteria & Test Matrix

3. **Generate Artifact:**
   - Write `.gsd/specs/M{X}_P{Y}_feature_spec.md` using `.gsd/templates/FEATURE_SPEC_TEMPLATE.md`.
   - Update `.gsd/STATE.json` with `current_state: 2`.

4. **Trigger HALT Gate:**
   - Present Feature Spec to user.
   - Prompt: *"Review this feature specification. Reply with **SPEC_APPROVED** to begin execution, or provide feedback/adjustments."*
   - **HALT:** DO NOT WRITE A SINGLE LINE OF CODE UNTIL `"SPEC_APPROVED"` IS RECEIVED.
