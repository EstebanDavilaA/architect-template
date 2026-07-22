---
name: verification
description: Automated test generation, build verification, and steering checkpoint auditing skill.
---

# Automated Verification & Steering Skill

## Operational Guidelines

1. **Spec-Bound Execution Verification:**
   - Verify code was built downstream of approved feature spec (`.gsd/specs/M{X}_P{Y}_feature_spec.md`).
   - Validate construction order: Types -> Logic -> UI -> Integration Wiring.

2. **Automated Test Auditing:**
   - Execute test suites using terminal commands.
   - Fix all compilation errors and test failures.
   - Write `.gsd/VERIFICATION_REPORT.md` with build logs, test results, and diff summary.

3. **Steering Checkpoint Presentation:**
   - Write `.gsd/STEERING_LOG.md` following `.gsd/templates/STEERING_CHECKPOINT_TEMPLATE.md`.
   - Present Steering Options Menu (Options A, B, C, D) and wait for user decision.
