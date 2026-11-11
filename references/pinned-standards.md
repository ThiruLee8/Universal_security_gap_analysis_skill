# Pinned security identifiers

Checked 6 November 2026. Cite these identifiers as written. Do not add a requirement number that is not in this file unless that number was read from the official source during the review and the source URL is included in the finding.

If a newer edition is published after 6 November 2026, keep using this pin until this file is updated. Say which edition was used.

## OWASP ASVS 5.0.0

Published 30 May 2025. Chapter names below match the `5.0/en` chapter files in the OWASP/ASVS repository. Section titles match the OWASP Cheat Sheet Series IndexASVS page for ASVS 5.0.x, checked 6 November 2026. Section titles are not individual requirement numbers.

| Chapter | Sections confirmed in that index |
|---|---|
| V1 Encoding and Sanitization | V1.1 through V1.5 |
| V2 Validation and Business Logic | V2.1 through V2.4, including V2.4 Anti-automation |
| V3 Web Frontend Security | V3.1 through V3.7, including V3.4 Browser Security Mechanism Headers and V3.5 Browser Origin Separation |
| V4 API and Web Service | V4.1 through V4.4 |
| V5 File Handling | V5.1 through V5.4, including V5.2 File Upload and Content |
| V6 Authentication | V6.1 through V6.6, including V6.2 Password Security and V6.5 Multi-factor authentication. Do not cite V6.7 or later without a live check. |
| V7 Session Management | V7.1 through V7.6, including V7.3 Session Timeout and V7.4 Session Termination |
| V8 Authorization | V8.1 through V8.4, including V8.2 General Authorization Design and V8.3 Operation Level Authorization |
| V9 Self-contained Tokens | V9.1 Token source and integrity, V9.2 Token content |
| V10 OAuth and OIDC | V10.1 through V10.7 |
| V11 Cryptography | V11.1 through V11.7 |
| V12 Secure Communication | V12.1 through V12.3 |
| V13 Configuration | V13.1 through V13.4, including V13.3 Secret Management |
| V14 Data Protection | V14.1 through V14.3 |
| V15 Secure Coding and Architecture | V15.1 through V15.4 |
| V16 Security Logging and Error Handling | V16.1 through V16.5 |
| V17 WebRTC | V17.1 TURN Server, V17.2 Media, V17.3 Signaling |

Cite the chapter, and the section when it fits. Example: `OWASP ASVS 5.0.0 V13.3 Secret Management`.

## OWASP API Security Top 10 2023

Latest published edition found on 6 November 2026 at the OWASP API Security project.

| ID | Category |
|---|---|
| API1:2023 | Broken Object Level Authorization |
| API2:2023 | Broken Authentication |
| API3:2023 | Broken Object Property Level Authorization |
| API4:2023 | Unrestricted Resource Consumption |
| API5:2023 | Broken Function Level Authorization |
| API6:2023 | Unrestricted Access to Sensitive Business Flows |
| API7:2023 | Server Side Request Forgery |
| API8:2023 | Security Misconfiguration |
| API9:2023 | Improper Inventory Management |
| API10:2023 | Unsafe Consumption of APIs |

## OWASP Top 10 for LLM Applications 2026

Published 4 August 2026. Source: OWASP GenAI LLM Top 10 2026 final list.

| ID | Category |
|---|---|
| LLM01:2026 | Prompt Injection |
| LLM02:2026 | Sensitive Information Disclosure |
| LLM03:2026 | Excessive Agency |
| LLM04:2026 | Supply Chain |
| LLM05:2026 | Data and Model Poisoning |
| LLM06:2026 | Unbounded Consumption |
| LLM07:2026 | Misinformation |
| LLM08:2026 | Hidden Context Exposure |
| LLM09:2026 | Vector and Embedding Weaknesses |
| LLM10:2026 | Improper Output Handling |

## CWE

Use a CWE only when the definition fits the root cause. These names were current on 6 November 2026. If none fits, describe the weakness and do not invent an identifier.

| ID | Name |
|---|---|
| CWE-250 | Execution with Unnecessary Privileges |
| CWE-285 | Improper Authorization |
| CWE-295 | Improper Certificate Validation |
| CWE-307 | Improper Restriction of Excessive Authentication Attempts |
| CWE-311 | Missing Encryption of Sensitive Data |
| CWE-321 | Use of Hard-coded Cryptographic Key |
| CWE-522 | Insufficiently Protected Credentials |
| CWE-598 | Use of GET Request Method With Sensitive Query Strings |
| CWE-613 | Insufficient Session Expiration |
| CWE-639 | Authorization Bypass Through User-Controlled Key |
| CWE-668 | Exposure of Resource to Wrong Sphere |
| CWE-770 | Allocation of Resources Without Limits or Throttling |
| CWE-798 | Use of Hard-coded Credentials |
| CWE-918 | Server-Side Request Forgery (SSRF) |
| CWE-942 | Permissive Cross-domain Policy with Untrusted Domains |

## Not pinned

Do not invent identifiers for WSTG tests, OWASP Top 10 2021 or later web categories, NIST SSDF controls, NIST SP 800-53 controls, CIS Benchmark recommendations, or CVE entries. Name the standard and the topic, or cite an identifier only after reading it from the official source during the review.
