---
name: proposal-pipeline
description: |
  Generate tailored Upwork proposals from job postings. 6-phase pipeline.
  Triggers: "write proposal", "proposal for", "upwork proposal", "generate proposal".
user-invocable: true
---

# Proposal Pipeline

MANDATORY: Follow all 6 phases in order. No draft before Phase 5. No delivery before Phase 6 passes.

This skill uses its own rules, not the social media rules in `.claude/rules/`. Proposals are private 1-to-1 communication, not public content. The content pipeline rules (opening under 10 words, specific numbers from source code, depth requirements, no org names in proof URLs) do not apply here.

---

## Phase 1: Job Intake

Parse the pasted job posting. Extract and present:

- **Job title / role**
- **Client's core problem** (what they actually need solved)
- **Technical requirements** (languages, frameworks, integrations)
- **Non-technical requirements** (timeline, budget, team size, process)
- **Budget** (if stated)
- **Timeline** (if stated)
- **Key phrases to mirror** (exact words from the posting to echo back in the proposal)

### Pillar Detection

Match job keywords to determine which pillar to use:

| Job Keywords | Pillar | Voice |
|---|---|---|
| polymarket, kalshi, prediction market, trading bot, market making, DeFi, crypto trading | **Polymaxr** | Data-driven, precise, crypto-native. Numbers over narratives. Risk-aware and honest. |
| AI agent, Claude, chatbot, automation, LLM, RAG, OpenAI, prompt engineering, openclaw, moltbot | **AIIn60** | Professional but approachable. Educational, not salesy. Practical and action-oriented. |
| Mixed (both categories) | Lead with the dominant pillar, mention the other | Blend both voices |
| Neither (general dev work) | Default to **AIIn60** | Professional, practical |

Present the structured brief and pillar assignment. Get user confirmation before proceeding.

---

## Phase 2: Client Assessment

Evaluate the client using signals visible in the posting text. Read `knowledge/client-signals.md` for the full guide.

Check for:
1. **Green flags**: Clear budget, defined problem, technical understanding, production intent
2. **Red flags**: Vague requirements, "easy/simple" language, no budget, unrealistic timeline
3. **Deal breakers**: Illegal projects, demands free work, disrespectful tone, crypto scams

Assign priority:

| Priority | Criteria |
|----------|----------|
| **HIGH** | Clear scope + verified payment + budget > $5K + our niche |
| **MEDIUM** | Good client + decent budget + close to our niche |
| **LOW** | Unclear scope OR budget concerns OR outside expertise |
| **SKIP** | Red flags OR deal breakers OR < $1.5K budget |

If SKIP: explain why and stop. Don't write proposals for bad-fit jobs.

Present assessment to user. Proceed on approval.

---

## Phase 3: Experience Mapping

Read `knowledge/portfolio.md` and `knowledge/proof-assets.md`.

1. **Select lead project** (Pattern 2): The single most relevant past project. Pick the one whose tech stack and problem domain overlap most with the job requirements.
2. **Select proof assets** (Pattern 3): 2-4 most relevant proof links. Don't dump all links. Choose ones that directly demonstrate capability for this specific job.
3. **Identify current relevance** (Pattern 4): What are you currently building or running that relates to this job? Frame in present tense.
4. **Check pricing** (read `knowledge/pricing.md`): What's the appropriate rate/package for this job's scope?

Present the mapping to user:
- Lead project: [name] because [reason]
- Proof assets: [2-4 URLs] because [reason each]
- Current relevance angle: [what to say]
- Suggested pricing: [range or rate]

Get approval before designing the proposal.

---

## Phase 4: Proposal Design

Select a copywriting framework based on the job type:

| Job Type | Framework | Why |
|----------|-----------|-----|
| Client has a clear pain point | **PAS** (Problem, Agitate, Solution) | Lead with their pain, show you understand it, present your fix |
| Client wants a transformation | **BAB** (Before, After, Bridge) | Show where they are, where they could be, how you get them there |
| Default / mixed | **AIDA** (Attention, Interest, Desire, Action) | Hook them, build interest with proof, create desire, close with CTA |

Outline all 7 Winning Patterns with specific planned content:

1. **Opening Hook**: What credibility claim? What connection to their specific problem?
2. **Lead Portfolio Project**: Which project? What technical specifics to highlight?
3. **Live Proof**: Which 2-4 URLs?
4. **Current Relevance**: What present-tense activity to mention?
5. **Scope / Approach**: What 3-6 deliverables? (Mirror their language)
6. **CTA with Timeline**: What specific deliverable and timeframe?
7. **Voice**: Which pillar voice? Any special tone considerations?

