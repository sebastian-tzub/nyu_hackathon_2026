---
name: mvp-development
description: Implement a scoped hackathon feature or critique fixes with targeted verification and a clear handoff to independent reviewers.
---

# MVP development

Read the supplied brief, HACKATHON.md and REVIEW-CONTRACT. Verify your absolute worktree and branch before editing. You are the sole source-code writer during DEVELOP/FIX; the parent owns staging, Git history, run records and delivery.

1. Trace the smallest end-to-end path through existing code. Reuse the project's stack, components, data access and error conventions. Confirm API inputs/outputs, nullability, units and ownership before coding across shared boundaries.
2. Build one working vertical slice. Avoid new dependencies, global rewrites or abstractions unless needed for the acceptance criteria. Use a shared-file owner if the team has one; absence is not a blocker. Ask the parent before crossing agreed scope or resolving ambiguous competing intent.
3. For dashboard/data-heavy surfaces, read `.cursor/skills/professional-dashboard-ui-ux/SKILL.md` before layout or component work. For other UI, preserve design tokens and deliver working loading/empty/error/success states, keyboard access and responsive layouts.
4. Keep credentials on the server, validate untrusted inputs at the boundary, reuse authorization checks and protect destructive actions. Use isolated test data. Do not introduce auth bypasses for demo convenience.
5. Test observable acceptance and the important failure case. Prefer existing test tools; add focused regression coverage for actual risks. Discover and run relevant existing lint/type checks, tests and build under HACKATHON.md defaults; execute a short demo smoke. Distinguish pre-existing failures with evidence, and escalate required check failures rather than ignoring them.
6. For UI, run the local app and inspect desktop and narrow viewports. Capture screenshots of relevant states plus interaction evidence. If browser access is unavailable, report the exact missing verification and request parent capture; do not infer visual success from compilation.
7. Return changed paths, acceptance-to-evidence mapping, commands/exit codes, local URL/port, screenshots, contracts changed, known limitations and suggested commit title. Stop editing while the reviewers run.

On fixes, reproduce each blocking finding first, make the smallest correct change, add/rerun relevant regression checks and report finding ID → fix → evidence. Do not erase requirements or weaken tests. If reviewers disagree, provide concrete evidence to the parent; neither the developer nor parent can grant reviewer approval.
