# AccountHack Internal Critic
### Quality Auditor for the Account War Room — v1.0

---

> **What this is:** An internal self-critique layer that runs *after* all research stages are complete, *before* the final Account War Room is rendered. The AI runs this as a hidden reasoning step — the AE never sees the raw audit, only the final output (or the specific gaps it surfaces).
>
> **Reference files:** `guardrails/VOICE.md` (output style), `guardrails/VERIFICATION.md` (sourcing standards), `guardrails/QUALITY_GATES.md` (stage checkpoints)

---

## AUDIT CRITERIA

Run all four checks in sequence. A single FAIL on any criterion blocks final output.

---

### Check 1 — Anti-Slop (Reference: VOICE.md)

Scan the full draft War Room for the following failure modes:

**Banned words and phrases** (any usage = instant flag):
- *leverage, utilize, comprehensive, robust, strategic alignment, holistic, synergy, cutting-edge, best-in-class, seamless integration, drive value, empower, delve, bespoke, tapestry, innovative, transformative*
- *"In today's fast-paced digital landscape..."*
- *"AI-breathless" openers* (e.g., "As AI continues to reshape...", "In an era of...")
- *Vague intensity* (e.g., "significant opportunity," "key stakeholders," "critical pain points" with no specifics)

**AI-breathless tone check:**
- Does any section read like it was written to impress rather than inform?
- Is there a single sentence that could appear in a vendor press release without modification? If yes, it fails.

**Action:** Flag each offending sentence for rewrite. Replace with specifics or delete.

---

### Check 2 — Verification Integrity (Reference: VERIFICATION.md)

Every factual claim in the War Room must carry a tier tag or be sourced.

**Failure conditions:**
- Any executive name, title, funding figure, headcount, or quote that appears without a source or `[UNVERIFIED]` tag
- A "Why Now" trigger that is generic (e.g., "They want to grow," "Industry trends suggest...") rather than specific (e.g., "Q3 earnings call, page 4: CEO cited 18% revenue miss in enterprise segment")
- A Verification Score below 8.0 with no `DONE_WITH_CONCERNS` tag in the Run Status block

**Calculate the Verification Score:**
`[Verified claims + (Inferred claims × 0.5)] / Total claims × 10`

| Score | Action |
|---|---|
| 8.0 – 10.0 | Proceed to output |
| 6.0 – 7.9 | Proceed but tag `DONE_WITH_CONCERNS` — list top 3 unverified claims in Run Status |
| Below 6.0 | Block output — return to the specific stage with the weakest sourcing |

---

### Check 3 — Earned Right Test (Reference: Stage 5.5)

The Earned Right Test determines whether the War Room earns executive outreach.

**Score the draft on a 1–10 scale using this rubric:**

| Score | What it means |
|---|---|
| 9–10 | A CXO would respond. The insight is specific, verified, and connects to their current strategic moment. |
| 8 | Strong — one non-generic insight confirmed, executive narrative is role-appropriate. Proceed to output. |
| 6–7 | Research shows effort but insight is slightly generic. One more depth-pass needed. |
| Below 6 | Fails. The draft reads like 15 minutes of Google, not 5 hours of research. Block executive outreach. |

**Minimum threshold: 8. Anything below requires a rewrite of the Executive Narrative section.**

**Specific failure signals:**
- The "one insight" in Section 7 could apply to any CEO at any company → fail
- The message draft opens with a greeting or a product feature → fail
- No specific earnings call page, keynote timestamp, LinkedIn post, or job posting is cited as the source of the insight → fail

---

### Check 4 — Actionability (The Monday Morning Test)

After reading this War Room, does the AE know exactly what to do tomorrow morning?

**Failure conditions:**
- The 30-Day Execution OS contains action items that require interpretation (e.g., "Research leadership" instead of "Search LinkedIn for [Name], filter by first-degree connections at [Company]")
- The Warm Path Priority List has entries without a specific next action attached
- The Intelligence Gaps section lists categories (e.g., "competitive intel") rather than specific gaps with named sources to check
- The First Message Drafts are templates, not messages (i.e., they contain placeholders like `[personalize this]` or `[insert relevant hook]`)

**Action:** Any vague action item must be rewritten as a specific, copy-paste-ready task before output.

---

## AUDIT OUTPUT FORMAT

After running all four checks, output one of two results:

**PASS:**
```
QC_PASSED
Verification Score: [X]/10
Earned Right Test Score: [X]/10
Anti-Slop: Clean
Actionability: Confirmed
→ Proceeding to final War Room output.
```

**FAIL:**
```
QC_FAILED
Failed checks: [list which of the 4 checks failed]
Required Fixes:
• [Specific sentence or section that failed — include the exact text that needs to change]
• [Specific sentence or section]
• [...]
→ Entering Refinement Loop (Attempt [1 or 2] of 2).
```

---

## REFINEMENT LOOP PROTOCOL

When QC_FAILED, enter the Refinement Loop. Do not output the final War Room until all Required Fixes are resolved.

### The Loop

**Step 1 — Acknowledge the failure.**
Identify exactly which check failed and which guardrail was hit.
Example: *"Failed Check 1 (Anti-Slop): 'strategic alignment' in Company Snapshot — Section 1. Failed Check 3 (Earned Right Test score: 6/10): insight in Section 7 is not specific to this exec."*

**Step 2 — Backtrack.**
Return to the specific research stage that produced the failing content:
- Anti-Slop failure → rewrite the specific sentence. No stage return needed.
- Verification failure → return to the stage where the unverified claim was generated (e.g., Stage 4 for financials, Stage 5 for executive background). Pull new data or downgrade the claim tier.
- Earned Right Test failure → return to Stage 5.5 and generate new research actions for the Earned Right Test. Do not write the executive narrative until the insight meets the threshold.
- Actionability failure → rewrite the specific vague action items to be task-specific.

**Step 3 — Draft 2.0.**
Generate the corrected section only — do not re-render the full War Room yet.

**Step 4 — Re-submit to Critic.**
Run all four audit checks again on the corrected section. If it passes: merge the fix into the War Room and proceed to output. If it fails again: proceed to Step 5.

### Loop Constraint

**Maximum 2 attempts.** If the draft fails the Critic check a third time:
- Output the War Room as-is
- Tag it `[STATUS: DONE_WITH_CONCERNS]` in the Run Completion block
- List the specific intelligence gaps that prevented a full PASS under a `CRITIC CONCERNS` heading in the Run Status

```
CRITIC CONCERNS (unresolved after 2 refinement attempts):
• [Specific gap or failure — not a category, a named issue]
• [Specific gap]
• [...]
```

This ensures the AE still gets a usable War Room with honest flags rather than a blocked run.

---

## WHEN TO RUN THIS CRITIC

The Critic runs once: after all research stages are complete and before the final War Room is rendered.

It does **not** run after each stage — that is QUALITY_GATES.md's role. The Critic is the final output auditor, not a stage checkpoint.

**Trigger:** The AI should run this internally whenever it is about to render the Account War Room section. The AE does not invoke it manually.
