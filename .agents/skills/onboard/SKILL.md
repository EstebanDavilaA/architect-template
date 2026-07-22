---
name: onboard
description: Onboarding and codebase mapping skill for initializing brand-new projects or auditing existing repositories into decoupled milestones.
---

# Unified Onboarding & Codebase Mapping Skill

## Operational Guidelines

### 1. Initial Elicitation Protocol
Prompt the user to determine project context:
- *"Welcome to Architect! What are we working on today?"*
  - **Option A (Brand-New Project):** Route immediately to `/discover`.
  - **Option B (Existing Codebase):** Execute the Codebase Audit Protocol below.

---

### 2. Codebase Audit Protocol (For Existing Projects)

1. **Ecosystem & Setup Analysis:**
   - Read package manifests, build scripts, configuration files, and project root documentation.

2. **4-Layer Architectural Mapping:**
   - Audit data models/types (Data Contracts layer).
   - Audit pure business logic functions & state reducers (Core Logic layer).
   - Audit UI components, pages, and layout routes (Presentation layer).
   - Audit database clients, network handlers, and API drivers (Integrations layer).

3. **Test Suite Verification:**
   - Run existing unit/integration tests to verify working vs. broken features.

4. **Framework State Initialization:**
   - Write `.gsd/ROADMAP.md` mapping existing architecture into decoupled milestones, marking verified features as `[x] Completed`.
   - Write `.gsd/STATE.json` with `current_state` pointing to the next unfulfilled phase.
   - Present the **Codebase Map & State of the Union** and transition to `/steer`.
