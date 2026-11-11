# Risk rating methodology

## Severity

Use this qualitative model when a defensible CVSS score cannot be calculated.

| Severity | Typical criteria |
|---|---|
| Critical | Practical exploitation can cause broad compromise, remote code execution, authentication bypass, unrestricted access to highly sensitive data, or severe cross-tenant compromise with major impact. |
| High | Significant unauthorized access, privilege escalation, sensitive data exposure, or disruption with realistic exploit conditions. |
| Medium | Meaningful weakness requiring specific conditions, limited privileges, or narrower impact; could enable further compromise. |
| Low | Limited impact or difficult-to-exploit weakness with meaningful compensating controls. |
| Informational | Hardening opportunity, observation, or best-practice gap without demonstrated direct security impact. |

Severity must be justified using:
- Impact on confidentiality, integrity, and availability.
- Scope: one user, one tenant, multiple tenants, or whole platform.
- Exposure: internet-facing, authenticated, internal, or local.
- Required attacker privileges and user interaction.
- Exploit complexity and preconditions.
- Data sensitivity and business criticality.
- Existing compensating controls.

## Confidence

- High: direct, clear evidence demonstrates the weakness and relevant execution path.
- Medium: evidence strongly suggests a weakness, but reachability or a compensating control is not fully established.
- Low: limited evidence or an inference that requires further validation.

## Finding status

- Confirmed: evidence demonstrates the weakness within the reviewed scope.
- Potential: a credible weakness pattern exists but exploitability or full context is not established.
- Not a finding: a suspected issue is disproven by evidence or a compensating control.

Do not label missing documentation as a confirmed technical vulnerability.

## CVSS

When using CVSS:
1. Use the current applicable CVSS version from FIRST.
2. Explain the chosen vector and assumptions.
3. Do not invent missing metrics.
4. Keep CVSS technical severity separate from business risk.
5. Do not assign a CVSS score to generic process observations without a meaningful vulnerability model.

## Priority

Suggested remediation priority:
- P0: address immediately; active compromise, exposed credentials, or critical exploitable issue.
- P1: urgent; critical/high-risk issue with credible exploit path.
- P2: planned near-term remediation; medium-risk or systemic weakness.
- P3: backlog hardening; low-risk or informational improvement.

Priority is a remediation sequencing aid, not a substitute for severity.
