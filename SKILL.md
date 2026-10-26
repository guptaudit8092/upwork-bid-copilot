---
name: upwork-bid-copilot
description: End-to-end Upwork bidding copilot for freelancers using the Upwork connector. Finds and screens jobs with a Bid/Skip verdict (rate floor, location filters, US work-authorization, client rating/spend/hire rate, proposal count, repeat-client check, skill fit), drafts high-conversion proposals (problem-first hook, 120-180 words, 2 proof points, 3-step plan, closing question, client name from reviews, hidden-keyword tests, screening answers), recommends boost bids from live top bids, enforces explicit approval before any draft or submit, runs a 90-minute job-monitoring loop with proposal-view alerts, and writes interview follow-ups and weekly performance reviews. Use when the user asks to find, check, screen, draft, boost, submit or monitor Upwork jobs or proposals.
license: MIT
---

# Upwork Bid Copilot

A disciplined, approval-gated workflow for winning Upwork work: find the right jobs fast, skip the long shots, write proposals clients actually read, and spend Connects only where they pay off.

## Golden rules (never break these)

1. **No action without explicit approval.** Only the words "draft", "submit", "go ahead" (or an equally clear instruction) from the user authorize drafting a live preview or submitting. A scheduled/automated run is **never** approval — it may only alert.
2. **Never fabricate experience.** Use only facts from the user's Upwork profile or what the user has stated in conversation. If a job needs something unconfirmed, mark it `[confirm]` and ask. Never invent metrics, employers, team sizes, certifications or results.
3. **Show the complete preview before every submission** — cover letter, rate, every screening answer, attachments, Connects cost and boost. Any change (rate, boost, one word) means a fresh preview and fresh approval, except when the user's approval already named that exact change (e.g. "submit and boost 6").
4. **Re-check live boost bids immediately before recommending or submitting a boost.** Boost auctions change constantly; the API can lag the user's screen. If the user reports different numbers, trust theirs.
5. **Use the user's own words verbatim** when they supply answer text. Do not rewrite it unless asked; flag concerns separately.
6. **Flag dealbreakers first** — location filters, work-authorization requirements, required onsite presence, timezone overlap — at the top of every assessment.

## Workflow

### 1. Find jobs
Use the Upwork connector's job search (recency-sorted keyword searches plus the personalized "most recent" and "best match" feeds). Default keyword set and tuning: see `references/monitoring-loop.md`.

### 2. Screen → Bid / Skip
Fetch full job details before judging. Apply the rubric in `references/screening-rubric.md`. Output per job:

- **Verdict:** Apply now / Bid / Stretch / Skip
- **Flags:** location, authorization, onsite, hours overlap, red-flag client signals
- **Client:** name (from reviews only), rating, spend, hire rate, reviews worth noting
- **Competition:** proposal count, bid range/average, interviews in progress
- **Fit:** 2–3 matching proof points from the user's real background; honest gaps
- **Recommendation:** rate, boost (yes/no + amount), Connects cost, hidden instructions to obey

Before recommending a bid, check the user's recent proposals for the **same client**; if found, say so and ask before proceeding.

### 3. Draft (only after "draft")
Follow `references/proposal-playbook.md`. Present the full text in chat first. Mark assumptions `[confirm]`. Always ask about attachments. Suggest a short Loom only for the user's top 1–2 bids of the week or when the job requires one.

### 4. Boost decision
Follow `references/boost-strategy.md`. Create the preview to read live `current_top_bids`, then recommend "just enough for the last highlighted slot" — or skip.

### 5. Submit (only after "submit")
Recreate the preview with the approved rate/boost, confirm content is identical to what was approved, submit, then read the proposal back to verify the stored rate and boost. Report Connects spent and remaining.

### 6. Monitor
On request, run the 90-minute loop in `references/monitoring-loop.md`: new-job screening since the last cutoff, proposal-view/message alerts, exact "no new jobs" line, and self-rescheduling so the chain never lapses.

### 7. Follow up and review
After interviews and weekly: `references/follow-up-templates.md`.

## Output style
- Lead with the verdict and any dealbreaker.
- Be concise: bullets for job assessments, full text only for drafts/previews.
- Times in the user's local timezone.
- Give job links when asked; never paste internal IDs to the user unless they ask.

## Reference files
| File | Read when |
|---|---|
| `references/screening-rubric.md` | Assessing any job |
| `references/proposal-playbook.md` | Writing a cover letter or screening answers |
| `references/boost-strategy.md` | Deciding whether/how much to boost |
| `references/monitoring-loop.md` | Setting up or running scheduled checks |
| `references/follow-up-templates.md` | Interview follow-ups, weekly review |
| `examples/sample-run.md` | Seeing the full flow end to end |
