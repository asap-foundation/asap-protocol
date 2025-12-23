# ASAP Security Model

This document describes the security assumptions, threat model,
and mitigations for the ASAP (AI Site Agent Protocol).

---

## Security Goals

ASAP is designed to ensure that:

- AI systems can verify the origin of responses  
- Websites retain control over their authoritative data  
- Responses cannot be silently altered or spoofed  
- Trust is cryptographic, not reputational  

---

## Trust Assumptions

- Website private keys remain under exclusive site control  
- Registry metadata integrity is protected  
- AI platforms perform signature verification  
- Transport security (HTTPS/TLS) is enforced  

---

## Actors and Trust Boundaries

| Actor       | Trust Boundary                          |
|------------|----------------------------------------|
| Site Agent | Trusted to sign only official data     |
| Registry   | Trusted to publish accurate public keys|
| AI Platform| Trusted to verify signatures correctly |

The registry is a **trust anchor**, not a data authority.

---

## Threat Model

### Threats Considered

1. Website impersonation  
2. Response tampering  
3. Replay attacks  
4. Man-in-the-middle (MITM) attacks  
5. Unauthorized agent endpoints  

---

## Mitigations

| Threat          | Mitigation                               |
|----------------|------------------------------------------|
| Impersonation  | Registry-verified public keys           |
| Tampering      | Digital signatures on responses         |
| Replay         | requestId + timestamp                    |
| MITM           | HTTPS + signature verification          |
| Fake agents    | Registry lookup + domain validation     |

Unsigned or unverifiable responses **MUST** be ignored by AI platforms.

---

## Non-Goals

ASAP does NOT attempt to:

- Judge semantic correctness  
- Moderate content  
- Resolve conflicting claims between sites  
- Enforce truth beyond site authority  

ASAP verifies **origin and intent**, not meaning.

---

## Security Philosophy

ASAP assumes that:

- Verification is cheaper than inference  
- Authority should be explicit  
- Trust should be machine-verifiable  

Security is achieved through **cryptographic proof**, not heuristics.

---

## Open Considerations

- Multi-registry trust models  
- Key rotation mechanisms  
- Revocation strategies  

These are intentionally left open for future iterations.

---

## Status

This document accompanies ASAP Whitepaper v0.1  
and represents the current security model for the protocol.
