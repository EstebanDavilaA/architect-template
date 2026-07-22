---
name: discovery
description: Intent discovery and domain mechanics investigation skill for transforming unstructured intent into categorized open questions.
---

# Intent Discovery Skill

## Operational Guidelines

1. **Unstructured Intent Analysis:**
   - Parse initial prompt to identify implicit assumptions, ambiguous domain rules, and missing business logic.
   - Do NOT propose tech stacks, frameworks, databases, or directory structures during discovery.

2. **Categorized Question Elicitation (Max 5 Questions):**
   - **Bucket 1: Value & Experience** — Elicit what constitutes real-world outcome and success for the user.
   - **Bucket 2: Domain Mechanics** — Elicit exact input/output behaviors, calculations, and state transformations.
   - **Bucket 3: Constraints & Non-Goals** — Elicit operational limits and explicit out-of-scope boundaries.

3. **Artifact Formatting:**
   - Write `.gsd/DISCOVERY.md` following `.gsd/templates/DISCOVERY_TEMPLATE.md`.
   - Maintain the **Answer Log** table tracking pending vs. answered questions.
