# Expansion Request Patterns

## Goal
Guide safe and coherent system growth without architectural drift.

## Pattern 1: Protocol Expansion
```text
Propose protocol expansion for <new capability>.

Include:
- new message types and schemas
- backward compatibility approach
- migration/rollout strategy
- validation for mixed-version operation
```

## Pattern 2: New Node Class or Variant
```text
Evaluate adding node class/variant <name>.

Assess:
- role boundaries
- interaction with masters/workers
- failure containment
- commissioning/service implications
```

## Pattern 3: Optional Transport Adoption
```text
Plan adding optional transport <ESP-NOW/Bluetooth/other> for use case <x>.

Constraints:
- no core control dependency
- isolation from critical CAN flows
- explicit fallback if transport unavailable
```

## Pattern 4: Supervisor Strategy Evolution
```text
Propose updates to 3-master supervisory strategy for <need>.

Must describe:
- arbitration/leadership behavior
- split-brain prevention approach
- state convergence expectations
- recovery testing strategy
```

## Pattern 5: PC/Server Capability Add-on
```text
Design PC/server feature <feature> as a non-essential support capability.

Include:
- data ingest/command boundaries
- offline behavior guarantees
- operator workflows
- security and audit considerations
```
