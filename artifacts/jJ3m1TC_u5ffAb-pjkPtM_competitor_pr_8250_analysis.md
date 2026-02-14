# Competitor Technical Analysis — PR #8250 (`Add additional server support for Debian 13`)

Source PR: https://github.com/coollabsio/coolify/pull/8250  
Raw diff: https://patch-diff.githubusercontent.com/raw/coollabsio/coolify/pull/8250.diff

## What competitor changed
1. In `app/Actions/Server/InstallDocker.php`:
   - Introduced `DOCKER_CODENAME=${VERSION_CODENAME}`.
   - Added runtime probe:
     - `curl -fsSL https://download.docker.com/linux/${ID}/dists/${VERSION_CODENAME}/Release`
   - If unavailable, forced fallback:
     - `DOCKER_CODENAME=bookworm`
   - Wrote apt source using `${DOCKER_CODENAME}` instead of `${VERSION_CODENAME}`.

2. Added test `tests/Unit/InstallDockerDebianFallbackTest.php` asserting key fallback strings are present.

## Why this approach is directionally correct
- Debian 13 (`trixie`) can pass OS checks before Docker repo has full codename publication.
- A runtime repo-availability probe + fallback to Debian 12 (`bookworm`) is a pragmatic bridge.
- Auto-reversion to trixie once Docker publishes repository metadata is a sensible future-proof behavior.

## Why PR #8250 still failed to convert
1. **Maintainer closed PR on Feb 10, 2026**.
2. **Branch deleted** after closure (`feat/debian-13-support`).
3. **GitGuardian flagged a hardcoded secret** in PR commit `548dc51` in `.claude/skills/pest-testing/SKILL.md`.

This is critical: even if core logic is acceptable, security hygiene and submission cleanliness can invalidate or de-prioritize a claim.

## Avoid-repeat guidance for our attempt
- Keep PR scoped to required files only (no unrelated skill/docs artifacts).
- Run secret scan locally before push; verify no credentials/tokens in git history.
- Include mandatory implementation plan comment on issue #8154 **before coding** (maintainer requirement).
- Prefer minimal, auditable diff + reproducible validation logs.

## Clean-room implementation principle
Use competitor intel only as risk-avoidance context; implement independently with:
- explicit acceptance test for Debian13 path,
- explicit negative test for missing codename repo,
- no copied commit history or artifact contamination.
