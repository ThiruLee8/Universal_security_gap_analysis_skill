# Universal Security Gap Analysis Agent Skill

> A technology-independent, evidence-based security gap analysis skill for AI coding assistants and agent environments (Google Antigravity, Claude Code, Cursor, Windsurf, Codex, and other LLM agent runtimes).

---

## Table of Contents

- [Overview](#overview)
- [What This Skill Is For](#what-this-skill-is-for)
  - [Core Purpose](#core-purpose)
  - [The Problem It Solves](#the-problem-it-solves)
  - [Guiding Principles](#guiding-principles)
- [What Is Covered (15 Security Domains)](#what-is-covered-15-security-domains)
- [Standards & Pinned Identifiers](#standards--pinned-identifiers)
- [Supported Technology Stacks](#supported-technology-stacks)
- [Repository Structure](#repository-structure)
- [How to Install](#how-to-install)
  - [Google Antigravity / Gemini CLI](#1-google-antigravity--gemini-cli)
  - [Claude Code](#2-claude-code)
  - [Cursor IDE](#3-cursor-ide)
  - [Windsurf & Other Agent Environments](#4-windsurf--other-agentic-ides)
  - [Manual / Direct Prompt Injection](#5-manual--prompt-injection)
- [How to Use](#how-to-use)
  - [The 9-Phase Assessment Workflow](#the-9-phase-assessment-workflow)
  - [Ready-to-Use Prompts by Scenario](#ready-to-use-prompts-by-scenario)
  - [Pre-Delivery Verification Checklist](#pre-delivery-verification-checklist)
- [Report Contract & Deliverable Format](#report-contract--deliverable-format)
  - [Required Report Sections](#required-report-sections)
  - [Finding Structure](#finding-structure)
  - [Risk Rating & Prioritization](#risk-rating--prioritization)
- [Safety, Non-Destructive Execution & Secret Protection](#safety-non-destructive-execution--secret-protection)
- [Important Limitations](#important-limitations)

---

## Overview

**Universal Security Gap Analysis** transforms your AI coding assistant into a structured, evidence-based security reviewer. It audits application codebases, architectures, cloud configurations, API definitions, dependencies, and deployment manifests without running destructive exploit tests or making unwanted modifications to code.

Rather than producing hundreds of low-signal automated scanner alerts or superficial recommendations, this skill enforces a disciplined engineering methodology: **every finding must cite concrete file paths, lines, and symbols; trace attacker-reachable input flows; map directly to pinned industry standards; and propose root-cause remediation.**

---

## What This Skill Is For

### Core Purpose

- **Architecture & System Design Reviews**: Evaluate trust boundaries, public exposure, component separation, blast radius, and failure modes.
- **Code-Level Security Audits**: Deep-dive static inspection across backend APIs, frontend clients, cloud services, workers, and data stores.
- **Pre-Release & Pull Request Gatekeeping**: Review newly introduced features, sensitive endpoints, or infrastructure changes before shipping to production.
- **Identity, Access & Multi-Tenancy Audits**: Uncover authentication bypasses, privilege escalations, broken object-level authorization (BOLA/IDOR), and cross-tenant data leakage.
- **Cloud & Supply Chain Exposure Checks**: Identify misconfigured containers, unpinned dependencies, exposed secrets, insecure IaC templates, and CI/CD attack vectors.
- **Emerging AI/LLM Security Checks**: Audit applications integrating LLMs for prompt injection, excessive agency, unsafe tool execution, vector storage isolation, and sensitive data leakage.

### The Problem It Solves

| Traditional Scanners / Generic AI Prompts | Universal Security Gap Analysis Skill |
|---|---|
| Dumps hundreds of noisy, unvalidated warnings. | Filters for reachable, exploitable paths and realistic business impact. |
| Hallucinates requirement IDs and standards citations. | Uses version-pinned, verified identifiers (ASVS 5.0, OWASP API 2023, LLM Top 10 2026, CWE). |
| Often exposes sensitive keys or secrets in output. | **Zero secret exposure rule**: cites path, key name, and type; never prints secret values. |
| Treats missing documentation as confirmed vulnerabilities. | Explicitly distinguishes **Confirmed**, **Potential**, and **Unable to verify** states. |
| Offers generic advice ("sanitize input", "use HTTPS"). | Provides specific root-cause remediations and regression test plans. |

### Guiding Principles

1. **Evidence Over Assumptions**: Every finding must cite a file path, line range, symbol, configuration key, or scan result. If evidence is incomplete, it is labeled as `Potential` or `Unable to verify`.
2. **Passive, Safe & Non-Destructive by Default**: Never runs active exploits, DoS attacks, or external network scans. Does not alter repository files without express user instruction.
3. **Strict Secrets Redaction**: Never prints, echoes, or transmits secret strings or API keys. Always suggests rotation and secure vault storage.
4. **Applicability-Aware**: Does not enforce mobile controls on serverless APIs, or cloud IAM rules on on-prem desktop tools.
5. **Business Impact Prioritization**: Ranks vulnerabilities by practical exploitability, attacker preconditions, and blast radius—not arbitrary issue counts.

---

## What Is Covered (15 Security Domains)

During an assessment, the skill methodically traverses all applicable domains from `SKILL.md`:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   Universal Security Assessment Domains                │
├────────────────────────────┬─────────────────────────────┬─────────────┤
│ A. Architecture & Design   │ B. Identity & Authentication│ C. Authz &  │
│    - Trust boundaries      │    - Password policies, MFA │    Tenancy  │
│    - Component separation  │    - OAuth 2.0 / OIDC / JWT │    - BOLA   │
│    - Blast radius & defense│    - Session lifecycles     │    - BFLA   │
├────────────────────────────┼─────────────────────────────┼─────────────┤
│ D. Input Handling & Output │ E. API & Integrations       │ F. Crypto & │
│    - SQL/NoSQL injection   │    - Mass assignment, CORS  │    Data     │
│    - XSS, SSRF, traversal  │    - Webhooks, replay, rate │    - TLS    │
│    - File uploads/parsers  │    - Message brokers        │    - Keys   │
├────────────────────────────┼─────────────────────────────┼─────────────┤
│ G. Database & Storage      │ H. Frontend & Browser       │ I. Supply   │
│    - Least-privilege DB    │    - CSP, security headers  │    Chain    │
│    - Cache isolation       │    - Token storage risks    │    - SCA    │
│    - Object storage ACLs   │    - Source maps, env leaks │    - Lock   │
├────────────────────────────┼─────────────────────────────┼─────────────┤
│ J. Cloud & Containers      │ K. Logging & Monitoring     │ L. Resili-  │
│    - IAM & workloads       │    - Audit logging          │    ence     │
│    - Non-root containers   │    - Secret-free logs       │    - Limits │
│    - Network policies & IaC│    - Alerting readiness     │    - Retries│
├────────────────────────────┼─────────────────────────────┼─────────────┤
│ M. Secure SDLC             │ N. AI / LLM Features        │ O. Mobile / │
│    - Branch protection     │    - Prompt injection, RAG  │    IoT      │
│    - Automated gates & SLAs│    - Excessive agency       │    - Storage│
│    - Production changes    │    - Tool authorization     │    - IPC    │
└────────────────────────────┴─────────────────────────────┴─────────────┘
```

---

## Standards & Pinned Identifiers

To prevent hallucinations and maintain audit-grade rigor, all findings map to version-pinned standards verified in `references/pinned-standards.md` and `references/standards-and-mappings.md`:

- **OWASP ASVS 5.0.0** (Application Security Verification Standard): Primary control catalog across chapters V1–V17 (e.g., `OWASP ASVS 5.0.0 V13.3 Secret Management`).
- **OWASP API Security Top 10 (2023)**: Categories `API1:2023` (BOLA) through `API10:2023` (Unsafe Consumption of APIs).
- **OWASP Top 10 for LLM Applications (2026)**: Pinned identifiers `LLM01:2026` (Prompt Injection) through `LLM10:2026` (Improper Output Handling).
- **MITRE CWE**: Exact root-cause weakness IDs (e.g., `CWE-285`, `CWE-639`, `CWE-798`, `CWE-918`).
- **CVSS (Common Vulnerability Scoring System)**: Calculated strictly when all metrics are evidenced, accompanied by explicit vector strings.
- **NIST SSDF (SP 800-218)**, **NIST SP 800-53**, and **CIS Benchmarks**: Cited for development lifecycle and platform hardening baselines.

---

## Supported Technology Stacks

The skill automatically inspects stack-specific configuration, code, and entry points as cataloged in `references/entry-points.md`:

- **ASP.NET Core / .NET**: `Program.cs`, middleware ordering, `[AllowAnonymous]`, claim mappings, data protection keys, EF Core queries, `TrustServerCertificate`.
- **Node.js / Express / NestJS**: HTTP middleware chain, prototype pollution, deserialization, child processes, SSRF, JWT signing algorithms.
- **Python / FastAPI / Django / Flask**: Settings, ORM injection, authentication dependencies, template injection, debug flags, pickle/deserialization.
- **Java / Spring Boot**: Security configuration, method authorization, Actuator exposure, XML parsers, deserialization, Maven/Gradle dependencies.
- **Frontend (Angular, React, Vue, Next.js)**: Token storage (`localStorage` vs `HttpOnly` cookies), route guards vs server auth, `dangerouslySetInnerHTML`, `bypassSecurityTrust`, CSP headers.
- **Databases & Caches**: SQL Server, PostgreSQL, MySQL, Redis, MongoDB; parameterization, tenant scoping, least-privilege connection strings.
- **Containers & Orchestration**: Dockerfiles, Docker Compose, Kubernetes manifests, non-root execution, privilege escalation flags, secret volumes.
- **Cloud Infrastructure & IaC**: Terraform, CloudFormation, Bicep, Helm charts, AWS/Azure/GCP IAM roles and network ACLs.
- **AI / LLM Orchestration**: LangChain, LlamaIndex, Semantic Kernel, direct API clients, prompt templates, vector store retrieval filters, function-call tool permissions.

---

## Repository Structure

```
universal-security-gap-analysis/
├── SKILL.md                                 # Core agent instructions, safety rules, and 9-phase workflow
├── README.md                                # User guide, installation, stack support, and examples (this file)
├── references/
│   ├── assessment-checklist.md              # Phase 5 required coverage verification checklist
│   ├── entry-points.md                      # Stack-specific inspection files, patterns, and search symbols
│   ├── pinned-standards.md                  # Authoritative version-pinned identifiers (ASVS, API Top 10, LLM Top 10, CWE)
│   ├── risk-rating.md                       # Qualitative severity, confidence, CVSS, and priority matrices
│   └── standards-and-mappings.md            # Comprehensive reference map and standard citation rules
└── templates/
    └── security-assessment-report.md        # Strict section contract for generated security assessment reports
```

---

## How to Install

Install the skill in your preferred agentic environment. **Keep only one copy per project workspace to prevent configuration drift.**

### 1. Google Antigravity / Gemini CLI

Place the folder inside your workspace's skill directory:
```bash
# Workspace-level skill (recommended)
mkdir -p .agent/skills
cp -r /path/to/universal-security-gap-analysis .agent/skills/

# Or in your user-global Antigravity skills directory:
cp -r /path/to/universal-security-gap-analysis ~/.gemini/antigravity/builtin/skills/
```
Reload or restart your Antigravity session. The agent will discover `universal-security-gap-analysis`.

### 2. Claude Code

Install either in the project root or globally in your user profile:
```bash
# Per-project installation:
mkdir -p .claude/skills
cp -r /path/to/universal-security-gap-analysis .claude/skills/

# Global personal installation:
mkdir -p ~/.claude/skills
cp -r /path/to/universal-security-gap-analysis ~/.claude/skills/
```
Ensure `SKILL.md` is directly located at `.claude/skills/universal-security-gap-analysis/SKILL.md`.

### 3. Cursor IDE

Install in your project's `.cursor` configuration:
```bash
mkdir -p .cursor/skills
cp -r /path/to/universal-security-gap-analysis .cursor/skills/
```
Ensure the path resolves to `.cursor/skills/universal-security-gap-analysis/SKILL.md`.

### 4. Windsurf & Other Agentic IDEs

Copy the directory to your project's agent skills directory or rules folder, or register `SKILL.md` as a custom workspace rule/instruction.

### 5. Manual / Prompt Injection

If using a web interface or an LLM environment without native skill directories, package the folder or paste the text of `SKILL.md` along with relevant files from `references/` into your system instructions or initial conversation prompt.

---

## How to Use

### The 9-Phase Assessment Workflow

The skill executes in nine structured phases:

```
  Phase 1 ──► Establish Scope & Stack Discovery
  Phase 2 ──► Build Application Inventory & Attack Surface
  Phase 3 ──► Threat Model (STRIDE & Abuse Cases)
  Phase 4 ──► Select Applicable Security Standards
  Phase 5 ──► Assess 15 Security Domains (Checklist Verification)
  Phase 6 ──► Validate Findings & Trace Reachability
  Phase 7 ──► Rate Risk (Severity, Confidence, Priority, CVSS)
  Phase 8 ──► Produce Deliverable Report (Template Contract)
  Phase 9 ──► Construct Prioritized Remediation Roadmap
```

1. **Phase 1 — Scope & Discovery**: Identifies business workflows, languages, frameworks, cloud services, and authentications. Consults `references/entry-points.md`.
2. **Phase 2 — Inventory & Attack Surface**: Catalogs all endpoints, sensitive data paths, webhooks, admin panels, and trust boundaries.
3. **Phase 3 — Threat Modeling**: Applies STRIDE and application-specific abuse cases (BOLA, account takeover, cross-tenant leaks).
4. **Phase 4 — Standards Selection**: Selects verified identifiers from `references/pinned-standards.md`.
5. **Phase 5 — Domain Assessment**: Verifies items in `references/assessment-checklist.md` across domains A through O, marking them `Pass`, `Fail`, `Partial`, `Not assessed`, or `Unable to verify`.
6. **Phase 6 — Validation**: Verifies that untrusted input actually reaches the vulnerable sink and checks for compensating controls.
7. **Phase 7 — Risk Rating**: Assigns Severity (Critical to Info), Confidence (High/Medium/Low), and Priority (P0 to P3) using `references/risk-rating.md`.
8. **Phase 8 — Report Deliverable**: Generates the assessment conforming to `templates/security-assessment-report.md`.
9. **Phase 9 — Remediation Roadmap**: Formulates an actionable immediate, short-term, medium-term, and long-term fix schedule.

---

### Ready-to-Use Prompts by Scenario

#### Full Application Security Audit (Recommended First Prompt)
```text
Use the Universal Security Gap Analysis skill to review this repository. Start with application discovery and scope, then assess all applicable security domains. Do not run active tests or modify files. Produce an evidence-based report conforming to your template contract with confirmed and potential findings separated, severity, confidence, exact file references, standards mappings, and remediation steps. Clearly list anything you could not verify.
```

#### Pre-Release / Feature Pull Request Audit
```text
Review the changes in this branch using the Universal Security Gap Analysis skill. Focus on newly introduced API endpoints, input handling, and authorization checks. Check for any regression in tenant isolation or secret leakage, and summarize findings in a prioritized table.
```

#### Authentication, Sessions & Multi-Tenancy Deep Dive
```text
Perform an in-depth security gap analysis on our authentication and authorization architecture. Trace how tenant identifiers and user claims are validated across backend services and database queries. Check for BOLA/IDOR, privilege escalation, or session management flaws.
```

#### API & Backend Attack Surface Review
```text
Using the Universal Security Gap Analysis skill, audit our API endpoints. Focus on input validation, SSRF, mass assignment, rate limiting, CORS configuration, webhook signatures, and data serialization. Cite exact file paths and lines for all gaps.
```

#### Cloud, Containers & Infrastructure Hardening Review
```text
Assess our deployment configurations, Dockerfiles, docker-compose files, and cloud IaC templates using the Universal Security Gap Analysis skill. Identify insecure defaults, exposed management ports, privileged containers, and missing secrets manager integration.
```

#### AI / LLM Feature Security Review
```text
Review our LLM orchestration code and prompt templates against OWASP Top 10 for LLM Applications 2026. Focus on prompt injection vectors, tool/function authorization, vector retrieval tenant isolation, and sensitive data leakage.
```

#### Generate a Saved Report File
```text
Use the Universal Security Gap Analysis skill to review this application and output the full assessment report into a markdown file named SECURITY-ASSESSMENT.md in the workspace root.
```

---

### Pre-Delivery Verification Checklist

Before accepting or delivering an assessment, the skill validates the following 10 pre-delivery conditions:

1. Every item in `references/assessment-checklist.md` has a recorded status and evidence (or reason skipped).
2. Every finding cites an exact file path, line range, symbol, or configuration key.
3. No secret values appear in the text (citations name the file, key, and secret type only).
4. Every finding is explicitly classified as `Confirmed` or `Potential`.
5. CVSS vectors and scores appear only when all metrics are evidenced.
6. Positive security controls and unverified areas are explicitly listed.
7. Standards identifiers strictly match `references/pinned-standards.md`.
8. Multi-application workspaces explicitly state which sub-projects were not reviewed.
9. No source, configuration, or infrastructure files were modified.
10. The report is output in chat or canvas, and only written to a file if explicitly requested.

---

## Report Contract & Deliverable Format

The output follows the section contract specified in `templates/security-assessment-report.md`.

### Required Report Sections

1. **Executive Summary**: High-level risk posture, count of critical/high/medium/low findings, and key themes.
2. **Scope and Methodology**: Components inspected, explicit exclusions, access limitations, and unverified areas.
3. **Application Inventory**: Table of components, languages, frameworks, exposure, and sensitive data handled.
4. **Architecture and Attack Surface**: Trust boundaries, external integrations, and sensitive data flows.
5. **Standards and Coverage**: Status of each evaluated standard (`Assessed`, `Partially assessed`, `Not assessed`, `Unable to verify`).
6. **Findings Summary**: Master table ranking issues by ID, title, status, severity, confidence, component, and priority.
7. **Detailed Findings**: In-depth analysis for each identified issue (format below).
8. **Positive Security Controls Observed**: Effective security mechanisms and defensive practices found in the codebase.
9. **Not Assessed / Unable to Verify**: Gaps where source code or configuration was unavailable or inconclusive.
10. **Remediation Roadmap**: Chronological action plan categorized into P0 (Immediate), P1 (Urgent), P2 (Near-term), and P3 (Backlog).
11. **Conclusion & Residual Risk**: Bounded summary of evaluated scope and remaining operational risks.

### Finding Structure

Each finding in Section 7 is detailed with the following structure:

```markdown
### [SEC-001] Missing Authorization on Tenant Document Endpoint

- Status: Confirmed
- Severity: High
- Confidence: High
- Priority: P1
- Affected component: `src/Controllers/DocumentsController.cs` (lines 45–62)
- Standard mapping: OWASP API Security Top 10 API1:2023 Broken Object Level Authorization, OWASP ASVS 5.0.0 V8.3 Operation Level Authorization, CWE-639
- Preconditions: Authenticated user with standard permissions.
- Attack scenario: An attacker changes the `documentId` route parameter to an ID belonging to another organization. The service queries the database solely by primary key without checking tenant ownership.
- Technical impact: Unauthorized read access to confidential documents across tenant boundaries.
- Business impact: Regulatory non-compliance (GDPR/HIPAA breach), loss of customer trust, legal liability.
- Root cause: Repository method `GetByIdAsync(id)` does not filter by `tenantId`.
- Recommended remediation: Scope the query to the authenticated tenant: `GetByIdAndTenantAsync(id, currentUser.TenantId)`.
- Validation and regression tests: Add an automated unit/integration test asserting HTTP 403 or 404 when querying an existing document with a mismatched tenant token.
```

### Risk Rating & Prioritization

#### Severity vs. Priority
- **Severity** measures the inherent technical impact and exploitability under realistic conditions (Critical, High, Medium, Low, Informational).
- **Priority** guides remediation sequencing:
  - **P0 (Immediate)**: Active compromise, hardcoded live credentials, or easily exploitable critical flaws.
  - **P1 (Urgent)**: High-impact authorization bypasses, injection flaws, or remote compromise paths.
  - **P2 (Near-Term)**: Medium-risk issues, missing defense-in-depth controls, or systemic hardening gaps.
  - **P3 (Backlog)**: Low-risk observations, best-practice deviations, or informational improvements.

#### Confidence Levels
- **High**: Direct code evidence demonstrates the vulnerable execution path.
- **Medium**: Strong code pattern suggests a flaw, but full reachability or compensating filters cannot be proven from available files.
- **Low**: Inferred risk requiring external environment verification.

---

## Safety, Non-Destructive Execution & Secret Protection

- **Passive Analysis**: Operates strictly via static code and configuration analysis. It does not initiate port scans, send live exploit payloads, test SQL injection against active databases, or perform brute-force attacks.
- **Zero Secret Exposure**: If credentials, API keys, or private certificates are discovered in source code or configuration files, the skill will **never** print the secret value. It will report only the file path, configuration key name, and secret type, alongside an immediate recommendation for secret rotation and vault migration.
- **Untrusted Content Isolation**: Code comments, documentation, and external scan logs are treated as untrusted data; any malicious prompt injection contained inside analyzed files will be ignored.
- **Code Preservation**: Does not modify repository code, configurations, or infrastructure templates unless the user explicitly requests a patch.

---

## Important Limitations

- **Not an Authorized Penetration Test**: Static analysis cannot detect runtime-only anomalies, dynamic race conditions under heavy load, or network-level firewall behavior.
- **Not a Compliance Guarantee**: A clean assessment does not constitute formal ISO 27001, SOC 2, PCI-DSS, or HIPAA certification.
- **Scope Bounded**: Findings are strictly limited to the files, documentation, and configuration made accessible within the workspace session. Unknown external dependencies and infrastructure are marked as `Unable to verify`.