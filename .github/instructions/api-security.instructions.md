---
name: API and security standards
description: REST API design, JWT, Spring Security, authorization and secure coding.
applyTo: "**/*Controller.java,**/*Security*.java,**/*Filter.java,**/*Config.java,**/*Dto.java,**/openapi/**"
---
# API and security standards
- Define API contracts before implementation; follow existing OpenAPI conventions if present.
- Use correct HTTP methods, status codes, pagination, filtering and stable error formats.
- Validate all untrusted input and enforce object-level authorization on every protected resource.
- Authentication is not authorization. Do not rely only on API Gateway checks.
- Prefer Spring Security OAuth2 Resource Server support for validating JWTs rather than hand-rolled token parsing.
- Verify issuer, signature, audience where applicable, expiry and permitted algorithms using configured trusted keys/JWKs.
- Never hardcode signing keys or secrets. Never log bearer tokens.
- Keep access tokens short-lived; define refresh-token handling, revocation and rotation requirements explicitly.
- Do not put sensitive personal or business data in JWT claims.
- Use least privilege and explicit role/authority mapping.
- Apply CSRF protections appropriate to the authentication mechanism and client type; do not disable CSRF without explaining the threat model.
- Configure CORS narrowly; never use wildcard origins with credentials.
- Rate-limit sensitive endpoints and protect authentication flows against abuse.
- Return generic authentication errors where detailed errors could aid attackers.
- Add tests for unauthenticated, unauthorized, forbidden, expired-token and malformed-token cases.
