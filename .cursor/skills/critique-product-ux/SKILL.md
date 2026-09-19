---
name: critique-product-ux
description: Independently review a frozen MVP candidate for acceptance, demo readiness and usable professional UI, including non-UI product behavior.
---

# Product and UX critique

Read `.cursor/skills/hackathon-feature/references/review-contract.md`. Stay read-only and verify candidate identity. Begin from the user's promised outcome, not the developer's account. Review actual code and product evidence.

1. Walk every acceptance criterion through the complete user journey. Can a new user find the entry point, understand the data, perform the action and recognize success or recovery? Check that demo steps are reproducible and controls really work.
2. For dashboards/data-heavy UI, read `.cursor/skills/professional-dashboard-ui-ux/SKILL.md` and assess its relevant gates. For all UI, inspect desktop/narrow screenshots and actual interaction evidence; use the running local app when available. Check loading, empty, error and success states, focus/keyboard use, names/labels, readability, overflow and misleading data.
3. Check primary-action hierarchy, alignment, spacing, typography, consistent controls and information density against the existing design system. Block on concrete usability or promised quality failures, not personal color preferences or unsolicited redesigns.
4. For backend/CLI-only features, mark visual review not applicable and inspect consumer ergonomics: understandable responses/errors, defaults, contract examples and whether the intended demo/consumer flow works. This reviewer is still required.
5. Check that fixtures are agreed and labeled, numbers have units/time ranges, errors are actionable and dead buttons/placeholder promises are absent.

Return REVIEW-CONTRACT's exact schema with specific route/viewport/reproduction evidence for UI findings. Missing required rendered/interaction evidence means BLOCKED, not guessed approval. Use nonblocking recommendations for polish beyond scope. Do not read the correctness critic's verdict before producing yours; re-review every revised candidate.
