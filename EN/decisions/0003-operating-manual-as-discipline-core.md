# ADR-0003: Adopt the Operating Manual as the canonical response discipline (Layer 2)

- **Status**: Accepted
- **Date**: 2026-07-08
- **Related**: OPERATING_MANUAL.md, INV-9·INV-10, internal stages S0~S5, EFFORT, RUNBOOK, DOD_GUIDE, ADR-0002

## Context
An Operating Manual (§1~§8 + pre-send self-test) became available — a codification written by observing the leaked answering style of Fable 5. It overlaps almost 1:1 with the existing harness's loop and invariants while deepening each point procedurally (premise verification, re-deriving pass-through material, registers, self-attack, cost-of-error allocation, dormancy). But §7 (answer first → reasoning → risks) prescribes output composition, creating tension with "output shape stays unchanged" (ADR-0002).

## Decision
Incorporate the OM into the pack as the canonical Layer 2 document (`OPERATING_MANUAL.md` — EN original, full KR translation). Integrate its procedures into S0~S5, EFFORT, RUNBOOK, and DOD_GUIDE, and add INV-9·INV-10. Adopt §7 **not as an output-style change but as the precise specification of the native Fable 5 norm** — since the OM itself is Fable's observed answering style, following it just is native-norm compliance (compatible with INV-8). "Answer first" is a composition principle, not a forced template, and requires no section labels.

## Rationale
The OM proceduralizes "how to verify," not "what to do," and fills exactly the existing harness's gaps (pass-through material, registers, refutation attempts). Keeping one canonical document while distributing the procedures keeps both the narrative and the operation alive.

## Consequences / trade-offs
- Gain: abstract instructions ("reason deeply") are replaced by Fable's observed actual working method, and the loop's gaps are filled with procedure.
- Cost: cross-document duplication (OM body ↔ phases summaries) and synchronization overhead — on conflict, the OM is canonical.

## Alternatives considered
- Keep the OM as a standalone document only — becomes a dual system alongside the loop and drifts. Rejected.
- Fully dismantle and absorb the OM, discarding the original — loses the canonical narrative and the baseline for future updates. Rejected.
