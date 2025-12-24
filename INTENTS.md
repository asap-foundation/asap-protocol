# ASAP Intent Model

> This document defines the intent abstraction used by ASAP (AI Site Agent Protocol).

---

## What Is an Intent?

An intent is a **semantic request category** representing what an AI wants to know, not how the data is stored.

**Key Distinctions:**

- Intent ≠ Query  
- Intent ≠ SQL  
- Intent ≠ Endpoint  

---

## Why Intents Exist

- **AI systems** think semantically  
- **Websites** store data structurally  
- **ASAP** bridges this gap  

Intent abstraction prevents:

- Schema coupling  
- Database dependency  
- Vendor lock-in  

---

## Intent Characteristics

Each intent:

- Is human-meaningful  
- Is site-defined  
- Has stable semantics  
- Is implementation-agnostic  

---

## Examples

| Intent        | Meaning                        |
|---------------|--------------------------------|
| `pricing`     | Official pricing information   |
| `features`    | Product or service features    |
| `availability`| Stock or service availability  |
| `policy`      | Legal or operational policies  |
| `status`      | Operational or service status  |
| `contact`     | Official contact information   |

---

## Intent Scope

ASAP does **NOT** define:

- Required intents  
- Internal execution logic  
- Data sources  

**Sites decide how to fulfill intents.**

---

## Intent Request Example

```json
{
  "intent": "pricing",
  "parameters": {},
  "requestId": "uuid",
  "timestamp": "ISO8601"
}
```
Notes

The target site is identified by the agent endpoint, not by request parameters

parameters MAY be empty

requestId and timestamp are required for replay protection and verification

---

## Intent Response Rules

- Responses MUST be explicit and unambiguous
- Unsupported intents MUST return a clear, machine-readable error
- All successful responses MUST be digitally signed
- Unsigned or unverifiable responses MUST be ignored by AI platforms.

---

## Intent Evolution

Sites MAY:
- Introduce new intents
- Deprecate existing intents
- Version intent behavior internally

However:

- Intent identifiers SHOULD remain stable once published
- Breaking semantic changes SHOULD introduce a new intent name

---

## Design Philosophy

Intents define what is requested, not how it is produced.

This ensures that ASAP remains:

- Simple
- Future-proof
- Backend-agnostic
- Compatible with diverse site architectures

Status: This document defines the intent abstraction for ASAP v0.1.
