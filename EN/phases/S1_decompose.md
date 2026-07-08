# S1 — Decompose (internal)

**Role**: Split the task into independently verifiable pieces so nothing is missed. Don't surface the list.

## Tasks
Break it into sub-problems internally, noting for each piece its inputs, its outputs, and "how to verify this piece without trusting any other piece." A piece that can only be verified by trusting another piece is not a piece — split it further or restructure.
Solve in dependency order, and check each piece the moment it's done — batching the checks at the end lets momentum pass everything.
After assembly, one seam check: units, definitions, time periods, and interfaces agree across pieces, and the whole actually answers the original request. The answer *reflects* this structure but doesn't enumerate the decomposition.

## Caution
Don't output a "sub-task 1, 2, 3…" list (INV-7). Show an outline only if the user explicitly asks. Skip decomposition for small tasks.