Present the outline. Do NOT draft until the user approves the design.

---

## Phase 5: Proposal Draft

Write the proposal following the approved design from Phase 4.

### The 7 Winning Patterns (follow in order)

**Pattern 1: Opening Hook**
Open with an immediate credibility claim tied to the client's specific problem. Not a generic intro.
- Bad: "Hi, I'm a developer with experience in many things."
- Good: "Hi, I am a [specific role] with [specific proof] currently [specific activity relevant to their job]."

**Pattern 2: Lead Portfolio Project**
Present the single most relevant past project. Include technical specifics that mirror what the client needs. Name the project, describe what it does, highlight the overlap with their requirements.

**Pattern 3: Live Proof**
Include at least 2 proof links. Non-negotiable. Pick the most relevant from the approved list. Use raw URLs only.

**Pattern 4: Current Relevance**
Show this is daily work, not a one-off. Use present tense: "I am currently building...", "I am actively running...", "I operate this daily..."

**Pattern 5: Scope / Approach**
Show you understand THEIR specific problem. Outline 3-6 concrete deliverables using unicode bullets. Mirror the client's language and requirements from their job posting.

**Pattern 6: CTA with Timeline**
Close with a specific deliverable and timeframe. Not vague.
- Bad: "Happy to discuss further."
- Good: "I can have your [specific deliverable] live within [X days]."

**Pattern 7: Voice**
First person ("I am", "I have", "I will"). Confident but not arrogant. No filler words. No buzzwords. Sign off as "Best regards, Sami".

### Format Rules

Apply these WHILE drafting, not after:

- **Max 280 words**. Every sentence must earn its place.
- **Plain text only**. No markdown. Upwork doesn't render it.
- **No bold/italic**. No `**bold**`, `*italic*`, `__underline__`.
- **No markdown links**. Raw URLs only (e.g., https://example.com).
- **Unicode bullets**. Use `•` instead of `-` or `*`.
- **No em dashes**. Use commas, periods, or restructure the sentence.
- **Line breaks for readability**. Use spacing to create visual structure.
- **Sign off**: "Sami" or "Best regards, Sami".

### Content Rules

- Write as Sami. First person. "I am", "I have", "I will".
- Never mention being AI or that this was generated.
- Personalize for EVERY job. No two proposals should be identical.
- Never use full channel names (WhatsApp, Telegram, Discord). Use TG, WA, or describe the capability without naming the channel.
- Polymarket has no testnet. Never reference "testnet" or "paper trading on Polymarket". Say "backtesting against historical data" or "dry-run mode with simulated orders".
- No AI vocabulary: Additionally, Furthermore, landscape, tapestry, testament, pivotal, showcase, delve, foster, robust, comprehensive, seamless, cutting-edge, harness, realm, paradigm, holistic, synergy, leverage, utilize.
- Org names don't appear in proposal body text (use "I" and "my team"). Proof asset URLs containing org domains are fine since they're evidence.

---

## Phase 6: Review & Delivery

Dispatch the `proposal-reviewer` agent.

The reviewer checks:
1. **Format compliance** (any fail = rejected): word count, plain text, unicode bullets, no em dashes, no markdown, sign-off present
2. **Pattern compliance** (all 7 patterns present, none below 6/10 quality)
3. **Persuasion score** (weighted criteria, threshold: 70/100)

If verdict is NEEDS WORK:
- Fix all Critical findings
- Address Improvement findings
- Re-submit to reviewer
- Max 3 iterations. If still stuck, present best version with remaining issues flagged.

If verdict is APPROVED, deliver:

```
=== Proposal (Ready to Paste) ===

[plain text proposal]

=== Metadata ===
Pillar: [AIIn60 | Polymaxr]
Word count: [N]/280
Proof assets: [URLs used]
Priority: [HIGH | MEDIUM | LOW]
```

---

## Rules

- NEVER skip Phase 2 (Client Assessment). Bad-fit jobs waste time.
- NEVER skip Phase 3 (Experience Mapping). Generic proposals lose.
- NEVER draft before Phase 5. Design first.
- NEVER deliver before Phase 6 passes. Review is mandatory.
- If the user changes the angle mid-pipeline, restart from Phase 4 (Proposal Design).
- One proposal per pipeline run. Don't batch.
- If proof assets return 404, flag to the user and suggest updating `knowledge/proof-assets.md`.
