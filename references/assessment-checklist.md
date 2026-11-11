# Universal assessment checklist

Phase 5 requires this file. Before writing findings, mark every item `Pass`, `Fail`, `Partial`, `Not assessed`, or `Unable to verify`, and record evidence or the reason it was not reviewed. Use this as a coverage prompt, not a universal pass/fail list. An unmarked or unreviewed item is not a confirmed vulnerability.

## Architecture
- [ ] Assets, trust boundaries, and data flows identified.
- [ ] Public entry points and administrative interfaces inventoried.
- [ ] Least privilege and defense in depth considered.
- [ ] Failure modes and blast radius reviewed.

## Identity and authorization
- [ ] Authentication flows and token validation reviewed.
- [ ] MFA and account recovery assessed where relevant.
- [ ] Session lifecycle and cookie protections reviewed.
- [ ] Object/function/property authorization checked.
- [ ] Tenant isolation checked across all data and processing layers.
- [ ] Service-to-service identity and credential rotation reviewed.

## Input, output, and API
- [ ] Input validation and output encoding reviewed.
- [ ] Injection, XSS, SSRF, path traversal and unsafe deserialization considered.
- [ ] File upload/download controls reviewed.
- [ ] API schema, mass assignment and resource limits reviewed.
- [ ] CORS, CSRF and security headers reviewed where relevant.
- [ ] Webhook signatures, replay protection and idempotency reviewed.

## Data and cryptography
- [ ] TLS and certificate validation reviewed.
- [ ] Encryption and key management reviewed.
- [ ] Password hashing reviewed.
- [ ] Secrets and sensitive data exposure checked.
- [ ] Database, cache, object storage and backup access reviewed.
- [ ] Retention and deletion practices reviewed.

## Dependencies and delivery
- [ ] Dependency inventory and known vulnerabilities reviewed.
- [ ] Runtime/framework support status checked.
- [ ] Lockfiles and package sources reviewed.
- [ ] CI/CD permissions and secrets reviewed.
- [ ] Build artifacts and container images reviewed.
- [ ] IaC and deployment configuration reviewed.

## Operations and resilience
- [ ] Security logging and alerting reviewed.
- [ ] Logs avoid credentials and unnecessary sensitive data.
- [ ] Rate limiting, timeouts, retries and quotas reviewed.
- [ ] Backup restoration and disaster recovery reviewed.
- [ ] Incident response and credential revocation considered.

## Specialized components
- [ ] Mobile controls assessed if mobile clients exist.
- [ ] Cloud controls assessed if cloud services exist.
- [ ] Container/Kubernetes controls assessed if applicable.
- [ ] AI/LLM controls assessed if AI features exist.
- [ ] IoT/device controls assessed if applicable.
