# AccountHack

Free MIT-licensed AI account research skill for greenfield enterprise prospecting.

AccountHack helps account executives, SDRs, founders, and GTM operators research complex target accounts before outreach. Instead of starting with generic cold messaging, you run the skill inside Claude, ChatGPT, Gemini, Cursor, or another capable assistant and build a structured account brief first.

## What It Does

AccountHack is designed to turn a single target account into a working outbound plan. A run should help you:

- identify timing signals and "why now" triggers
- find internal and external warm paths before defaulting to cold outreach
- map executives, champions, and technical buyers
- translate company research into persona-specific messaging
- produce a usable 30-day account plan instead of a loose pile of notes

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
- first-message drafts by persona and channel
- LinkedIn / Sales Navigator search strings
- intelligence gaps and next actions
- a 30-day execution plan

## How It Works

AccountHack uses an 11-stage research framework:

1. Trigger Radar
2. Internal Intelligence
3. Company Website and Product Analysis
4. Hiring Signals and Growth Intelligence
5. Market and Financial Intelligence
6. Leadership Deep Dive
7. LinkedIn and Change Agent Intelligence
8. Relationship and Warm Path Mapping
9. Technical Landscape and Competitive Intelligence
10. Industry Language and the "One Level Deeper" Rule
11. Persona-Driven Messaging

The final output is an Account War Room plus a 30-day execution OS.

## Operating Principles

AccountHack is opinionated about research quality:

- no generic output
- branch on the AE's actual answers
- go one level deeper than surface industry knowledge
- distinguish verified facts from assumptions
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

## Repository Contents

- [ACCOUNT_HACK.md](./ACCOUNT_HACK.md): the canonical public skill file
- [SKILL.md](./SKILL.md): installable skill definition
- [agents/openai.yaml](./agents/openai.yaml): installer metadata
- [LICENSE](./LICENSE): MIT license

## Website

Landing page: [accounthack.tools](https://accounthack.tools)

Mangosteen Studio: [mangosteen.studio](https://mangosteen.studio)

## License

AccountHack is released under the MIT License. See [LICENSE](./LICENSE).
