# Screening Rubric — Bid / Skip

Always fetch the full job (description, client record, reviews, screening questions, preferred qualifications, activity) before giving a verdict. Snippets hide dealbreakers.

## Step 1 — Hard dealbreakers (check first, report at the top)

| Check | Skip if… |
|---|---|
| Location | Preferred/required countries exclude the user's country **and** `location_required` is true. If it's only a preference, flag it and continue. |
| Work authorization | Post requires authorization to work in a specific country "without sponsorship" and the user lacks it. Treat as a hard skip regardless of fit. |
| Onsite | Requires onsite presence the user can't meet. |
| Hours overlap | Required live overlap the user can't provide (convert to the user's timezone and state it). |
| Rate | Max budget is below the user's floor (default **$25/hr**) — unless the job is unusually strong; then say why. Convert fixed-price "full-time" budgets to an effective hourly rate. |
| Exclusivity | Demands exclusivity the user can't offer. |

## Step 2 — Client quality

| Signal | Good | Caution | Skip |
|---|---|---|---|
| Rating | ≥ 4.7 | 4.3–4.7 | < 4.0, or recent 1★ reviews describing the same role |
| Total spend | ≥ $10k | $1k–10k | < $1k with no hires, or unverified payment |
| Hire rate | ≥ 50% | 25–50% | < 20% |
| History | Repeat hires, long contracts | Few contracts | Same role re-posted after short failed contracts |

Read the written reviews: they reveal the contact's name (use it in the letter) and warning signs (scope squeezing, unpaid trials, micromanagement).

## Step 3 — Competition and timing

- **< 5 proposals** → "Apply now" (aim to bid within the first hour).
- **5–20** → normal.
- **20–50** → bid only on strong fit; consider a boost.
- **50+** → skip unless the user insists.
- Note interviews in progress and invites sent — many interviews already running lowers odds.
- Older than ~4 days with high proposal counts → usually stale.

## Step 4 — Fit

- Map 2–3 requirements to **real** proof points from the user's profile or statements.
- List honest gaps. If a must-have is unconfirmed, ask the user before drafting.
- Distinguish role types: PM/ops/account management vs. hands-on builder/developer roles. If the user has said they skip a role type, skip it.

## Step 5 — Repeat-client check

Search the user's recent proposals for the same client. If found, tell the user before recommending another bid.

## Step 6 — Hidden instructions

Scan for "start your proposal with…", keyword tests, "find the mistakes in this post", required Loom, required screenshots. List them in the recommendation — missing one usually means instant rejection.

## Verdict scale

- **Apply now** — strong fit, good client, < 5 proposals.
- **Bid** — good fit and client, competitive but winnable.
- **Stretch** — real gaps or weaker client; explain the trade-off.
- **Skip** — any dealbreaker, weak client, or long shot. One line on why.

## Assessment template

```
[Verdict] — [Job title]
⚠️ Flags: [location / authorization / onsite / hours]
Client: [name if in reviews], [rating]★, [spend], [hire rate]% — [notable review]
Competition: [n] proposals, bids $[min]–[max] (avg $[avg]), [n] interviewing
Fit: [proof 1]; [proof 2]. Gaps: [gap]
Recommend: $[rate]/hr · boost [yes n / no] · [Connects] Connects
Required: [hidden instructions, Loom, keyword]
```
