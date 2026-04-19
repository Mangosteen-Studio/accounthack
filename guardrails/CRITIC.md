# AccountHack Internal Critic
### Quality Auditor for the Account Brief — v1.0

---

> **What this is:** An internal self-critique layer that runs *after* all research stages are complete, *before* the final Account Brief is rendered. The AI runs this as a hidden reasoning step — the AE never sees the raw audit, only the final output (or the specific gaps it surfaces).
>
> **Reference files:** `guardrails/VOICE.md` (output style), `guardrails/VERIFICATION.md` (sourcing standards), `guardrails/QUALITY_GATES.md` (stage checkpoints)

---

## AUDIT CRITERIA

Run all four checks in sequence. A single FAIL on any criterion blocks final output.

---

### Check 1 — Anti-Slop (Reference: VOICE.md)

Scan the full draft Account Brief for the following failure modes:

**Banned words and phrases** (any usage = instant flag):
- Use the numbered banned-phrase list in `VOICE.md` as the canonical list. When you flag one, cite the exact phrase and list number in `Required Fixes`.
- Also flag close-cousin filler outside the numbered list: *bespoke, tapestry, innovative, transformative*
- *"In today's fast-paced digital landscape..."*
- *"AI-breathless" openers* (e.g., "As AI continues to reshape...", "In an era of...")
- *Vague intensity* (e.g., "significant opportunity," "key stakeholders," "critical pain points" with no specifics)

**AI-breathless tone check:**
- Does any section read like it was written to impress rather than inform?
- Is there a single sentence that could appear in a vendor press release without modification? If yes, it fails.

**Action:** Flag each offending sentence for rewrite. Replace with specifics or delete.

---

### Check 2 — Verification Integrity (Reference: VERIFICATION.md)

Every factual claim in the Account Brief must carry a tier tag or be sourced.

**Failure conditions:**
- Any executive name, title, funding figure, headcount, or quote that appears without a source or appropriate verification handling
- A "Why Now" trigger that is generic (e.g., "They want to grow," "Industry trends suggest...") rather than specific (e.g., "Q3 earnings call, page 4: CEO cited 18% revenue miss in enterprise segment")
- Any inline `[UNVERIFIED — confirm before use]` claim appearing in Account Brief Sections 1-10 instead of in `Intelligence Gaps — Verify Before Outreach`
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

The Critic does not invent a second Earned Right Test. It audits whether Stage 5.5 applied the canonical definition correctly.

**Pass conditions:**
- The insight is specific to the selected executive
- The insight connects directly to the wedge
- The insight is non-obvious to a competitor rep who spent 15 minutes on Google

**Failure conditions:**
- The "one insight" in Section 7 could apply to any executive at any company
- The insight is interesting but not actually connected to the proposed wedge
- The insight looks obvious from a shallow search
- Executive drafts appear even though the Earned Right Test result is `NOT YET PASSED`
- The wrong executive route is unlocked, or multiple executive routes are treated as unlocked

---

### Check 4 — Actionability (The Monday Morning Test)

After reading this Account Brief, does the AE know exactly what to do tomorrow morning?

**Failure conditions:**
- The 30-Day Execution OS contains action items that require interpretation (e.g., "Research leadership" instead of "Search LinkedIn for [Name], filter by first-degree connections at [Company]")
- The Warm Path Priority List has entries without a specific next action attached
- The Intelligence Gaps section lists categories (e.g., "competitive intel") rather than specific gaps with named sources to check
- The `Triggers-Based Adjustments` block is missing, generic, or detached from the 30-Day Execution OS table
- The First Message Drafts are templates, not messages (i.e., they contain placeholders like `[personalize this]` or `[insert relevant hook]`)

**Action:** Any vague action item must be rewritten as a specific, copy-paste-ready task before output.

---

## AUDIT OUTPUT FORMAT

After running all four checks, output one of two results:

**PASS:**
```
QC_PASSED
Verification Score: [X]/10
Earned Right Test: PASSED
Anti-Slop: Clean
Actionability: Confirmed
→ Proceeding to final Account Brief output.
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

When QC_FAILED, enter the Refinement Loop. Do not output the final Account Brief until all Required Fixes are resolved.

### The Loop

**Step 1 — Acknowledge the failure.**
Identify exactly which check failed and which guardrail was hit.
Example: *"Failed Check 1 (Anti-Slop): 'strategic alignment' in Company Snapshot — Section 1. Failed Check 3 (Earned Right Test): insight in Section 7 is not specific to the selected executive."*

**Step 2 — Backtrack.**
Return to the specific research stage that produced the failing content:
- Anti-Slop failure → rewrite the specific sentence. No stage return needed.
- Verification failure → return to the stage where the unverified claim was generated (e.g., Stage 4 for financials, Stage 5 for executive background). Pull new data or downgrade the claim tier.
- Earned Right Test failure → return to Stage 5.5 and generate new research actions for the Earned Right Test. Do not write the executive narrative until the insight meets the threshold.
- Actionability failure → rewrite the specific vague action items to be task-specific.

**Step 3 — Draft 2.0.**
Generate the corrected section only — do not re-render the full Account Brief yet.

**Step 4 — Re-submit to Critic.**
Run all four audit checks again on the corrected section. If it passes: merge the fix into the Account Brief and proceed to output. If it fails again: proceed to Step 5.

### Loop Constraint

**Maximum 2 attempts.** If the draft fails the Critic check a third time:
- Output the Account Brief as-is
- Tag it `[STATUS: DONE_WITH_CONCERNS]` in the Run Completion block
- List the specific intelligence gaps that prevented a full PASS under a `CRITIC CONCERNS` heading in the Run Status

```
CRITIC CONCERNS (unresolved after 2 refinement attempts):
• [Specific gap or failure — not a category, a named issue]
• [Specific gap]
• [...]
```

This ensures the AE still gets a usable Account Brief with honest flags rather than a blocked run.

---

## WHEN TO RUN THIS CRITIC

The Critic runs once: after all research stages are complete and before the final Account Brief is rendered.

It does **not** run after each stage — that is QUALITY_GATES.md's role. The Critic is the final output auditor, not a stage checkpoint.

**Trigger:** The AI should run this internally whenever it is about to render the Account Brief section. The AE does not invoke it manually.
