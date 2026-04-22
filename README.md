# Greenfield

Free MIT-licensed AI skill for breaking into greenfield accounts and producing an Account Brief.

Greenfield helps account executives, SDRs, founders, and GTM operators build a real plan before outreach starts. Instead of guessing the way in, you run the skill inside Claude, ChatGPT, Gemini, Cursor, or another capable assistant and work through a structured 14-part research process first.

The output is an Account Brief: a verified, stakeholder-specific plan with a warm-path map, executive route, trigger-adjusted first-message drafts, and a 30-day execution OS.

## What It Does

A Greenfield run helps you:

- identify timing signals and "why now" triggers before investing in the account
- find internal and external warm paths before defaulting to cold outreach
- map executives, champions, and technical buyers with verified sourcing
- decide whether executive outreach is actually warranted — the Earned Right Test gate
- turn company research into persona-specific messaging and executive narratives
- produce a usable Account Brief and 30-day execution plan instead of a loose pile of notes

## Quick Start

### 1. Install from npm

```bash
npm i -g @mangosteenstudio/greenfieldaccount
greenfieldaccount init
```

This copies the canonical prompt, skill wrapper, guardrails, and focused skills into a local `./greenfield` folder.

### 2. Install as a skill (Claude Code, Gemini CLI, Antigravity, Codex)

```bash
npx skills add mangosteen-studio/greenfield
```

### 3. Use the raw markdown file directly

```bash
curl -O https://raw.githubusercontent.com/Mangosteen-Studio/greenfield/main/GREENFIELD.md
```

### 4. Paste directly into web chat

Copy the full contents of [GREENFIELD.md](./GREENFIELD.md) into Claude, ChatGPT, Gemini, Cursor, or another assistant that can follow long-form instructions.

Then prompt:

```text
Run Greenfield on [Company Name]
```

## What You Get From One Run

- company snapshot and strategic moment summary
- Why Now score with urgency-tagged triggers (HIGH / MEDIUM / LOW)
- target personas with specific hooks
- ranked warm-path priority list
- account wedge: pain, stakeholder, initiative, and rationale
- executive narrative and access plan
- conditional first-message drafts by persona and channel
- warm intro brief when a connector exists
- LinkedIn / Sales Navigator search strings
- intelligence-gaps footer with exact verification actions
- 30-day execution plan with trigger-based adjustments
- human-readable completion block plus a JSON status sidecar

## How It Works

Greenfield uses a 14-part research framework:

1. Stage 0 — Account Identity Disambiguation
2. Trigger Radar
3. LinkedIn Connections Co-Pilot
4. Pre-Stage company context qualifier
5. Internal Intelligence
6. Company Website and Product Analysis
7. Hiring Signals and Growth Intelligence
8. Market and Financial Intelligence
9. Leadership Deep Dive
10. Executive Narrative & Access Strategy
11. Warm Path Activation
12. Technical Landscape and Competitive Intelligence
13. Industry Language and the "One Level Deeper" Rule
14. Persona-Driven Messaging

## Operating Principles

Greenfield is opinionated about research quality:

- no generic output — if it could apply to any company, it is not good enough
- ask one question at a time instead of dumping question batches
- branch on the AE's actual answers, not a fixed script
- go one level deeper than surface industry knowledge
- distinguish verified facts from assumptions and inference
- mark unsupported claims `UNVERIFIED`
- keep unverified claims out of the Account Brief body and move them to the intelligence-gaps footer
- cite or label evidence when account-specific claims are made
- adapt to available tools instead of implying access you do not have

## Recommended Usage

Greenfield works best when you can provide or verify:

- current company news
- job postings
- earnings transcripts or investor materials
- LinkedIn or Sales Navigator research
- CRM history
- customer or partner context
- raw pasted source material for synthesis

If browsing or source material is not available, the run treats company-specific claims as unverified hypotheses, not facts.

## Focused Skills

Don't need a full run? Greenfield includes focused skills you can invoke independently:

| Skill | What It Does | When to Use |
|---|---|---|
| **Quick Scan** | 5-minute triage: snapshot, triggers, top personas, go/no-go | Fast read before investing in a full run |
| **Trigger Radar** | Urgency signals + Why Now Score (1-10) | Check if an account is worth pursuing right now |
| **Warm Path** | LinkedIn CSV analysis, internal intel, and Warm Path Activation | Find the easiest doors before going cold |
| **Leadership Intel** | Executive deep dive, canonical Earned Right Test, narrative, message drafts | Earn the right to contact a specific executive |
| **Account Review** | Quality audit of a completed Account Brief | Validate your research before going into the field |

Each skill enforces the same guardrails as the full run.

## Guardrails

Greenfield includes a structured guardrail system:

| Document | Purpose |
|---|---|
| [QUALITY_GATES.md](./guardrails/QUALITY_GATES.md) | Stage-by-stage checkpoints. The AI must pass each before advancing. |
| [VOICE.md](./guardrails/VOICE.md) | Anti-slop writing rules. Bans generic AI vocabulary. Enforces specificity. |
| [VERIFICATION.md](./guardrails/VERIFICATION.md) | Three-tier verification (Verified / Inferred / Unverified). Source attribution. Escalation rules. |
| [CRITIC.md](./guardrails/CRITIC.md) | Final output audit for verification integrity, the Earned Right Test, and actionability before delivery. |

Every full run ends with a completion block:

```
STATUS: DONE | DONE_WITH_CONCERNS | INCOMPLETE | BLOCKED
VERIFICATION SCORE: [X]/10
EARNED RIGHT TEST: PASSED | NOT YET PASSED
```

## Repository Contents

- [GREENFIELD.md](./GREENFIELD.md) — canonical full skill file (14-part system)
- [SKILL.md](./SKILL.md) — installable skill definition with routing rules
- **guardrails/** — quality enforcement system
  - [QUALITY_GATES.md](./guardrails/QUALITY_GATES.md): stage checkpoints
  - [VOICE.md](./guardrails/VOICE.md): output quality rules
  - [VERIFICATION.md](./guardrails/VERIFICATION.md): verification discipline
  - [CRITIC.md](./guardrails/CRITIC.md): final output audit
- **skills/** — focused, independently-runnable skills
  - [trigger-radar/](./skills/trigger-radar/SKILL.md): urgency scanning
  - [warm-path/](./skills/warm-path/SKILL.md): warm path mapping
  - [leadership-intel/](./skills/leadership-intel/SKILL.md): executive research & access
  - [quick-scan/](./skills/quick-scan/SKILL.md): 5-minute account triage
  - [account-review/](./skills/account-review/SKILL.md): Account Brief quality audit
- **.agents/workflows/** — orchestration workflows for full runs, trigger-only scans, and warm-path-only runs

## Website

[greenfield.tools](https://greenfield.tools)

Mangosteen Studio: [mangosteen.studio](https://mangosteen.studio)

## License

MIT. See [LICENSE](./LICENSE).
