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

---

## Intent Response Rules

- Responses must be explicit
- Unsupported intents must return a clear error
- Responses must be signed

---

## Intent Evolution

Sites may:

- Add new intents
- Deprecate intents
- Version intent behavior

Intent names should be stable once published.

---

## Design Philosophy

Intents describe what, not how.

This keeps ASAP simple, future-proof, and database-agnostic.

Status: This document defines the intent abstraction for ASAP v0.1.
