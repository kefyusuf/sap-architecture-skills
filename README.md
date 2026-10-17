# SAP Architecture Skills — M0 Research Foundation

**Status:** M0 documentation-only, desk-audited candidate (v0.4.2; NOT formally accepted, NOT an implemented Agent Skills collection).

## Purpose

Establish a traceable, vendor-neutral research foundation for:

1. Explaining SAP enterprise architecture and business behavior accurately.
2. Translating verified enterprise concepts into independent ERP design guidance.

SAP-specific observations and proposed independent designs must remain distinguishable. This project is not an SAP clone, a reimplementation of SAP internals, or an official SAP product.

## M0 deliverables

| Document | Purpose |
|---|---|
| [`docs/m0-research-charter.md`](docs/m0-research-charter.md) | Goal, boundary, research questions, quality gate |
| [`docs/evidence-policy.md`](docs/evidence-policy.md) | Evidence classification and claim controls |
| [`docs/m0-source-review.md`](docs/m0-source-review.md) | Source applicability review, corrections and remaining gates |
| [`docs/m0-desk-audit-v0.3.md`](docs/m0-desk-audit-v0.3.md) | Historical v0.3 assistant desk audit and review rubric |
| [`docs/m0-acceptance-review-v0.4.md`](docs/m0-acceptance-review-v0.4.md) | Historical v0.4 source corrections, gate verdict and sign-off handoff |
| [`docs/m0-reassessment-v0.4.1.md`](docs/m0-reassessment-v0.4.1.md) | Historical evidence recheck, source access limits and remaining review gate |
| [`docs/m0-errata-v0.4.2.md`](docs/m0-errata-v0.4.2.md) | Corrects S07 PO-history invariant and documents preflight outcome |
| [`docs/decisions/ADR-0001-independent-knowledge-repository.md`](docs/decisions/ADR-0001-independent-knowledge-repository.md) | Project separation decision |
| [`research/sources.md`](research/sources.md) | Source register with exact URLs and version context |
| [`research/procure-to-pay/process.md`](research/procure-to-pay/process.md) | First bounded research scenario |
| [`research/procure-to-pay/claim-register.md`](research/procure-to-pay/claim-register.md) | Testable SAP behavior claims |
| [`research/procure-to-pay/verification-matrix.md`](research/procure-to-pay/verification-matrix.md) | Scenario evidence and acceptance questions |

## Boundaries

- Focus: one procurement flow linking MM and FI, initially SAP S/4HANA on-premise documentation (2025 FPS01, Feb 2026).
- On-premise reference scope does not imply universal behavior; invoice-verification mode, product submodule, stock type and valuation affect outcomes.
- No live SAP access has been used. No runtime observation or reverse-engineering execution has occurred.
- No ERP implementation, SAP connector, provider adapter, MCP runtime, autonomous SAP write, transport, or deployment in M0.
- No `SKILL.md` has been advertised as production-ready; Agent Skills are planned only after M0 passes its quality gate.
- Any future REA use requires authorization and explicit handling of sensitive information.

## Next gate

Human-review the M0 source findings and either accept a documentation-only baseline or demand runtime evidence; then consider **M1: the first `sap-business-process-analysis` Agent Skill** using this research as a reference. No implementation is authorized by this M0 package alone.

## Relationship to existing work

[`kefyusuf/sap-agent-workbench`](https://github.com/kefyusuf/sap-agent-workbench) remains a separate workbench with its own milestones and change controls. Future read-only consumption of verified skill/knowledge material is a possible integration, **not implemented**.
