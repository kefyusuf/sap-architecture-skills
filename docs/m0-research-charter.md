# M0 Research Charter

**Stage:** M0 — bounded research foundation  
**Target system:** SAP S/4HANA, initially on-premise documentation edition **2025 FPS01 (Feb 2026)**  
**First process:** Procure-to-Pay (Purchasing / Inventory Management / Invoice Verification; MM↔FI)

## Product goal

Build an evidence-bound knowledge foundation that can later supply provider-independent Agent Skills for two separate questions:

- **SAP analysis:** What does a stated SAP product/version do, under which configuration or organizational assumptions?
- **Independent ERP design:** Which domain concepts and observable behavior can inform an original, framework-independent ERP design?

The second answer must never be represented as a reproduction of proprietary SAP implementation details.

## Users

SAP functional and technical consultants, ABAP developers, solution architects, and developers designing their own ERP systems.

## Research questions (M0)

1. How do purchase orders, goods receipts, invoice receipts, and purchasing history relate?
2. Under which documented conditions do stock valuation and the GR/IR clearing account change?
3. How do partial receipts, invoice-before-receipt ordering, tolerances, blocked stock, and reversals affect the flow?
4. What is documented, what needs an authorized SAP environment, and what is merely a proposed independent ERP behavior?

## In scope

- Source inventory with explicit URLs, authority and version.
- Evidence status for each behavioral claim.
- One representative process model and tightly bounded scenario matrix.
- Explicit deviations and unanswered questions.
- Future skill input/output expectations, but no skill implementation.

## Out of scope

- All other SAP modules; general-purpose ERP architecture or framework selection.
- Real SAP system integration; direct access to ABAP internals, HANA tables, or customer landscapes.
- Proprietary binaries and unapproved runtime observation.
- Accounting/legal correctness for any jurisdiction beyond the illustrative scenario.
- Skill runtime, LLM/provider adapters, MCP server, automatic code generation, autonomous SAP writes, transports, deployment.

## Non-negotiable rules

1. A document-backed claim is **not** a live-verified system outcome.
2. Name the SAP product, release and configuration scope, or mark them unknown.
3. Do not infer ABAP classes, tables, execution order or persistence mechanisms from network/UI behavior.
4. If behavior depends on customizing, articulate the branch, not a universal rule.
5. Keep SAP claims and independent design proposals in separate sections/artifacts.
6. Mark synthetic examples as synthetic; do not pass generated results off as observed output.
7. Preserve company/customer data privacy; use authorized test systems only.

## M0 acceptance criteria

- [x] A single, bounded process and product/release are selected.
- [x] Every substantive SAP claim in the first process has an identified source or is explicitly UNKNOWN; contextual-only source limitations are stated.
- [x] Invoice-before-GR, partial GR, reversal, blocked-stock and tolerance branches are represented.
- [x] Documented vs. observed vs. proposed statuses are unambiguous.
- [x] The current workbench boundary is documented.
- [ ] Human review of source applicability and context (on-premise variant and release; Retail and Maintenance boundaries) completed.
- [ ] Scenario matrix reviewed against an authorized SAP system or clearly accepted as documentation-only scope.

**M0 status:** Evidence review completed for a documentation-only candidate; human approval and live verification remain outstanding. See [`m0-source-review.md`](m0-source-review.md).

## Next milestone (deferred)

M1 may add a single Agent Skills specification-compliant `SKILL.md` for SAP business-process analysis, backed by M0 research. This is not part of M0.
