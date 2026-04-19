---
name: leadership-intel
description: |
  Deep executive research and outreach strategy for a target account. Maps leadership,
  builds executive narratives, enforces the Earned Right Test, and generates persona-specific
  message drafts. Use when the AE is preparing to contact a specific executive. Runs
  Stage 5, Stage 5.5, and Stage 9.
---

# Leadership Intel & Executive Access

Use this skill when the AE knows who they want to reach at a target account and needs the deep executive research, narrative construction, and message drafts to do it right. This is the highest-stakes skill in AccountHack — bad executive outreach permanently poisons an account.

## Required Context
Before running, collect:
- Company name
- What you're selling
- Who the AE wants to reach (role, name if known)
- What you already know about this executive (even if nothing)

Recommended but not required:
- Trigger Radar results (Why Now Score)
- Warm Path Map results

## Guardrails
Read and enforce:
- [QUALITY_GATES.md](../../guardrails/QUALITY_GATES.md) — Stage 5, Stage 5.5, and Stage 9 checkpoints
- [VOICE.md](../../guardrails/VOICE.md) — anti-slop rules, especially message draft rules
- [VERIFICATION.md](../../guardrails/VERIFICATION.md) — executive data is the highest-risk category for hallucination

## Critical Rule
**The canonical Earned Right Test is a hard stop.** Executive outreach is allowed only if the insight is specific to the selected executive, connected to the wedge, and non-obvious to a competitor rep who spent 15 minutes on Google.

## Workflow

### Step 1 — Open
Say exactly:

*"Let's earn the right to contact the executive at [Company]. We’re not writing a message until we know why this person should actually care. Who's your primary target — and what do you actually know about them beyond their LinkedIn title?"*

### Step 1a — Branch examples
- If the AE says `"I only know the title"` → go straight into research mode and do not draft messaging yet.
- If the AE says `"I already have a strong public insight from their keynote"` → carry that into the route decision and canonical Earned Right Test immediately.

### Step 2 — Leadership Deep Dive (Stage 5)
For each key executive, generate research actions:

**Career and background:**
- Full LinkedIn profile analysis (previous companies, what they built, problems they solved)
- Previous companies → current customer cross-reference (reference call opportunity)
- University → alumni connection check
- Board seats → network and priority mapping

**Video and audio intelligence:**
- YouTube search: `[Name] keynote` or `[Name] interview`
- If video found: extract key themes, strategic priorities, and exact language
- Podcast search: `[Name] podcast`
- LinkedIn articles or Medium posts they've written

**Personal alignment:**
- Charity work, non-profit board seats, public causes
- One genuine, specific connection to your value proposition
- **Rule:** Never fake alignment. One real connection beats ten manufactured ones.

**The thoughtful entry point:**
- Book, report, event, or content that bridges their interest and your solution
- Personalized resource tied to their actual passion

### Step 3 — Executive Route Decision (Stage 5.5, Step 1)
Ask the AE:
1. What is your solution actually solving — strategic, technical, cost/risk, or operational?
2. Who has the most to gain if it works — and the most to lose if it doesn't?
3. Does this deal require executive sign-off, or can it close at Director/VP level?
4. Is there a credible champion who could pull this upward?

Output the routing decision:
```
EXECUTIVE ROUTE DECISION — [Company]

Recommended primary target: [CEO / CTO / CIO / CFO / CRO / CMO / CPO / Not C-suite yet]
Rationale: [2 sentences]
Secondary target: [Role]
NOT recommended: [Roles that don't fit + why]
```

Apply the routing logic strictly. Route to "Not C-suite yet" if the AE has no credible executive narrative. State this honestly.

### Step 4 — The Earned Right Test (Stage 5.5, Step 2)

**THE GATE.** Ask the AE:

*"Give me the one thing you know about this executive's strategic situation — from their earnings call, keynote, LinkedIn post, podcast, or board announcement — that most salespeople calling on this account don't know. One insight that makes your outreach non-generic."*

Apply the canonical pass criteria:
- specific to the selected executive
- connected directly to the wedge
- non-obvious to a competitor rep who spent 15 minutes on Google

**If the AE cannot answer, or the insight fails the canonical pass criteria:**
```
EARNED RIGHT TEST: NOT YET PASSED

The following research actions will help you find the insight:
1. [YouTube search for CEO keynotes from last 6 months]
2. [Earnings call transcript — what did they emphasize?]
3. [LinkedIn posts by the executive in last 90 days]
4. [Board announcements or investor letters]
5. [Industry analyst coverage mentioning executive priorities]

Executive message drafts are BLOCKED until this test is passed.
I'll generate champion and technical buyer drafts instead.
```

**If the AE has the insight and it passes:**
- Emit `PASSED`
- Unlock only the selected executive route
- Continue to the executive narrative for that single route

### Step 4a — Branch examples
- If the AE says `"The CFO is talking publicly about vendor consolidation, and our wedge is cost control"` → test it against the canonical criteria and, if it passes, unlock only the CFO route.
- If the AE says `"They’re transforming the business"` → fail it as too generic and generate the next research actions instead of drafting.

### Step 5 — Executive Narrative (Stage 5.5, Step 3)
Only if Earned Right Test PASSED. Build the narrative for the routed executive:

Use the appropriate frame:
- **CEO:** Strategic moment → your connection → low-friction ask
- **CTO/CIO:** Technical moment → specific decision → technical reference
- **CFO:** Cost/risk/efficiency → financial signal → risk reduction frame
- **CRO:** Revenue/GTM signal → their number → rep-level clarity
- **CMO:** Demand/attribution signal → growth mandate → outcome focus
- **CPO:** Product velocity → build vs. buy → product-led thinking

Include "What never to say" for each.

### Step 6 — Access Path (Stage 5.5, Step 4)
Generate ranked access paths:

1. **Board/investor path** — highest probability
2. **Peer executive path** — your CEO/CRO/mutual board member
3. **Champion escalation** — bottom-up with escalation script
4. **Direct outreach** — only if Earned Right Test passed

### Step 7 — Message Drafts (Stage 9 + Account Brief Section 8)

**If Earned Right Test PASSED:**
- Draft 1 — Primary Executive Target: 4 sentences max. Opens with insight. No features.
- Draft 2 — Technical Buyer / Director-VP: 5 sentences max. Different hook.
- Draft 3 — Champion: 6 sentences max. Leads with day-to-day pain.
- Warm Intro Brief: Forwardable one-paragraph brief for the connector.

**If Earned Right Test NOT PASSED:**
- Draft 1 — Technical Buyer only: 5 sentences max.
- Draft 2 — Champion only: 6 sentences max.
- State clearly: "Executive draft withheld — Earned Right Test not yet passed."

For each draft include:
- Persona / Title
- Channel (LinkedIn DM / Email / X)
- Message body (written to send, not template)
- What makes this non-generic (one sentence)

### Step 8 — Output

The complete Stage 5.5 output block as defined in ACCOUNT_HACK.md, including:
- Routing Decision
- Earned Right Test result
- Executive Narrative
- Access Path (ranked)
- Warm Intro Brief
- Message Drafts (conditional)
- First Call Opening — 60 Seconds

### Step 9 — Checkpoints
Run the Stage 5, Stage 5.5, and Stage 9 checkpoints from QUALITY_GATES.md.

### Step 10 — Completion
```
STATUS: DONE | DONE_WITH_CONCERNS | BLOCKED
EARNED RIGHT TEST: PASSED | NOT YET PASSED
EXECUTIVE TARGET: [Name / Role]
ACCESS PATH: [Highest-priority tier with specific action]
NEXT ACTION: [One sentence — what to do right now]
```
