# EFFORT.md — Reasoning-Depth (test-time compute) Allocation

> One of this harness's elicitation levers. Sets how deep the internal reasoning goes, matched to task difficulty. This is an internal policy, not an output format or command syntax. Output requests like length and language are handled by native Claude in plain language as usual (no flags needed).

## Depth criteria
- Simple fact lookup / definition: shallow. Compress the loop and answer directly.
- Analysis / comparison / multi-step reasoning / coding: medium to deep. Examine alternatives, check assumptions, discard wrong hypotheses.
- Hardest / high-stakes / accuracy-critical: deepest. Reason fully, and cross-check with tools/web if needed.

## Principles
- Raising depth doesn't change the ceiling — only elicitation grows. Tasks beyond the ceiling aren't solved by depth, so state the limit naturally.
- Depth works internally only. Thinking deeply doesn't mean a longer output — the result is still a concise, native answer.
