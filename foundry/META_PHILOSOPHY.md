# Meta Philosophy

## Purpose
This repository is a persistent meta-foundry for building a resilient embedded house-control platform in controlled, testable increments.

This file defines the doctrine that all future planning, architecture, implementation, and validation artifacts must follow.

## Core Intent
- Keep house-control fundamentals operational without dependency on a PC/server.
- Favor deterministic behavior and graceful degradation over feature richness.
- Build in small slices that can be verified independently.
- Make every expansion consistent with shared principles, message contracts, and safety expectations.

## Non-Negotiable Principles
1. Safety first.
2. Local autonomy first.
3. Determinism over convenience.
4. Explicit state models over hidden behavior.
5. Incremental evolution over monolithic redesign.
6. Verifiability over assumptions.

## Operating Doctrine
### 1. Embedded-First Control
- Essential control loops and fail-safe logic live on embedded nodes.
- PC/server is additive for observability, analytics, and engineering support.

### 2. Resilience Through Distribution
- Use multiple master/supervisor nodes with bounded responsibilities.
- Eliminate single-point dependency for essential operation.
- Define takeover/election/fallback behavior explicitly.

### 3. Bounded Interfaces
- Every subsystem has a clear contract: inputs, outputs, timing, error behavior.
- No subsystem reaches into another subsystem's internals.

### 4. Stable Message Semantics
- Messages are versioned and explicitly typed.
- Backward compatibility is designed, not accidental.
- Unknown fields must be tolerated where possible.

### 5. Observability by Design
- Add diagnostics, state reporting, and fault counters from day one.
- Make degraded modes visible and machine-detectable.

### 6. Test Before Integrate
- Validate each node/subsystem in isolation.
- Define failure-injection and recovery tests before broad integration.

## Quality Heuristics
- Prefer simple protocols and state machines over opaque abstractions.
- Prefer idempotent command handling.
- Prefer timeouts, retries, and bounded queues over unbounded waiting.
- Prefer explicit recovery paths over reboot-only recovery.

## Layered Responsibility
- CAN bus: deterministic wired backbone for core control and inter-node coordination.
- ESP32 nodes: local control, sensing/actuation, and distributed intelligence.
- Supervisor masters (3x): orchestration, consensus/failover, cross-zone policy enforcement.
- Optional ESP-NOW/Bluetooth: edge onboarding, service flows, temporary extensions.
- Optional PC/server: configuration, fleet insights, dashboards, updates, engineering tooling.

## Expansion Rules
Any new feature or architecture change must answer:
1. What safety or resilience risk does this introduce?
2. How does this behave when network segments fail?
3. Does essential operation continue without PC/server?
4. What versioning and compatibility strategy is used?
5. How is this validated, including fault injection?

## Anti-Patterns to Avoid
- Coupling essential logic to cloud/PC availability.
- Hidden global state and implicit cross-node assumptions.
- Protocol changes without version and migration strategy.
- Feature additions without degraded-mode behavior definition.
- Logging-only error handling with no recovery behavior.

## Definition of Done for Any Increment
- Clear scope with explicit interfaces.
- Updated architecture notes and message model.
- Validation plan with normal and fault scenarios.
- Acceptance criteria include degraded/offline behavior.
