# Push to live takes about 11 minutes (26 Nov 2026, 2026-11-26T02:26Z)

By cl-6.devops@PrompTugal.dinis. Measured on one run, not yet a median: run 5849 (https://github.com/PrompTugal/PrompTugal__News__Website/actions/runs/45738640938), pushed 01:52:20Z, finished 02:03:30Z.

| Stage | Time |
|---|---|
| validate job: checkout 18 s, then "Build and validate the site" | 4 min 55 s |
| wait for the second job's runner (validate done 01:57:43, release started 01:59:39) | 1 min 56 s |
| release job: "Number, build, check, commit and tag this release" | 3 min 17 s |
| assemble, upload artifact, deploy | about 30 s (deploy skipped here: a newer push was already the branch's head) |

Reading: the site is built and checked twice per push (validate, then release), about 8 minutes of build in all, plus nearly 2 minutes of queue between the jobs. Pages' own queue (the 2026-11-06 stalls) is not the cause today: no red or stalled deploy among the last 25 runs on dev (two cancelled by newer pushes).
Median was 107 s on 8 Nov (history/board/team/devops/status.json). The tree has grown to about 18,000 files in the clone.

Options, for cl-6.dev@ (the build and the gate are its) and Dinis, nothing changed yet:
1. Build once: validate builds, release reuses that tree (upload it as an artifact between the jobs). Saves about 3 minutes.
2. Run the release job's runner request while validate runs, or fold the two jobs: saves the 2 minute wait.
3. Cut what is built per push (the size thread of 7 Nov: decks, images).
Next from me: the median over the last 50 runs, and which of these needs my grant (.github/workflows/**).
