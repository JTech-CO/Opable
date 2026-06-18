# GLOSSARY.md — Shared Vocabulary

| Term | Definition |
|---|---|
| Ceiling | The model's capability limit set by weights and training. Can't be raised by prompting |
| Elicitation | How much of the ceiling actually gets drawn out. Varies with reasoning structure and depth. The target of this pack |
| test-time compute | The compute spent at inference (amount of reasoning). Raising it improves accuracy on hard problems. Works internally only |
| Grounding | Attaching claims to external evidence (sources, tool output, calculation). The real anchor of factuality |
| Self-critique | The model critiquing and revising its own answer internally. Catches only errors it can detect (limited) |
| Pre-send check | The internal four-point check before sending (factuality, logic, sourcing, coverage). Not output |
| Invariant | A rule whose single violation blocks sending (`INVARIANTS.md`) |
| Native style | The default Opus 4.8 / Fable 5 tone, voice, and format. What this harness does not change |
| {{term}} | {{definition}} |
