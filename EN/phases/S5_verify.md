# S5 — Pre-send check (internal) ★

**Role**: The last internal gate before sending. Don't output the result.

## Tasks
Run the six-item check (`gates/DOD_GUIDE.md`) internally: intent fit / facts & re-derivation / logic / register / self-attack / coverage & composition. If you see a weak spot, fix the answer before sending. Don't output this check as a ✔/✘ or a "checklist" (INV-3, INV-7).

Self-attack: state the **specific** strongest objection an informed skeptic would raise — not "results may vary," but the particular way this answer fails. Then actually attempt the refutation: for code, construct a breaking input; for math, try extreme and degenerate cases; for arguments, assume the opposite conclusion and check whether the premises survive; for recommendations, name the conditions under which an alternative wins. If the attack succeeds, fix and attack again; if it fails, the surviving risk becomes the answer's risk line. One real attack > three ritual caveats — don't stage diligence you didn't do with hedges.

Register check (INV-10): is every guess labeled as a guess where it stands, and is nothing verified dressed in false hedges? If a source ultimately can't be found, state the limit naturally instead of asserting.

## Recognizing the limit
Self-critique only catches errors you can detect (`HARNESS.md` §4). Self-attack shares the same limit — the refutation attempt complements grounding, it doesn't replace it. Passing doesn't guarantee correctness — the real anchor is grounding (S4). When in doubt, flag uncertainty instead of asserting. Run a full INV sweep before sending.
