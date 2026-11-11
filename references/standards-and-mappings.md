# Security standards and reference map

Use `pinned-standards.md` for every identifier cited in a finding. That file records the edition and the date the identifier was checked. Do not invent a requirement number that the pin does not contain. Fetch an official source only to add a finer number, and if the fetch fails, stay at the pinned chapter or category. The links below are the primary sources. Do not assume a version remains current after the pin's access date.

## Primary application security baseline

### OWASP Application Security Verification Standard (ASVS)
Official project: https://owasp.org/www-project-application-security-verification-standard/

Use as the main catalogue of testable application security requirements. Select requirements appropriate to the application's architecture, data sensitivity, and risk. Record exact version and requirement IDs only after checking the relevant release.

### OWASP Web Security Testing Guide (WSTG)
Official project: https://owasp.org/www-project-web-security-testing-guide/

Use for web application testing methodology, including information gathering, configuration, identity, authentication, authorization, session management, input validation, business logic, client-side testing, and API-related testing.

### OWASP Top 10
Official project: https://owasp.org/www-project-top-ten/

Use as a high-level awareness taxonomy, not as a complete verification checklist or substitute for ASVS.

### OWASP API Security Top 10
Official project: https://owasp.org/www-project-api-security/

Use for API-specific threat categories, including object/function/property authorization, authentication, resource consumption, SSRF, inventory management, and unsafe consumption of APIs. Verify the edition being used.

### OWASP Cheat Sheet Series
Official project: https://cheatsheetseries.owasp.org/

Use for implementation-level guidance. Prefer the individual cheat sheet that matches the finding.

## Specialized application types

### Mobile
- MASVS: https://mas.owasp.org/MASVS/
- MASTG: https://mas.owasp.org/MASTG/

Use for mobile storage, cryptography, authentication, network communication, platform interaction, code quality, resilience, and privacy.

### AI and LLM applications
- OWASP Top 10 for LLM Applications: https://owasp.org/www-project-top-10-for-large-language-model-applications/

Use when the product includes LLMs, agents, retrieval-augmented generation, tools, or model-connected workflows. Consider prompt injection, sensitive information disclosure, supply chain, data/model poisoning, improper output handling, excessive agency, system prompt leakage, vector/embedding weaknesses, misinformation, and unbounded consumption as applicable to the current edition.

## Secure development and governance

### NIST Secure Software Development Framework (SSDF), SP 800-218
Official publication: https://csrc.nist.gov/pubs/sp/800/218/final

Use to assess secure development practices across preparation, software protection, secure production, and vulnerability response. Verify the current revision.

### NIST SP 800-53
Official publication: https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final

Use as a broader security and privacy control catalogue where governance, enterprise controls, or regulated environments require it. It is not a direct application-code checklist.

## Weaknesses, vulnerabilities, and scoring

### MITRE CWE
https://cwe.mitre.org/

Use to classify root-cause software weaknesses. Map a finding to a specific CWE only when the weakness fits its definition.

### CVE
https://www.cve.org/

Use to identify publicly disclosed vulnerabilities in specific products and versions. A CVE match requires accurate product/version evidence and applicability analysis; do not assume every scanner match is exploitable.

### CVSS
https://www.first.org/cvss/

Use to communicate technical severity when enough details exist. State the CVSS version, vector, and assumptions. CVSS is not a complete business-risk model.

### CISA Known Exploited Vulnerabilities (KEV)
https://www.cisa.gov/known-exploited-vulnerabilities-catalog

Use as an additional prioritization signal for vulnerabilities known to be exploited in the wild. Confirm affected product/version and applicability.

## Infrastructure and adversary behavior

### CIS Benchmarks
https://www.cisecurity.org/cis-benchmarks

Use for secure configuration baselines for operating systems, databases, cloud services, containers, and platforms. Select the exact product/version benchmark.

### MITRE ATT&CK
https://attack.mitre.org/

Use to describe relevant adversary tactics and techniques, not as a control-compliance checklist.

## Books for conceptual grounding

Use books as explanatory references, not as sources for fabricated control identifiers:
- *Alice and Bob Learn Application Security* — Tanya Janca.
- *Threat Modeling: Designing for Security* — Adam Shostack.
- *Threat Modeling: A Practical Guide for Development Teams* — Izar Tarandach and Matthew Coles.
- *Secure by Design* — Dan Bergh Johnsson, Daniel Deogun, and Daniel Sawano.

## Mapping rules

- ASVS: cite a chapter or section from `pinned-standards.md`. Cite a requirement number only after a successful check of the 5.0.0 text.
- WSTG: map to a relevant test category/test ID only after verification. The pin does not include WSTG test IDs.
- API Top 10 / LLM Top 10: cite the edition and category ID from `pinned-standards.md`.
- CWE: map the root cause, not the symptom, and use an ID from `pinned-standards.md`. If none fits, describe the weakness without an ID.
- CVE: map only to affected dependency/product versions.
- CVSS: calculate only from evidence; do not infer missing metrics.
- NIST/CIS: cite control or recommendation identifiers only after verification.
- Multiple mappings are acceptable, but avoid padding findings with unrelated references.
