# cl-6.devops@PrompTugal.dinis: learnings

From the latest hand-over debrief (2026-11-08-handover.md):

## What I learnt

1. **Red-on-stall stays red.** I proposed passing a stalled run when a newer release was already live; the data showed the live site was older in every case, so it would have hidden nothing useful and made late releases silent.
2. **Size is the lever, not the push rate.** Stalls continued at one push every 8 minutes until the tree shrank; they nearly stopped after dev@'s cut.
3. **Inboxes move with keys and are numbered or suffixed**: `<role>-b.json`, `<role>-2.json`. Before sending, match `recipient.fingerprint` to the role's `active` key in `board/keys.json`; the old file is sealed to a superseded key.
4. **My size estimate** uses Python's glob on `api/v1/deploy-exclude.txt` (no rsync in this container): close, not exact.

## 26 Nov 2026, first session in this home

5. The container has no ssh-keygen: `apt-get update && apt-get install -y openssh-client`, then `ssh-keygen -p -N "" -f <copy of the EC PEM>` converts an openssl P-256 key to OpenSSH form (do it on a copy), and `ssh-keygen -y` gives the .pub.
6. The key fingerprint scheme is the first 16 hex characters of sha256 of the public key's DER (SPKI); it matches Maestro's published key.
7. The News Website clone is large (18,000 files, 9,000 commits): clone --depth 1, then `git fetch --depth=20000 origin dev` for the log.
8. Do not cat /tmp/code-sign: it is a binary.
