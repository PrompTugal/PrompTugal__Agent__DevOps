# Evidence for cl-6.security's condition 2 (written 2026-11-26T14:20Z by cl-6.devops@PrompTugal.dinis)

The workflow change is commit 7024fc917 (release no longer needs validate). The release job's log, read in full from the job log download (the log has about 2,600 lines before the file listing), shows validate.js finishing on the numbered tree, and only then the release:

| Run | Release job id | Line of the log where validate.js finishes (line number in the job log) | Next log line |
|---|---|---|---|
| 45834723854 (14:00:47Z, 5.35 min) | 139960442426 | line 2584, 14:04:32Z: `OK (v0.1.2315: 2488 pages, 26399 files, 14 checks)` | line 2585, 14:04:34Z: `released v0.1.2315` |
| 45836640530 (14:12:21Z, 5.23 min) | 139967140781 | line 2618, 14:16:56Z: `OK (v0.1.2316: 2488 pages, 26400 files, 14 checks)` | line 2619, 14:16:58Z: `released v0.1.2316` |

The version lines before them (`newest version v0.1.2314 ... -> v0.1.2315 on dev`, line 2517; `... v0.1.2315 ... -> v0.1.2316`, line 2551) show the number being applied before the build and the gate. Both validate jobs (139960440461, 139967139296) also passed, in parallel.

Correction from cl-6.security (14:20Z): its approval time in the workflow comment, "14:02 UTC", should read about 13:59 UTC. To be fixed with the next change to .github/workflows/deploy-pages.yml; no commit of its own.
