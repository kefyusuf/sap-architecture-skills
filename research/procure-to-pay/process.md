# P2P-001 — Purchase Order → Goods Receipt → Supplier Invoice

**Status:** documentation-backed process model; **not executed in SAP**.  
**Target:** SAP S/4HANA on-premise, 2025 FPS01 (Feb 2026), procurement / inventory / invoice verification.  
**Example conditions (synthetic):** externally procured, inventory-managed and valuated material; no special stock, account assignment, taxes, freight, discounts or currency conversion. Quantity 100 units, PO unit price 100 hypothetical currency units (CU). Actual accounting depends on configuration and valuation method.

## Business actors and artifacts

- Purchaser creates purchase order (PO) items for supplier/material/plant.
- Warehouse staff posts goods receipt against the PO; the scoped procedure creates the related material document (`SAP-014`, `SAP-016`).
- Accounts payable verifies supplier invoice with reference to the purchase order/receipt depending on configured verification method.
- Purchasing history associates subsequent transactions with the PO item (`SAP-006`).

## Baseline branch: GR before IR

```text
Purchase Order: 100 units × 100 CU
        |
        v
Goods Receipt: 60 units (partial; movement type 101 in the scoped MM-IM PO-to-warehouse branch (`SAP-014`, `SAP-016`))
        |
        +--> Material document / stock movement
        +--> Valuation reference: 60 × 100 CU = 6,000 CU
        |    under the scoped example assumptions
        v
Supplier invoice: 60 units at 100 CU
        |
        +--> Invoice verification; GR/IR clearing account implications
        v
Purchasing history & reconciliation
```

Supported documentation: `SAP-001` (GR/IR and receipt ordering), `SAP-002` (pre-invoice valuation based on order), `SAP-013` (PO-based IV across multiple partial deliveries), `SAP-014` (movement 101 for this MM-IM scenario), `SAP-006` (PO history), `SAP-016` (material/financial document results and important branches). `SAP-003` (Retail) and `SAP-010` (multiple account assignment) are contextual comparisons only and do not define the baseline behavior.

## Accounting illustration (not a universal SAP posting specification)

For a valuated receipt with appropriate account determination, one conceptual posting arrangement is:

- At goods receipt: **debit inventory 6,000 CU; credit GR/IR 6,000 CU**.
- At supplier invoice: **debit GR/IR 6,000 CU; credit vendor payable 6,000 CU**.

These are **illustrative conceptual entries**, not observed accounting documents. Actual account determination, pricing, valuation, taxes, price differences and whether accounting is posted at receipt depend on the materials and system settings. Account numbers and SAP internals are intentionally omitted.

## Alternative branch: IR before GR

Invoice can precede goods receipt **under PO-based invoice verification**. SAP documentation describes a different valuation basis and GR/IR clearing order, with additional complications for partial invoices and price differences (`SAP-001`, `SAP-002`). **With GR-based invoice verification, the receipt comes first** (`SAP-015` with specialized corroboration from `SAP-009`); do not teach unrestricted invoice-first behavior.

**Synthetic contrast (not a real posting):** PO 100 @ 10 CU, invoice first for 50 @ 12 CU, then GR 70 -> SAP-002 documentation illustrates valuation 50 × 12 + 20 × 10 = 800 CU in the relevant branch; do not generalize accounting document lines from this valuation example.

## Alternative branch: blocked-stock receipt

Receipt into GR blocked stock with movement type 103 in the documented on-premise process creates a material document but no FI accounting document; neither total valuated stock nor ordinary stock types are updated. The PO history tracks the blocked-stock quantity, while the open PO quantity is not reduced by this step (`SAP-007`). It must not be modeled as an ordinary valuated 101 receipt.

## Reversal branch

MM permits goods-movement reversal (`SAP-011`), and movement type 102 appears in particular documented Maintenance Management cancellation cases (`SAP-005`). Do not treat a reversal as deletion of the historical document or assume it is always permitted in any subsequent process state. Test exact preconditions later in an authorized environment.

## Boundary to an independent ERP design

The following are **potential design objectives**, NOT SAP claims: an idempotency key on posting requests; atomic application transaction for local ledger/stock records; an append-only audit trail; explicit `PostingCommand` state; a relational DB schema; optimistic locking. These concepts belong in a future ERP-design artifact and must be justified independently.
