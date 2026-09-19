# Verified Hiring: Strategy Brief

*Working draft, September 2026*

## 1. One-sentence thesis

AI made job applications free to produce, so an application no longer proves who someone is, whether they want the job, or whether they can do it. We build the layer that restores those three signals for employers, starting with ability.

## 2. Context: what broke

Hiring used to rely on the application itself as a filter. Writing a tailored resume and cover letter took effort, so applying was a weak signal of interest, and the document was a weak signal of competence. Generative AI removed the effort. The consequences:

- **Volume.** Greenhouse's 2025 hiring report found about 22% of job seekers use bots to auto-apply, and applications per recruiter rose roughly 412%.
- **Uniform polish.** In a 2026 Resume Genius survey of 1,000 US hiring managers, 79% said resumes are more polished and tailored than five years ago. Polish no longer separates anyone.
- **Live cheating.** A 2026 Greenhouse report found 91% of US hiring managers have encountered or suspected AI-generated answers in online interviews. One analysis of about 19,000 live interviews flagged 38.5% for AI-assisted cheating, and most flagged candidates still passed.
- **Identity fraud.** Gartner projects up to one in four candidate profiles could be fake by 2028.

Caveat: nearly all of these figures come from vendors selling a fix. The direction is reliable; the magnitudes should be treated with skepticism.

## 3. The baseline: what the hiring side does today

| Problem | Current response | Limit |
|---|---|---|
| Resumes carry no signal | Semantic parsing and fit scoring inside the ATS (for example, Oracle scores applicants 0 to 5 on education, experience, skills, profile match). Lever added a structured screening step at the point of application in 2026. | Scoring a self-reported document that was itself generated from the job description is circular. No mainstream ATS detects AI authorship, because detection is unreliable. |
| Bots and spam | Device and network risk signals. Greenhouse Real Talent checks phone, email, IP, and location through IPQualityScore (26 signals), plus employer-managed blocklists. | Detects fakeness, not quality. A real person who mass-applied passes cleanly. Tools only flag; they do not decide. |
| Identity and interview cheating | Selfie-based ID verification (Greenhouse with CLEAR), deepfake detection on video, and a retreat to in-person rounds. About 72% of recruiting leaders now use in-person interviews to combat fraud. | In-person works but discards the reach of online hiring and favors candidates with proximity and networks. |

## 4. The gaps

1. **Quality of the honest middle is unmeasured.** Fraud tools confirm a person is real. Nothing reliably tells an employer whether a real, AI-polished applicant is any good.
2. **Intent is unmeasured.** Application cost is zero, so applying signals nothing.
3. **Evidence is self-reported.** Scoring is anchored to claims, not verified work.
4. **The fallback (in-person, referrals) is regressive.** It works by shrinking the pool.
5. **Regulation constrains the obvious fixes.** NYC Local Law 144 requires bias audits of automated hiring tools, the EU AI Act treats hiring AI as high-risk, and Mobley v. Workday has made vendors cautious about automated rejection. Any product here must flag and inform, with humans deciding. (Not legal advice; needs counsel before launch.)

**We are targeting gaps 2 and 3, with gap 1 as the payoff.**

## 5. The model: three layers

Each layer proves exactly one thing. None substitutes for another.

### Layer 1: Identity ("the passport")
- **Proves:** one account corresponds to one real person.
- **How:** university SSO for students, since the school has already done identity proofing. Third-party ID verification for non-students later.
- **Why it matters:** it is the precondition for Layer 2. Scarcity is meaningless if people can create multiple accounts.
- **Status:** largely solved by others. Handshake already verifies students through career centers across roughly 1,600 institutions. We do not compete here; we depend on it or integrate with it.

### Layer 2: Intent (scarce signals)
- **Proves:** this person genuinely prioritizes this job.
- **How:** unlimited applications, but each verified person gets a small budget of priority signals (starting assumption: 5 per month). Recruiters can sort and filter by signal.
- **Why signals and not application caps:** entry-level offer rates are low, so candidates rationally need volume. A hard cap pushes them to other platforms. A signal budget keeps volume while creating a credible, costly marker.
- **Precedent:** the economics PhD job market and US medical residency applications both use capped preference signals, and in both a signal meaningfully raises interview odds.
- **Core insight:** AI makes effort free. It cannot make scarcity free. Any intent signal based on effort (cover letters, custom questions) is dead; signals based on scarcity survive.

