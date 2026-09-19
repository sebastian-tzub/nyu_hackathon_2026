# Candidate and approval contract

The parent coordinator owns state and Git mutations. The developer edits only while in DEVELOP/FIX. Reviewers are independent and read-only. Never run the writer concurrently with reviewers.

## Local run record

Resolve `git rev-parse --git-path hackathon-runs/<feature-id>` to an absolute path and store the brief, state, evidence, findings and reports there. This is local Git metadata, not the feature index. Use a safe unique slug. Do not commit these mutable logs. The parent writes reviewer responses verbatim.

Record: feature ID, owner, absolute worktree, branch, kit revision, brief revision, start/deadline, round, allowed paths, base SHA, pre-commit HEAD, candidate tree ID, integration source SHA and expected commit parents if any, delivery mode (new commit or review existing hook-altered commit), command results, reviewer statuses, blockers, next action and final commit SHA. Resume only after reconciling the record with live Git state. For a pending normal merge, verify `git rev-parse MERGE_HEAD` equals the recorded source SHA and HEAD equals the recorded integration base. If the merge was aborted or reconstructed, invalidate approvals and prepare the merge again; matching file contents alone do not prove correct ancestry. For a completed integration commit, verify its parents against the recorded base and source. For an explicitly agreed squash, record the source-to-result mapping and expect only the integration base as parent.

## Freeze a candidate

1. Stop the writer. Inspect tracked changes, untracked files and ignored files that might be required at runtime. Inventory intentional feature files, additions and deletions. Never include secrets or unrelated work.
2. Run agreed checks on this candidate. Store command, working directory, exit code, concise output and manual evidence. Failed or unavailable required checks are blockers; do not mark them passed. Fix first, then rerun affected checks.
3. Coordinator stages explicit intended paths with `git add -- <paths>`. Review `git diff --cached --stat`, `git diff --cached`, `git diff --cached --check`, `git diff --exit-code`, and `git status --short`. Any unstaged tracked changes or unresolved entries prevent a freeze. Account for all untracked files; runtime must not rely on omitted local files.
4. Record `git rev-parse HEAD` and `git write-tree`. The candidate identity is **brief revision + base SHA + HEAD + tree ID**, and source SHA for integration. Every acceptance or code change invalidates both approvals. Review records live outside the tree to avoid self-referential hashes.
5. Pass both critics the same brief, identity, complete feature diff (base to candidate), code paths, check evidence and runnable local URL/screenshots when relevant. Do not send either critic the other's verdict. Use separate contexts, in parallel if supported; sequential independent contexts are acceptable.
6. Critics verify the recorded identity against the current index using read-only inspection (`git diff --cached`, `git rev-parse HEAD`, and `git diff --cached <tree-id> --exit-code`). Any mismatch means BLOCKED. Parent rechecks the tree after both return and immediately before committing.

For an initial feature, base is the worktree's integration starting commit. For a merge, base is the current integration HEAD, and the staged tree is the complete combined result. Include relevant unchanged code/contracts during review; a diff alone is insufficient.

## Review response — required from each critic

```text
Reviewer: correctness-critic | product-ux-critic
Candidate: brief=<revision> base=<sha> head=<sha> tree=<sha> source=<sha-or-na>
Verdict: APPROVE | CHANGES_REQUESTED | BLOCKED
Acceptance coverage: <criterion IDs → observed evidence / not verified>
Checks inspected: <commands/results or manual evidence>
Findings:
- <stable ID> | <blocking or nonblocking> | <path:line or route>
  Reproduction: ...
  Expected / actual: ...
  Smallest appropriate fix: ...
Limitations: <unverified areas and reason>
```

APPROVE means no unresolved blocking findings in the reviewer's remit, sufficient evidence, and exact identity match. Bugs on the promised path, data loss/exposure, broken contracts, required failed checks, unusable UI and unmet acceptance criteria block. Taste, optional abstractions and future scalability suggestions do not. BLOCKED means evidence, tools or a decision is missing; it is not approval.

The parent merges findings by root cause, preserves their IDs, and sends actionable fixes to the developer. Both critics re-review every revised candidate, including regressions outside the fixed lines. They may accept evidence that a finding was mistaken, but only that critic may withdraw its finding. The coordinator cannot override a verdict. No majority vote, self-approval or reuse of one old approval with one new approval.

Critics may request additional checks. Their read-only configuration may prevent test commands that write caches/artifacts: the parent/developer runs these serially and returns evidence. A required live UX review needs browser access or sufficient captured visual and interaction evidence; without it, report BLOCKED rather than claim the UI was inspected.

## Exit states

`INTAKE → DEVELOP → VERIFY → REVIEW → FIX → VERIFY → REVIEW → APPROVED → COMMITTED → READY_TO_INTEGRATE → INTEGRATED`.

Any phase can enter BLOCKED. Budget expiration, three unsuccessful rounds, unavailable independent reviewers, missing credentials/checks, unresolved contract ambiguity or permission failure preserve the branch and evidence, identify the smallest unblock, and stop before delivery. Do not silently reduce criteria. A human may approve a smaller brief; increment its revision and restart both reviews within a newly agreed budget.
