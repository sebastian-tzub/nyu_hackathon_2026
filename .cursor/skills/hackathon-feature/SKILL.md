---
name: hackathon-feature
description: Automatically implement plain-language requests to add, build, improve or fix MVP features with a developer, two independent reviewers and approved local commits.
---

# Hackathon feature coordinator

Read `.cursor/HACKATHON.md` and `.cursor/skills/hackathon-feature/references/review-contract.md` from the repository root. You are the parent coordinator. Use the named custom subagents; do not simulate their independent verdicts yourself.

## Low-friction experience

A normal feature request is the complete input. Never require a form, slash command, team board, named owner, detailed acceptance checklist or manual agent selection. Infer stack, commands, feature slug and acceptance checks from the request and repository. Use `.cursor/HACKATHON.md` defaults without asking users to fill anything in. Keep the brief and workflow records internal; briefly mention material assumptions while continuing. Only ask about ambiguity that changes the requested outcome, missing credentials needed for the feature, or genuinely conflicting teammate intent. Routine design and implementation choices are yours.

## Intake and isolation

1. Read the user’s plain-language request, repository instructions and relevant code/scripts. Convert the request into a narrow vertical slice with numbered observable acceptance criteria, explicit exclusions, contracts, allowed paths and evidence requirements. Record assumptions; ask only for choices that block correct implementation.
2. Read HACKATHON.md defaults and any existing permissions; discover commands from the repository. Discover actual Git branch/remote and status; never assume `main` or a clean directory. Do not modify existing dirty work. Use the existing exclusively assigned feature worktree, or create a new `feat/<owner>/<slug>` branch/worktree from a fetched, agreed integration ref. If Git has no initial commit, create an empty baseline commit using the configured Git identity before feature work; never include existing uncommitted files in that baseline. If no repository exists, initialize one for the requested project. Missing Git identity is a real blocker to committing; do not invent one. Do not build from an uncommitted sibling feature.
3. Use a board claim or shared-file owner only if the team already has one; absence is not a blocker. Infer the owner handle from existing Git identity when needed, otherwise use a unique neutral branch slug. Give the worktree a unique app port and test data namespace. Open/use that absolute worktree for every delegated task; subagents must not silently operate in the original directory.
4. Initialize the local run record per REVIEW-CONTRACT. Default 50 minutes, 3 review rounds; cap at a feature freeze only if the user/team provided one. Reserve roughly 10% intake, 50% build, 30% review/fixes, 10% delivery. Record a real deadline and check elapsed time between phases.

## Develop and review

5. Delegate to `mvp-developer` with the frozen brief, absolute worktree, permitted paths, commands, deadline and contract. Require `mvp-development`; for dashboard/data-heavy UI require `professional-dashboard-ui-ux`. Generic frontend still needs the UI acceptance/review checks.
6. Wait for developer completion. Verify evidence, then freeze the candidate exactly as REVIEW-CONTRACT specifies. You alone stage files and write run records. No commits yet.
7. Invoke `correctness-critic` and `product-ux-critic` independently against the same candidate. They return reports; you persist them. Both must actually run. If only one concurrent slot exists, run them sequentially in independent contexts. If custom subagent capability is unavailable, explain that this installation cannot run the required independent reviews and identify the capability to enable. Preserve progress; never make the user orchestrate reviewer chats, invent tool names, or fabricate approvals.
8. If either requests changes, deduplicate findings, return the smallest fix batch to the developer, then run relevant checks and freeze a new candidate. Rerun BOTH critics. No writer operates during review. If an acceptance criterion changes, record a new brief revision and obtain fresh approvals.
9. Continue until both approve, the real deadline expires or 3 review rounds have run. Failure to converge means BLOCKED with preserved code, outstanding findings and a concrete next action. Do not commit/deliver the feature as approved, disable tests or pressure critics into accepting it.

## Deliver

10. After exact-match approvals, read and execute `.cursor/skills/git-delivery/SKILL.md`. Local commit is part of this pipeline. Remote push/PR actions follow previously granted HACKATHON.md/user permissions without redundant confirmation. If integration was requested and authorized, route to `git-integration` with the agreed integrator; otherwise finish locally without asking for additional setup.
11. Give a short final response with feature outcome, verification (including both reviews), commit SHA and delivery state; mention limitations only when material. Keep detailed reports internal unless requested. Distinguish COMMITTED, READY_TO_INTEGRATE and INTEGRATED. Update the local run record after every transition, including on interruption.
