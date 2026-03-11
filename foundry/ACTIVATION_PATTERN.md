# Activation Pattern

## Purpose
Define how this meta-foundry is activated when a new request arrives, so outputs remain consistent and aligned with platform doctrine.

## Activation Trigger
Use this pattern whenever a request asks for one of the following:
- New subsystem design
- Prototype generation
- Protocol or message extension
- Validation strategy
- Copilot prompt generation
- Architecture evolution

## Standard Activation Sequence
1. Read doctrine files:
   - `foundry/META_PHILOSOPHY.md`
   - `foundry/META_SKILL.md`
   - `foundry/META_FRAMEWORK.md`
2. Read relevant system context:
   - `system/SYSTEM_OVERVIEW.md`
   - `system/ARCHITECTURE.md`
   - `system/NODE_CLASSES.md`
   - `system/PROTOCOLS.md`
3. Select template(s) from `/frameworks`.
4. Instantiate a bounded work package.
5. Generate implementation or planning prompts from `/prompts`.

## Request Triage
Classify incoming request type first:
- `prototype`: narrow demonstration slice
- `framework`: reusable subsystem scaffold
- `extension`: architecture/protocol evolution
- `validation`: testing and fault-injection plan
- `operation`: Copilot operating guidance

## Minimal Intake Questions
1. What must work if PC/server is offline?
2. Which node classes are involved?
3. What timing and reliability constraints apply?
4. What faults must be tolerated?
5. What is the smallest shippable increment?

## Output Contract
Every generated output must include:
- Scope and assumptions
- Boundaries and interfaces
- State and failure behavior
- Validation strategy
- Risks and next step prompt

## Guardrails During Activation
- Keep core control on CAN and embedded nodes.
- Preserve multi-master resilience assumptions.
- Avoid introducing hard dependencies on optional transports.
- Require explicit degraded-mode behavior.

## Escalation Path
If requirements conflict with doctrine:
1. Mark the conflict explicitly.
2. Offer two doctrine-compliant alternatives.
3. If deviation is required, request explicit approval with risk statement.

## Activation Checklist
- Doctrine loaded.
- Scope bounded.
- Interfaces named.
- Failure modes listed.
- Validation plan sketched.
- Next implementation prompt generated.
