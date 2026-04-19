# AccountHack

Free MIT-licensed AI-guided interrogation skill for breaking into greenfield accounts and producing an Account Brief.

AccountHack helps account executives, SDRs, founders, and GTM operators pressure-test complex target accounts before outreach. Instead of starting with generic cold messaging, you run the skill inside Claude, ChatGPT, Gemini, Cursor, or another capable assistant and build a structured Account Brief first.

Version 4 makes the Account Brief the canonical output artifact. The skill stays standalone for the Tuesday launch: 14-part workflow, warm-path unification, canonical Earned Right Test, guardrails, focused skills, and a machine-parseable completion block. The later Account Brief / Account Memory product can keep that same artifact updated over time without changing the core workflow.

## What It Does

AccountHack is designed to turn a single target account into a working outbound plan. A run should help you:

- identify timing signals and "why now" triggers
- find internal and external warm paths before defaulting to cold outreach
- map executives, champions, and technical buyers
- decide whether executive outreach is actually warranted
- turn company research into persona-specific messaging and executive narratives
- produce a usable Account Brief and 30-day account plan instead of a loose pile of notes

## Quick Start

Use any one of these options:

### 1. Install as a skill for Claude Code, Gemini CLI, Antigravity, or Codex

```bash
npx skills add mangosteen-studio/accounthack
```

### 2. Use the raw markdown file directly

```bash
curl -O https://raw.githubusercontent.com/mangosteen-studio/accounthack/main/ACCOUNT_HACK.md
```

### 3. Copy the full contents directly

Copy the full contents of [ACCOUNT_HACK.md](./ACCOUNT_HACK.md) into Claude, ChatGPT, Gemini, Cursor, or another assistant that can follow long-form instructions.

Then prompt:

```text
Run AccountHack on [Company Name]
```

## What You Get From One Run

A good run should produce:

- a company snapshot and strategic moment summary
- a "Why Now" score with urgency-tagged triggers
- target personas with specific hooks
- a ranked warm-path priority list
- an account wedge: pain, stakeholder, initiative, and rationale
- an executive narrative and access plan
- conditional first-message drafts by persona and channel
- a warm intro brief when a connector exists
- LinkedIn / Sales Navigator search strings
- an intelligence-gaps footer with exact verification actions
- a 30-day execution plan with trigger-based adjustments
- a human-readable completion block plus a JSON status sidecar

## How It Works

AccountHack uses a 14-part research framework:

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

The final output is an Account Brief, warm intro brief, trigger-adjusted 30-day execution OS, and a human + JSON run-completion block.

## Operating Principles

AccountHack is opinionated about research quality:

- no generic output
- branch on the AE's actual answers
- go one level deeper than surface industry knowledge
- distinguish verified facts from assumptions and inference
- mark unsupported claims `UNVERIFIED`
- keep unverified claims out of the main Account Brief body and move them to the intelligence-gaps footer
- cite or label evidence when account-specific claims are made
- adapt to available tools instead of pretending every system is accessible

## Recommended Usage

AccountHack works best when you can provide or verify:

- current company news
- job postings
- earnings transcripts or investor materials
- LinkedIn or Sales Navigator research
- CRM history
- customer or partner context
- raw pasted source material for synthesis

If browsing or source material is not available, the run should treat company-specific claims as unverified hypotheses, not facts.

## Focused Skills

Don't always need a full run? AccountHack includes focused skills you can invoke independently:

| Skill | What It Does | When to Use |
|---|---|---|
| **Quick Scan** | 5-minute triage: snapshot, triggers, top personas, go/no-go | Fast read before investing time in a full run |
| **Trigger Radar** | Urgency signals + Why Now Score (1-10) | Check if an account is worth pursuing right now |
| **Warm Path** | LinkedIn CSV analysis, internal intel, and Warm Path Activation | Find the easiest doors before going cold |
| **Leadership Intel** | Executive deep dive, canonical Earned Right Test, narrative, message drafts | Earn the right to contact a specific executive |
| **Account Review** | Quality audit of a completed Account Brief | Validate your research before going into the field |

Each skill enforces the same guardrails as the full run — quality gates, anti-slop rules, and verification discipline.

## Guardrails

AccountHack v4 includes a structured guardrail system inspired by [gstack](https://github.com/garrytan/gstack):

| Document | Purpose |
|---|---|
| [QUALITY_GATES.md](./guardrails/QUALITY_GATES.md) | Stage-by-stage checkpoints. The AI must pass each before advancing. |
| [VOICE.md](./guardrails/VOICE.md) | Anti-slop writing rules. Bans generic AI vocabulary. Enforces specificity. |
| [VERIFICATION.md](./guardrails/VERIFICATION.md) | Three-tier verification (Verified / Inferred / Unverified). Source attribution. Escalation rules. |
| [CRITIC.md](./guardrails/CRITIC.md) | Final output audit for verification integrity, the canonical Earned Right Test, and actionability before delivery. |

Every full run ends with a human completion block plus a JSON sidecar:
```
STATUS: DONE | DONE_WITH_CONCERNS | INCOMPLETE | BLOCKED
VERIFICATION SCORE: [X]/10
EARNED RIGHT TEST: PASSED | NOT YET PASSED
```

## Repository Contents

- [ACCOUNT_HACK.md](./ACCOUNT_HACK.md): the canonical full skill file (14-part system)
- [SKILL.md](./SKILL.md): installable skill definition with routing rules
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
- [agents/openai.yaml](./agents/openai.yaml): installer metadata
- [LICENSE](./LICENSE): MIT license

## Website

Landing page: [accounthack.tools](https://accounthack.tools)

Mangosteen Studio: [mangosteen.studio](https://mangosteen.studio)

## License

AccountHack is released under the MIT License. See [LICENSE](./LICENSE).
