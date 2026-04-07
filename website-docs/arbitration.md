# Arbitration rules

Report and arbitration for contributions or entries: level limits, case closure, no new reports after closure.

## 1. Why closure

Review, reports, and arbitration can chain: e.g. A’s contribution rejected by B → C reports B → D arbitrates C’s report → E reports D → F arbitrates… Without limits, one matter could be reported and arbitrated indefinitely. So the platform defines: a single contribution or single entry update is one «case»; the report/arbitration chain for that case has a level cap; once the cap is reached the case is closed and no new reports on that case are accepted.

## 2. What is a «case»

One case = one contribution submit or one entry update, identified by `contribution_id`; if it’s an update to an existing entry, also by `entry_id`.

All later reports and arbitrations about that contribution, that first review, or reports/arbitrations on them belong to the same case. Multiple updates to the same entry (`entry_id`) create multiple contributions and multiple cases, each with its own level and closure.

## 3. Levels and cap

Each case allows at most:

- **Level 0** — First review: reviewer’s first decision (approve / reject / request changes). Only once.
- **Level 1** — One appeal or one report + one arbitration: contributor’s appeal of that review, or anyone’s report on that contribution/review; one arbitration. Only one Level 1 per case (appeal and report share the slot).
- **Level 2** — One report on Level 1 arbitration + one arbitration (final): only one report against the Level 1 outcome; a different reviewer/panel does one arbitration. This is final; after Level 2 the case is closed.

After closure, no new reports are accepted for that case (whether the target is the contribution, the first review, Level 1 or Level 2 arbitration). Submitting a report on a closed case is rejected with a clear message.

## 4. After closure

When Level 2 is done, the case is marked closed. Then:

- New reports on any object in that case (contribution, first review, Level 1 or Level 2 arbitration) are rejected.
- API reports targeting a closed case return **409 Conflict** with code `CASE_CLOSED`, e.g. «Reports and arbitration for this entry/contribution are closed; no new reports accepted.»

This keeps «supervisors can report unfair review» while avoiding infinite report/arbitration chains.

Role recusal in the same case: contributors cannot review their own; reviewers who did Level 0 or Level 1 cannot do Level 2 for that case.

## 5. Multiple updates to the same entry

Multiple updates to the same entry (`entry_id`) are separate contributions and separate cases. E.g. entry X has contribution 1 (approved), then 2 (update), then 3 (update). Cases 1, 2, 3 each have Level 0 → 1 → 2 and close independently. So one entry is not «never closed»; each version’s case closes on its own.
