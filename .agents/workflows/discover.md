# Discover Workflow

**Command Trigger:** `/discover`  
**Operational State:** `STATE 0: Intent Discovery & Domain Investigation`  
**Assigned Agent:** `intent-discoverer`  
**Skill:** `skills/discovery`

---

## Workflow Action Sequence

1. **Parse User Intent:**
   - Extract core problem taxonomy, intended human outcomes, domain rules, and contextual boundaries from the user's prompt.
   - Do NOT propose tech stacks or write production code.

2. **Formulate High-Leverage Questions:**
   - Formulate up to 5 categorized open questions across *Value & Experience*, *Domain Mechanics*, and *Constraints & Non-Goals*.

3. **Generate Artifact:**
   - Create or update `.gsd/DISCOVERY.md` using `.gsd/templates/DISCOVERY_TEMPLATE.md`.
   - Update `.gsd/STATE.json` with `current_state: 0`.

4. **Trigger HALT Gate:**
   - Present `.gsd/DISCOVERY.md` to the user. Ask the user to answer the open domain questions.
   - **HALT:** Wait for user responses before proceeding to State 1 (`/map`).
