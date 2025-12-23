# ARCHITECTURE.md
# ASAP Architecture

This document describes the logical and trust architecture of
ASAP (AI Site Agent Protocol).

---

## Architectural Principles

ASAP is designed around the following principles:

- **Separation of trust and data**
- **Minimal surface area**
- **Cryptographic verifiability**
- **No central data authority**
- **Explicit site ownership**

---

## Core Components

### 1. Registry

The Registry acts as a **trust root and discovery layer**.

#### Responsibilities
- Publish site metadata
- Publish site public keys
- Declare supported intents
- Declare agent endpoint URLs

#### Non-Responsibilities
- No data processing
- No query routing
- No response generation
- No content storage

The Registry MUST NOT act as a proxy.

It exists only to answer:
> “Where is the official agent and how do I verify it?”

---

### 2. Site Agent

The Site Agent is deployed by the website owner.

#### Responsibilities
- Receive intent-based requests
- Access authoritative internal data
- Generate responses
- Digitally sign responses

The Site Agent represents the **single authoritative voice** of the website.

---

## Trust Boundaries

