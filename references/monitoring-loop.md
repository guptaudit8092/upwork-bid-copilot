# Monitoring Loop (every 90 minutes)

A self-rescheduling check that alerts the user to new fits and proposal activity. **A scheduled run is never approval** — it only alerts.

## Each run

1. **Search**
   - Personalized feeds: "most recent" and "best match".
   - Recency-sorted keyword searches (customize to the user's niche). Default PM/ops set:
     `project manager`, `operations manager`, `product manager`, `program manager OR delivery manager OR chief of staff`, `implementation manager`, `technical product manager`, `account manager`, `project coordinator`, `process improvement`, `change management`, `AI adoption`, plus the user's tools (e.g. `monday.com`, `asana`, `hubspot`, `make.com`, `klaviyo`, `shopify`).
2. **Filter** — only jobs published after the stored **cutoff** and not in **SEEN**. Apply `screening-rubric.md`.
3. **Proposal activity** — list the user's proposals; compare `viewedByClient` and messages against the last known state. Alert on any *new* view, message or interview.
4. **Report**
   - Good fits or new views → message the user (and send a push notification if available) with the assessment template.
   - Nothing new → reply with exactly:
     `No new jobs as of <time> — next check ~<time + 1h30>.`
5. **Reschedule** — schedule the next run in 90 minutes with the updated state. Never let the chain lapse; if a run is missed, the next manual check should restart it.

## State carried between runs

Keep this compact block in the scheduled message so each run starts with full context:

```
CUTOFF: <ISO timestamp of last check>
WATCH: <proposal id> (<client / job>, $rate, boost n) …
ALREADY VIEWED: <proposal id> … (alert only on messages/interviews)
PENDING (awaiting user decision): <job id> — <one-line summary + open questions>
DO NOT BID: <job id> (<reason>) …
APPLIED CLIENTS: <client names> (flag before bidding on their other jobs)
SEEN: <job ids since cutoff>
USER RULES: rate floor, location, authorization, role types to skip
```

## Hygiene

- Drop pending jobs once they pass 50 proposals or ~4 days old.
- Move skipped jobs to DO NOT BID with a reason, so they're never re-alerted.
- When the user applies, move the job to APPLIED and add the proposal to WATCH.
