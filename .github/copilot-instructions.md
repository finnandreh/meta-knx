# Copilot Instructions

## Foundry Operating Context
This repository is a meta-foundry for a resilient embedded house-control platform built around CAN and distributed ESP32 nodes with 3 supervisor/master nodes.

Copilot must prioritize resilience, deterministic behavior, and embedded-first operation.

## Required Context Files
Before generating substantial outputs, review:
- `foundry/META_PHILOSOPHY.md`
- `foundry/META_SKILL.md`
- `foundry/META_FRAMEWORK.md`
- `foundry/ACTIVATION_PATTERN.md`
- `system/SYSTEM_OVERVIEW.md`
- `system/ARCHITECTURE.md`
- `system/NODE_CLASSES.md`
- `system/PROTOCOLS.md`

## Core Invariants
1. Essential operation must continue without PC/server.
2. CAN is the primary control backbone.
3. Multi-master supervision resilience must be preserved.
4. Optional transports (ESP-NOW/Bluetooth) must not become core dependencies.
5. Message contracts must be explicit and versioned.

## Output Expectations
For design/planning tasks, produce:
- Scope and assumptions
- Interface/message implications
- State and failure behavior
- Validation strategy (normal + fault + recovery)
- Risks and mitigations

For implementation tasks, produce:
- Small, testable increments
- Clear done criteria
- Backward-compatible change notes
- Operational diagnostics hooks

## Preferred Working Pattern
1. Clarify request type (prototype/framework/extension/validation/operation).
2. Use matching templates in `/frameworks`.
3. Generate bounded artifacts with explicit contracts.
4. Include validation and acceptance criteria.

## Risk Checks to Apply
- Does this add a single point of failure?
- Does this require PC/server for core behavior?
- Are degraded and recovery modes explicit?
- Are timing and retry assumptions documented?
- Is version migration strategy defined?

## Style Guidelines
- Be concrete and technical.
- Avoid vague architecture prose.
- Favor tables and checklists for contracts.
- Keep proposals incremental and composable.
- Explicitly list assumptions and open questions.

## If Information Is Missing
When request context is incomplete, ask focused questions about:
- affected node classes
- required offline behavior
- failure scenarios to tolerate
- timing and safety constraints
- expected validation depth
