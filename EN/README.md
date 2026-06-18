# Opus 4.8 Plus — Response Elicitation Harness

**Version**: 0.2
**Target model**: Claude Opus 4.8 (claude.ai Project / Claude Code / API system prompt)
**Related docs**: `CLAUDE.md` (auto-loaded contract), `HARNESS.md` (master manual), `INVARIANTS.md` (invariants)

> This pack ports the Schema-Hub build harness's multi-file, separation-of-concerns skeleton to response quality. But it **does not change the shape of the output.** It only makes the reasoning deeper and more rigorous.

## Design principle — read first
This harness changes **only how Claude thinks (internally), not how Claude writes (output).**

- Tone, voice, formatting, and length stay **exactly as native Opus 4.8 / Fable 5**: natural prose, minimal formatting, a direct-but-warm tone, honesty about uncertainty — the existing Claude norms.
- **Never surface the procedure in the output.** Stage labels ("Problem framing:", "Draft:"), ✔/✘ checklists, forced section templates, "now I'll self-critique" meta-narration — none of it. That is form-template-style scaffolding, and it is not the goal of this pack.
- Decomposition, verification, and belief revision all happen **internally (in the reasoning step).** What the user sees is the single, natural answer that results.
- The only observable difference should be **quality**: deeper reasoning, fewer errors, better-grounded claims, more honest uncertainty.

## Elicitation, not a higher ceiling
The capability limit set by weights and training (the ceiling) can't be raised by prompting. This pack increases how much of that ceiling actually gets drawn out (elicitation). So "like Fable" means rigor and depth of the answer — not impersonating a model or bypassing safeguards (INV-4, INV-5) — and Fable's gated capabilities (cyber, biology, etc., which aren't in Opus's ceiling) won't come out under any configuration.

## File map
| File | Role | Change frequency |
|---|---|---|
| `CLAUDE.md` | Auto-loaded contract: value priority, output style, identity, internal reasoning loop, red lines | Rare |
| `HARNESS.md` | Master manual: internal reasoning loop, pre-send check (internal), verification priority, STOP | Rare |
| `INVARIANTS.md` | Invariants (INV-n). A single violation blocks sending | Rare |
| `gates/DOD_GUIDE.md` | Pre-send internal check criteria + per-answer-type emphasis | Rare |
| `phases/_TEMPLATE.md` | Internal reasoning-stage card template | Fixed |
| `phases/S*.md` | Internal reasoning stages (frame -> decompose -> reason -> draft -> ground -> check). All hidden | Rare |
| `RUNBOOK.md` | Response failure modes (symptom -> cause -> action) | Grows |
| `decisions/*.md` | Architecture Decision Records (ADR) | On decision |
| `EFFORT.md` | Per-task reasoning-depth (test-time compute) allocation policy | Occasional |
| `GLOSSARY.md` | Shared vocabulary | Occasional |
| `THREAD.md` | (Multi-turn research) internal working notes: claims, sources, open items, discarded hypotheses | During a thread |

## One line
Leave the native Opus 4.8 / Fable 5 answer as is, but pull the thinking behind it up to the ceiling. The user sees a better answer, not a different format.

## How to adopt
1. For a claude.ai Project, paste `CLAUDE.md`'s contents into the Project instructions. For Claude Code, place the folder at the repo root (or `harness/`) and `CLAUDE.md` is auto-loaded.
2. Add any project-specific invariants to `INVARIANTS.md`.
3. Check/adjust the default reasoning depth in `EFFORT.md`.
