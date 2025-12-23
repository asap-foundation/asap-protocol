ASAP — AI Site Agent Protocol
Whitepaper v0.1 — Canonical Draft
1. Abstract

Artificial Intelligence systems increasingly generate answers about websites without direct access to authoritative sources. This results in hallucinations, outdated information, and growing legal and reputational risk.
ASAP (AI Site Agent Protocol) proposes a web-native protocol that allows websites to expose official, cryptographically verifiable answers directly to AI systems via site-owned agents and a registry-backed trust model.

ASAP does not replace crawling, APIs, or search engines. Instead, it introduces a verification layer that enables AI systems to distinguish between inferred information and site-authoritative responses.

2. Motivation

Current AI systems rely on:

Crawled content

Training snapshots

Heuristic inference

These methods:

Cannot guarantee correctness

Cannot prove authority

Cannot detect official updates in real time

As AI-generated answers increasingly influence decisions, websites lack a standardized way to declare:

“This answer is official, current, and originates from us.”

ASAP exists to solve this gap.

3. Scope & Non-Goals
In Scope

Authoritative, site-owned answers

Cryptographic verification of responses

Intent-based querying by AI systems

Decentralized data ownership

Explicitly Out of Scope

Opinionated or subjective content

User-generated content moderation

Replacing APIs or search engines

Centralized data aggregation

ASAP is a communication and trust protocol, not a data platform.

4. Terminology

Agent: A service deployed by a website that responds to AI intents using official site data.

Registry: A trust directory that publishes site metadata and public keys.

Intent: A structured request describing what information is requested, not how to fetch it.

AI Platform: Any system requesting authoritative information from websites.

Signed Response: A cryptographically signed payload produced by a site agent.

5. Actors & Roles
Website Owner

Deploys the agent

Controls data and private keys

Defines supported intents

Registry Operator

Publishes site public keys

Provides verification metadata

Acts as a trust anchor, not a data source

AI Platform

Discovers registered sites

Sends intent-based requests

Verifies signed responses

6. Protocol Overview

A website registers its agent and public key with a registry.

An AI platform queries the registry for site metadata.

The AI platform sends an intent request to the site agent.

The agent generates a response using official data.

The response is digitally signed.

The AI platform verifies the signature and consumes the result.

At no point does the registry proxy data or answer intents.

7. Trust & Security Model

ASAP is built on cryptographic trust, not reputation.

Trust Assumptions

Private keys remain under site control

Registry metadata is integrity-protected

AI platforms reject unsigned or unverifiable responses

Threats Addressed

Website impersonation

Response tampering

Replay attacks

Man-in-the-middle attacks

Verification replaces inference.

8. Comparison with Existing Approaches
Crawling

Passive

Unverifiable

Often outdated

APIs

Fragmented

Manual integration

Not AI-discoverable

ASAP

Intent-driven

Verifiable

Site-authoritative

AI-native

ASAP complements existing methods rather than replacing them.

9. Governance & Evolution

ASAP is published as an open protocol proposal.

Specification is public

Feedback-driven evolution

Multiple implementations are expected

Canonical reference is maintained via public documentation

Future governance models may include:

Community stewardship

Formal standardization paths

Multi-registry trust models

10. Limitations

Requires explicit site participation

Depends on cryptographic infrastructure

Does not resolve semantic disagreement

Adoption depends on demonstrated value

ASAP reduces hallucination risk; it does not eliminate ambiguity.

11. References (Placeholders)

AI Hallucination Studies

Web PKI and Trust Models

Intent-Based Systems

AI Safety and Regulation

(To be expanded.)