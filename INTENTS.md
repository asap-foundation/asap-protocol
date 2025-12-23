# INTENTS.md
# ASAP Intent Model

This document defines the intent abstraction used by
ASAP (AI Site Agent Protocol).

---

## What Is an Intent?

An intent is a **semantic request category**
representing what an AI wants to know,
not how the data is stored.

Intent ≠ Query  
Intent ≠ SQL  
Intent ≠ Endpoint

---

## Why Intents Exist

- AI systems think semantically
- Websites store data structurally
- ASAP bridges this gap

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

| Intent | Meaning |
|------|--------|
| pricing | Official pricing information |
| features | Product or service features |
| availability | Stock or service availability |
| policy | Legal or operational policies |
| status | Operational or service status |
| contact | Official contact information |

---

## Intent Scope

ASAP does NOT define:
- Required intents
- Internal execution logic
- Data sources

Sites decide how to fulfill intents.

---

## Intent Request Example

```json
{
  "intent": "pricing",
  "parameters": {},
  "requestId": "uuid",
  "timestamp": "ISO8601"
}
