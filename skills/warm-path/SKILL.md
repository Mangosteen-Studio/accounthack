---
name: warm-path
description: |
  Map every warm path into a target account — LinkedIn connections, internal intel,
  customer networks, investor overlap, partner relationships, alumni. Use when the AE
  wants to find who they know before going cold. Combines LinkedIn Co-Pilot, Pre-Stage
  company branching, Stage 1, and Stage 7.
---

# Warm Path Mapper

Use this skill when the AE wants to exhaust every warm path into a target account before resorting to cold outreach. This combines the LinkedIn Co-Pilot, company context qualifier, internal intelligence (Stage 1), and relationship mapping (Stage 7) into a focused warm-path-only workflow.

## Required Context
Before running, collect:
- Company name
- What you're selling
- Your company size (startup / growth / enterprise)
- Whether you want to export LinkedIn connections (CSV)

## Guardrails
Read and enforce:
- [QUALITY_GATES.md](../../guardrails/QUALITY_GATES.md) — Stage 1 and Stage 7 checkpoints
- [VOICE.md](../../guardrails/VOICE.md) — anti-slop rules
- [VERIFICATION.md](../../guardrails/VERIFICATION.md) — verification discipline

## Workflow

### Step 1 — Open
Say exactly:

*"Let's find every warm path into [Company]. First — are you at a startup, growth-stage company, or large enterprise? This changes which warm path assets we check first."*

### Step 2 — LinkedIn CSV Decision
Ask:

*"Do you want to supercharge this with your LinkedIn connections? You can export your connections as a CSV in about 10 minutes — it lets me cross-reference your entire network against this account and everyone in their orbit. Want to do that now, or should we work with Sales Nav searches?"*

If yes → provide the exact LinkedIn export instructions from ACCOUNT_HACK.md and wait for the CSV.
If no → proceed with Sales Nav search strings.

### Step 3 — LinkedIn CSV Analysis (if provided)
When the AE pastes the CSV, run the full 5-step analysis immediately:

1. **Direct connections at the target** — scan Company column for matches
2. **Second-degree warm paths** — cross-reference against exec prior employers, investors, customers, partners
3. **Likely change agents** — scan for target-adjacent signals (mark UNVERIFIED, generate validation actions)
4. **Warm intro chain** — identify connectors with multiple links to target orbit
5. **Connection recency scoring** — weight by connection date

Output the LinkedIn Warm Path Report in the format defined in ACCOUNT_HACK.md.

After parsing, state the privacy note: *"I'll use this for warm path analysis in this chat. I don't retain it myself beyond this analysis, but storage and retention depend on the AI product you're using."*

### Step 4 — Company-Type Branch
Based on the AE's company size, run the appropriate branch:

**Startup (under ~200 people):**
- Investor network sweep
- Founder LinkedIn check
- Advisor ask
- Cap table cross-reference
- Accelerator alumni search
- Co-investor introduction

**Growth Stage (~200–2,000):**
- Partnership team ask
- Customer overlap sweep
- Executive connection check
- CRM warm path filter
- LinkedIn employee search
- Board and investor overlap

**Large Enterprise (2,000+):**
- Product and customer overlap
- Partnership and alliance sweep
- Corporate venture and investment
- Alumni network search
- Research and standards body connections
- Geographic and physical proximity
- Industry analyst relationships

### Step 5 — Internal Intelligence (Stage 1)
Ask the Stage 1 questions:
1. Has your company ever touched this account?
2. Any departments with existing relationships you don't know about?
3. Is there a Slack channel or internal forum to post in?

Generate the internal bat signal message as paste-ready copy.

### Step 6 — Relationship Mapping (Stage 7)
Ask:
1. Do any existing customers know someone there?
2. Have you asked your manager, SE, exec sponsor, CSM?
3. Shared investors, advisors, board members?

Generate specific asks for the AE's top 3 champion relationships.

### Step 7 — Pre-Warm Plan
Generate the engagement-before-outreach plan:
- Follow the key executive on LinkedIn
- One genuine comment on their post
- One relevant content share with no ask
- Do this once each — never more.

### Step 8 — Output

```
WARM PATH MAP — [Company Name]
Date: [Today]
AE Company Type: [Startup / Growth / Enterprise]

TIER 1 — DIRECT CONNECTIONS (act today)
[Ranked list with DM drafts]

TIER 2 — SECOND-DEGREE (act this week)
[Ranked list with specific asks]

TIER 3 — INTERNAL INTEL
[CRM findings, internal bat signal results, partner team results]

TIER 4 — CUSTOMER NETWORK
[Champion connections, customer overlap]

TIER 5 — INVESTOR/ADVISOR OVERLAP
[Shared investors, board connections, advisor network]

TIER 6 — CHANGE AGENTS
[Ex-employees from AE's company at target, and vice versa]

PRE-WARM SEQUENCE
1. Follow [Name] on LinkedIn — [date]
2. Comment on [specific post] — [date + 2 days]
3. Share [specific content] — [date + 5 days]
4. First outreach — [date + 7 days]

WARM PATHS EXHAUSTED: YES / NO
If NO: [specific paths not yet activated]

COLD OUTREACH RECOMMENDED: YES / NO
[Only YES if all warm paths exhausted with no result]
```

### Step 9 — Checkpoint
Run the Stage 1 and Stage 7 checkpoints from QUALITY_GATES.md.

### Step 10 — Completion
```
STATUS: DONE | DONE_WITH_CONCERNS | BLOCKED
WARM PATHS FOUND: [count]
TOP PRIORITY PATH: [one sentence — the single warmest path and the action to take today]
```

### Routing
*"Warm path mapping complete. Want to run a full AccountHack, or focus on leadership intel for your top exec target?"*
