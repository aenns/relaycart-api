# RelayCart API: product scope

## Status

Design baseline approved. Implementation has not started; no functioning features, pipelines, releases or deployments are claimed.

## Purpose

The secure order and inventory service, owning business transactions, durable workflows and authorized evidence retrieval.

## Planned stack

Python, FastAPI, PostgreSQL and MongoDB

## Engineering contract

- This repository owns its source, checks, documentation and releases.
- Public interfaces are versioned and tested.
- The development harness is optional tooling, not a runtime dependency.
- Examples and demonstration data are synthetic.
- Architecture decisions and exact local commands will be documented
  as their implementation checkpoints pass.

## Approved design baseline

- A modular FastAPI service owns order/inventory transactions, identity/object authorization, isolated sandbox capabilities and authorized evidence retrieval.
- PostgreSQL is authoritative; MongoDB holds flexible documents and replayable read projections, with no cross-store transaction guarantee.
- Durable SQL jobs/outbox, scoped idempotency and replay/version guards support restart recovery and duplicate-effect protection.
- Free-host job advancement is bounded and request-driven; sleeping services do not guarantee due-time execution.
- Gateway service proof and end-user authorization are independently checked. Shared SQL admission budgets complement gateway per-instance limits.

## Required engineering evidence

Each component has applicable automated checks: unit, integration, functional/contract and security tests; dependency/container/IaC scanning and secret detection where relevant. Main builds, deployments, scheduled regressions and availability observations are distinct. Build/candidate numbers increment automatically; stable semantic versions are calculated from reviewed changes and promoted through the release-readiness gate. Retain immutable artifacts, sanitized evidence and compatible rollback instructions. These are requirements, not implementation claims.

Use the portable harness during development once its core is usable; record any bypasses and feedback. The application does not import the harness at runtime.

## Design references

- [Harness release scope](https://github.com/aenns/portable-ai-harness/blob/96cc799/docs/release-scope.md)
- [Harness architecture](https://github.com/aenns/portable-ai-harness/blob/40476cf/docs/architecture.md)
- [Harness configuration and commands](https://github.com/aenns/portable-ai-harness/blob/99d47a1/docs/configuration-and-commands.md)
- [RelayCart system architecture, revision 4](https://github.com/aenns/relaycart-docs/blob/f5cf12d/docs/architecture/system.md)
