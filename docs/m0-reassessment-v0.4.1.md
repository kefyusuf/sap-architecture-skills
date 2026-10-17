# M0 v0.4.1 — Evidence Traceability Reassessment

**Review date:** 2026-10-17  
**Scope:** P2P-001 only; no new SAP module, Agent Skill, connector or ERP implementation.  
**Gate state:** `READY_FOR_HUMAN_REVIEW` — **NOT ACCEPTED**.  
**Live runtime verification:** none, all 9 scenarios `NOT_RUN`.

## Purpose of this patch

The previous v0.4 package remained a valid **documentation-only candidate**, not a human-accepted or SAP-tested baseline. This reassessment tightens two evidence boundaries rather than moving to M1.

1. **S03 invoice-before-goods-receipt:** `SAP-001` and `SAP-002` directly support the PO-based invoice-first branch; `SAP-009` and `SAP-015` are evidence for the *opposite GR-based prerequisite* and must not be counted as independent support for invoice-first permission. The verification-matrix row now labels those counterexamples separately.
2. **P2P-C13 GR-based sequencing:** `SAP-009` explicitly states the goods-receipt-first requirement in its market-price article; `SAP-013` explains goods-receipt-referenced invoices; `SAP-015` corroborates the restriction in a quality-inspection context. None of these proves the user's own PO item settings or release.
3. **SAP Help version links:** Several exact documentation URLs ending in `?version=2025.001` could not be opened by the browsing environment even though indexed official article results showed the title/content and, for key pages, **2025 FPS01 (Feb 2026)**. Do not mark all URLs as directly accessible or archived. Reviewer must open them in a compatible environment and confirm the visible edition.

## Source-level checkpoint (official SAP Help indexed content)

| Source | Specific claim checked | Desk observation | Citation mode / limitation |
|---|---|---|---|
| SAP-001 | PO-based IR can precede GR in the described process | Matched SAP Help *Invoices for Purchase Orders* | Indexed article; exact versioned link not directly fetched |
| SAP-002 | Documented 50 × 12 + 20 × 10 = 800 valuation illustration | Matched SAP Help *Goods Receipt for a Purchase Order* | Indexed article; exact versioned link not directly fetched |
| SAP-004 | Upper invoice variance tolerance may block payment, not posting | Matched SAP Help *Blocking Invoices* | Official article indexed as 2025 FPS01; environment-specific tolerance still unknown |
| SAP-007 | 103 material doc; no FI doc/valuated stock; open PO quantity unchanged | Matched SAP Help *Posting a Goods Receipt into Goods Receipt Blocked Stock* | Official article indexed as 2025 FPS01; exact link in source register requires manual open |
| SAP-013 | PO-based invoices can settle PO items across multiple partial deliveries | Matched SAP Help *Invoice Processing* | Indexed article; review edition before sign-off |
| SAP-014 | Movement 101 for scoped PO warehouse/consumption receipts | Matched SAP Help *Entering a Goods Receipt for a Purchase Order* | Official article indexed as 2025 FPS01 |
| SAP-015 | QM-specific statement about GR-based ordering | Matched SAP Help *Variance in an Invoice Item* | QM-scoped example; cannot be treated as universal runtime observation |
| SAP-016 | Receipt document, stock update and accounting branch distinction | Matched SAP Help *Results of a Goods Receipt Posting* | Official article indexed as 2025 FPS01 |

This is **not** a fresh assertion that every source row (SAP-001..SAP-016, STD-001, REA-001) passed link validation. All remain subject to independent source review. No SAP system was accessed.

## Reviewer verification work (outstanding)

- [ ] Open each primary source link from `research/sources.md`, record actual resolved URL, article title, displayed product/release and access date; flag redirects, missing content or edition mismatch.
- [ ] Confirm S03 uses PO-based invoice verification, while C13 is a separate GR-based prerequisite; review corresponding scope notes.
- [ ] Confirm that the 101/103 differences apply to the described valuated warehouse versus GR blocked stock branches and not all goods movements.
- [ ] Examine all claim statuses and ensure `UNKNOWN`/`PROPOSED` entries cannot be represented as observed SAP facts.
- [ ] Confirm documentation-only acceptance is permitted despite 9/9 unexecuted runtime cases.
- [ ] Record reviewer identity, date, approval decision, and any changes requested. Do not represent assistant/source review as independent human sign-off.

**Review decision:** `PENDING`  
**Reviewer:** `PENDING`  
**M0 acceptance:** `NOT_GRANTED`  
**M1 authorization:** `NOT_GRANTED`  
**Remote repository / PR:** `NOT_CREATED` (checked against connected GitHub 2026-10-17).