### Layer 3: Ability (proctored work sample)
- **Proves:** this verified person can do the work, under known conditions.
- **How:** an in-person, proctored, role-specific work-sample session for finalists only, paid for by the employer.
- **Key design choices:**
  - **Verify late, not early.** Only the top 10 to 20 candidates sit the session. Asking everyone to travel to a test before any interest is shown drives away the best candidates (adverse selection).
  - **Proctor the conditions, not the absence of AI.** AI tools are allowed and logged. The employer sees how the person actually works with modern tools. The value of proctoring is that identity and conditions are known, not that the environment is artificially stripped.
  - **Role-specific work samples, not general aptitude tests.** Work samples are among the strongest predictors of job performance in the I/O psychology literature, and general aptitude tests carry disparate-impact risk under Griggs v. Duke Power and its successors.
  - **Rent, do not build, physical space.** University testing centers, Prometric or Pearson VUE seats.
  - **Monitoring lives here and only here.** Session logging belongs inside the proctored test, where the candidate has opted into test conditions.

## 6. What we are explicitly not doing

- **Not building a rival job platform.** Handshake has the distribution (about 20M users, 1M employers) and is already moving toward portfolio evidence through its OpenAI student build challenge and AI project showcase.
- **Not detecting AI-written text.** Unreliable, and it penalizes the wrong people.
- **Not monitoring keystrokes on applications.** It verifies who typed, which nobody cares about, is beaten by retyping, feels like surveillance, and invites privacy-law exposure.
- **Not banning AI in assessments.** The job includes AI; the test should too.
- **Not charging candidates.** When the test-taker pays the issuer, the issuer is incentivized to pass people. That is how certifications became fluff.
- **Not making automated reject decisions.** We supply evidence; humans decide.

## 7. Exactly what we are aiming at

**Phase 1 product (the only thing to build now):** a proctored, AI-allowed, logged work-sample service that employers buy for their finalists in one entry-level role family.

- **Customer:** employers doing campus recruiting at NYU for a single role family (starting assumption: entry-level data analyst).
- **Buyer:** the university recruiting lead or hiring manager.
- **Unit of sale:** per-candidate verified session, delivered with a structured report (task output, process log, rubric score).
- **Why this first:** needs no network effect, produces revenue from the first customer, and generates the outcome data everything else depends on.

**Phase 2:** make the result portable. A candidate who has a verified session result can share it with other employers, which amortizes the friction across applications.

**Phase 3:** add identity and scarce signals on top of the portable result, either by integrating with an existing platform or, only if the data justifies it, building the passport ourselves.

**The moat:** outcome data. If our score predicts 6 to 12 month job performance better than the employer's own interviews, that is simultaneously the sales pitch, the defensibility, and the legal validation evidence.

## 8. Precedents to learn from

- **Triplebyte** (assess once, skip to final rounds at many companies) did not survive. Lessons: the best candidates never sit the test because referrals get them jobs first; employers re-interviewed anyway, so friction was added, not removed; the two-sided cold start was severe.
- **CodeSignal and Karat** are the living descendants (reusable scores, outsourced interviews). Neither is in-person, and both are engineering-only.
- **CPA, bar, actuarial, CFA exams** show that credentials keep their signal when they are hard, proctored, and not pay-to-pass.

## 9. Biggest risks

1. **Employers will not skip their own rounds.** If our session is added on top of the existing process, we have increased friction. This is the risk that killed the closest precedent and must be tested first.
2. **Adverse selection.** Strong candidates with options decline the extra step. Mitigation: late-stage only, employer-paid, and portable results that save them time elsewhere.
3. **Test content decay.** Tasks leak and AI capability shifts. Requires a rotating task bank and ongoing re-validation.
4. **Legal exposure.** Employment tests need job-relatedness evidence, ADA accommodations, and bias monitoring. Budget for counsel and an I/O psychologist early.
5. **Platform risk.** Handshake or an ATS vendor could add proctored verification. Our defense is outcome data and the physical-delivery operation, which software incumbents are slow to build.
6. **Operational load.** In-person delivery is logistics-heavy for a solo founder. Keep Phase 1 to one campus and one role family.

## 10. Validation plan (before writing code)

1. Interview 15 to 20 campus recruiters. The single question that matters: "If a finalist arrived with a verified, proctored work-sample result, which of your current rounds would you drop?" If the answer is "none," rethink.
2. Interview 15 to 20 students on willingness to sit a 90-minute in-person session for a finalist slot, and whether a portable result changes that.
3. Run a manual pilot with 2 to 3 employers: design one work sample with their hiring manager, proctor it by hand in a campus room, deliver the report as a PDF. No software needed.
4. Track pilot hires for 6 months and compare our score against the employer's interview ratings and early performance reviews.

## 11. Open questions

- Which role family has the best mix of high volume, measurable output, and employer pain?
- What is an employer willing to pay per verified finalist, and how does that compare to the cost of a bad entry-level hire?
- Does NYU career services become a partner, a channel, or a gatekeeper?
- How large must the task bank be to keep leakage from eroding the signal?
- Is the portable result (Phase 2) something employers will trust if another employer's task generated it?
- Integrate with Handshake for identity, or stay independent of it?
