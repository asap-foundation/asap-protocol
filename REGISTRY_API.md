# ASAP Registry API

This document defines the API surface of an ASAP-compatible registry implementation.

## Registry Role

The registry provides **discovery, verification metadata, and authenticated query routing**.

It provides:
- Site registration and metadata storage
- Authenticated query proxying to site agents
- Public key distribution for signature verification
- Rate limiting and authentication

## API Endpoints

### 1. Site Registration
Register a new site and its agent with the registry.

#### Request
```
POST /register
Content-Type: application/json
```

```json
{
  "site": "example.com",
  "agent_url": "https://example.com/ai/agent",
  "public_key": "BASE64_PUBLIC_KEY",
  "intents": ["pricing", "features"]
}
```

#### Response (Success)
```json
{
  "success": true,
  "message": "example.com registered."
}
```

#### Response (Error)
```json
{
  "error": "Missing required fields"
}
```

### 2. Query Site Agent
Send an authenticated query to a registered site agent through the registry.

#### Request
```
POST /query
Content-Type: application/json
Authorization: Bearer <api_key>
```

```json
{
  "intent": "pricing",
  "parameters": {
    "site": "example.com",
    "language": "en"
  },
  "requestId": "550e8400-e29b-41d4-a716-446655440000",
  "timestamp": "2025-12-24T12:00:00.000Z",
  "clientInfo": {
    "platformName": "ASAP-Consumer",
    "platformVersion": "v1.0",
    "publicKey": "BASE64_PUBLIC_KEY"
  }
}
```

#### Response (Success)
```json
{
  "verified": true,
  "data": {
    "requestId": "550e8400-e29b-41d4-a716-446655440000",
    "intent": "pricing",
    "answer": {
      "data": "We offer three plans: Free, Professional, Enterprise.",
      "confidence": 0.97,
      "language": "en"
    },
    "updatedField": "2025-12-24T12:00:00.000Z",
    "signature": "hex_signature"
  }
}
```

#### Response (Verification Failed)
```json
{
  "verified": false,
  "error": "Invalid signature"
}
```

### 3. Get Public Key
Retrieve public key and metadata for a registered site.

#### Request
```
GET /publicKey?site=example.com
Authorization: Bearer <api_key>
```

#### Response (Success)
```json
{
  "site": "example.com",
  "publicKey": "BASE64_PUBLIC_KEY",
  "intents": ["pricing", "features"],
  "agent_url": "https://example.com/ai/agent",
  "metadataSignature": "registry_signature"
}
```

#### Response (Error)
```json
{
  "error": "Site not registered",
  "available_sites": ["example.com", "test.com"]
}
```

## Authentication

The registry implements authentication and rate limiting:

- **API Key Authentication**: Required for `/query` and `/publicKey` endpoints
- **Rate Limiting**: Applied to prevent abuse
- **Registration**: Open endpoint for site registration

## Security Considerations

- HTTPS is mandatory for all endpoints
- API keys must be kept secure
- Public keys are safe to publish
- Registry signs metadata responses for integrity
- Rate limiting prevents abuse

## Validation Rules

- Site domain must match agent ownership
- Public key must be valid base64-encoded key
- Agent URL must be reachable and respond to ASAP protocol
- Supported intents must be declared during registration

## Error Responses

### Authentication Error
```json
{
  "error": "Authentication required"
}
```

### Rate Limit Exceeded
```json
{
  "error": "Rate limit exceeded"
}
```

### Invalid Request Format
```json
{
  "error": "Invalid request format",
  "required": ["intent", "parameters", "requestId", "timestamp", "clientInfo"]
}
```

### Site Not Registered
```json
{
  "error": "Site not registered"
}
```

### Agent Unreachable
```json
{
  "error": "Agent unreachable"
}
```

## Registry Independence

AI platforms may:
- Cache registry responses and public keys
- Use multiple registries for redundancy
- Implement fallback mechanisms for non-ASAP sites

**Registry availability should not block AI systems from functioning.**

## Discovery Mechanism

Sites can be discovered through:
- `.well-known/asap.json` files on websites
- Registry APIs for programmatic discovery
- Manual registration and configuration

## Implementation Notes

- Registry stores site metadata in memory/database
- Authentication is implemented via API keys
- Rate limiting is configurable per endpoint
- Registry acts as a proxy but does not store response data
- All responses include appropriate HTTP status codes
