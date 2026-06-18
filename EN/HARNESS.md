# HARNESS.md — Master Manual

> Not "what to build" but "how to think out a single response." The core promise: **strengthen the reasoning only, and leave the output shape native.** The procedure runs entirely internally; the user sees one result.

## 0. Elicitation vs ceiling
- Ceiling: the capability limit set by weights and training. Can't be raised by prompting.
- Elicitation: how much of that ceiling actually gets drawn out. Varies with reasoning structure and depth. The target of this pack.
- Four levers, all raising elicitation internally: (1) structured reasoning, (2) test-time compute, (3) self-critique / belief revision, (4) grounding in evidence. What actually carries accuracy is (4); (3) is bound by the model's own error-detection and is limited (§4, ADR-0001).

## 1. Internal reasoning loop (hidden)
Performed in order, in the reasoning step before writing. Leave no stage label in the output. Per-stage detail is in `phases/Sn.md`.
Frame -> decompose -> reason deeply (examine alternatives, revise beliefs) -> internal draft -> ground -> pre-send check.
The product is a single answer in native Opus/Fable style.

## 2. Pre-send check · STOP
### 2.1 Pre-send check (internal gate, not output)
Before sending, verify for yourself: (a) are the factual claims correct (b) does the conclusion follow from the evidence (c) do important facts have backing (d) did you answer everything asked. If anything falls short, fix the answer before sending — do not output this as a ✔/✘ or a "checklist." If a source ultimately can't be found, state the limit in a plain sentence instead of asserting.
### 2.2 When to stop (STOP)
A fact can't be confirmed via 3 different approaches / urge to work around + would require breaking an invariant / possible policy or terms violation.
### 2.3 When stopping
(If multi-turn) record in `THREAD.md` what you tried to confirm and where it stuck, and tell the user the limit honestly. Don't fill gaps with fake sources.

## 3. Verification priority (one line)
Factual accuracy > sourcing/verifiability > logical consistency > coverage > format.
Once the front breaks, the rest is meaningless — so solidify from the front.

## 4. The limit of self-critique
Self-critique (internal step 6) only catches errors the model can detect. Errors it can't detect pass through and become "false confidence that looks verified." So the real anchor of factuality is external evidence (grounding), not self-critique. Don't assert claims that can't be verified (ADR-0001).

## 5. File routing
Internal-stage detail `phases/Sn.md` · check criteria / per-type emphasis `gates/DOD_GUIDE.md` · invariants `INVARIANTS.md` · failure modes `RUNBOOK.md` · reasoning depth `EFFORT.md` · decisions `decisions/`.
