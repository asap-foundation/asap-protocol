# GOVERNANCE.md
# ASAP Governance Model

This document defines the governance philosophy of
ASAP (AI Site Agent Protocol).

---

## Purpose

ASAP is designed as an **open protocol**
with a **single canonical origin**.

This governance model exists to:
- Prevent protocol fragmentation
- Avoid trust root hijacking
- Preserve compatibility and credibility

---

## Canonical Specification

The canonical ASAP specification is defined by:
- This repository
- The accompanying whitepaper
- Versioned markdown documents

Any implementation claiming ASAP compatibility
MUST reference this repository.

---

## Registry Governance

ASAP allows multiple registries.

However:
- Only registries that adhere to this specification
  may claim compatibility.
- No registry may claim exclusivity over the protocol.
- No registry may alter protocol semantics.

Registries are **replaceable**, not sovereign.

---

## Non-Ownership Principle

No entity owns:
- Website data
- Responses
- Site agents

ASAP explicitly avoids data centralization.

---

## Forking Policy

Forking is permitted.

However:
- Forks MUST rename the protocol if behavior diverges
- Compatibility claims must be explicit
- Silent incompatibility is forbidden

---

## Evolution Policy

Changes to ASAP:
- Must be versioned
- Must preserve backward compatibility when possible
- Must be documented publicly

Breaking changes require a new major version.

---

## Anti-Capture Clause

No single actor may:
- Control all registries
- Control key distribution
- Act as both registry and data authority

This separation is fundamental.

---

## Governance Philosophy

ASAP follows a **minimal governance model**:

> Trust is technical, not political.

Governance exists only to protect:
- Interoperability
- Verifiability
- Origin integrity

---

## Status

This governance model applies to ASAP v0.1
and may evolve with community feedback.
