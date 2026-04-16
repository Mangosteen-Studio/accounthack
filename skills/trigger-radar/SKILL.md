---
name: trigger-radar
description: |
  Quick urgency scan for a target account. Identifies triggers, scores urgency (1-10),
  and tells you whether to move now, build slowly, or park. Use when you need a fast
  read on whether an account is worth pursuing right now. Runs Stage 0.5 only.
---

# Trigger Radar — Standalone Urgency Scan

Use this skill when the AE wants a quick urgency assessment on a target account without running the full AccountHack interrogation. This is Stage 0.5 extracted as an independent, focused skill.

## Required Context
Before running, collect:
- Company name
- Industry / vertical
- What you're selling (one sentence)

## Guardrails
Read and enforce:
- [QUALITY_GATES.md](../../guardrails/QUALITY_GATES.md) — specifically the Stage 0.5 checkpoint
- [VOICE.md](../../guardrails/VOICE.md) — anti-slop rules
- [VERIFICATION.md](../../guardrails/VERIFICATION.md) — verification discipline

## Workflow

### Step 1 — Open
Say exactly:

*"Let's scan for urgency. Give me the company name, what you're selling, and any signals you've already spotted — funding, leadership changes, earnings, news, anything. Even if you have nothing, I'll dig."*

### Step 2 — Interrogate
Ask these 3 questions:
1. What's the one thing that would make this account urgent in the next 90 days — for them, not for you?
2. Have you already seen any signals — recent funding, leadership change, earnings miss, acquisition, new product launch, regulatory shift?
3. Is there a specific internal event at your company (QBR, SKO, end of quarter) that creates a timing reason to move on this now?

### Step 3 — Research Actions
Generate these actions (adapted to available tools):

- **90-day news scan:** Google `"[Company Name]" news` filtered to last 90 days
- **Crunchbase check:** Recent funding rounds or leadership updates
- **LinkedIn "People" changes:** Filter by "joined in last 90 days" and "left in last 90 days"
- **Set live alerts:** Google Alert + LinkedIn Sales Navigator alert for ongoing monitoring

If the AI has web search: run the searches and synthesize.
If not: generate the exact search strings as copyable actions for the AE.

### Step 4 — Co-Pilot Mode
Invite the AE to paste raw data:

*"If you have any news articles, earnings snippets, or job postings for this company, paste them now. I'll extract the urgency signals immediately."*

When data is pasted: synthesize, don't ask questions about it. Extract the 2-3 most urgent signals.

### Step 5 — Output

```
TRIGGER RADAR — [Company Name]
Date: [Today]

TRIGGERS IDENTIFIED
⚡ [Trigger] — [detail + source] HIGH
📉 [Trigger] — [detail + source] MEDIUM  
📢 [Trigger] — [detail + source] LOW

WHY NOW SCORE: [X]/10 — [one sentence rationale]

INTERPRETATION
[8-10] → Move now. This account has active urgency.
[5-7]  → Build slowly. Monitor triggers. Start warming paths.
[<5]   → Park it. Set alerts. Revisit when a trigger surfaces.

RECOMMENDED NEXT ACTIONS
1. [Most urgent action — specific]
2. [Second action — specific]
3. [Third action — specific]

MONITORING SETUP
☐ Google Alert set for "[Company Name]"
☐ LinkedIn Sales Nav alert set
☐ Next check-in: [date — 2 weeks from now]

VERIFICATION
[X] claims verified · [Y] inferred · [Z] unverified
```

### Step 6 — Stage Checkpoint
Run the Stage 0.5 checkpoint from QUALITY_GATES.md before delivering output.

### Step 7 — Completion
Output:
```
STATUS: DONE | DONE_WITH_CONCERNS | BLOCKED
```

If DONE_WITH_CONCERNS: list the concerns.
If BLOCKED: state what's missing and what the AE needs to provide.

### Routing
After completing the trigger scan, tell the AE:

*"Trigger scan complete. Want to go deeper? I can run a full AccountHack on this account, or focus on just warm paths or leadership intel."*

- Full run → direct to [ACCOUNT_HACK.md](../../ACCOUNT_HACK.md)
- Warm paths → direct to [warm-path skill](../warm-path/SKILL.md)
- Leadership intel → direct to [leadership-intel skill](../leadership-intel/SKILL.md)
