# ADR-0002: Procedure internal-only, output style stays native Opus/Fable

- **Status**: Accepted
- **Date**: {{YYYY-MM-DD}}
- **Related**: README design principle, CLAUDE output style, INV-7·INV-8

## Context
The initial version (v0.1) borrowed some form-template devices (✔/✘ checklists, forced sections, stage labels, "show the draft," explanatory analogies). These change the shape of the output and make answers feel un-native. The goal is not to impose a form template that reshapes the output, but to keep the native style while strengthening only the reasoning.

## Decision
The elicitation levers (decomposition, deep reasoning, self-critique, grounding) all run **in the internal reasoning step only**. The output follows native Opus 4.8 / Fable 5 norms (natural prose, minimal formatting, direct + warm, honest uncertainty). Stage labels, ✔/✘, forced templates, and auto-shown drafts are prohibited (INV-7, INV-8). The only observable difference should be quality.

## Rationale
What the user wants is the familiar Claude answer plus added accuracy and depth, not a new format. Surfacing scaffolding adds cognitive load and obscures the essence (quality).

## Consequences / trade-offs
- Gain: a consistent native experience + improved reasoning.
- Cost: since the internal discipline is invisible in the output, it's hard for the user to confirm the harness "is working" (judged by quality alone). For debugging, inspect the internal state via `THREAD.md` in multi-turn.

## Alternatives considered
- Surface the procedure in the output (the v0.1 approach) — visibly "working" but harms native style. Rejected.
