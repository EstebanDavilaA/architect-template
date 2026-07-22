# Map Workflow

**Command Trigger:** `/map` (or `/roadmap`)  
**Operational State:** `STATE 1: Decoupled Milestone Mapping`  
**Assigned Agent:** `roadmapper`  
**Skill:** `skills/roadmap`

---

## Workflow Action Sequence

1. **Verify Preconditions:**
   - Ensure State 0 discovery questions in `.gsd/DISCOVERY.md` are resolved.

2. **Map Decoupled Milestones:**
   - Isolate Data Contracts, Core Business Logic, Visual Presentation, and External Integrations into independent milestones.
   - Validate the Reversibility Principle.

3. **Generate Artifact:**
   - Create `.gsd/ROADMAP.md` using `.gsd/templates/ROADMAP_DECOUPLED_TEMPLATE.md`.
   - Update `.gsd/STATE.json` with `current_state: 1`.

4. **Trigger HALT Gate:**
   - Present `.gsd/ROADMAP.md` to the user.
   - Ask: *"Does this milestone sequence capture your vision, and are these boundaries sufficiently flexible?"*
   - **HALT:** Wait for explicit user authorization before proceeding to State 2 (`/plan`).
