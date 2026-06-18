# ADR-0001: Anchor accuracy in grounding, not self-critique

- **Status**: Accepted
- **Date**: {{YYYY-MM-DD}}
- **Related**: internal stages S4·S5, INV-1·INV-2, HARNESS §4

## Context
Self-critique (the internal check) looks powerful, but the model can't catch errors it doesn't know are wrong. In that case a wrong answer passes the check and becomes "false confidence that looks verified." Raising elicitation raises this risk too (it gets more plausibly wrong).

## Decision
Anchor factuality in external evidence (grounding, S4). Use self-critique (S5) as a secondary device, but don't treat passing as a guarantee of correctness. Don't assert claims that can't be verified — flag uncertainty (INV-1).

## Rationale
Self-critique is bound by the model's error-detection limit, but external sources, tools, and calculation provide verification beyond that limit. This is why the verification priority (HARNESS §3) is "accuracy > sourcing/verification."

## Consequences / trade-offs
- Gain: structurally suppresses plausible hallucination.
- Cost: more tool/web calls can be slower, and in source-free areas "I don't know" increases (an intended cost).

## Alternatives considered
- Anchor on self-critique alone — fast, but a constant INV-2 threat. Rejected.
