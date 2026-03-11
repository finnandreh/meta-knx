# System Request Patterns

## Goal
Standardize high-level system prompts so outputs are deterministic, scoped, and doctrine-compliant.

## Pattern 1: System Baseline Clarification
```text
Using foundry and system docs, produce a concise baseline of current architecture assumptions for <domain>.

Include:
- essential control path
- optional dependencies
- resilience assumptions
- open unknowns
```

## Pattern 2: New System Capability Proposal
```text
Propose how to add capability <capability> to the platform.

Constraints:
- do not break core offline operation
- preserve CAN-centric control path
- maintain multi-master resilience

Output:
1) architecture impact
2) node role impact
3) protocol/message impact
4) validation strategy
5) migration plan
```

## Pattern 3: Resilience Review Request
```text
Review the current concept for <feature> from a resilience-first perspective.

Check:
- single-point failures
- degraded-mode behavior
- recovery completeness
- observability adequacy

Return prioritized risks with mitigations.
```

## Pattern 4: Operational Readiness Request
```text
Evaluate readiness of <subsystem/system slice> for field trial.

Require:
- defined failure envelopes
- telemetry readiness
- rollback strategy
- validation evidence summary
```

## Pattern 5: Doctrine Compliance Check
```text
Validate proposal <proposal-id> against foundry doctrine.

Return:
- compliant items
- non-compliant items
- required corrections before implementation
```
