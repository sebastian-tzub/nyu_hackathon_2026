---
name: professional-dashboard-ui-ux
description: Design and implement clean professional dashboards, analytics views and data-heavy admin interfaces when a feature requires them.
---

# Professional dashboard UI/UX

Apply when building or materially changing dashboards, analytics, monitoring, tables, filters or data-heavy admin screens. Adapt to the existing product; do not redesign unrelated pages. This is an implementation and review skill, not another mandatory agent.

## Define the information hierarchy

- Write the user's main decision, primary action and 3–5 essential metrics before laying out the screen. Use meaningful labels, units, reporting period and comparison basis. Avoid vanity cards that do not help the decision.
- Prefer a clear page heading/context and one primary action, a compact filter row, a small KPI group, a main chart or analysis panel, and actionable detail rows. Omit sections that add no value. Preserve the established shell/navigation.
- Sketch the layout in a short implementation note. Desktop can use a restrained grid; narrow screens must retain the main action and useful summary without squeezing every panel into tiny cards.

## Visual system

- Reuse existing components, icons and tokens. If none exist, establish a small consistent palette: neutral backgrounds/surfaces, high-contrast text, one brand accent, and semantic status colors. Use borders or subtle elevation deliberately; avoid decorative gradients and nested card clutter.
- Use a consistent spacing scale such as 4/8/12/16/24/32 px, restrained radii, aligned panel edges and a clear type hierarchy. Use tabular numerals for changing/comparable values. Keep secondary labels readable; do not hide important context in tiny gray text.
- Give related controls consistent heights and states. Distinguish primary, secondary and destructive actions; include visible hover/focus/disabled states. No decorative buttons that do nothing.

## Honest, useful data presentation

- Use lines for trends, bars for category comparisons and tables for exact values/actions. Avoid 3D charts and excessive series. Label axes, units and legends; expose values without relying only on hover or color. Bar lengths use a zero baseline; disclose any deliberately narrowed scale elsewhere.
- Every KPI, chart and detail table must agree on filters, time boundaries, units and source. Distinguish zero from unavailable data. Label currencies, percentage versus percentage-point changes, timezone and freshness when relevant. Never invent positive trends or hide fixture mode.
- Tables need clear column labels, aligned numeric columns, stable row identity, and honest sorting/filtering/pagination. Offer a useful empty state and filter reset. On narrow screens, prioritize columns or contain horizontal scroll inside the table; do not overflow the whole page.
- Filters need labels and visible selections; apply/reset behavior should be clear. Prevent stale responses from overwriting newer selections. Mutations need pending/success/error feedback and duplicate-submit protection.

## Required states and accessibility

- Provide loading (stable layout), genuinely empty data, no filter matches, request error with working recovery, populated state, and applicable disabled/permission states. Preserve user context after recoverable errors.
- Use semantic headings, native buttons/inputs, programmatic labels, visible keyboard focus and logical tab order. Manage focus for dialogs and return it when they close. Give icon-only controls accessible names.
- Target WCAG AA text contrast (4.5:1 normal, 3:1 large), sufficient control contrast, no color-only status, comfortably sized controls and reduced-motion support where animation exists. These are design targets, not a claim of certified conformance.

## Evidence before handoff

Inspect at approximately 1440px desktop and 390px narrow width, plus a layout breakpoint that changed. Test the main action, filter/reset, loading/empty/error recovery, long labels and realistic data counts. Check the browser console for feature errors. Confirm keyboard access to the primary flow. Capture representative screenshots and interaction results for the product critic. If an explicit state cannot be exercised, report the gap; never claim a screenshot proves behavior.

Done means coherent hierarchy, consistent alignment/spacing, readable truthful data, functional controls, responsive layout and no blocking usability findings. Keep cosmetic extras outside the critical six-hour path.
