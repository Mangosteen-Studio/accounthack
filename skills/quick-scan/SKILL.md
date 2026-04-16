---
name: quick-scan
description: |
  Lightweight 5-minute account snapshot. Company overview, top 3 triggers, top 3 personas,
  and a go/no-go recommendation. Use when the AE wants a fast read on an account before
  deciding whether to invest time in a full AccountHack run. No War Room, no message drafts.
---

# Quick Scan — 5-Minute Account Snapshot

Use this skill when the AE wants a fast read on a target account. This is not a full AccountHack. It's a triage tool: snapshot the company, identify the top signals, name the top personas, and give a go/no-go recommendation in under 5 minutes.

## Required Context
- Company name
- What you're selling (one sentence)

That's it. This skill is designed to run with minimal input.

## Guardrails
Read and enforce:
- [VOICE.md](../../guardrails/VOICE.md) — anti-slop rules
- [VERIFICATION.md](../../guardrails/VERIFICATION.md) — mark everything UNVERIFIED unless sourced

## Workflow

### Step 1 — Open
Say exactly:

*"Quick scan mode. Give me the company name and what you're selling. I'll give you a snapshot, the top urgency signals, and the 3 people you'd want to reach — in about 5 minutes."*

### Step 2 — Research (fast)
Run as much as tools allow. Prioritize speed over depth:

1. **Company snapshot:** What they do, how big they are, public or private, current strategic moment
2. **Top 3 triggers:** Most compelling urgency signals from the last 90 days. Tag HIGH/MEDIUM/LOW.
3. **Top 3 personas:** Who the AE should target, with roles and a one-line reason for each
4. **Competitive landscape:** Who else is in this space? Any signals they're using a competitor?
5. **One-line wedge hypothesis:** The single best angle to approach this account

### Step 3 — Output

```
═══════════════════════════════════════
QUICK SCAN — [Company Name]
Date: [Today]
═══════════════════════════════════════

COMPANY SNAPSHOT
[2-3 sentences: who they are, what they do, their current moment]
[Public/Private] · [Industry] · [HQ Location] · [~Employee Count]

TOP TRIGGERS
1. ⚡ [Trigger] — [one line] HIGH
2. 📉 [Trigger] — [one line] MEDIUM
3. 📢 [Trigger] — [one line] LOW

WHY NOW SCORE: [X]/10 — [one sentence]

TOP 3 PERSONAS
1. [Title] — [why they matter to this deal in one sentence]
2. [Title] — [why they matter]
3. [Title] — [why they matter]

COMPETITIVE SIGNAL
[One sentence: who they might be using, or "no competitive signal found"]

ACCOUNT WEDGE (HYPOTHESIS)
[One sentence: the single best angle to approach this account]

GO / NO-GO
[GO — worth a full AccountHack run]
[MAYBE — worth monitoring, run Trigger Radar in 2 weeks]
[NO-GO — no urgency, no angle, park this account]

VERIFICATION: [X] of [Y] claims are UNVERIFIED
═══════════════════════════════════════
```

### Step 4 — Routing
Based on the recommendation:

- **GO:** *"This looks worth digging into. Want to run a full AccountHack, or focus on just triggers or warm paths?"*
  - Full run → [ACCOUNT_HACK.md](../../ACCOUNT_HACK.md)
  - Triggers → [trigger-radar](../trigger-radar/SKILL.md)
  - Warm paths → [warm-path](../warm-path/SKILL.md)
  
- **MAYBE:** *"Not urgent yet, but worth watching. I'd recommend setting a Google Alert and checking back in 2 weeks. Want me to set up the monitoring actions?"*

- **NO-GO:** *"I don't see a compelling angle right now. The urgency signals are weak and there's no clear wedge. I'd park this account and focus your time elsewhere. Want to scan a different account?"*

### Step 5 — Completion
```
STATUS: DONE
RECOMMENDATION: GO | MAYBE | NO-GO
```
