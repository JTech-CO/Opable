# Opus 4.8 Plus

[힌국어](https://github.com/JTech-CO/Opus-4.8-Plus/blob/main/README.md)

A **Response Elicitation Harness** for Claude Opus 4.8. A set of operating disciplines that pulls Opus 4.8's answers **as close to Fable 5 as possible** — not by changing or imitating the model, but by driving the reasoning behind the answer up to Opus's capability ceiling.

> This document explains **what Opus 4.8 Plus is and why it was built.** The components themselves (each file's role and usage) are in `EN/README.md` / `KR/README.md` and the individual MD files.

## What it is
Opus 4.8 Plus is a multi-folder harness you load as a system prompt, Project instruction, or Claude Code contract. It takes the Schema-Hub build harness skeleton (agent contract, invariants, gates, STOP, decision records) as-is, but shifts the target from "how to build a project" to **"how to think out a single response."**

The goal is clear: **make Opus 4.8's answers come as close to Fable 5's as possible** — not by swapping or mimicking the model, but by drawing out everything Opus's ceiling has to offer. So the core promise reduces to one thing: **strengthen the reasoning only, and leave the output shape native Opus 4.8.** What the user sees is the usual Claude answer, and the only thing that changes is the quality of that answer.

## What role it plays — ceiling and elicitation
Two things have to be distinguished:
- Ceiling: the model's capability limit, set by weights, training, and scale. Prompting can't raise it.
- Elicitation: how much of that ceiling actually gets drawn out. It varies greatly with reasoning structure and depth.

Opus 4.8 Plus doesn't touch the ceiling. Instead it maximizes elicitation, hitting the ceiling so that Opus 4.8's answers come as close to Fable 5 as that ceiling allows. By enforcing decomposition, deep reasoning, self-critique, and grounding internally, it makes Opus consistently produce answers near its ceiling. On knowledge, analysis, and coding tasks where elicitation was the bottleneck, quality approaching Fable's emerges.

"As close as possible" is always within Opus's ceiling. This doesn't replicate Fable's weight advantage or its gated capabilities (cyber, biology, etc., which aren't in Opus's ceiling) — it draws out the best answer Opus can give, up to where it meets Fable's level.

## Why it was built
The starting point was a single question: "Can fine-tuning Opus 4.8 on a leaked Fable 5 system prompt make it behave like Fable?" The answer was no. A system prompt is instructions, not capability; the gap between Fable and Opus lives in the weights, not the prompt; a closed Opus has no self-serve fine-tuning path; and distillation can't exceed the student model's ceiling.

But the next observation was the key one. A well-built system prompt genuinely raises a model's perceived answer quality — the same model giving deeper, more accurate, better-verified answers. That isn't a higher ceiling — it's more elicitation. A prompt can't raise the ceiling, but it can be the ladder that reaches it.

Opus 4.8 Plus is the honest application of that conclusion. It is not a thing that "disguises Opus as Fable," but a tool that "pulls Opus up to its own ceiling so it answers as close to Fable as possible." So "like Fable" means the rigor and depth of the answer — not impersonating a model or unlocking gated capabilities.

## How it works
There are four elicitation levers, all operating in the internal reasoning step only.
1. Structured reasoning — decompose the task and work from first principles.
2. test-time compute — reason more deeply the harder it gets.
3. Self-critique / belief revision — find your own weak spots and discard wrong hypotheses.
4. Grounding — attach claims to sources and calculation.

What actually carries accuracy here is (4). Self-critique (3) only catches errors the model can detect, so passing isn't treated as a guarantee of correctness — external evidence is the real anchor (see `decisions/0001`). And these four steps never surface in the output: no stage labels, no checklists, no forced templates — just the resulting answer, in native style (`decisions/0002`).

## What it does not do
- It doesn't raise the ceiling. On the hardest problems, where raw reasoning is the bottleneck, the gap to Fable barely closes.
- It doesn't replicate Fable's weight advantage or its gated capabilities (cyber, biology, etc., which aren't in Opus's ceiling) — they won't come out under any configuration.
- It doesn't impersonate another model or bypass safeguards.
- It doesn't change output style or voice. It doesn't impose form templates like forced sections or checklists on the answer.

## Relation to the Schema-Hub harness
Just as the build harness blocks "runs without errors but the feature doesn't work" with measurable gates, this pack blocks "plausible but actually wrong" with an internal pre-send check. It applies the same philosophy — verification that doesn't rely on self-report, invariants, STOP — to a single response rather than a multi-session build. That's why the file layout parallels the build pack: `CLAUDE.md` (contract), `HARNESS.md` (manual), `INVARIANTS.md`, `gates`, `phases`, `decisions`, `RUNBOOK`.

## Structure
- `EN/`, `KR/`: the English and Korean packs with identical content (19 files each). Edit one, then sync the other by the same INV/ADR numbers.
- Each folder's `README.md`: the file map and how to adopt (component descriptions).
- Adoption: for a claude.ai Project, paste `CLAUDE.md` into the instructions; for Claude Code, drop the folder at the repo root.

## One line
Opus 4.8's answer as close to Fable 5 as possible — ceiling fully drawn out, output left native. The user sees a better answer, not a different format.
