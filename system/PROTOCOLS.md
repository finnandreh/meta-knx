# Protocols

## Intent
Define protocol and message conventions for resilient, evolvable communication across embedded and optional support layers.

## Transport Roles
### CAN (Primary)
- Deterministic backbone for essential control and state coordination.
- Prioritized traffic classes recommended for critical commands/events.

### ESP-NOW (Optional)
- Local wireless edge integration path.
- Use for non-critical or adapter-gated interactions.

### Bluetooth (Optional)
- Service/setup and commissioning workflows.
- Avoid runtime dependency for core control.

### PC/Server Link (Optional)
- Configuration, telemetry ingestion, dashboards, update support.
- Must remain non-blocking for embedded core logic.

## Message Contract Baseline
Each message should define:
- `schema_version`
- `message_type`
- `source_node`
- `target_scope` (node, class, domain, broadcast)
- `timestamp` or sequence marker
- `payload`
- `integrity metadata` (as needed)

## Message Categories
- `command`: requests an action
- `event`: reports notable change
- `state`: periodic or on-change status snapshot
- `fault`: error/degraded condition notification
- `service`: maintenance/commissioning operations

## Reliability Patterns
- Idempotent command handling for retried operations.
- Correlation identifiers for request/response flows.
- Bounded retries with timeout and fallback behavior.
- Duplicate detection where command replay is plausible.

## Versioning Rules
1. Every schema change increments version according to compatibility impact.
2. Backward-compatible additions use optional fields.
3. Breaking changes require migration strategy and staged rollout plan.
4. Unknown optional fields must be safely ignored.

## Timing and Health
- Define heartbeat cadence per critical class.
- Define stale-state thresholds.
- Define failover trigger criteria and stabilization windows.

## Security and Access (Baseline)
- Restrict service-mode operations to authorized workflows.
- Separate commissioning privileges from normal runtime control.
- Track audit events for high-impact commands.

## Validation Expectations
- Validate normal traffic under expected load.
- Validate behavior under packet loss/drop simulation.
- Validate failover and rejoin synchronization.
- Validate schema compatibility across version boundaries.
