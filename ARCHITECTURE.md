# ASAP Architecture

This document describes the logical, cryptographic, and trust architecture of
**ASAP (AI Site Agent Protocol)**.

ASAP is designed to separate **data authority**, **trust verification**, and **AI consumption**
into clearly defined components with explicit boundaries.

---

## Architectural Principles

ASAP is built around the following core principles:

- **Separation of trust and data**
- **Minimal surface area**
- **Cryptographic verifiability**
- **No central data authority**
- **Explicit site ownership**
- **AI as verifier, not arbiter**

No component is trusted implicitly. Every claim must be verifiable.

---

## Core Components

### 1. Registry

The Registry acts as a **trust root and discovery layer**.

It provides *identity and verification metadata* but never participates in data exchange.

#### Responsibilities

- Publish site identifiers
- Publish site public keys
- Declare supported intents per site
- Declare Site Agent endpoint URLs
- Provide metadata required for signature verification

#### Non-Responsibilities

- No data processing
- No intent execution
- No query routing
- No response generation
- No content storage
- No aggregation or interpretation

The Registry **MUST NOT** act as a proxy.

The Registry exists only to answer:

> "Where is the official site agent, and how can its responses be verified?"

---

### 2. Site Agent

The Site Agent is deployed and fully controlled by the website owner.

It represents the **single authoritative interface** between a website and AI systems.

#### Responsibilities

- Receive intent-based requests
- Validate request structure and freshness
- Access authoritative internal data sources
- Generate structured responses
- Digitally sign responses using site-controlled private keys

#### Properties

- Stateless or state-light
- No dependency on registry availability after discovery
- Implementation-defined internal logic
- Fully replaceable by the site owner

The Site Agent is the **only entity allowed to produce authoritative answers** for the site.

---

### 3. AI Platform (Verifier Role)

AI platforms are **consumers and verifiers**, not trust authorities.

#### Responsibilities

- Discover site metadata via the Registry
- Send intent-based requests to Site Agents
- Verify cryptographic signatures
- Validate freshness and integrity
- Decide whether to consume or reject responses

AI platforms **MUST NOT** infer authority without verification.

---

## Trust Boundaries

ASAP defines explicit trust boundaries between components.

```text
+------------------+        +------------------+        +------------------+
|    Registry      |        |    Site Agent    |        |   AI Platform    |
|                  |        |                  |        |                  |
| - Public keys    |        | - Private keys   |        | - Verification   |
| - Agent URLs     |        | - Official data  |        | - Consumption    |
+--------+---------+        +--------+---------+        +--------+---------+
         |                           |                           |
         | Discovery only            | Signed responses          |
         |                           |                           |
         +-------------------------->+-------------------------->+
```

## Trust Rules

- Registry data is **read-only** to AI platforms
- Private keys **never leave** the Site Agent
- AI platforms trust responses **only after verification**
- Registry compromise does **not** expose site data
- Agent compromise does **not** compromise registry

---

## Failure & Degradation Model

| Component Failure   | Result                         |
| ------------------- | ------------------------------ |
| Registry offline    | Discovery fails; no fallback   |
| Agent offline       | No authoritative response      |
| Invalid signature   | Response rejected              |
| Stale timestamp     | Response rejected              |
| Unsupported intent  | Explicit error                 |

ASAP favors **fail-closed** behavior.

---

## Cryptographic Model

- Each Site Agent controls a private signing key
- Corresponding public key is published via the Registry
- Responses include:
  - Payload
  - Timestamp
  - Request ID
  - Signature

Verification is deterministic and implementation-agnostic.

---

## Deployment Model

- **Registry**: public, highly available, metadata-only
- **Site Agent**: site-owned, colocated with internal systems
- **AI Platform**: external verifier

ASAP does not require shared infrastructure or centralized hosting.

---

## Architectural Non-Goals

- Defining intent semantics
- Standardizing data schemas
- Ranking or prioritizing answers
- Resolving conflicts between sites

ASAP defines **how authority is proven**, not **what authority means**.

---

## Summary

ASAP architecture enforces:

- Clear ownership
- Minimal trust assumptions
- Cryptographic verification
- Decentralized data control

**Authority is explicit.**  
**Trust is verifiable.**  
**Inference is optional.**
