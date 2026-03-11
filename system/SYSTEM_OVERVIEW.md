# System Overview

## Mission
Build a resilient distributed embedded house-control platform that maintains core operation under partial failures and without dependence on an online PC/server.

## System Scope
- Wired backbone: CAN bus
- Compute/control fabric: distributed ESP32 nodes
- Supervisory resilience: 3 ESP32 master/supervisor nodes
- Optional edge links: ESP-NOW and Bluetooth
- Optional support plane: PC/server for engineering and operations support

## Primary Goals
1. Reliable local control of essential house functions.
2. Graceful degradation under node/link failures.
3. Deterministic and observable behavior.
4. Expandability through modular subsystem patterns.

## Essential vs Optional Functions
### Essential
- Core sensing and actuation paths
- Local supervisory coordination
- Safety and fallback logic

### Optional
- Dashboarding and historical analytics
- Bulk configuration workflows
- Engineering diagnostics UI
- Over-the-air update orchestration support

## Operating Modes
- `normal`: all core nodes and backbone operational.
- `degraded`: one or more nodes/links unavailable, core control retained.
- `recovery`: rejoin/resync operations after transient fault.
- `service`: controlled maintenance/setup mode.

## Baseline Constraints
- Core control must not require internet or cloud services.
- PC/server outages must not disable essential behaviors.
- Message contracts and node roles must be version-aware.
- Fault detection and recovery must be explicit and testable.

## Expected Evolution Path
1. Stand up deterministic core control slices.
2. Add subsystem frameworks with strict contracts.
3. Expand optional edge/service channels.
4. Add advanced observability and engineering tooling.

## Success Criteria
- Core house-control behavior survives representative failure scenarios.
- Multi-master supervisory behavior prevents single-point control failure.
- New features integrate via documented templates and validation plans.
