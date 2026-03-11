# Template: Message Model

## 1. Model Identity
- Model name:
- Domain/subsystem:
- Version:
- Author/date:

## 2. Message Catalog
List all message types in this model.

| Message Type | Direction | Criticality | Transport Preference |
|---|---|---|---|
|  |  |  |  |

## 3. Common Envelope
Define shared fields for all messages.

| Field | Type | Required | Notes |
|---|---|---|---|
| schema_version | integer/string | yes | contract version marker |
| message_type | string | yes | stable identifier |
| source_node | string | yes | sender identity |
| target_scope | string | yes | node/class/domain/broadcast |
| sequence_or_ts | integer/string | yes | ordering/freshness |
| payload | object | yes | typed content |

## 4. Per-Message Definitions
### Message: `<name>`
- Category: `command|event|state|fault|service`
- Producer(s):
- Consumer(s):
- Trigger condition:
- Expected frequency:

Payload schema table:

| Field | Type | Required | Constraints | Description |
|---|---|---|---|---|
|  |  |  |  |  |

## 5. Reliability and Idempotency
- Retry policy:
- Duplicate detection key:
- Idempotency behavior:
- Timeout and stale handling:

## 6. Compatibility Strategy
- Backward-compatible additions:
- Breaking change policy:
- Migration notes:
- Unknown-field behavior:

## 7. Security/Access Notes
- Sensitive fields:
- Authorization requirements:
- Integrity checks:

## 8. Validation Cases
- Happy path cases:
- Invalid payload cases:
- Version mismatch cases:
- Replay/duplicate cases:

## 9. Example Payloads
### Example 1: Normal command
```json
{
  "schema_version": "1.0",
  "message_type": "example.command",
  "source_node": "master-1",
  "target_scope": "zone-a",
  "sequence_or_ts": 12345,
  "payload": {
    "action": "set",
    "value": 1
  }
}
```

### Example 2: Fault event
```json
{
  "schema_version": "1.0",
  "message_type": "example.fault",
  "source_node": "worker-3",
  "target_scope": "domain-control",
  "sequence_or_ts": 12346,
  "payload": {
    "fault_code": "timeout",
    "severity": "warning"
  }
}
```
