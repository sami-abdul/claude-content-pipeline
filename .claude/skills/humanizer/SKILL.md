---
name: humanizer
description: |
  3-pass humanization for post drafts. Detects AI patterns, rewrites,
  then runs final checks (Coffee, Template, Scroll, AI Detector tests).
  Triggers: "humanize", "make it sound human", "ralph wiggum", "AI check".
user-invocable: true
---

# Humanizer

Every post draft MUST pass through this skill before delivery. This is a self-correction loop that rewrites AI-sounding copy into natural human writing.

## When to Use

- ALWAYS before delivering a final draft (Phase 6 of content-pipeline)
- When a draft "sounds AI" or "too polished"
- When you suspect a draft is formulaic

## Pass 1: AI Pattern Detection

Read the draft and flag every instance of these patterns:

**Kill on sight (ANY of these = draft FAILS this pass):**
- Em dashes (any occurrence)
- Emoji (any occurrence)
- "Here's the thing" / "Here's why" / "Let that sink in" / "Full stop."
- "Let me break this down" / "Let's dive in" / "Here's what I mean"
- Starting 3+ sentences with the same word
- "That is" instead of "That's" / "do not" instead of "don't" / missing contractions
- "It's not X. It's Y." / "Not only...but also..." (negative parallelisms)
- Imperative commands: "Stop doing X. Start doing Y."
- AI vocabulary: Additionally, Furthermore, landscape, tapestry, testament, pivotal, showcase, delve, foster, robust, comprehensive, seamless, cutting-edge, harness, realm, paradigm, holistic, synergy, leverage, utilize
- "Serves as", "stands as", "functions as" when "is" works
- "On another level", "marks a shift", "changes everything" (inflated significance)
- "Innovation, inspiration, and insights" style forced triplets
- Synonym cycling (same concept, 3+ different words)
- "Could potentially", "it's worth noting that" (over-hedging)
- "From startups to enterprises" (false ranges)
- Any organization name

**Structure fail (ANY = draft is too AI-structured):**
- All numbered points the same length
- Every paragraph 2-3 sentences (no variation)
- Blog outline format
- Thesis, explanation, numbered list, question pattern
- Every numbered point same grammatical start
- Opening line longer than 10 words
- Post ends with a question

**Missing elements (ANY missing = add before proceeding):**
- At least one sentence under 5 words
- At least one mid-post question (NOT at the end)
- At least one specific number from source code
- At least 5 contractions
- At least one vulnerable/honest moment
- At least one parenthetical aside (using parentheses)
- "I" or "we" appearing naturally

## Pass 2: Rewrite

Fix every flagged issue:

1. Keep the same core message and structure.
2. Make it sound like someone typing a post, not drafting an essay.
3. Word swaps: leverage->use, architect->build, utilize->use, facilitate->help, implement->build/add/set up, comprehensive->cut, robust->cut, seamless->cut, harness->use, delve->cut, foster->build or cut, pivotal->cut, showcase->show
4. Fix negative parallelisms: "It's not X. It's Y." becomes a single merged sentence.
5. Fix em dashes: replace ALL with commas, periods, or parentheses. Zero tolerance.
6. Fix vague claims: "on another level" -> specific metric. If you can't find a number, cut the claim.
7. Fix synonym cycling: if you used "retrieval" once, use "retrieval" again. Don't switch words.
8. Add pattern breaks: a parenthetical aside, a one-word sentence, a sentence that interrupts the flow.
9. If numbered points exist, vary their lengths and opening words.
10. Opening line: would you actually stop scrolling? If not, make it shorter and more blunt. Under 10 words.
11. Closing line: must be a statement, not a question. Must land with weight.
12. Remove all organization names.

## Pass 3: Final Check

Read the rewritten draft and apply four tests:

**Coffee Test:** Does this sound like someone telling you about it over coffee, or like a LinkedIn thought leadership post? If the latter, rewrite.

**Template Test:** Could you swap the topic (trading bots -> databases -> deployment) and the post still works with minimal changes? If yes, it's too generic. Add specific details that ONLY apply to this topic.

**Scroll Test:** Read ONLY the first line. Would you stop scrolling? If not, make it shorter, more blunt, more specific. Must be under 10 words.

**AI Detector Test:** Read as a skeptic looking for AI tells. Check:
- Any em dashes remaining?
- Any "It's not X. It's Y." constructions?
- Any AI vocabulary from the kill list?
- Any vague claims without numbers?
- Uniform sentence/paragraph lengths?
- Synonym cycling?
- If you find even ONE AI tell, fix it.

Could you tell this was written by AI? If yes, do another pass.

## Self-Scoring (Internal Only)

After the final draft, score internally:
- Human-sounding: 1-10 (target: 8+)
- Specificity: 1-10 (target: 7+)
- Hook strength: 1-10 (target: 8+)

If any score below target, do one more rewrite pass focused on that area. Do not share scores.

## Output

Return only the final rewritten draft. No commentary, no "here's the improved version", no before/after. Just the clean post text.
