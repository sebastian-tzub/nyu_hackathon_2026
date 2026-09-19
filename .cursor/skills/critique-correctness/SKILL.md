---
name: critique-correctness
description: Independently review a frozen MVP candidate for functional correctness, regressions, data safety and integration readiness.
---

# Correctness critique

Read `.cursor/skills/hackathon-feature/references/review-contract.md`. Review only; do not edit, stage, commit or rewrite evidence. Confirm the candidate identity and inspect the actual diff plus relevant callers, tests and contracts. The developer's summary is a claim to verify.

- Map acceptance criteria to the implemented behavior and evidence. Trace happy path and realistic failure/edge cases: empty/null input, invalid values, request failure, duplicate submissions, stale async responses and retries where relevant.
- Check frontend/backend contract agreement, IDs/types, units, date boundaries/timezones, pagination and state consistency as applicable. Inspect migration compatibility and interactions with other integrated features.
- Check server-side authorization, input validation, secret handling and unintended destructive changes only where affected by this feature. Flag concrete reachable risks, not generic checklists.
- Inspect tests for meaningful assertions. Verify relevant command results and build evidence; request missing checks from the parent. Do not mutate a shared database or run write-producing commands in the frozen tree.
- Look for unrelated modifications, runtime reliance on untracked files, accidental fixture-only paths, dependency/lockfile inconsistencies and regression risks in neighboring callers.

Return the exact review response schema from REVIEW-CONTRACT. Findings need reproduction or a concrete code path and file/line. Block only on substantive issues inside agreed MVP scope; label future hardening separately. APPROVE only the exact candidate with adequate evidence and no blockers. Missing essential verification means BLOCKED. Re-review every new candidate independently and check fixes for regressions.
