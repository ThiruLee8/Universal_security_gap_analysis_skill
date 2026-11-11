# Application Security Gap Analysis Report

This file is the section contract. Do not save a filled copy into the application repository unless the user asks for a report file. In Cursor, render these sections as a canvas. When citing a secret, name the file path, the configuration key, and the secret type. Do not include the value.

## 1. Executive summary

- Application:
- Assessment date:
- Assessment type: Repository review / Architecture review / Configuration review / Authorized testing / Combined
- Overall assessment:
- Critical findings:
- High findings:
- Medium findings:
- Low findings:
- Key risk themes:

Summarize the most consequential risks, business impact, and immediate actions. Do not state that the application is secure or compliant.

## 2. Scope and methodology

### In scope
- Repositories/components:
- Environments:
- Interfaces:
- Data flows:

### Out of scope
- Explicit exclusions:

### Assumptions and limitations
- Access limitations:
- Missing artifacts:
- Testing restrictions:
- Unverified controls:

## 3. Application inventory

| Component | Technology/version | Purpose | Exposure | Sensitive data |
|---|---|---|---|---|

## 4. Architecture and attack surface

Describe:
- Main components and data flows.
- Trust boundaries.
- Authentication and authorization boundaries.
- External integrations.
- Sensitive assets and entry points.

## 5. Standards and coverage

| Standard and version | Applicable areas | Assessment status | Notes |
|---|---|---|---|

Coverage status: Assessed / Partially assessed / Not assessed / Unable to verify.

## 6. Findings summary

| ID | Finding | Status | Severity | Confidence | Component | Priority |
|---|---|---|---|---|---|---|

## 7. Detailed findings

Repeat this section for each finding.

### [SEC-001] Finding title

- Status: Confirmed / Potential
- Severity:
- Confidence:
- Priority:
- Affected component:
- Evidence: file path, symbol, line range, configuration key, or architecture element.
- Standard mapping: verified standard/version/requirement or category.
- Preconditions:
- Attack scenario:
- Technical impact:
- Business impact:
- Root cause:
- Recommended remediation:
- Validation and regression tests:

Redact secrets and personal data from evidence.

## 8. Positive security controls observed

| Control | Evidence | Scope/limitations |
|---|---|---|

## 9. Not assessed / unable to verify

| Area | Reason | Evidence needed | Recommended next step |
|---|---|---|---|

## 10. Remediation roadmap

| Priority | Action | Finding IDs | Suggested owner role | Completion criterion |
|---|---|---|---|---|

## 11. Conclusion and residual risk

State what was reviewed, the most important residual risks, and what additional testing or evidence is required. Do not imply certification or complete assurance.
