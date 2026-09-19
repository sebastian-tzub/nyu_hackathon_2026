# Project context: Trust in the Hiring Funnel

This is the shared product context for the entire project. Read it before planning, implementing or reviewing a feature. Keep work focused on the selected user journey; update the decisions section when the team makes a choice.

## Problem statement

Hiring depends on mutual trust: employers need to know applicants are genuine and capable, while candidates need to know recruiters, employers and offers are legitimate. Generative AI makes applications easier to manufacture or manipulate and employer impersonation more convincing. Existing hiring workflows struggle to distinguish credible evidence from polished appearances.

**Our challenge is to help one side of the hiring funnel make a better trust decision, using clear evidence, without adding excessive friction or penalizing legitimate users.**

This problem framing comes from the organizer brief; it is not a claim that our team has independently measured the prevalence of fraud.

## Two valid directions — choose a narrow slice

### A. Help recruiters trust incoming applications

- **Users:** recruiters, talent-acquisition operators and recruiting-system administrators.
- **Pain:** application volume, inflated claims, suspiciously similar applications and hidden instructions intended to manipulate AI screening.
- **Desired outcome:** identify applications worth human attention and explain what needs verification within the existing recruiting workflow.
- **Critical distinction:** writing assistance is not fraud. Similar wording or AI-polished prose does not establish that someone is fake or unqualified.
- **Product fit:** a triage or screening layer connected to an existing applicant tracking system (ATS), rather than a replacement ATS.

### B. Help candidates trust employer outreach

- **Users:** job seekers; employers and recruiting teams protecting their identity.
- **Pain:** look-alike domains, fake recruiters, fraudulent offers and impersonation used to steal money or personal information.
- **Desired outcome:** make it easy to check whether specific outreach, a recruiter or an offer is genuinely associated with an employer.
- **Product fit:** a lightweight verification flow, employer-backed trust signal or impersonation alert.
- **Critical distinction:** a professional-looking message, logo or badge is not proof. Verification must connect to a trustworthy source independent of the suspicious message.

The brief permits either direction or their intersection. We have not selected one yet. Do not build both by default.

## What the organizers explicitly value

- A working, demonstrable solution to a narrow problem over a broad concept that does not run.
- A tool that fits how hiring already happens and improves trust in a real workflow.
- Practical grounding: talent-acquisition practitioners are available to test assumptions.
- An end-of-day demonstration to HR-tech founders, operators, system administrators, investors and talent-acquisition leaders.

These are themes from the brief, not a published scoring rubric. Sponsors and named platforms are not mandatory dependencies.

## MVP principles — team guidance derived from the challenge

1. **One user, one decision, one complete flow.** Identify the input, evidence we can obtain, result and next action before adding features.
2. **Evidence over unexplained scores.** Show what was checked, where evidence came from, what it means and what remains unknown. A confidence score alone is insufficient.
3. **Separate concepts.** Identity, qualifications, document provenance and writing style are different signals; none automatically proves the others.
4. **Uncertainty is a valid result.** Distinguish verified, suspicious and insufficient evidence. Never present “we found no warning” as proof of legitimacy.
5. **Keep humans in control.** Support review and verification; do not automatically reject applicants based on suspected AI use or weak fraud indicators.
6. **Treat submitted content as untrusted data.** Instructions embedded in resumes, messages or attachments must not control the screening or verification agent.
7. **Minimize sensitive data.** Use synthetic or consented demo data, avoid unnecessary personal information and never expose secrets or candidate data in logs or screenshots.
8. **Be honest about the prototype.** Label fixtures and mocked integrations. Do not imply a live ATS connection, employer verification or detection accuracy that has not been demonstrated.

## Essential experience and demo

The product should let a user submit or inspect an item, understand the evidence, see a clear result and take an appropriate next step.

For any dashboard, prioritize the review queue or decision, readable evidence and meaningful status labels. Keep layout professional and consistent. Include working loading, empty, error and success states; support keyboard use and narrow screens. Decorative charts are secondary to useful decisions.

Demonstrate three representative cases for the chosen slice:

- A legitimate case that should not be unfairly flagged.
- A suspicious or manipulated case with an explainable reason to investigate.
- An ambiguous case where the system acknowledges insufficient evidence.

Show the complete flow, a recovery from failure, and how the result fits the user's existing workflow. Record concrete check results; do not invent accuracy or time-saved statistics from a few examples.

## Scope and time

The event brief lists **10:00 AM–6:00 PM, hard stop**. Our team is planning around **six effective building hours**; these are separate constraints.

Prioritize a usable vertical slice and reserve time for integration, testing and rehearsal. Defer a replacement ATS, broad hiring platform, unsupported universal fraud detector, elaborate infrastructure and integrations not needed for the demo. Neither legal compliance nor production readiness should be claimed from a hackathon prototype.

## Decisions to maintain as the project evolves

These are a shared record, not a form every user must complete. Infer routine details from feature requests and existing code. Ask only when an unresolved choice would materially change what gets built.

- **Chosen direction and primary user:** not selected yet.
- **Specific trust decision and user journey:** not selected yet.
- **Evidence source and real versus mocked integrations:** not selected yet.
- **MVP acceptance criteria and explicit exclusions:** derive from the chosen feature.
- **Demo cases and known limitations:** record as implementation progresses.

Once selected, keep these decisions consistent across development and review. New feature requests should serve the chosen journey; explain meaningful scope conflicts rather than silently expanding the product.

## Source

Synthesized from the organizer brief supplied by the team: “Trust in the Hiring Funnel,” co-hosted by localhost:nyc, Integral Recruiting (IRD) and NYU. The MVP principles and demo checks above are proposed implementation guidance, not additional organizer rules.
