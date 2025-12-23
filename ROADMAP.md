# ASAP — AI Site Agent Protocol

ASAP (AI Site Agent Protocol) is a web-native protocol proposal that enables
websites to provide **official, cryptographically verifiable answers**
directly to AI systems.

This repository serves as the **canonical reference** for the ASAP protocol.

---

## Why ASAP Exists

Modern AI systems generate answers about websites using:
- Crawling
- Static training data
- Heuristic inference

These approaches cannot guarantee:
- Authority
- Freshness
- Verifiability

As a result, AI systems increasingly hallucinate or provide outdated
information about websites.

Websites currently have no standardized way to declare:
> “This is our official answer, at this time.”

ASAP is designed to solve this gap.

---

## What ASAP Is

- An **intent-based communication protocol**
- A **verification layer**, not a data platform
- A way for websites to answer AI systems directly and authoritatively

ASAP allows AI systems to verify responses instead of guessing them.

---

## What ASAP Is NOT

- Not a crawler
- Not a search engine
- Not an API replacement
- Not an AI model
- Not a centralized data service

ASAP complements existing approaches rather than replacing them.

---

## Core Components

### 1. Site Agent
A lightweight service deployed on the website that:
- Accesses official site data
- Responds to structured intents
- Digitally signs responses

### 2. Registry
A trust directory that:
- Publishes site metadata and public keys
- Enables response verification
- Does NOT proxy data or answer queries

---

## High-Level Flow

