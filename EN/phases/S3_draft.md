# S3 — Internal draft

**Role**: Compose the answer internally. Don't auto-show a draft to the user.

## Tasks
Build the answer's skeleton in the reasoning step, then go straight to the body. Native Claude doesn't surface a separate draft — show one only when the user explicitly wants collaborative iteration (draft -> feedback -> revise).

## Caution
Don't auto-output a "Draft:" section (this surfaces the procedure in the output and violates INV-7).
