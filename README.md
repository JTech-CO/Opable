# Opable

> **A response-elicitation harness that pulls Claude Opus 4.8's answers as close to Fable 5 as possible — by transplanting Fable's working method, not by changing the model.**

[English](README.md) · [한국어](README-KR.md)

## 1. Introduction

Opable (formerly *Opus 4.8 Plus*) is an instruction harness for Claude Opus 4.8. It strengthens only the reasoning behind the answer — the output style stays native, and the only observable difference is quality. It cannot raise the model's capability ceiling; it maximizes how much of that ceiling is actually drawn out (elicitation).

**Key features**
- **Layer 1 — Reasoning loop**: six internal stages per response (frame → decompose → reason → draft → ground → check), all hidden from the output (`phases/`, `EFFORT.md`).
- **Layer 2 — Response discipline**: the Operating Manual — a codification of the leaked Fable 5's observed way of answering — plus 10 invariants and a six-point pre-send check (`OPERATING_MANUAL.md`, `INVARIANTS.md`, `gates/`).
- **Layer 3 — Situational skills**: the 35 fable-skills (per-task-type senior working habits) that fire only when the task type matches (`skills/`, indexed in `SKILLS.md`).
- **Native output**: no stage labels, no checklists, no forced templates — the user sees a better answer, not a different format.

## 2. Tech Stack

- **Target model**: Claude Opus 4.8
- **Format**: plain Markdown instruction packs — `KR/` and `EN/` (23 files each, identical content) + shared `skills/`
- **Deployment**: claude.ai Project / Claude Code / API system prompt
- **Sources**: the original harness skeleton + the Operating Manual + [fable-skills](https://github.com/adamentwistle/fable-skills) (MIT)

## 3. Quick Start

**Requirements**: access to Claude Opus 4.8 (claude.ai, Claude Code, or the API)

1. **Install**
   ```bash
   git clone https://github.com/JTech-CO/Opus-4.8-Plus.git
   cd Opus-4.8-Plus
   ```

2. **Adopt** (pick your deployment)
   - **claude.ai Project**: paste `EN/CLAUDE.md` (or `KR/CLAUDE.md`) into the Project instructions, and upload the remaining pack files to the Project knowledge.
   - **Claude Code**: copy one pack's contents to your repo root so `CLAUDE.md` sits at the root. Optionally copy `skills/` into `.claude/skills/` to enable the Skill tool.
   - **API**: put `CLAUDE.md` (and `OPERATING_MANUAL.md` if needed) into the system prompt.

3. **Tune**
   Add project-specific invariants to `INVARIANTS.md`; check the default reasoning depth in `EFFORT.md`.

## 4. Structure

```text
Opus-4.8-Plus/
├── KR/                      # Korean pack (23 files)
│   ├── CLAUDE.md            # Auto-loaded contract (binds the three layers)
│   ├── OPERATING_MANUAL.md  # Canonical response discipline (Layer 2)
│   ├── HARNESS.md / INVARIANTS.md / SKILLS.md / EFFORT.md / RUNBOOK.md …
│   ├── phases/              # The six internal reasoning stages (Layer 1)
│   ├── gates/               # Pre-send check criteria
│   └── decisions/           # Architecture Decision Records (ADR)
├── EN/                      # English pack (identical layout)
├── skills/                  # 35 vendored fable-skills (Layer 3, MIT)
└── Operating Manual.md      # Preserved pre-merge original
```

Full background (ceiling vs. elicitation, design decisions) lives in each pack's `README.md` and `decisions/`.

## 5. Info

- **License**: MIT
- **Attribution**: [fable-skills](https://github.com/adamentwistle/fable-skills) (MIT, vendored unmodified); the Operating Manual is based on a codification of the leaked Fable 5's way of answering
- **Contact**: [JTech-CO](https://github.com/JTech-CO) — issues and PRs welcome
