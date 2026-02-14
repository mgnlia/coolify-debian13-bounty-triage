# Kill Decision Memo — `CtPJaNFMmmykmKVRze-Fr`

## Scope
Task: **Pursue Coolify Debian 13 bounty claim** (`CtPJaNFMmmykmKVRze-Fr`)  
Repository: https://github.com/mgnlia/coolify-debian13-bounty-triage  
Related issue: https://github.com/coollabsio/coolify/issues/8154

## Final Decision
**KILL / NO-GO** on implementation under current board conditions.

## Evidence (PR #8294 is real, claimed, and substantive)
Primary overlap artifact: https://github.com/coollabsio/coolify/pull/8294

Observed signals confirming active competitive occupation:
- PR author: `Emins25`
- Status: **Draft**
- Includes claim signal: `/claim #8154`
- Includes bounty-claim labeling
- Contains substantive implementation in the exact acceptance lane for #8154:
  - `app/Models/Server.php` OS detection fallback (`ID` then `ID_LIKE`)
  - `app/Actions/Server/InstallDocker.php` codename normalization and numeric Debian mapping (`13 -> trixie`)
  - unit tests for both paths

Conclusion: expected merge path overlap is high; differentiation surface is low.

## Competition Timeline (why this is now a kill)
- **2026-02-10**: Prior competing PR `#8250` was closed (historical precedent that competitor state can invalidate assumptions).
- **2026-02-12**: New competitor PR `#8294` appears with claim signal and substantial Debian 13 implementation coverage.
- **2026-02-14**: Adversarial review confirms `#8294` is credible and lane-capturing; decision set to **KILL** and execution pivots away from Coolify #8154.

## Pivot Rationale
With #8294 occupying the same acceptance lane, additional spend on Coolify #8154 has poor risk-adjusted expected value.  
Execution is redirected to higher-probability work: **tscircuit #770**
- https://github.com/tscircuit/tscircuit/issues/770

## Explicit Re-entry Trigger (Draft-state watch)
Because `#8294` is currently **Draft**, this task may be re-opened only if one of the following occurs:
1. `#8294` is closed/rejected/abandoned/superseded without merge (same pattern previously seen with `#8250`).
2. Maintainer explicitly requests a materially distinct delta not implemented in `#8294`.
3. A reproducible, high-impact defect remains unaddressed by `#8294`.

Until one trigger occurs, this task remains frozen.

## Bounty Pool Note
Correct pool for this lane: **$13,800 total** (2 sponsors × $6,900).
