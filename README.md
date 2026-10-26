# Upwork Bid Copilot

**A Claude skill that runs your entire Upwork bidding workflow — from finding jobs to winning interviews — with strict approval gates so nothing is ever sent without you.**

Built by a freelance project manager who uses it daily. It encodes a proven process: bid early, skip long shots, lead with the client's problem, and spend Connects only where they pay off.

---

## What it does

### 🔎 Finds and screens jobs (Bid / Skip verdicts)
- Searches recency-sorted keywords plus your personalized "most recent" and "best match" feeds
- Flags **dealbreakers first**: preferred/required location, **work-authorization** requirements, onsite presence, timezone overlap, exclusivity
- Enforces your **rate floor** (default $25/hr) and converts fixed "full-time" budgets to effective hourly rates
- Scores **client quality**: rating, total spend, hire rate, written reviews, repost patterns, failed prior contracts
- Reads **competition**: proposal count, bid range and average, interviews already running
- Marks jobs with **< 5 proposals as "Apply now"** and skips 50+ proposal jobs
- **Repeat-client check**: warns before you bid again with a client you recently applied to
- Detects **hidden instructions** (opening keywords, "find the mistakes in this post", required Loom)

### ✍️ Drafts proposals clients actually read
- **Problem-first hook** in the first 150–200 characters (what clients see in their list)
- **120–180 words**: hook → 2 proof points → 3-step plan → one closing question
- Uses the **client's name** only when reviews or the post state it
- **Screening answers** in 2–4 sentences with a concrete example each
- Uses **your own answer text verbatim** when you provide it
- **Never fabricates experience** — unconfirmed claims are marked `[confirm]`
- Asks about attachments; suggests a **Loom** only for your top 1–2 bids per week

### 🚀 Recommends boosts with live data
- Reads the **live top boost bids** right before recommending or submitting
- Bids **just enough for the last highlighted slot** — never chases #1 by default
- Targets roughly **1 boost per 4 proposals**; never boosts low-rate, vague or 50+ proposal jobs

### 🔒 Approval-gated submission
- Nothing is drafted live or submitted without an explicit **"draft"** or **"submit"**
- **Scheduled runs are never treated as approval**
- Shows the **complete preview** (letter, rate, every answer, Connects, boost) before every submit
- Reads the proposal back after submitting to verify the stored rate and boost

### ⏱️ 90-minute monitoring loop
- Screens only jobs newer than the last check
- Alerts on **new proposal views, messages and interviews**
- Sends a clean `No new jobs as of <time> — next check ~<time>` line when quiet
- Carries compact state (cutoff, watch list, pending, do-not-bid, seen) and **reschedules itself** so it never lapses

### 📈 Follow-ups and weekly review
- Interview **follow-up message** (recap, 1-week plan, one clarifying question)
- **Weekly performance review**: views/replies vs. boost, timing, rate band and client quality, with 3–5 data-backed adjustments

---

## Requirements

- Claude with **Skills** enabled
- The **Upwork connector** (job search, proposals, boost previews)
- Optional: a scheduling/reminder tool for the monitoring loop, and push notifications for alerts

## Installation

1. Download or clone this repository.
2. Zip the `upwork-bid-copilot` folder (the folder containing `SKILL.md`).
3. In Claude, go to **Settings → Capabilities → Skills** and upload the zip.
4. Connect the Upwork connector.

> Claude Code users: copy the folder into `~/.claude/skills/upwork-bid-copilot/`.

## Usage

| Say | What happens |
|---|---|
| "Any new fits?" / "Check for jobs" | Searches, screens, returns Apply now / Bid / Skip verdicts |
| "Is this a good fit — [job title]?" | Full assessment of one job with flags and recommendation |
| "Draft" | Writes the cover letter and screening answers for review |
| "Should I boost?" | Reads live top bids and recommends an amount (or skip) |
| "Submit and boost 6" | Submits exactly the approved preview, then verifies it |
| "Check every 1.5 hours" | Starts the self-rescheduling monitoring loop |
| "Weekly review" | Read-only performance report with next-week adjustments |

## Repository structure

```
upwork-bid-copilot/
├── SKILL.md                     Core rules and workflow
├── README.md                    This file
├── LICENSE                      MIT
├── references/
│   ├── screening-rubric.md      Bid/Skip criteria and assessment template
│   ├── proposal-playbook.md     Cover-letter formula, screening answers, checklist
│   ├── boost-strategy.md        Boost decision table
│   ├── monitoring-loop.md       Scheduled-check procedure and state format
│   └── follow-up-templates.md   Interview follow-up and weekly review
└── examples/
    └── sample-run.md            Anonymized end-to-end example
```

## Customizing

- **Rate floor, keywords, role types to skip:** edit `references/screening-rubric.md` and `references/monitoring-loop.md`, or simply tell Claude ("my floor is $40/hr", "skip developer roles").
- **Your experience:** the skill reads your Upwork profile and what you tell it in chat. It will ask rather than guess.

## Principles

1. Honesty over polish — never invent experience.
2. You stay in control — no draft or submission without explicit approval.
3. Fewer, better bids — skip long shots, bid early, boost selectively.

## License

[MIT](LICENSE) © 2026 Udit Gupta
