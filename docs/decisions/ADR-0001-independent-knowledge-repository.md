# ADR-0001: Independent research and skill repository

**Status:** Adopted for M0 baseline (no remote repository created)  
**Date:** 2026-10-17

## Context

The existing `kefyusuf/sap-agent-workbench` is a provider-independent SAP engineering agent workbench with its own verified M0–M3 and selected subsequent adapter work. The new goal includes public education on SAP behavior and independent ERP design, which is broader than that workbench's product boundary.

## Decision

Develop a stand-alone, provider-neutral SAP/ERP research corpus, which can later produce Agent Skills. Its name **`sap-architecture-skills` is provisional**. Keep the workbench unchanged. In the future, a narrow read-only dependency on versioned research or skills may be evaluated independently.

## Alternatives

- Put all material in `sap-agent-workbench`: rejected for now due to scope coupling and diverging audiences.
- Begin with a full ERP reference implementation: rejected as premature.
- Build an MCP runtime first: rejected; no knowledge validation yet.

## Consequences

- M0 produces only research artifacts and a quality gate.
- Skills remain optional consumers of evidence rather than owners of facts.
- Versioned SAP claims are separated from transferable ERP patterns.
- Repository creation, publishing, licensing, runtime integration and deployment need later explicit decisions.
