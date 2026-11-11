# Stack entry points

Read this after Phase 1 names the stack. Open only the matching sections. Search for the listed symbols. A missing file means that control was not found at that path. It does not prove the control exists somewhere else. Record files that were not opened when the tree is large.

These prompts are places to look. Do not treat a match as a finding until Phase 6 traces an attacker-controlled input to the behavior.

## Any application

Open configuration and deployment files first:

- `appsettings*.json`, `*.env`, `*.env.*`, `local.settings.json`, `docker-compose*.yml`, `Dockerfile*`, `wrangler*`, `*.csproj`, `package.json`, `angular.json`

Search:

- `AllowAnonymous`, `AddAuthentication`, `AddAuthorization`, `UseCors`, `SigningKey`, `ConnectionString`, `Password`, `ApiKey`, `TrustServerCertificate`, `Seed`, `RateLimit`, `innerHTML`, `bypassSecurityTrust`

## ASP.NET Core

Open:

- `Program.cs` or `Startup.cs`
- `appsettings.json` and every `appsettings.*.json`
- Controllers, hubs, and minimal-API maps
- Authentication, seeding, and `DependencyInjection` classes
- `Dockerfile` and `docker-compose*.yml`

Check:

- Middleware order for authentication, authorization, and CORS
- JWT issuer, audience, lifetime, signature, and claim mapping
- Access tokens copied from the query string
- Development user seeding and the environment that enables it
- Migrations or schema changes executed by the running app
- Database account privilege and `TrustServerCertificate`
- `[AllowAnonymous]` routes and role lists wider than the service-layer check
- Data Protection key persistence and where decrypted secrets are sent
- Exception handlers that return or log upstream response bodies

## Angular, React, and other browser clients

Open:

- `index.html` and server or worker config
- Auth store, HTTP interceptor, and route guards
- `environment*.ts`, `Dockerfile`, `package.json`

Check:

- Where the access token is stored
- Route guards used as if they were server authorization
- `innerHTML`, `bypassSecurityTrust`, `document.write`, and `eval`
- Content Security Policy and other security headers
- A development server used as the container command

## Node.js

Open the HTTP entrypoint, middleware registration, and `package.json` / lockfile. Check middleware order, prototype pollution, unsafe deserialization, child processes, SSRF, and secrets in config.

## Java / Spring

Open security configuration, controller and method authorization, `application*.yml`, and actuator exposure. Check deserialization and dependency versions.

## Python / FastAPI / Django

Open the app factory, authentication dependencies, settings, and debug flags. Check ORM or raw queries, template and upload handling, and unsafe serialization.

## SQL Server or PostgreSQL

Open connection strings and migration code. Check the login's privileges, parameterization, tenant predicates, TLS settings, and exposed management ports.

## Containers and compose

Open every `docker-compose*.yml` and `Dockerfile`. Check the default environment, published ports, passwords in the file, privileged database users, and whether the process command is a dev server.

## Cloud

Open IAM, network, storage, and secret-store definitions only when those files exist. Do not assume a cloud account from a local compose file.

## AI / LLM features

Open prompt templates, the orchestrator, the provider catalog, and the vector-store client. Check untrusted text joined into prompts, tenant metadata on vectors, base-URL allowlists, and whether model output can call a tool.
