# Evidence Policy (v0.1)

## Why

Answers about an ERP may blend product documentation, observed external effects, guessed internals, and suggestions for a new system. This repository must keep them distinguishable and auditable.

## Claim statuses

| Status | Definition | Permitted conclusion |
|---|---|---|
| `DOCUMENTED` | Directly supported by a cited, version-scoped authoritative source. | "Documentation describes X under Y." |
| `OBSERVED` | Captured in an authorized, reproducible system test with environment/provenance. | "In environment Z, X occurred." |
| `INFERRED` | Reasoned from evidence but not directly established. | "X may explain Y; verification required." |
| `PROPOSED` | Original independent design recommendation, not a claim about SAP. | "Our ERP could implement X." |
| `UNKNOWN` | Insufficient evidence. | "Unknown; investigate." |
| `CONFLICTING` | Sources or observations disagree. | "Conflicting; state both and narrow context." |

`DOCUMENTED` is not equivalent to `OBSERVED`; a source-grounded behavior is never declared validated in the user's particular landscape without an authorized runtime check.

## Required claim fields

- Stable claim ID and precise proposition.
- Product and release; configuration/organizational assumptions where relevant.
- Claim status, citations linked to `research/sources.md`, and access date.
- Counterexamples / known branches / unknowns.
- Optional runtime record with environment (sanitized), steps, expected vs actual, timestamp, approver and redacted evidence reference.

## Source preference

1. Official documentation for the exact SAP product/release and scoped process.
2. Official SAP API specifications, samples and technical training materials.
3. Controlled observation in systems the investigator owns or is authorized to inspect.
4. Open-source ERP implementations as **comparative design evidence only**; never proof of SAP internals.
5. Community discussion or agent output as research leads, not stand-alone authoritative proof.

## REA policy

REA is optional. Only capture authorized targets; respect contracts and licenses; avoid credentials, business records, proprietary customer code and personal data. Record tools and versions and disclose capture limitations. Browser traffic can reveal the externally observable API contract; it does not reveal undisclosed SAP backend implementation. Local reverse engineering is not a requirement to complete M0.

## Dispute handling

If two sources differ: retain both, check release, deployment model, material type, valuation method, account assignment, configuration and sequencing; set `CONFLICTING` or scope claims more narrowly. Do not average contradictory rules.

## Document quality gate

Reject material that (a) states unscoped SAP universals, (b) lacks sources for non-trivial SAP behavior, (c) invents SAP object names or proprietary internal architecture, (d) labels hypothetical fixtures as observations, or (e) conflates an original ERP proposal with a SAP system fact.
