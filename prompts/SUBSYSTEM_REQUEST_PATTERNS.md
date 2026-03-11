# Subsystem Request Patterns

## Goal
Provide precise request formats for subsystem-level planning and implementation.

## Pattern 1: Subsystem Definition
```text
Define subsystem <name> using the subsystem framework template.

Must include:
- scope boundaries
- interfaces
- state machine
- failure/recovery logic
- acceptance criteria
```

## Pattern 2: Interface Contract Refinement
```text
Refine interfaces for subsystem <name>.

Focus on:
- message directions and timing
- idempotency and retries
- compatibility versioning
- fault signaling semantics
```

## Pattern 3: Node Role Allocation
```text
Map subsystem <name> responsibilities across node classes.

Include:
- which functions run on worker nodes
- supervisor/master responsibilities
- optional edge/service responsibilities
- fallback behavior when a class becomes unavailable
```

## Pattern 4: Minimal Prototype Slice
```text
Design the smallest runnable prototype slice for subsystem <name>.

Constraints:
- isolate one critical flow
- include one fault case
- produce measurable pass/fail outputs
```

## Pattern 5: Implementation Prompt Generation
```text
Generate implementation prompts for subsystem <name> in 3-7 tasks.

Each task must specify:
- code target
- interface expectations
- tests
- done criteria
```
