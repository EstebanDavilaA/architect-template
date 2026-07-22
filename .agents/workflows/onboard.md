# Onboard Workflow

**Command Trigger:** `/onboard`  
**Operational Context:** Unified Project Initialization & Codebase Mapping  
**Assigned Agents:** `intent-discoverer` (Greenfield) or `codebase-mapper` (Existing Codebase)  
**Skill:** `skills/onboard`

---

## Workflow Action Sequence

1. **Initial Elicitation Prompt:**
   - Present the onboarding question to the user:
     > *"Welcome to Architect! How would you like to initialize this workspace?"*  
     > - **Option 1 (New Project):** Build a brand-new project from scratch.  
     > - **Option 2 (Existing Codebase):** Onboard and map an existing codebase or cloned repository.

2. **Branching Execution Paths:**

   - **Path A — Brand-New Project (User Selects Option 1):**
     - Automatically execute **`/discover`** (`intent-discoverer` agent) to initiate State 0 Intent Discovery & Domain Question Elicitation.

   - **Path B — Existing Codebase (User Selects Option 2):**
     - Spawn the **`codebase-mapper`** sub-agent to audit directory tree, package dependencies, data contracts, core logic, UI routes, and test suites.
     - Reverse-engineer layer-decoupled milestones into `.gsd/ROADMAP.md` and mark completed features as `[x] Completed`.
     - Initialize `.gsd/STATE.json` with `current_state` pointing to the next pending milestone/phase.
     - Present the **Codebase Map & State of the Union** to the user and trigger **`/steer`**.
