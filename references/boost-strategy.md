# Boost Strategy

A boost is a Connects bid for one of the highlighted top slots on the client's proposal list (typically 4). Upwork generally charges the boost only if you finish in the top slots or the client engages before the auction closes.

## Always do first

1. Create (or refresh) the proposal preview to read the **live** `current_top_bids`.
2. If the user sees different numbers on their screen, use theirs — the API can lag.
3. Re-check again right before submitting; bids move constantly.

## Decision table

| Situation | Recommendation |
|---|---|
| Fewer boosted bids than slots | Boost at the auction minimum + 1 (cheap guaranteed slot) |
| Last slot is cheap (≤ ~10 Connects) | Boost just above the last slot |
| Strong fit, good client, 10+ proposals | Boost just above the last slot if affordable |
| Top slots very expensive (30+) | Usually skip; boost only for a standout job, and say what it costs |
| Low rate, vague post, low hire rate, 50+ proposals | Don't boost |
| Dealbreaker flags (location/authorization) | Don't boost |

**Target:** roughly 1 boost per 4 proposals. Bid *just enough* for the last highlighted slot — never chase #1 by default.

## How to present it

```
Boost: yes, [n] Connects.
Current top bids: [a, b, c, d] → [n] takes the last highlighted slot.
Total cost if charged: [apply + boost] Connects (balance after: [x]).
```

## After submitting

Read the proposal back and confirm the stored boost amount. A boost cannot be raised later; a proposal submitted without one can usually have one added via edit.
