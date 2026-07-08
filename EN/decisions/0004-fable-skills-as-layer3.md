# ADR-0004: Merge the 35 fable-skills as Layer 3 (situational skills)

- **Status**: Accepted
- **Date**: 2026-07-08
- **Related**: skills/, SKILLS.md, internal stages S0·S1, DOD_GUIDE, ADR-0003

## Context
fable-skills (MIT, adamentwistle/fable-skills) is a set of 35 engineering-discipline skills Fable used to pull lighter models up to its own working standard. In benchmarks, applying the skills lifted Opus 4.8 across every area (debugging 5.2→7.8/8, etc.) and reduced variance. The existing harness had only universal discipline and no per-task-type procedures.

## Decision
Vendor all 35 into root `skills/` (English originals as-is, with source and MIT attribution). Add a `SKILLS.md` index to each pack (KR/EN) recording situation→skill matching, application-surface classification (conversation+coding / coding-centric / agent sessions), and mappings to existing invariants and the OM. Activation: at S0/S1, match the task type against each skill's description and load only what applies. In Claude Code, copying `skills/` to `.claude/skills/` also enables activation via the Skill tool.

## Rationale
Skills are situationally activated, not "always loaded," so they raise per-type elicitation without growing the standing context. Keeping the full set is right because the benchmark validated it as a set, and the application-surface classification allows per-deployment selection.

## Consequences / trade-offs
- Gain: greater per-task-type elicitation without bloating the standing context.
- Cost: skill bodies are English-only (files read by the model, so no practical issue; half the maintenance). Possible drift from upstream (vendoring point frozen; tracked via source link).

## Alternatives considered
- Translate all 35 into KR — doubles maintenance, and the only beneficiary is the model. Rejected.
- Curate a subset only — breaks the set-level validation, and the application-surface classification suffices. Rejected.
- Inline into phases — bloats the standing context and negates the situational-activation design itself. Rejected.
