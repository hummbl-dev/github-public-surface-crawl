# Amendment Proposal v0.2.1 — CodeRabbit Governance Review

**Status:** Proposed; not adopted

**Date:** 2026-07-13

This document records the disposition of the ten CodeRabbit requests raised
against the bootstrap preservation PR. It proposes follow-up governance
amendments without changing the approved Plan v0.2. Plan v0.2 remains the
canonical approved artifact until a separately reviewed amendment is merged.

## Provenance

- Bootstrap issue: [hummbl-dev#214](https://github.com/hummbl-dev/hummbl-dev/issues/214)
- Bootstrap plan PR: [hummbl-dev#215](https://github.com/hummbl-dev/hummbl-dev/pull/215)
- Bootstrap commit: [`4973542501e20d786998c2a2de549040ac8471b2`](https://github.com/hummbl-dev/hummbl-dev/commit/4973542501e20d786998c2a2de549040ac8471b2)
- Dedicated-repository migration PR: [github-public-surface-crawl#1](https://github.com/hummbl-dev/github-public-surface-crawl/pull/1)
- Current Plan v0.2 merge commit: [`24492c85461d265ee3c4e04552bcf6a00b92aa2c`](https://github.com/hummbl-dev/github-public-surface-crawl/commit/24492c85461d265ee3c4e04552bcf6a00b92aa2c)

## Disposition

### A1 — Git-governed first-run authorization

**Disposition: ACCEPT — amendment indicated.** Define “equivalent explicit
authorization” as another Git-governed, merged, hash-bound run-authorization
record. Starts, scope expansion, and closeout must reference the approved
record and its exact plan/policy hashes.

### A2 — Credential-free rendered crawling

**Disposition: ACCEPT — amendment indicated.** Require clean unauthenticated
HTTP and browser contexts, prohibit cookies/tokens/credential injection, and
quarantine a run when authentication indicators are detected. This is a
pre-execution safety requirement, not authorization to crawl.

### A3 — Replayable selector variants

**Disposition: ACCEPT — amendment indicated.** Require canonical normalized
selector names and values, an ordered browser interaction trace, a
deterministic state fingerprint, and observation evidence for every selector
state. Do not create a separate route identity for a selector variant.

### A4 — Redirect-hop validation

**Disposition: ACCEPT — amendment indicated.** Validate every redirect
destination before following it against the approved host/path policy and
resolved-IP allowlist. Block external, private, link-local, and cloud-metadata
destinations before issuing the next request.

### A5 — Explicit terminal denial resolutions

**Disposition: ACCEPT — amendment indicated.** Record robots, terms,
authentication, CAPTCHA, explicit-access, rate-limit, and technical-barrier
denials as explicit terminal resolutions. Completion and coverage claims must
separate policy-denied resources from attempted or equivalently resolved
resources.

### A6 — Interim coordination-repository control-plane policy

**Disposition: OBSOLETE — do not amend Plan v0.2 for this request.** The
dedicated control repository now exists and the approved plan has been migrated
and merged. The bootstrap repository and migration receipts provide the
historical provenance needed for this transition.

### A7 — Discovery/reconciliation saturation

**Disposition: ACCEPT — amendment indicated.** Define a discovery/reconciliation
round, its frozen inventories and evidence inputs, and a bounded stop condition
based on no new identities and no unresolved reconciliation changes. Apply the
same rule before inventory freeze and during repeated discovery guidance.

### A8 — Audit sampling across record populations

**Disposition: ACCEPT — amendment indicated.** Define the eligible population
count `N`, major surface, canonical serialization, and required strata. Ensure
failed, partial, and not-found outcomes are represented rather than restricting
the routine sample to successful records. Preserve the separate 100% mandatory
review population.

### A9 — Unambiguous deterministic hash ranking

**Disposition: ACCEPT — amendment indicated.** Replace ambiguous string
concatenation with canonical UTF-8 serialization and unambiguous delimiters or
length prefixes for `crawl_id`, `audit_round`, and `record_id`. Sort by the
complete SHA-256 digest in a specified byte or hexadecimal order, with
`record_id` as the deterministic tie-breaker.

### A10 — Acceptance-threshold denominator

**Disposition: ACCEPT IN PRINCIPLE — amendment indicated, subject to design
review.** The amendment must state whether minor defects in the mandatory-review
population are included in the denominator or governed by a separate explicit
threshold. Closeout must not pass while substantial unresolved minor defects
remain in mandatory-review populations.

## Proposed amendment boundary

This proposal is documentation and governance design only. It does not:

- modify Plan v0.2;
- authorize reconnaissance, page retrieval, or crawling;
- design append-only ledgers;
- provision an executor, Cloud Run, GCS, or other infrastructure;
- create host policies or run-authorization records;
- resolve or approve the historical CodeRabbit review on the closed bootstrap PR.

Any adopted amendment must be merged through a new branch-scoped PR, receive a
non-author review, preserve Plan v0.2 and migration provenance, and include
explicit validation of all changed governance language. Implementation must
remain downstream of that adopted amendment and a separate run authorization.

## Review questions

1. Are A1–A5 and A7–A9 sufficiently precise to adopt as governance language?
2. Should A10 use a combined denominator or a separate mandatory-review
   threshold?
3. Does the proposal correctly treat A6 as obsolete after migration?
4. Are any proposed controls stronger than the approved Plan v0.2 in a way
   that requires an explicit operator amendment decision?
