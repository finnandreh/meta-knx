# Resilient Embedded House-Control Foundry

A markdown-first Foundry for designing, governing, and growing a resilient embedded house-control platform based on a deterministic CAN backbone, distributed ESP32 nodes, optional local wireless edge access, and service layers that must never become hidden dependencies for core operation.

This repository does **not** begin by building the final full system.

It begins by building the **governing meta-foundation** that allows the system to be developed in small controlled steps while preserving architectural consistency over time.

---

## Purpose

This repository exists to provide a persistent design and generation foundation for a house-control architecture with these intended characteristics:

- **CAN bus** as the primary wired backbone for critical control
- **Distributed ESP32 nodes** for room control, IO, gateways, and supervisory roles
- **3 embedded master/supervisor nodes** for resilient coordination and failover
- **Optional ESP-NOW** for local wireless edge devices
- **Optional Bluetooth** for service, provisioning, and local setup
- **Optional PC/server layer** for configuration, logging, dashboarding, updates, and engineering support
- **Core embedded operation must continue** even when the server or PC layer is offline

The repository is designed to support:

- small first prototypes
- subsystem frameworks
- protocol decisions
- architecture extensions
- prompt generation
- future Copilot-assisted development
- long-term system growth without architectural drift

---

## Core Idea

The system is governed by a layered Foundry model:

1. **Meta Philosophy**  
   Defines the doctrine, priorities, and tradeoff rules.

2. **Meta Skill**  
   Defines the reusable method for analyzing, classifying, and designing new parts of the system.

3. **Meta Framework**  
   Defines how new frameworks must be generated so future outputs stay structured and aligned.

4. **Activation Pattern**  
   Defines how to apply the meta layers only to the requested scope, so future work can stay small, controlled, and forward-compatible.

This means the repository can support both:

- a **tiny first prototype**
- and a **much larger future distributed platform**

without restarting the design process from scratch every time.

---

## Design Doctrine

This project is built around a few non-negotiable ideas:

- critical control belongs in the embedded layer
- deterministic backbone communication is preferred for critical functions
- service layers must remain optional
- resilience must stay understandable and debuggable
- future growth must not weaken the reliability of the core
- convenience features must not become hidden control dependencies
- protocols must be chosen by role, not by trend
- architecture should expand in small validated steps
- documentation must be updated with every meaningful change

In short:

**the house must still work when the dashboard does not**

Documentation discipline is part of this doctrine: implementation, validation, and operational behavior changes are not complete until the corresponding docs are updated.

---

## Repository Structure

```text
/foundry
  META_PHILOSOPHY.md
  META_SKILL.md
  META_FRAMEWORK.md
  ACTIVATION_PATTERN.md

/system
  SYSTEM_OVERVIEW.md
  ARCHITECTURE.md
  NODE_CLASSES.md
  PROTOCOLS.md

/frameworks
  TEMPLATE_SUBSYSTEM_FRAMEWORK.md
  TEMPLATE_MESSAGE_MODEL.md
  TEMPLATE_VALIDATION_PLAN.md

/prompts
  PROMPT_LIBRARY.md
  SYSTEM_REQUEST_PATTERNS.md
  SUBSYSTEM_REQUEST_PATTERNS.md
  EXPANSION_REQUEST_PATTERNS.md

/.github
  copilot-instructions.md
```

## Current Maturity Level

This repository is intentionally at the **meta-foundry/design-governance level** right now.

It currently defines:

- doctrine
- architecture boundaries
- node class roles
- protocol and message conventions
- reusable framework templates
- prompt patterns for consistent future generation

It does not yet claim to be a full implementation repository.

That separation is intentional and helps keep future implementation increments controlled, testable, and resilient by design.

## Functional Progress Note

The repository now also includes a documented and tested WSL instance-cloning lifecycle as an operational baseline for future simulation work:

1. Start a fresh source instance.
2. Create an image/export copy with a proper target name.
3. Remove the original source instance/image.
4. Start only the newly copied instance.

This does not replace the queued architecture task. It confirms the core clone workflow is already functional and can be treated as a validated building block for the upcoming WSL simulation orchestration plan.
