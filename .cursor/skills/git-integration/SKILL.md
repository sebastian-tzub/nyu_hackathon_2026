---
name: git-integration
description: Integrate approved team features one at a time, resolve Git conflicts safely and obtain fresh approvals for the combined result.
---

# Git integration and conflicts

Read HACKATHON.md and REVIEW-CONTRACT. Only one agreed integration owner advances the shared integration branch. If none is named, establish this only when shared integration is requested; do not make it a prerequisite for local feature work. Other users prepare an integration handoff. Respect existing merge permissions; do not request them again if already granted.

## Prepare a combined candidate

1. Use the team's existing integration queue or agreed single-integrator convention; no specific board tool is required. Verify a clean dedicated integration worktree, actual remote/branch, permissions, feature approval evidence and exact source SHA. Fetch and fast-forward the integration branch to the remote tip using `--ff-only`; if it diverged, inspect and coordinate rather than resetting it. Pin the base and source SHAs. Do not pull blindly or modify another person's dirty worktree.
2. Record the base SHA and start an integration run. Prepare the merge with `git merge --no-ff --no-commit <source-sha>` so even a possible fast-forward produces a reviewable combined tree before its integration commit. If already integrated, verify ancestry and report that fact; do not create a redundant merge. Follow an existing team-required squash policy only by preserving the same pre-commit combined-tree review gate.
3. A clean textual merge still needs semantic review. A conflict invokes the procedure below. No one else writes to this worktree while integration is underway.

## Resolve conflicts deliberately

- Use `git status --short` and `git diff --name-only --diff-filter=U` to inventory unresolved paths. Inspect common-ancestor, ours and theirs versions (`git show :1:<path>`, `:2:`, `:3:` where present), both feature intents and affected callers. In this merge, ours is integration and theirs is the pinned feature source; do not transfer this assumption to a rebase.
- Resolve each hunk to preserve both intended behaviors. Never bulk-select ours/theirs, discard a branch, run `reset --hard`/`clean -fd`, or force-push to conceal the conflict. Preserve unrelated functionality and document nontrivial decisions.
- For delete/modify, binary, API or schema disagreements with unclear intent, ask the shared-file owner a targeted question and stop that dependent change. Preserve the pending merge or abort only the merge you started with `git merge --abort` after checking for later user edits. No guessed contracts.
- Resolve dependency manifests semantically; regenerate lockfiles using the project's package manager and agreed versions. Do not hand-combine lockfile markers. Reconcile migration IDs/order with the schema owner; never rewrite an already applied shared migration.
- Stage explicit resolved paths. Confirm `git ls-files -u` is empty, inspect for accidentally retained conflict markers, and run `git diff --cached --check`. Marker-like fixture strings need manual interpretation.

## Verify, review and land

4. Run combined-tree checks: relevant tests, build/type checks and the shared demo smoke, covering both incoming behavior and existing features affected by shared files. Review cross-feature routing, state, dependencies and contract interactions. Source-branch approvals are not approvals of the merge result.
5. Before freezing, verify HEAD still equals the recorded integration base and MERGE_HEAD equals the pinned source SHA (normal merge). Freeze the merged candidate per REVIEW-CONTRACT with integration base, pre-merge HEAD, source SHA and staged tree. Delegate `correctness-critic` and `product-ux-critic` independently. For fixes, use `mvp-developer` as sole writer, then repeat checks and BOTH reviews under the same bounded budget. Do not resolve a conflict and skip review to save time.
6. When both approve, use `git-delivery` for the integration commit's local identity/hook safeguards. Its feature-PR step does not apply here. Fetch again before pushing: if the remote integration tip moved from the recorded base, keep the approved local commit, prepare a new combined candidate against the latest tip, and rerun checks and both reviews. Never force-push the integration branch. If a remote race rejects the push, repeat this reconciliation or release the slot as BLOCKED at the budget limit.
7. Push or merge through the agreed host workflow only when authorized. With required PR/CI policy, wait for checks on the final integration result; do not bypass protections or use a host merge that changes the reviewed tree without revalidation. Verify the landed SHA/tree, then run the shared demo smoke from the integrated state. Deployment is a separate authorized action.
8. Record INTEGRATED only when the shared branch contains the reviewed result and smoke passes. If post-landing smoke fails, stop the landing queue, investigate, and either fix through the review loop or perform an authorized revert. Preserve history; do not reset the shared branch. Release the integration slot and report final SHA and evidence.
