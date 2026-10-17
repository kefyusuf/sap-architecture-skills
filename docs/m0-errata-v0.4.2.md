# M0 v0.4.2 — Documentation Erratum and Review Handoff

**Date:** 2026-10-17  
**Scope:** Only P2P-001 evidence/acceptance correctness.  
**Status:** `READY_FOR_HUMAN_REVIEW` — not accepted.  
**Runtime evidence:** none; S01–S09 remain `NOT_RUN`.

## Corrected inconsistency

In v0.4.1 the S07 verification row incorrectly requested confirmation of **unchanged PO history** for movement 103. This contradicted the same package's process narrative and the underlying SAP-007/SAP-016 documentation.

The SAP Help article *Posting a Goods Receipt into Goods Receipt Blocked Stock* (SAP-007) states that movement 103 creates a material document but no accounting document, does not increase total valuated stock or normal stock types, **increases GR blocked stock recorded in purchase-order history**, and **does not reduce open PO quantity** in the stated scenario.

Changes in v0.4.2:

- `research/procure-to-pay/verification-matrix.md` S07: expect an updated PO-history blocked-stock quantity, without reduction of open PO quantity.
- `research/procure-to-pay/claim-register.md` P2P-C06: explicitly distinguishes both outcomes.
- `README.md`: records this erratum in the M0 deliverable index.

**The future release/105 posting remains an unanswered runtime question.** No new SAP scenario, architecture, Agent Skill, source, or implementation has been added.

## Evidence

- SAP-007: https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/91b21005dded4984bcccf4a69ae1300c/d963bd534f22b44ce10000000a174cb4.html
- SAP-016: https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/91b21005dded4984bcccf4a69ae1300c/ac63bd534f22b44ce10000000a174cb4.html

The indexed SAP Help entries identify **S/4HANA on-premise 2025 FPS01 (Feb 2026)**. Exact `?version=2025.001` links still require human confirmation in a compatible reader. Direct URL failure must not be described as a completed URL resolution check.

## Gate disposition

- Corpus structure / references / scenario statuses: checked programmatically in this delivery.
- Independent SAP-domain human review: `PENDING`.
- Authorized SAP runtime verification: `NOT_RUN` (9/9).
- Repository / PR: `NOT_CREATED` (not accessible via connected GitHub during this check).
- M1 authorization: `NOT_GRANTED`.

**Human reviewer decision:** `PENDING` — this patch does not substitute for independent review.
