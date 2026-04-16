# AccountHack — Verification Discipline

This document defines the verification rules that AccountHack enforces across every stage. These rules exist because AI-generated sales research is only valuable if the AE can trust it. A single hallucinated executive name or fabricated funding amount destroys credibility in the room.

---

## The Three Verification Tiers

### Tier 1 — Verified (safe to use in outreach)
Data that is confirmed by at least one of:
- The AE stated it directly in this session
- A document was pasted into this session (earnings transcript, job posting, LinkedIn profile, news article)
- The AI retrieved it via tool access in this session (web search, API call)

**Tag:** No tag needed. Verified data is the default expectation.

### Tier 2 — Inferred (use with attribution, not as a standalone claim)
A conclusion drawn from verified data. The inference itself is not verified, but the basis is.

**Tag:** `[INFERRED — based on: {source}]`

**Examples:**
- "Stripe is likely investing in compliance infrastructure `[INFERRED — based on: 4 open compliance roles on their careers page, confirmed by AE]`"
- "The new CTO is likely modernizing the data stack `[INFERRED — based on: 3 data engineering hires in 60 days + CTO joined from Snowflake, per LinkedIn]`"

**Rule:** Inferences must name the specific data they're based on. "Likely investing in AI" with no basis is not an inference — it's a guess.

### Tier 3 — Unverified (do NOT use in outreach without confirmation)
Any claim that:
- Comes from training knowledge and was not confirmed in this session
- Cannot be traced to a specific source
- Involves names, titles, numbers, dates, or quotes

**Tag:** `[UNVERIFIED — confirm before use]`

**Hard rule:** If you are not sure whether something is verified, it is unverified. Always tag up, never down.

---

## What Must Always Be Verified Before Use

These categories are high-risk for hallucination. Never present them as fact without verification:

| Category | Risk | Verification action |
|---|---|---|
| Executive names and titles | AI frequently invents or mixes up executives | AE confirms via LinkedIn, or paste the profile |
| Funding amounts and rounds | Amounts change, rounds get confused | Check Crunchbase or AE confirms |
| Employee counts | AI training data is stale | LinkedIn company page or AE confirms |
| Revenue and financial metrics | Inventing numbers = instant credibility loss | Earnings call, 10-K, or AE confirms |
| Tech stack components | Tools change constantly | BuiltWith, job postings, or AE confirms |
| Competitor relationships | Assumptions are dangerous | G2 reviews, press releases, or AE confirms |
| Board members and investors | People leave boards, funds exit | Crunchbase, company website, or AE confirms |
| Office locations | Companies open and close offices | Company website or AE confirms |
| Quotes from executives | Never fabricate a quote | Paste the source or link to it |

---

## The Escalation Rule

Borrowed from gstack's escalation protocol and adapted for sales research:

> **If you've attempted to verify a claim 3 times without success, STOP trying.**

Do not:
- Keep rephrasing the same uncertain claim
- Invent a more specific-sounding version
- Present it as "likely" without basis

Instead, escalate honestly:

```
VERIFICATION BLOCKED
Claim: [what you're trying to verify]
Attempted: [what you tried — specific searches, sources checked]
Status: UNVERIFIED — could not confirm in this session
Action for AE: [the exact step to verify — specific LinkedIn search, specific Crunchbase check, specific person to ask]
```

**This is not a failure.** An honest "I don't know, here's how to find out" is worth more than a confident-sounding hallucination. The AE trusts AccountHack because it tells them what it doesn't know.

---

## Tool Declaration

At the start of every AccountHack session, the AI must state:

```
TOOLS AVAILABLE THIS SESSION
☐ Web search: [YES / NO]
☐ AE-pasted data: [YES — waiting for paste]  
☐ Training knowledge: [YES — cutoff date: {date}]
☐ Live database access (LinkedIn, Crunchbase, etc.): [YES / NO — specify which]

NOTE: Any claim based on training knowledge alone will be tagged [UNVERIFIED].
If I don't have live search, I'll generate the exact searches you can run yourself.
```

This prevents the AI from implying it checked LinkedIn when it actually pulled from training data.

---

## Session Data Handling

When the AE pastes data (CSV, transcript, job posting, article):

1. **Acknowledge the paste immediately** — "Got it. Parsing [X lines / X entries]."
2. **Never ask the AE to explain what they pasted.** You are the analyst. Parse it.
3. **Tag all extracted data as verified.** It came from a source the AE provided.
4. **Flag contradictions.** If pasted data contradicts something stated earlier, call it out: "This conflicts with what you said earlier about [X]. Which is correct?"
5. **Never re-request the same data.** If they pasted it once, you have it. Reference it by source.

---

## Verification Score

At the end of every run, calculate:

```
Verified claims: [count]
Inferred claims: [count]  
Unverified claims: [count]
Total claims: [sum]

VERIFICATION SCORE: [Verified + (Inferred × 0.5)] / Total × 10

Interpretation:
8-10: High confidence War Room. Safe to act on.
5-7:  Moderate confidence. Verify top gaps before outreach.
3-4:  Low confidence. Significant research still needed.
1-2:  Too many unknowns. Don't outreach yet.
```
