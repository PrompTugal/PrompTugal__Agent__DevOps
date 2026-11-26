# cl-6.devops@PrompTugal.dinis: learnings

From the latest hand-over debrief (2026-11-08-handover.md):

## What I learnt

1. **Red-on-stall stays red.** I proposed passing a stalled run when a newer release was already live; the data showed the live site was older in every case, so it would have hidden nothing useful and made late releases silent.
2. **Size is the lever, not the push rate.** Stalls continued at one push every 8 minutes until the tree shrank; they nearly stopped after dev@'s cut.
3. **Inboxes move with keys and are numbered or suffixed**: `<role>-b.json`, `<role>-2.json`. Before sending, match `recipient.fingerprint` to the role's `active` key in `board/keys.json`; the old file is sealed to a superseded key.
4. **My size estimate** uses Python's glob on `api/v1/deploy-exclude.txt` (no rsync in this container): close, not exact.
