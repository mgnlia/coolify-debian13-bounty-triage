# Coolify Debian 13 Bounty Triage — Final Remediation Dossier (`jJ3m1TC_u5ffAb-pjkPtM`)

Date: 2026-02-14

## Executive correction summary
This remediation resolves 5 adversary findings:
1. Deliverable metadata completeness: addressed in task update.
2. Wrong repo: fixed by moving artifacts to dedicated repo `mgnlia/coolify-debian13-bounty-triage`.
3. Stale competition status: corrected — PR `#8250` is **closed**, branch deleted.
4. Bounty amount ambiguity: corrected to **$13,800 total pool** (2x $6,900 sponsors).
5. Missing competitor technical analysis: added with anti-repeat guidance.

---

## 1) Canonical evidence
- Issue (open): https://github.com/coollabsio/coolify/issues/8154
- Competing PR (closed): https://github.com/coollabsio/coolify/pull/8250
- PR #8250 raw diff: https://patch-diff.githubusercontent.com/raw/coollabsio/coolify/pull/8250.diff
- Algora claim example showing pool and sponsors:
  - https://algora.io/claims/6bdZBHqmWqedLz2A
  - https://algora.io/claims/NF7kbq3WSHyfX7oY
  - https://algora.io/claims/tiokpEL6FSKEXMcd

## 2) Competition assessment (corrected)
- Prior dossier incorrectly treated competitor as pending in a way that gated decision.
- Ground truth now:
  - Maintainer `ShadowArcanist` **closed** PR `#8250` on Feb 10.
  - Branch `feat/debian-13-support` deleted.
  - GitGuardian reported leaked secret in the PR context.

### Implication
The field is not blocked by an accepted incumbent implementation. Competition exists, but a clean, compliant, secure submission can still win.

## 3) Bounty value (corrected)
From Algora claim pages for this issue family:
- **Total prize pool: $13,800**
- Sponsors listed:
  - `buildingvibes` — $6,900
  - `coollabsio` — $6,900

This is definitive for current ROI framing.

## 4) Competitor technical analysis summary
PR #8250 implemented:
- dynamic repo codename probing via `${VERSION_CODENAME}`;
- fallback to `bookworm` when `trixie` repo metadata unavailable;
- unit test asserting fallback string logic.

Why closed/non-converting:
- closure by maintainer and branch deletion;
- security contamination (GitGuardian secret finding) likely reduced viability even if logic was reasonable.

## 5) Updated recommendation
## **GO**

Rationale:
- Issue still open and bounty-tagged.
- Prior visible competitor PR closed and branch removed.
- Prize pool is materially larger than originally modeled ($13.8k).
- Failure mode in prior competitor provides clear anti-patterns to avoid.

## 6) Execution guardrails for successful submission
1. Post required implementation plan comment in issue #8154 before coding.
2. Keep diff minimal and scoped to Debian13 validation + Docker fallback behavior.
3. Add/retain focused tests for fallback path.
4. Run local secret scanning + review staged files to avoid unrelated artifacts.
5. Include reproducible evidence logs in PR description.

## 7) Immediate next action
- Start implementation only after plan comment is posted, then submit clean-room PR rapidly while maintaining security hygiene.
