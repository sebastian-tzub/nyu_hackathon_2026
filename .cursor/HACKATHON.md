# Optional team preferences

Ready to use as provided. Do not ask users to complete a setup form.

- Feature budget: 50 minutes, at most 3 review rounds. Respect any deadline the user supplies; do not ask for an event end time just to start.
- Stack, install/dev/check commands, design system: discover from repository files and existing CI. Reuse them. If a check does not exist, use an appropriate focused smoke check; missing infrastructure alone is not a reason to invent a large test suite or block work. Existing required checks must pass.
- Branch/base: discover from Git and repository instructions. Prefer the remote default branch for new isolated feature work; use an explicitly assigned feature branch when available. Never assume a branch is named main.
- Parallel work: automatically use an isolated feature branch/worktree when the current checkout is shared, dirty or on the integration branch. Use unique ports and isolated test data. Do not ask users to manage worktrees. Do not discard their edits.
- Ownership: use existing team conventions/board if present. No board or owner list is required. Ask a teammate only when overlapping changes have genuinely ambiguous intent; handle straightforward conflicts yourself.
- Permissions: approved local commits are part of this workflow. Push, PR creation, shared-branch merges and deployment follow explicit permissions already provided by the user/team. Without them, finish locally. Do not interrupt implementation to ask about remote publishing.
- Integration: only one person advances the shared integration branch at a time. Use the team's existing integrator if named; otherwise establish who will integrate when shared delivery is actually requested. This does not block local feature completion.
- Credentials: never commit secrets or private data. Never force-push, discard other people's edits, disable checks to pass, or silently change shared API/schema semantics.

A maintainer can replace these defaults or add team permissions here once for everyone. Ordinary users only describe what they want.
