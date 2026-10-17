# P2P Claim Register

**No live SAP observations have been made.** `DOCUMENTED` means backed by a specified source, not verified in a target landscape.

| ID | Claim (scope-limited) | Status | Evidence | Caveat / counterexample |
|---|---|---|---|---|
| P2P-C01 | For PO-based invoice verification, invoice receipt can precede or follow goods receipt; NOT a universal rule for GR-based verification. | `DOCUMENTED` | SAP-001 | Valuation and clearing behavior depend on ordering and prices. |
| P2P-C02 | For the illustrated GR-before-invoice branch, goods receipt value can be calculated from received quantity and net PO unit price. | `DOCUMENTED` | SAP-002 | Does not cover all account assignments, valuation modes or price differences. |
| P2P-C03 | In the documented S/4HANA PO-based invoice-verification process, a PO item can have several partial deliveries and the items can be invoiced together. | `DOCUMENTED` | SAP-013 | Does not imply identical behavior for GR-based verification, non-valuated items, special stock, or every PO item category. |
| P2P-C04 | PO history includes goods and invoice receipts against a PO item. | `DOCUMENTED` | SAP-006 | Availability/exact technical usage of CDS view depends on SAP deployment and release. |
| P2P-C05 | MM supports reversing goods movements, and certain 102 reversal scenarios are documented. | `DOCUMENTED` | SAP-005, SAP-011 | 102 detail from Maintenance Management; do not assume every 101 posting can be reversed after invoice. |
| P2P-C06 | Movement 103 can post PO receipts into GR blocked stock with a material document but no FI document and no update to total valuated stock or ordinary stock types; **PO history records GR blocked-stock quantity while open PO quantity is not reduced** in the documented scenario. | `DOCUMENTED` | SAP-007 | Not equivalent to 101; applicability depends on scenario. |
| P2P-C07 | Configured invoice variance tolerances may block an invoice **for payment** while the accounting invoice is still posted. | `DOCUMENTED` | SAP-004 | On-premise S/4HANA 2025 FPS01; not unconditional rejection of the invoice or all variance outcomes. |
| P2P-C08 | SAP automatically de-duplicates identical repeated goods-receipt API requests. | `UNKNOWN` | none | Do not assume; may depend on API, request keys or transaction usage. |
| P2P-C09 | All over-receipts are rejected unconditionally. | `UNKNOWN` | none | Must investigate configured overdelivery tolerance; do not assert. |
| P2P-C10 | SAP always posts the two journal entries shown in the illustrative process. | `UNKNOWN` | none | Entries are a simplification; no evidence for an unconditional rule. |
| P2P-C11 | A particular ABAP class or HANA table is called/written by the Fiori flow. | `UNKNOWN` | none | UI observation cannot prove backend internals. |
| P2P-C12 | An independent ERP should protect posting via idempotency keys and transactional consistency. | `PROPOSED` | future design rationale | Not a fact about SAP. |
| P2P-C13 | With GR-based invoice verification, the relevant goods receipt must occur before the invoice; GR-based invoices reference receipt items. | `DOCUMENTED` | SAP-009 (explicit prerequisite in market-price article), SAP-013 (receipt-reference mode), SAP-015 (QM corroboration) | The prerequisite is explicit in SAP-009 but that article covers market-price determination; SAP-015 confirms it in QM context. This is a documentation-level claim, not a finding about the configuration or behavior of any particular SAP landscape. |
| P2P-C14 | Purchase-order item data model contains overdelivery tolerance and unlimited-overdelivery indicators. | `DOCUMENTED` | SAP-012 | Field availability does not prove a specific overdelivery is accepted or rejected; S05 remains UNKNOWN. |
| P2P-C15 | The S/4HANA MM-IM PO goods-receipt procedure provides movement type 101 for goods intended for warehouse or consumption. | `DOCUMENTED` | SAP-014 | This does not prove identical financial posting for warehouse versus consumption or special-stock scenarios. |
| P2P-C16 | In the documented MM-IM goods-receipt result description, a normal valuated warehouse GR produces a material document and relevant FI document, updating stock; a consumption receipt and GR blocked stock follow different branches. | `DOCUMENTED` | SAP-016 | Do not generalize the stock or FI outcome to 103, special stocks, non-valuated materials or all account assignments. |

## Review disposition

- Documentation-only process statements can be taught with their conditions and citations.
- Unknowns cannot be smuggled into Agent Skill instructions as SAP facts.
- Runtime and backend mechanics stay unverified until directly inspected with authorization.
