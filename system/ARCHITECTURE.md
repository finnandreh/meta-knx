# Architecture

## Topology Summary
- CAN bus: primary deterministic communication backbone for core control.
- ESP32 workers: distributed node set handling sensing/actuation and local logic.
- ESP32 masters (x3): supervisory coordination, resilience, and policy control.
- Optional transports: ESP-NOW for local wireless edge, Bluetooth for setup/service.
- Optional PC/server: configuration, logging, visualization, update orchestration.

## Layer Model
1. Physical/Link Layer
   - CAN bus (core)
   - ESP-NOW/Bluetooth (optional adjunct)
2. Transport/Message Layer
   - Structured, versioned command/event/state messages
3. Control Layer
   - Local node state machines
   - Master coordination and failover
4. Service Layer
   - Diagnostics, logging, configuration workflows
5. Engineering Layer (optional PC/server)
   - Fleet visibility and operator tooling

## Supervisory Resilience Concept
- Three master/supervisor nodes provide redundancy.
- One active coordinator at a time for bounded domains where required.
- Others monitor health and can assume responsibility on failure conditions.
- Arbitration and leadership transitions must be deterministic.

## Failure Domains
- Node failure
- Segment communication degradation
- Optional transport outage
- PC/server unavailability

Architecture goal: contain each failure domain and preserve essential control behavior.

## Control Path Expectations
- Critical commands and state updates traverse CAN first.
- Optional transports carry non-critical workflows or edge adapters.
- PC/server interactions never become mandatory in runtime control loops.

## Interface Boundaries
- Node-local control logic is private.
- Inter-node behavior is exposed only through message contracts.
- Supervisor logic is explicit and versioned.

## Design Rules
1. Keep timing-sensitive control on deterministic paths.
2. Declare all assumptions on clock/timing tolerance.
3. Use idempotent handling where retries are expected.
4. Isolate optional features from core safety/control paths.

## Architecture Artifacts to Maintain
- Node class definitions (`NODE_CLASSES.md`)
- Protocol and message conventions (`PROTOCOLS.md`)
- Subsystem framework instances from `/frameworks`
