# ASAP — AI Site Agent Protocol

**Canonical Reference Repository**  
Version: 0.1 Draft

---

## Overview

ASAP (AI Site Agent Protocol) is a web-native protocol designed to enable websites to provide **official, cryptographically verifiable answers** directly to AI systems.  
It is **not a product**—it is a protocol specification and canonical reference.

ASAP allows AI systems to distinguish between inferred content and **site-authoritative responses**, reducing hallucinations, outdated information, and liability risk.

---

## Why ASAP Exists

Current AI systems often rely on:
- Crawled content
- Training snapshots
- Heuristic inference

These approaches cannot guarantee correctness or authority. Websites currently have no standardized way to declare:

> "This answer is official, current, and originates from us."

ASAP solves this problem by creating a **machine-verifiable layer of trust**.

ASAP does not attempt to judge truth or correctness.
It only verifies origin and authority.

---

## Core Components

### 1. Site Agent
A service deployed by the website that:
- Receives intent-based requests
- Accesses official site data
- Generates digitally signed responses

### 2. Registry
A trust directory that:
- Publishes site public keys
- Declares agent URLs and supported intents
- Enables verification of responses
- Does **not** proxy data

---

## High-Level Flow

AI Platform
↓ (lookup public key)

Registry
↓ (intent request)

Site Agent
↓ (signed response)

AI Platform verifies signature → uses response

---

## Key Principles

- Authority over truth — website defines official data
- Intent-driven communication — AI specifies **what**, not **how**
- Verification over inference — cryptographically signed responses
- Decentralized data, minimal trust anchor — registry publishes metadata only
- AI as verifier, not judge — no assumption beyond signature verification

---

## Intent Model

See [INTENTS.md](INTENTS.md) for:
- Definition of intents
- Examples (`pricing`, `features`, `availability`, `policy`, `contact`, `status`)
- Request and response rules

---

## Security Model

See [SECURITY.md](SECURITY.md) for:
- Threats
- Mitigation
- Trust assumptions
- Verification rules

---

## Architecture

See [ARCHITECTURE.md](ARCHITECTURE.md) for:
- Component overview
- Flow diagram
- Deployment and failure models
- Cryptography and trust boundaries

---

## Governance

See [GOVERNANCE.md](GOVERNANCE.md) for:
- Canonical reference rules
- Registry governance
- Forking and evolution policy
- Anti-capture clause

---

## Registry API

See [REGISTRY_API.md](REGISTRY_API.md) for:
- Minimal registry endpoints
- PublicKey lookup
- Supported intents
- Response format
- Security considerations

---

## Standardization Roadmap

See [STANDARDIZATION.md](STANDARDIZATION.md) for:
- RFC / W3C / ISO paths
- Versioning and adoption strategy
- Canonical reference and open process

---

## Status

- Draft / Proposal  
- Ready for public feedback and pilot implementations  
- Repository serves as canonical reference for ASAP v0.1

---

## Citation

If implementing or referencing ASAP, cite this repository and version:


ASAP — AI Site Agent Protocol. Version 0.1 Draft. canonical reference: github.com/asap-foundation/asap-protocol


---
## Authorship

The ASAP protocol concept and canonical specification
were proposed and authored by **Shahram Nematzadeh**.

---
## License

This specification is published for public reference. Implementations are permitted.  
No entity may claim to be the canonical ASAP registry without attribution to this repository.


