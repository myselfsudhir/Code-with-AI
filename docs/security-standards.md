# Security Standards

- Use Spring Security's supported OAuth2 Resource Server JWT support where suitable.
- Validate signature, issuer, expiry and audience according to the token contract.
- Use approved asymmetric keys/JWKs and key rotation for distributed validation; never hardcode secrets.
- Keep access tokens short-lived and define refresh/revocation behavior.
- Keep sensitive data out of JWT claims and logs.
- Enforce authorization at the service and resource/object level.
- Use least privilege for service identities, database users, Kafka principals, MCP tools and Kubernetes RBAC.
- Validate inputs and encode outputs.
- Apply CORS, CSRF and rate limiting according to a documented threat model.
- Store secrets in approved secret stores; never commit `.env`, private keys, passwords or tokens.
- Use TLS for service-to-service and infrastructure communication.
- Keep dependencies patched and scan images/dependencies in CI.
- Return safe errors without stack traces or internal topology.
- Test unauthenticated, unauthorized, forbidden, token-expiry and cross-tenant access cases.
