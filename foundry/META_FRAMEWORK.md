# Meta Framework

## Framework Purpose
Provide a repeatable structure for converting ideas into robust, testable subsystem increments.

## Canonical Work Package Model
Each work package must include:
1. Context
2. Scope
3. Interface contract
4. State model
5. Failure model
6. Validation plan
7. Delivery criteria

## Lifecycle Stages
1. Discover: gather constraints, dependencies, and operational risks.
2. Define: formalize subsystem boundaries and contracts.
3. Design: map states, message flow, and failure handling.
4. Validate: run unit/integration/fault scenarios.
5. Integrate: merge with neighboring subsystems.
6. Observe: monitor with diagnostics and metrics.

## Artifact Graph
- `SYSTEM_OVERVIEW.md`: platform mission and boundaries.
- `ARCHITECTURE.md`: topology, roles, and data/control paths.
- `NODE_CLASSES.md`: node responsibilities and capabilities.
- `PROTOCOLS.md`: transport and message-level conventions.
- Templates in `/frameworks`: normalized authoring structure.
- Prompt libraries in `/prompts`: generation patterns for future tasks.

## Engineering Guardrails
- Keep hard real-time or near-real-time logic isolated from non-critical services.
- Preserve deterministic control flow on CAN paths.
- Use explicit arbitration for multi-master behavior.
- Define mode transitions (normal, degraded, recovery) as state machines.

## Work Package Sizing Rules
- Should be independently implementable within a short cycle.
- Should touch limited interfaces.
- Should include complete validation for that slice.
- Should not require broad simultaneous refactors.

## Traceability Matrix (Minimum)
For each new subsystem or change, map:
- Requirement -> design section
- Design -> message/interface definition
- Interface -> test cases
- Test results -> acceptance criteria

## Quality Gates
1. Architecture gate: no resilience regressions.
2. Interface gate: versioning and compatibility stated.
3. Validation gate: normal + fault + recovery tested.
4. Operational gate: diagnostics and event reporting defined.

## Risk Categories
- Functional correctness risk.
- Timing/performance risk.
- Fault containment risk.
- Interoperability risk.
- Deployability and rollback risk.

## Completion Standard
An increment is complete only when:
- Documentation and message model are updated.
- Validation evidence exists for success and failure scenarios.
- Deployment/rollback considerations are documented.
