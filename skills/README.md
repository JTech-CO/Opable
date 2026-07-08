# skills/ — Vendored fable-skills (Layer 3 of Opable)

**Source**: [adamentwistle/fable-skills](https://github.com/adamentwistle/fable-skills) — 35 engineering-discipline skills distilled from how Fable 5 works, written to pull lighter models up toward that standard.
**License**: MIT (see `LICENSE` in this directory).
**Vendored**: 2026-07-08, verbatim.

## Vendoring principle — originals are not modified

Every `SKILL.md` here is the upstream original, byte-for-byte intent. Do not edit, translate, or "improve" these files; fixes belong upstream. The benchmark evidence behind ADR-0004 covers the set as vendored — local edits would silently detach this copy from what was validated. Drift relative to upstream is accepted and tracked only through the source link above.

## Where this sits in Opable

This directory is **Layer 3 — situational skills**: work habits that fire only when the task type matches, unlike Layer 2 (the always-on response discipline in `OPERATING_MANUAL.md` and `INVARIANTS.md`).

- The catalog and activation rules live in each pack's index: `../KR/SKILLS.md` and `../EN/SKILLS.md`. The index maps situations to skills, classifies each skill's applicability surface (conversation+coding / coding-centric / agent-session-only), and records overlaps with the invariants and the Operating Manual.
- Activation is internal: during framing and decomposition (S0/S1), the task type is matched against each skill's frontmatter `description`, and only matching skills are loaded. Skill names and checklists never appear in the output (INV-7).
- Skill bodies are English-only by design (ADR-0004): the model is the reader, and a single-language vendored copy halves maintenance.

## Layout

One directory per skill, each containing a single `SKILL.md` with YAML frontmatter (`name`, `description`) followed by the discipline itself. 35 skills total, plus `LICENSE`.

## Using with Claude Code

Copy this directory into a project's `.claude/skills/` (one folder per skill, as-is). Claude Code then exposes each skill through the Skill tool, in addition to the internal S0/S1 matching described above. Nothing else in the pack requires this step.

## Cross-reference mapping — read before following "see …" pointers

Some skill bodies cite companion skills by names that were later consolidated or renamed upstream. Those names do not exist as directories here. Per the vendoring principle the originals are left untouched; resolve references with this table:

| Name cited in skill bodies | Resolves to |
|---|---|
| `ground-before-edit` | `workmanship` |
| `honest-report` | `workmanship` |
| `self-review-diff` | `workmanship` |
| `verify-before-done` | `workmanship` |
| `pre-done-review` | `workmanship` |
| `read-what-came-back` | `workmanship` |
| `search-existing-patterns` | `codebase-orientation` |
| `scope-discipline` | `estimation-and-scoping` · `surgical-refactoring` §5 |
| `security-reflex` | `security-reflexes` |
| `root-cause-debug` | `root-cause-debugging` |
