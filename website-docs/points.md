# Points system

How points are earned and deducted; rules for contribution, review, reports, feedback and consumption; capability limits when points are low.

## 1. What are points

Each account has a points balance tied to `user_id`. New users get limited initial points for cold start; the platform may release more in phases. Points change with your actions and are shown in Account.

Points are community currency: they affect what you can do. When low, writes (e.g. contribute, report) may be rejected or rate-limited; consistent compliance and quality contributions build points and higher limits.

## 2. Earning and deducting

The following trigger point changes (positive = earn, negative = deduct). Exact amounts are configured by the platform.

### Contribution

- **Contribution approved** — Your entry is approved and listed; you earn points.
- **Contribution rejected** — Rejected by reviewer; small deduction (or 0) to signal quality.
- **Changes requested then approved** — You resubmit after changes and get approved; you earn (often less than direct approve).

### Review

- **Review completed** — You approved/rejected/requested changes on a pending contribution; earn per item.
- **Your review reported and upheld** — A report against your review was upheld (unfair or wrong); points deducted.

### Reports

- **Report upheld** — Your report was upheld; you earn points.
- **Report dismissed / abuse** — Report dismissed or deemed abuse; points deducted.
- **You were reported and upheld** — Your contribution, feedback, or review was reported and upheld; points deducted.

### Feedback and consumption

- **Valid feedback** — Your rating or comment was accepted or not reported; may earn a little (or 0).
- **Your feedback reported and upheld** — Your feedback was reported and upheld (e.g. fake review); points deducted.
- **Consume / redeem** — Use points for benefits (e.g. priority listing); points deducted by benefit.
- **Violation deduction, activity reward** — Platform violations deduct points; activities or tasks may award points.

Each event triggers at most one change; if an appeal or report reverses the outcome, points are adjusted and noted in the ledger.

To prevent gaming, some rewards may be delayed (T+N) or released in phases; if deemed abnormal, rewards may be frozen, clawed back, or sent to manual review.

## 3. Points and capability limits

When points are low, some actions are blocked or more restricted.

- **Submit contribution** — Below the contribution threshold (e.g. < 0) you cannot submit; earn via review, valid reports, or feedback first.
- **Submit report** — Below the report threshold you cannot submit; after abuse deductions you may be blocked from reporting for a period.
- **Review** — If your «review reported and upheld» drops your points below a limit, review access may be suspended until recovery or manual restore.
- **Rate limits** — Higher points can mean higher daily/hourly write limits; low points trigger rate limits (e.g. 429) sooner.
- **Cold start** — New accounts may have stricter daily limits and risk thresholds even with points.

`POST /points/consume` returns 409 with `INSUFFICIENT_POINTS` when balance is too low (see live API).

## 4. Ledger and query

Each change records event type, delta, balance after, related ids, and time. View in Account; APIs are `GET /api/v1/points/account` and `GET /api/v1/points/records` (authenticated). Public leaderboard: `GET /api/v1/points/leaderboard`.
