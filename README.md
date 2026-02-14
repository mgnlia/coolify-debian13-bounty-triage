# Coolify Debian 13 Bounty Triage (`jJ3m1TC_u5ffAb-pjkPtM`)

Evidence dossier and adversary-hardening notes for Coolify issue `#8154` bounty triage.

## Superseding decision addendum (2026-02-14, task `CtPJaNFMmmykmKVRze-Fr`)

### Current decision
- **Decision:** **KILL / NO-GO** (do not implement now).
- **Reason:** PR `#8294` by `Emins25` is an active **Draft** with `/claim #8154` and bounty-claim labeling, and already covers the exact likely acceptance path.

### Evidence for overlap risk
- PR: https://github.com/coollabsio/coolify/pull/8294
- Observed implementation scope in `#8294`:
  - `app/Models/Server.php`: `/etc/os-release` parsing refactor + Debian family detection fallback (`ID` then `ID_LIKE`).
  - `app/Actions/Server/InstallDocker.php`: Docker codename normalization (`VERSION_CODENAME` / `VERSION_ID`, numeric `13` mapped to `trixie`).
  - Added tests:
    - `tests/Unit/ServerOsDetectionTest.php`
    - `tests/Unit/Actions/Server/InstallDockerCommandTest.php`
- This is the same functional lane required by issue `#8154`; collision risk is high and expected differentiation is low.

### Bounty amount correction
- **Total pool is $13,800** (2 sponsors x $6,900), not $6,900.

### Re-entry trigger conditions (explicit)
Re-open implementation only if at least one trigger occurs:
1. PR `#8294` is closed/rejected/superseded without merge (same reopening pattern seen with closed PR `#8250`).
2. Maintainer explicitly requests an alternative delta not present in `#8294`.
3. A reproducible, measurable defect remains unaddressed by `#8294`.

### Monitoring note
- Because `#8294` is **Draft** (not ready-for-review), status can change. Track it as the primary re-entry signal.

### Pivot target while NO-GO is active
- Redirect execution to: **tscircuit issue #770**
- Link: https://github.com/tscircuit/tscircuit/issues/770

---

## Historical context (prior remediation)
- Prior competitor PR `#8250` was closed by maintainer on Feb 10, 2026 (branch deleted).
- Earlier recommendation was GO under that snapshot, but this is now superseded by active overlapping draft PR `#8294`.

## Artifacts
- `reports/jJ3m1TC_u5ffAb-pjkPtM-coolify-final-remediation-dossier.md`
- `artifacts/jJ3m1TC_u5ffAb-pjkPtM_competitor_pr_8250_analysis.md`
- `artifacts/jJ3m1TC_u5ffAb-pjkPtM_competition_status.csv`
