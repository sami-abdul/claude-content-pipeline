---
name: copywriting
description: |
  Apply copywriting frameworks to post drafts. PAS, AIDA, BAB, 4Ps, StoryBrand.
  Triggers: "apply framework", "structure the post", "which framework".
  Includes anti-AI writing constraints applied during drafting, not after.
user-invocable: true
---

# Copywriting

Apply structured copywriting frameworks to posts. The reader should never notice a framework was used. If a step feels forced, skip it and let the post flow naturally.

## Frameworks

| Framework | Best For | Structure |
|-----------|----------|-----------|
| **PAS** | Mistakes, anti-patterns, "most people do X wrong" | Problem, Agitation, Solution |
| **AIDA** | New technique, tool, or approach that worked | Attention, Interest, Desire, Action |
| **BAB** | Transformation, "we used to do X, now we do Y" | Before, After, Bridge |
| **4Ps** | Deep technical breakdown with proof | Promise, Picture, Proof, Push |
| **StoryBrand** | War stories, production incidents, project narratives | Hero, Problem, Guide, Plan, CTA |

## Default Selection

- Post about a common mistake or anti-pattern: **PAS**
- Post sharing a new technique or tool: **AIDA**
- Post about "we used to do X, now we do Y": **BAB**
- Deep technical explainer with numbered points: **4Ps**
- Story about a production incident or project: **StoryBrand**

## Runbook (4 Steps)

### Step 1: Analyze the Topic

Read the insight brief. Identify:
- **Who cares?** The specific audience segment (AI builders, crypto engineers, backend devs)
- **What's the tension?** The problem, mistake, or gap
- **What's the payoff?** The insight, fix, or realization

Output: One line each for audience, tension, payoff.

### Step 2: Select Framework

Pick the framework that best fits the tension/payoff dynamic. State which and why in one sentence. If unsure between two, pick the one that lets the non-obvious insight land hardest.

### Step 3: Draft Using Framework

Write the post following the framework structure. Apply ALL constraints while drafting:

**Opening**: Under 10 words. Short and blunt. No preamble.

**Body**:
- Zero em dashes. Use commas, periods, parentheses for asides.
- Zero AI vocabulary (see `.claude/rules/never-do.md` for kill list).
- No negative parallelisms. No "It's not X. It's Y." Just state what IS true.
- No synonym cycling. Pick one word for each concept and repeat it.
- At least one sentence under 5 words.
- At least 5 contractions throughout.
- At least one honest/vulnerable moment.
- At least one parenthetical aside (using parentheses).
- At least one specific number from the source code.
- Varied sentence lengths. Mix short bursts with longer explanations.
- No organization names.

**Closing**: A strong declarative statement. Never a question. Must land with weight.

**LinkedIn mode** (default):
- 150-300 words
- Unicode bold for emphasis
- Line breaks for readability
- No hashtags

**Twitter mode** (when specified):
- Single tweet: max 280 characters total
- Thread: each tweet max 280 chars, first tweet is the hook
- Plain text only
- No hashtags
- Each tweet stands alone while building the narrative

### Step 4: Score and Refine

Score the draft (1-10 each, weighted):

| Criterion | Weight | Check |
|-----------|--------|-------|
| Hook strength | 3x | Would you stop scrolling? Under 10 words? |
| Specificity | 3x | Concrete numbers from actual code? Any vague claims? |
| Human voice | 2x | Sounds like a person? Contractions present? |
| Anti-AI | 3x | Zero em dashes? No parallelisms? No AI vocab? No synonym cycling? |
| Structure | 1x | Framework flows naturally without feeling formulaic? |
| Close | 1x | Strong closing statement? Not a question? |

Weighted score out of 130. If below 100, rewrite weak areas and re-score.

For Twitter: verify character count per tweet. If over 280, rewrite to fit (don't truncate).

## Rules

- Never sacrifice voice for framework adherence.
- The reader should never detect a framework was used.
- Every sentence must earn its place. If you can remove it without losing meaning, remove it.
- Apply constraints DURING drafting. Don't write freely then fix. Build clean from the start.
