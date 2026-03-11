# Prompt Library

## Purpose
Reusable high-quality prompt blocks for generating architecture, subsystem, implementation, and validation outputs aligned with Foundry doctrine.

## Usage Rules
1. Always include context references to `/foundry` and `/system` docs.
2. Request one bounded increment per prompt.
3. Require explicit assumptions and risks.
4. Require failure-mode and recovery behavior.
5. Require acceptance criteria and test strategy.

## Prompt Block: Subsystem Framework Draft
```text
Use the Foundry doctrine files and system context to draft a subsystem framework.

Target subsystem: <name>
Goal: <what must be achieved>
Constraints: <timing/memory/safety/bus>

Output requirements:
1) scope and boundaries
2) interface contract
3) state model
4) failure and recovery model
5) observability
6) acceptance criteria

Use frameworks/TEMPLATE_SUBSYSTEM_FRAMEWORK.md structure.
```

## Prompt Block: Message Model Draft
```text
Create a versioned message model for subsystem <name>.

Requirements:
- include message catalog
- define common envelope
- define per-message payload fields and constraints
- describe idempotency, retries, and compatibility policy
- include invalid and fault scenarios

Use frameworks/TEMPLATE_MESSAGE_MODEL.md.
```

## Prompt Block: Validation Plan
```text
Produce a validation plan for subsystem <name> version <x.y>.

Must include:
- functional tests
- fault injection tests
- failover/recovery tests
- compatibility tests
- pass/fail exit criteria

Use frameworks/TEMPLATE_VALIDATION_PLAN.md.
```

## Prompt Block: Architecture Extension
```text
Propose an architecture extension for <feature> while preserving resilience constraints.

Evaluate:
- impact on CAN backbone and node roles
- impact on multi-master resilience
- offline behavior without PC/server
- versioning and migration strategy

Return:
- proposed changes
- risks and mitigations
- phased rollout approach
- validation requirements
```

## Prompt Block: Implementation Task Breakdown
```text
Break subsystem <name> into 3-7 implementation tasks, each independently testable.

For each task include:
- objective
- touched interfaces/messages
- risks
- concrete done criteria
- tests to run
```

## Prompt Block: Copilot Operating Prompt
```text
Generate a Copilot operating prompt for implementing <subsystem/task>.

Include:
- required context documents
- coding constraints
- test-first expectations
- resilience and offline invariants
- output format expectations
```
