# P2P Verification Matrix (M0)

**Execution:** None. The table defines future tests, not SAP test results.  
**Evidence classes:** `DOCUMENTED` = verified in cited documentation; `OBSERVED` = executed and captured in authorized system (none yet).

| Scenario | Input / variation | Documentation status | Runtime status | Question / acceptance observation |
|---|---|---|---|---|
| S01 baseline | PO 100 @ 100 CU, GR 60, invoice 60; PO-based IV | SAP-001, SAP-002, SAP-013, SAP-014, SAP-016 | NOT_RUN | Identify PO/GR/IR document links and scoped valuation/posting effects. |
| S02 split receipt | PO 100, GR 60 then GR 40 | SAP-013 (general PO-based IV); SAP-003/010 contextual | NOT_RUN | Observe multiple material docs and PO item receipt totals. |
| S03 invoice first | PO-based IV (NOT GR-based), PO 100, IR partial at different unit price, then GR | SAP-001, SAP-002 (direct support); SAP-009, SAP-015 (GR-based counterexample only) | NOT_RUN | Determine valuation/GR/IR differences under specific settings; the GR-based counterexample cannot serve as evidence for invoice-first permission. |
| S04 tolerance | Price or quantity variance on invoice | SAP-004 (same on-premise edition) | NOT_RUN | Determine local on-premise tolerance configuration and blocking behavior. |
| S05 overdelivery | Receive 110 against PO 100 | UNKNOWN | NOT_RUN | Which configured overdelivery tolerance/unlimited indicator applies; what is observed? `SAP-012` proves fields, not result. |
| S06 reversal | Attempt reversal of applicable 101 receipt with 102 | SAP-005 (Maintenance context), SAP-011 (MM general) | NOT_RUN | Determine prerequisites, new document links, stock and FI effects. |
| S07 blocked stock | Receive to 103, later release if configured | SAP-007, SAP-016 | NOT_RUN | Confirm material document but no FI document at 103; no valuated-stock increase; GR blocked-stock quantity **is recorded in PO history**, while open PO quantity is **not reduced**. Subsequent release remains unverified. |
| S08 duplicate request | Resubmit same posting request / key | UNKNOWN | NOT_RUN | Identify exact API/transaction and whether duplicate postings occur. |
| S09 authorization | Attempt posting without movement authorization | SAP-011 (MM role overview only) | NOT_RUN | Verify denial and absence of posting side effects; record role and assignment. |

## Future runtime evidence capture template

```yaml
scenario_id: S01
environment:
  product: SAP S/4HANA
  deployment: on-premise
  release: unknown
  client_or_tenant: REDACTED
  relevant_configuration: unknown
authorization_confirmed: false
execution_timestamp: null
steps: []
expected_documented_behavior: []
actual_observations: []
artifacts_redacted: []
claim_status: UNKNOWN
reviewer: null
```

## Exit criteria for this matrix

- It covers successful and alternative process branches without asserting they were executed.
- Every SAP-specific expected branch has a source, or is marked UNKNOWN.
- The data-capture template cannot inadvertently claim success without explicit test evidence.
