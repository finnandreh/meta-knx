# Meta Skill

## Role
This meta-skill governs how future prompts, plans, and generated artifacts are produced for this platform.

It is a reusable operating skill for turning high-level requests into small, coherent, validated engineering increments.

## Skill Objectives
- Translate broad goals into bounded subsystem work packages.
- Preserve architecture integrity while allowing gradual evolution.
- Enforce shared language for nodes, messages, state, and validation.
- Prevent drift between intent, implementation, and tests.

## Required Inputs for Any Work Item
1. Problem statement and intended outcome.
2. Affected subsystem boundaries.
3. Failure/degraded-mode expectations.
4. Acceptance criteria.
5. Constraints (timing, memory, power, safety, bus load).

## Required Outputs for Any Work Item
1. Scope statement (in and out).
2. Architecture impact summary.
3. Message or interface model updates.
4. Validation plan (normal + fault paths).
5. Implementation prompt(s) for next execution step.

## Execution Cadence
1. Clarify objective.
2. Identify impacted layers.
3. Draft interface/message changes.
4. Specify state machine and failure behavior.
5. Define tests and instrumentation.
6. Generate implementation tasks.

## Skills Checklist
- Does this preserve autonomous operation without PC/server?
- Are master-node failover implications addressed?
- Is CAN bus traffic impact estimated?
- Are retry and timeout behaviors explicit?
- Are updates backward compatible or version-gated?
- Are operational diagnostics included?

## Prompt Construction Rules
- Ask for one subsystem slice at a time.
- Require explicit assumptions and unknowns.
- Require interfaces before internals.
- Require tests with negative and recovery cases.
- Require acceptance criteria tied to observable signals.

## Deliverable Format Standard
- Section 1: Intent and scope.
- Section 2: Architecture and dependency impact.
- Section 3: Interfaces/messages/state.
- Section 4: Validation and fault injection.
- Section 5: Risks and rollout notes.

## Refusal Conditions
Reject or reframe work that:
- Introduces hidden single points of failure.
- Depends on PC/server for core control.
- Lacks defined degraded-mode behavior.
- Omits validation for failure recovery.
