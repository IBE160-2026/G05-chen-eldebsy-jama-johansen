---
title: "Product Brief: AI CV & Job Application Assistant"
status: draft
created: 2026-09-26
updated: 2026-09-26
---

# Product Brief: AI CV & Job Application Assistant

**Course:** IBE160 Programmering med KI — Høgskolen i Molde, Fall 2026
**Group:** G05 — David Chen, Hatem M Eldebsy, Mahad H Jama, Emelie Klingstrøm Johansen

## Executive Summary

Job applications are a high-stakes, low-feedback loop: a student rewrites the same CV and cover letter for every posting, gets no signal on whether it actually matches what the employer is looking for, and finds out only via silence or rejection. The AI CV & Job Application Assistant closes that loop. A student logs in, uploads their CV and a target job posting; the tool produces a tailored cover letter, concrete CV improvement suggestions, a gap analysis against the posting's stated qualifications, and ATS-readiness feedback — turning one CV into a fitted application in minutes instead of hours, while making visible exactly how AI-driven recruitment screening actually evaluates a candidate.

Beyond the immediate utility, the assignment brief frames this explicitly as a teaching artifact: it should give students "a realistic experience of how AI is used in recruitment." That framing is a first-class design goal here, not a side effect — the tool should show its reasoning (why a qualification is flagged as missing, why a phrase is more ATS-relevant than another), not just hand over a black-box rewrite.

## The Problem

Students applying for internships and jobs face the same friction repeatedly:

- **Every application should be tailored, but tailoring is slow.** Matching a CV and cover letter to a specific posting's language and requirements takes real effort, so most students reuse a generic version instead — which reads as generic to the employer too.
- **There's no feedback loop.** A student rarely learns *why* they weren't shortlisted. They can't see the gap between what they claim and what the posting asks for, or whether their document even survives automated screening.
- **ATS screening is opaque.** Most employers now filter applications through an Applicant Tracking System before a human ever reads them, but students have no visibility into how that filtering works or whether their formatting/phrasing is working against them.
- **The stakes are personal.** A CV carries real personal data (identity, address, full work history, sometimes photo/national ID) — students hand this to any tool they use, often without knowing how it's stored.

## The Solution

A tool that takes a student's existing materials and a specific job posting, and produces a tailored application package plus the reasoning behind it — behind a login, with every uploaded document encrypted at rest (explicitly required by the assignment given the personal data involved; see `addendum.md` for the GDPR-aligned handling this implies).

**Inputs:**
- CV (PDF / DOC / TXT)
- Job posting (text/link)
- Keywords the student wants emphasized
- Desired tone/style
- Previous applications (optional, for consistency/learning across a student's own history)

**Outputs:**
- Tailored cover letter matched to the posting
- CV improvement suggestions
- Gap analysis: qualifications the posting asks for that the CV doesn't currently evidence
- ATS-readiness feedback

**On the ATS feedback specifically:** modern ATS platforms increasingly match on semantic relevance, not raw keywords, and penalize keyword-stuffing (see `addendum.md` for sourced detail). `[ASSUMPTION]` This tool's ATS feedback should be framed as *evidence-based phrasing against the posting's actual requirements*, not keyword injection — confirm as a team since it shapes how the gap-analysis and ATS modules get built.

## What Makes This Different

Gap analysis and tone-matched cover-letter generation are not what the existing market has commoditized — ATS keyword-scoring is now table-stakes (JobScan, Rezi, Teal, Kickresume, and others all do it). Where this project can differentiate, within a course-project scope:

- **"What to do about the gap," not just "here's the gap."** Existing tools flag missing qualifications; few pair that with a concrete next step (a skill to name, a project/experience to surface from what the student already has). `[ASSUMPTION]` — worth deciding as a team whether this is in scope for the graded version or a stated stretch goal.
- **Transparency as a feature, not a limitation.** Because the assignment's real goal includes teaching how AI recruitment screening works, showing the *reasoning* behind each suggestion (not just the rewritten text) is both pedagogically the point and a genuine differentiator versus commercial tools that hide their scoring logic.
- **Built for the student's own document history.** Accepting previous applications as an optional input lets the tool learn a student's own voice/track record rather than generating generic AI-sounding text — most commercial tools don't do this.

## Who This Serves

**Primary user:** students preparing job or internship applications who have a CV but are applying to a specific posting and want it tailored — not written from zero. `[ASSUMPTION]` Framed here as the general student population (any field), not this course's students specifically; narrow this if the course intends a specific target group (e.g., only IBE160/HiMolde students, or a specific study program) as the pilot audience.

**What success looks like for them:** they understand *why* their materials do or don't match a posting, they get a usable tailored draft they still recognize as their own writing, and they leave with a clearer sense of what a real ATS is actually doing with their application.

## Success Criteria

`[ASSUMPTION]` — this brief doesn't have the course rubric, so these are proposed and should be checked against it directly:

- The tool successfully ingests a real CV (PDF/DOC/TXT) and a real job posting and produces all four outputs (cover letter, CV suggestions, gap analysis, ATS feedback) without manual intervention.
- Login and encrypted storage of uploaded documents are implemented and demonstrable.
- A test user (e.g., a group member using their own CV) can point to at least one suggestion or gap-analysis result that they'd genuinely act on — the output isn't just plausible-sounding filler.
- The reasoning behind at least gap-analysis and ATS feedback is visible to the user, not just a final score.

## Scope

**In (for the graded deliverable):** CV upload and parsing (PDF/DOC/TXT), job posting input, tailored cover letter generation, CV improvement suggestions, qualification gap analysis, ATS-readiness feedback, login, encrypted document storage.

**Explicitly out:** any payment/e-commerce flow (per assignment); `[ASSUMPTION]` actual submission of applications on the student's behalf (this tool prepares materials, it doesn't apply for them); `[ASSUMPTION]` multi-tenant/recruiter-facing features (this is a student-facing tool only, not a recruiter dashboard).

The assignment also leaves three decisions open; rather than resolving them silently, here's each with a recommended default (full reasoning in `addendum.md`) so the team can move fast and revisit only if someone disagrees:

- **Rewrite vs. suggestion** — default to Suggestion Mode (lower risk of output feeling inauthentic), with a full-rewrite option on request.
- **Output file format** — default to PDF for the cover letter, Markdown/plain text for suggestions and gap analysis.
- **Language/style level** — default to student-selectable tone, Norwegian and English supported at minimum.

The group chose to keep the assignment's full feature scope intact rather than cut anything now; if time runs short before the deadline, these three defaults are where scope actually gets tightened in practice.

## Vision

If this tool works as intended for the course, the natural next step is for it to become something students actually reach for before every real application, not just a one-time graded demo — the two features that would carry that (pairing each gap with a concrete next step, and learning a student's own voice from their application history) are exactly the pieces the current commercial landscape (JobScan, Rezi, Teal, Kickresume) doesn't do well, so that's where a longer-term version earns its differentiation rather than competing on ATS scoring, which is already commoditized.

Within Høgskolen i Molde specifically, a tool that's honest about what AI screening actually does — rather than promising a magic keyword trick — is also a small, concrete rebuttal to the cynicism students often have about "AI in recruitment": it could plausibly outlive this course as something the school's career services point students to, if the group wanted to take it that far.
