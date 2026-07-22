# Execute Workflow

**Command Trigger:** `/execute`  
**Operational State:** `STATE 3: Execution & Automated Verification`  
**Assigned Agent:** `executor` & `verifier`  
**Skill:** `skills/verification`

---

## Workflow Action Sequence

1. **Verify Preconditions:**
   - Confirm explicit user input containing `"SPEC_APPROVED"` is received.

2. **Spec-Bound Construction (Layered Order):**
   - Step 1: Types, Interfaces, Data Models
   - Step 2: Core Logic Engine & Transformations
   - Step 3: UI / Component Binding (if applicable)
   - Step 4: Event Handling & Integration Wiring

3. **Automated Test Generation & Build Verification:**
   - Write unit and integration tests for every Acceptance Criterion in the feature spec.
   - Run test suite via terminal tooling.

4. **Trigger Verification:**
   - Execute `/verify` to audit test passage, compile `.gsd/VERIFICATION_REPORT.md`, and transition to `/steer`.
