# SKILLS.md — Situational Skill Index

> Layer 3: the index of 35 working habits (situational skills) that fire only when the task type matches. Unlike Layer 1 (the reasoning loop) and Layer 2 (the response discipline), which apply to every response, a skill switches on only for its kind of task. The bodies live in `../skills/` (shared by the KR/EN packs, English originals).

## Source and activation
- Source: fable-skills (adamentwistle/fable-skills, MIT). The 35 engineering-discipline skills Fable wrote to lift lighter models to its own working standard. Vendored unmodified into `../skills/` (details in `../skills/README.md`).
- Activation: in S0 (framing) and S1 (decomposition), match the task type against the "When it fires" column below and each skill's frontmatter description, and load internally only the ones that match.
- Skills are internal discipline too — never surface a skill's name, checklist, or stage labels in the output (INV-7).
- In Claude Code, copying `skills/` to `.claude/skills/` also makes them available to the Skill tool.

## Applicability
| Mark | Applicability |
|---|---|
| ◎ | Conversation + coding — fires even in pure conversation, with no files or terminal |
| ○ | Coding-centric — fires on tasks that read and write code |
| △ | Agent sessions only — meaningful only in sessions with file, terminal, or git manipulation |

## Catalog (35 skills)

In the harness-correspondence column, Sn is a stage in `phases/`, OM §n is a section of `OPERATING_MANUAL.md`, and INV-n is an invariant in `INVARIANTS.md`. — means no correspondence.

### Orientation & planning
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| codebase-orientation | ○ | Entering a repo or module untouched this session, or before designing against an existing architecture | — |
| task-decomposition | ◎ | At the start of work spanning 3+ files or steps, and mid-task when the approach gets invalidated | S1, OM §2 |
| estimation-and-scoping | ◎ | When sizing work, when scope balloons mid-task, when a "quick fix" turns out to be architectural | EFFORT, OM §3 |
| ambiguity-commit | ◎ | A request with multiple plausible readings or an unstated parameter (which file, which env, how thorough, what format) | S0, OM §1 |
| question-vs-task | ◎ | A message readable as either a question or a change request — bug descriptions, "why does X happen", thinking out loud | S0, OM §1 |

### Correctness & debugging
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| root-cause-debugging | ○ | Any bug, test failure, regression, or flaky behavior — before proposing a fix, and whenever a first fix didn't work | — |
| edge-case-sweep | ◎ | After the happy path works, before declaring any function, handler, parser, or transformation done | S5 (the falsification attempt, made concrete for code) |
| numerical-care | ◎ | Any arithmetic beyond a counter — money, percentages, averages, durations, aggregations, comparisons of computed values | INV-9, OM §4 |
| concurrency-reasoning | ○ | Async fan-out, streams/SSE, jobs, caches, or flaky bugs with a timing smell | — |
| environment-first | ○ | A command fails unexpectedly, a test that "can't" fail fails, or behavior contradicts the code you're reading | — |
| stop-thrashing | ◎ | Third failed attempt at the same problem, re-editing the same lines, attempts that are guesses rather than deductions | S2 (belief revision) |

### Security & safety
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| security-reflexes | ○ | Any code touching user input, authn/authz, secrets, paths, URLs, subprocesses, SQL, HTML rendering, or external APIs | — |
| untrusted-content-guard | ◎ | Processing external or user-generated content that could contain directive-sounding text (prompt-injection defense) | INV-6 |
| data-loss-guard | △ | The moment a planned action would destroy hard-to-recreate state — rm, overwrite, force-push, reset --hard, DROP, bulk delete, killing processes | — |
| api-surface-care | ○ | Before modifying anything other code depends on — exported functions, endpoints, CLI flags, config formats, schemas | — |

### Change discipline
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| surgical-refactoring | ○ | Renames touching 3+ sites, signature/type reshapes, moving code, or codebase-wide pattern swaps | — |
| dependency-changes | ○ | Before touching package manifests, on security advisories, or on version-mismatch errors | — |
| data-migration-safety | ○ | Schema changes, stored-JSON shape changes, backfills, or renaming/removing persisted or API fields | — |

### Testing & verification
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| test-design | ○ | Writing tests, adding regression coverage for a fix, or judging whether existing tests protect anything | S5 (the falsification attempt, made concrete for code) |
| verify-ui-visually | △ | After any change to components, styles, layouts, templates, charts, emails, or generated documents/images | — |
| workmanship | ○ | Any task involving code changes, investigation, or a final report the user will act on — the standing candidate for every coding task | INV-3, OM §6·§7 |

### Performance & operations
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| performance-investigation | ○ | Any "make it faster", any latency/memory investigation, or before adding caching/memoization on intuition | — |
| perf-sanity | ○ | Loops over data of unknown size, database access inside loops, anything on a request path | — |
| incident-diagnosis | △ | Production is broken right now, or before restarting/redeploying/deleting as a first move | — |

### Communication
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| calibrated-recommendation | ◎ | "Which should I use", "what's the best way", "A or B?", or proposing a design choice | INV-10, OM §5 |
| explain-at-the-right-level | ◎ | Any explanatory question — "how does X work", "why does this happen", "what's the difference", "walk me through" | — |
| error-message-quality | ○ | Writing any throw/raise, log statement, validation message, or CLI/API error response | — |
| escalate-vs-decide | ◎ | Uncertain mid-task, tempted to ask "should I…?", or before destructive, outward-facing, or scope-changing actions | — |
| generalize-the-correction | ◎ | The moment the user points out an error, rejects an approach, or states a preference about how you work | RUNBOOK growth principle |

### Working style & hygiene
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| git-hygiene | △ | Committing, branching, or starting any change large enough to want an undo point | — |
| leave-no-mess | △ | At the end of any task that spawned servers, wrote scratch files, added debug output, or altered state beyond the intended diff | — |
| context-checkpoint | △ | At the start of any task likely to exceed ~30 minutes or span many files, and again at each phase boundary | — |
| subagent-fanout | △ | A sweep across many files/directories, several independent investigations that could run in parallel, or raw tool output that would flood the working context | — |
| cross-platform-care | ○ | Writing shell scripts, CI steps, path manipulation, file I/O, or setup instructions others will run | — |

### LLM application code
| Skill | Applicability | When it fires | Harness correspondence |
|---|---|---|---|
| llm-app-code | ○ | Agent loops, tool definitions, or prompt/model changes — any code calling LLM APIs | INV-6 (transitive injection) |

## Caution — cross-references inside skill bodies
Some names referenced inside skill bodies (see …) predate an upstream merge or rename. The originals stay unmodified per the vendoring principle — read them through this mapping.

| Name appearing in a body | Actual skill |
|---|---|
| ground-before-edit, honest-report, self-review-diff, verify-before-done, pre-done-review, read-what-came-back | workmanship |
| search-existing-patterns | codebase-orientation |
| scope-discipline | estimation-and-scoping, surgical-refactoring §5 |
| security-reflex | security-reflexes |
| root-cause-debug | root-cause-debugging |
