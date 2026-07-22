# Verify Workflow

**Command Trigger:** `/verify` (or `/verification`)  
**Operational Context:** Automated State 3 Verification or On-Demand Codebase Audit  
**Assigned Agent:** `verifier`  
**Skill:** `skills/verification`

---

## Workflow Action Sequence

1. **Identify Audit Target:**
   - Locate active feature specification (`.gsd/specs/M{X}_P{Y}_feature_spec.md`), active phase source code, or targeted codebase area requiring verification.

2. **Automated Test Execution & Build Verification:**
   - Execute project unit/integration test commands via terminal tooling.
   - Audit test results against Acceptance Criteria & Test Matrix.

3. **Goal-Backward Codebase Audit:**
   - Verify code implementation against spec contracts.

4. **Generate Verification Report:**
   - Create or update `.gsd/VERIFICATION_REPORT.md` detailing build status, test logs, acceptance criteria coverage, and diff summary.

5. **Transition Routing:**
   - **If 100% Test Pass:** Automatically proceed to `/steer`.
   - **If Test Failures / Gaps:** Output failure evidence and return to `/execute` or `/plan` for targeted remediation.
