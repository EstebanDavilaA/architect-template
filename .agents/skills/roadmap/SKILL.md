---
name: roadmap
description: Decoupled milestone mapping and architectural layer separation skill.
---

# Decoupled Roadmap Skill

## Operational Guidelines

1. **Layer Separation Strategy:**
   - **Milestone 1 (Data Contracts):** Define pure types, interfaces, schemas, and state contracts.
   - **Milestone 2 (Core Logic Engine):** Build deterministic business logic, state reducers, and calculations. Zero UI coupling.
   - **Milestone 3 (Visual Presentation):** Implement UI components, layouts, and rendering.
   - **Milestone 4 (Integrations):** Wire external persistence drivers, network handlers, and third-party APIs.

2. **Reversibility Principle:**
   - Ensure choices in later milestones never force refactoring of earlier milestone structures.

3. **Artifact Formatting:**
   - Write `.gsd/ROADMAP.md` following `.gsd/templates/ROADMAP_DECOUPLED_TEMPLATE.md`.
   - Specify boundary interfaces and verification thresholds for every milestone.
