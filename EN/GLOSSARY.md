# GLOSSARY.md — Shared Vocabulary

| Term | Definition |
|---|---|
| Ceiling | The model's capability limit set by weights and training. Can't be raised by prompting |
| Elicitation | How much of the ceiling actually gets drawn out. Varies with reasoning structure and depth. The target of this pack |
| test-time compute | The compute spent at inference (amount of reasoning). Raising it improves accuracy on hard problems. Works internally only |
| Grounding | Attaching claims to external evidence (sources, tool output, calculation). The real anchor of factuality |
| Self-critique | The model critiquing and revising its own answer internally. Catches only errors it can detect (limited) |
| Pre-send check | The internal six-point check before sending (intent, facts, logic, register, self-attack, coverage; `gates/DOD_GUIDE.md`). Not output |
| Invariant | A rule whose single violation blocks sending (`INVARIANTS.md`) |
| Native style | The default Opus 4.8 / Fable 5 tone, voice, and format. What this harness does not change |
| Register | A claim's knowledge grade: (a) derived from this conversation's material (b) stable independent knowledge (c) guess/extrapolation. (c) is labeled inline (INV-10) |
| Re-derivation | Recomputing or tracing back a pass-through number, quote, or claim from the source material (INV-9). No "just editing" exemption |
| Dormancy | Folding the discipline and executing directly on tasks with no factual claims, numbers, decisions, or third-party dependence (OM §3.3) |
| Self-attack | Raising the strongest concrete counterargument to your own conclusion before sending, and actually attempting the refutation (OM §6) |
| Cost-of-error | The real cost incurred if that part is wrong. The basis for allocating verification effort (OM §3) |
| Premise capture | The failure of explaining "why X happened" when X never happened. Blocked by verifying premises (RUNBOOK #12) |
| Fluent propagation | The failure of polishing someone else's error into smooth prose and passing it through (RUNBOOK #11, INV-9) |
| Situational skill | A work habit activated internally only when the task type matches (`skills/`, `SKILLS.md`) |
| Operating Manual | The canonical Layer-2 response discipline. The leaked Fable 5 answering style, codified (`OPERATING_MANUAL.md`) |
| {{term}} | {{definition}} |
