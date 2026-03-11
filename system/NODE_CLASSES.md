# Node Classes

## Purpose
Define canonical node roles to keep subsystem design consistent across expansions.

## Class A: Master/Supervisor Node (ESP32)
### Count
- 3 nodes

### Responsibilities
- Health monitoring of critical nodes and links
- Coordination and policy arbitration
- Leadership/failover participation
- Global state summarization for critical domains

### Constraints
- Must tolerate peer loss and continue coordinated supervision.
- Must expose observable leadership and health status.

## Class B: Control Worker Node (ESP32)
### Responsibilities
- Local control loops for sensors/actuators
- Execution of bounded commands
- Local fallback behavior during transient comms disruptions

### Constraints
- Must fail-safe or fail-operational per subsystem policy.
- Must publish explicit local state and fault indicators.

## Class C: Edge Wireless Adapter Node (Optional ESP32)
### Responsibilities
- Bridge ESP-NOW edge devices into core message model
- Enforce filtering/rate-limits and normalization

### Constraints
- Must not destabilize CAN traffic or core control loops.
- Failure should isolate to edge capability loss only.

## Class D: Service/Commissioning Node (Optional Bluetooth Path)
### Responsibilities
- Setup, maintenance, diagnostics handoff
- Controlled service mode operations

### Constraints
- Service access must be gated and auditable.
- Service mode must not silently weaken safety behavior.

## Class E: PC/Server Companion (Optional)
### Responsibilities
- Config generation and deployment support
- Logging, dashboards, analytics
- Engineering tooling and fleet-level visibility

### Constraints
- Outage must not disable essential house-control operation.
- Commands from this layer must follow same contract rules.

## Cross-Class Contract Rules
1. All external interactions are message-based and versioned.
2. Health/state reporting is mandatory for critical nodes.
3. Fault states are explicit and machine-readable.
4. Recovery procedures are documented per class.

## Required Metadata Per Node
- Node class and firmware version
- Capability profile
- Health heartbeat profile
- Supported message schema versions
- Recovery behavior policy
