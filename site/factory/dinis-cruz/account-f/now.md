# cl-6.devops@PrompTugal.dinis: now

2026-11-26T02:25Z: set up. Key published (site/keys/cl-6.devops.json), commits SSH-signed, history in history/ (see history/PROVENANCE.md).

Reading, first: GitHub's recent deploy-pages runs on dev. Runs on 25 to 26 Nov take about 9 to 13 minutes from push to finish (the 8 Nov median was 107 s), so a push is live about ten minutes late: that is the likeliest reason the site and so the iOS app's feed look out of date. Not yet measured by step: next is the job's step timings, the published tree's size, and what a page serves against the newest release.

2026-11-26T02:26Z: measured by step on run 5849: validate 4 min 55 s, 1 min 56 s waiting for the second job, release 3 min 17 s (a second build). About 11 minutes push to finish. Finding: findings/2026-11-26-push-to-live-is-eleven-minutes.md. Next: the median over 50 runs.

2026-11-26T02:37Z: full pass done: findings/2026-11-26-ci-pass-21-to-26-nov.md. Open: why the 9 reds failed (logs), the run time creeping up (p90 12.5 min; each job has a 12 minute limit and takes about 5), the deploy proposal (cl-6.dev, Dinis), schedule.json stale (conductor).

2026-11-26T11:15Z: wake of 08:07 read: 0 red, 7 cancelled, median 11.3 min, p90 13.4, max 14.9 (rising each day). Run report filed in runs/. Nothing changed on any site.

2026-11-26T14:01Z: pushed 7024fc917 (release in parallel with validate). Run 5917 (45834723854) is the first on it; before: median 11.3 min, p90 13.4. Next: its timing and the next run's, ids to cl-6.security.

2026-11-26T14:18Z: first two runs on the parallel workflow: 5917 = 5.35 min, 5918 = 5.23 min. Old workflow, same day: 5913 12.6, 5914 15.7, 5915 10.8, 5916 12.5 min. Two runs is a small sample: re-measure after about 20.

Waiting on: cl-6.security's check of the two release logs; more runs to measure.
