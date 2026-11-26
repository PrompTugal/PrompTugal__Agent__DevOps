# Hand-over of cl-6.devops@PrompTugal.dinis, 2026-11-26T16:54Z

From the first session (https://claude.ai/code/session_016CrbJLNFt4cFTXMVgkqcCY, Sonnet, replaced at 54% of its window, at Dinis's word "reset them" via cl-6.maestro). Wake: trig_01ABYHjvXT9THELBSgM2PaSg (08:07 and 19:07 Lisbon), to be moved to the new session by cl-6.maestro.

## Done today (26 Nov 2026)
- Key, history (33 files, history/PROVENANCE.md, git-log.md), area written. Key in the website's board/keys.json as devops-promptugal-cl-6 (commits e277f7c9d, and 228c0c6d9 which fixed its ssh field: my own rsplit bug had left only the key type; fixed in site/keys/cl-6.devops.json too).
- CI pass 21 to 26 Nov (findings/2026-11-26-ci-pass-21-to-26-nov.md): 764 runs, 9 red, all cleared by the next push; 8 were the gate's email check reading agent names (cl-6.dev widened AGENT_NAME to @account-a to @account-f.dinis), 1 a maestro.c status.json slip.
- Deploy speed (Dinis's yes via the conductor, cl-6.security's yes): 7024fc917 drops needs: [validate] from the release job. Runs 5917 and 5918 took 5.35 and 5.23 min (before: median 11.3, p90 13.4; the four runs before 10.8 to 15.7). Evidence in review/2026-11-26-release-parallel-evidence.md (validate.js OK before "released" in both release logs).
- PT decision: a UTC time on each new versions.json row (tag_release.sh, v0.1.2323, security yes).
- R10 run report filed by hand (runs/cl-6.devops/); grant read (ABP v1.2.0).

## Open
1. Re-measure run time after about 20 releases on the parallel workflow: median and p90 per day, from the runs API (GitHub read tools are in mandate). Send the conductor one line.
2. At the next change to .github/workflows/deploy-pages.yml fix the comment "security@ approved 14:02 UTC" to "about 13:59 UTC" (cl-6.security's correction). Keep this job's .gitattributes step and the gate in tag_release.sh; any change that skips validate.js in the release job goes to cl-6.security first (its condition 1).
3. cl-6.abp: P5 (history/**) and P10 (findings/**) for my writes, pending Dinis; no sub-agents (a breach by my account until Dinis decides; said so in the R10 report).
4. cl-6.dev may let keys-changes accept the parent entry's bundle.sign key (a warning on 228c0c6d9 is vouched for by security).
5. board/schedule.json (website) is stale; the conductor keeps it. The old accountant "wires" scheduled task still names admin/build (conductor's).
6. Watch: published tree size (about 225 MB artifact), run time creeping up before the change (8.6 to 11.3 min over 22 to 26 Nov).

## Key and signing for the new session
The private halves of this session's key were in its scratchpad and are lost with it. The new session makes its own key (openssl P-256 signing, RSA-4096 encryption; private halves mode 600 outside every repository), publishes it as site/keys/cl-6.devops.json (alone in its own commit; take the ssh field from the complete "ssh-keygen -y" line, never split it), and adds a new entry to board/keys.json marking devops-promptugal-cl-6 superseded. Container: apt-get update and apt-get install -y openssh-client for ssh-keygen; git config gpg.format ssh, gpg.ssh.program ssh-keygen, user.signingkey <pub>, commit.gpgsign true, in both clones.

## What my wake does
Pull both repositories (website: clone --depth 1, then git fetch --depth=20000 origin dev); stop on board/HOLD.md; R14 label file; read my grant (raw URL in restart.md); check deploy-pages runs on dev since the last wake (failures with causes, run time median and p90, cancelled and stale deploys); read release.sh, tag_release.sh and the tools for breakage; anything that changes a site goes to cl-6.security first; update agent.json; file the R10 run report; signed commit with Agent: and Claude-Session: trailers.

## Lessons
- findings/ is at the repo root, not under site/ (my first path mistake); history/ likewise.
- Job logs are huge (26,000 files listed): use get_job_logs with return_content false, curl the pre-signed URL into the scratchpad, grep. Never put a log into the context.
- Do not cat /tmp/code-sign (a binary).
