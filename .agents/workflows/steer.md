# Steer Workflow

**Command Trigger:** `/steer`  
**Operational State:** `STATE 4: Steering Checkpoint & Adaptive Feedback`  
**Assigned Agent:** `verifier`  
**Skill:** `skills/verification`

---

## Workflow Action Sequence

1. **Present State of the Union:**
   - Summarize built features, passed test suites, and alignment with initial human intent.

2. **Generate Steering Artifact:**
   - Create or update `.gsd/STEERING_LOG.md` using `.gsd/templates/STEERING_CHECKPOINT_TEMPLATE.md`.
   - Update `.gsd/STATE.json` with `current_state: 4`.

3. **Present Steering Options Menu:**
   - **Option A (Refine):** Submit comments/adjustments on current phase (Triggers `/plan` or `/execute`).
   - **Option B (Proceed Phase):** Advance to next Phase in current Milestone (Triggers `/plan`).
   - **Option C (Pivot Roadmap):** Adjust future Milestones based on insights gained (Triggers `/map`).
   - **Option D (Complete):** Mark Milestone complete and move to next Milestone (Triggers `/map` or `/plan`).

4. **Trigger HALT Gate:**
   - **HALT:** Wait for user choice (Option A, B, C, or D). Do not clear context or run auto-commands until directed.
