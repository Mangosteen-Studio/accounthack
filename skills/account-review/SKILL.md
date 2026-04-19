---
name: account-review
description: |
  Score and audit an existing Account Brief. Finds gaps, unverified claims, missing
  warm paths, weak messaging, and the overall quality of the intelligence. Use after
  a full AccountHack run to validate quality, or as a manager reviewing an AE's account plan.
---

# Account Review — Account Brief Quality Audit

Use this skill to audit an existing Account Brief. This is the quality gate that catches sloppy research, generic messaging, unexhausted warm paths, and intelligence gaps before the AE goes into the field.

**Who uses this:**
- AEs reviewing their own work before outreach
- Managers reviewing account plans from their team
- Anyone who has an Account Brief and wants to know: "Is this good enough?"

## Required Context
The AE or manager pastes a completed (or partial) Account Brief into the chat.

## Guardrails
This skill IS the guardrail. It enforces the full guardrail stack:
- [QUALITY_GATES.md](../../guardrails/QUALITY_GATES.md) — run every checkpoint
- [VOICE.md](../../guardrails/VOICE.md) — check for slop
- [VERIFICATION.md](../../guardrails/VERIFICATION.md) — count and flag unverified claims
- [CRITIC.md](../../guardrails/CRITIC.md) — align the final audit with the canonical output rules

## Workflow

### Step 1 — Open
Say exactly:

*"Paste the Account Brief you want me to audit. I’m going to pressure-test it before it goes into the field — verification, specificity, warm-path coverage, executive logic, and execution quality. Be ready for honest feedback — a 6/10 Account Brief beats a confident 3/10 in the field."*

### Step 2 — Parse & Analyze
When the Account Brief is pasted, run the following analysis silently (don't ask questions — just audit):

**A. Verification Audit**
- Count every factual claim
- Categorize each as: Verified (sourced), Inferred (basis stated), or Unverified (no source)
- Flag the top 5 highest-risk unverified claims (exec names, funding, financials, tech stack)

**B. Specificity Audit**
- Run the Competitor Test on every section: "Would a competitor rep who spent 15 minutes on Google know this?"
- Flag every generic claim, phrase, or recommendation
- Check for banned AI vocabulary from VOICE.md

**C. Warm Path Audit**
- Check: were all tiers of Warm Path Activation explored (direct, change agents, customer network, investor/board/advisor, event overlap, pre-warm)?
- Flag any unexplored warm path categories
- Determine: is "cold outreach" the recommendation ONLY because warm paths were exhausted, or because they were never tried?

**D. Executive Narrative Audit**
- Was the Earned Right Test applied? What was the result?
- Does the executive insight meet the canonical test: specific to the selected executive, connected to the wedge, non-obvious to a competitor rep who spent 15 minutes on Google?
- Is the executive narrative specific to this person, or generic to the role?
- Are the message drafts consistent with the Earned Right Test result?
- Could these messages have been written without the Account Brief research? If yes, they're too generic.

**E. Intelligence Gaps Audit**
- Are the listed gaps specific and actionable, or vague categories?
- Are unverified claims kept out of the main Account Brief body and moved into `Intelligence Gaps — Verify Before Outreach`?
- Are there obvious gaps NOT listed? (e.g., no competitive intel, no financial data, no hiring analysis)
- Is the 30-Day Execution OS populated with specific actions or generic tasks?
- Is the `Triggers-Based Adjustments` block present and specific?

### Step 3 — Output

```
═══════════════════════════════════════
ACCOUNT REVIEW — [Company Name]
Reviewed: [Date]
═══════════════════════════════════════

OVERALL SCORE: [X]/10

VERIFICATION SCORE: [X]/10
├── Verified claims: [count]
├── Inferred claims: [count]
├── Unverified claims: [count]
└── Highest-risk unverified:
    1. [claim] — [why this is risky to use without verification]
    2. [claim] — [why]
    3. [claim] — [why]

SPECIFICITY SCORE: [X]/10
├── Generic claims flagged: [count]
├── AI slop detected: [YES/NO — list offending phrases]
└── Competitor Test failures:
    1. [section] — [what's generic + specific suggestion to fix]
    2. [section] — [what's generic + fix]

WARM PATH SCORE: [X]/10
├── Paths explored: [list]
├── Paths NOT explored: [list — these are gaps]
├── Warm paths exhausted: [YES/NO]
└── Cold outreach justified: [YES/NO + reason]

EXECUTIVE NARRATIVE SCORE: [X]/10
├── Earned Right Test: [PASSED / NOT PASSED / NOT APPLIED ⚠️]
├── Narrative specificity: [Specific to this exec / Generic to role]
├── Draft consistency: [Consistent with ERT result / INCONSISTENT ⚠️]
└── "Written without research?" test: [PASS / FAIL per draft]

INTELLIGENCE GAPS SCORE: [X]/10
├── Listed gaps are actionable: [YES/NO]
├── Footer-only unverified rendering: [PASS/FAIL]
├── Missing gap categories: [list]
└── Execution plan quality: [Specific actions + trigger adjustments / Generic tasks]

═══════════════════════════════════════
TOP 5 ACTIONS TO IMPROVE THIS ACCOUNT BRIEF
═══════════════════════════════════════
1. [Most impactful action — specific]
2. [Second action]
3. [Third action]
4. [Fourth action]
5. [Fifth action]

FIELD READINESS: 
[READY — this Account Brief is good enough to act on]
[ALMOST — fix the top 2-3 issues first]
[NOT READY — significant gaps need to be addressed]
═══════════════════════════════════════
```

### Step 4 — Discussion
After delivering the audit, offer:

*"Want me to help fix any of these issues? I can re-run specific stages, deepen the executive research, or expand the warm path search."*

### Step 5 — Completion
```
STATUS: DONE
FIELD READINESS: READY | ALMOST | NOT READY
TOP PRIORITY FIX: [one sentence]
```
