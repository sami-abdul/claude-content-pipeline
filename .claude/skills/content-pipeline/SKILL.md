---
name: content-pipeline
description: |
  Use when generating a post, creating content, or finding insights from code.
  Triggers: "generate post", "create content", "draft a post", "find insights".
  7-phase structured content development. No draft before Phase 5.
user-invocable: true
---

# Content Pipeline

MANDATORY: Follow all 7 phases in order. No draft before Phase 5. No delivery before Phase 6 passes.

## Phase 1: Discovery

Read the request carefully. Identify:
- **Topic area**: Which repo(s)? Which product line? (polymaxr, megafi, ai60)
- **Depth target**: Bug story? Architecture decision? Platform quirk? Rewrite story?
- **Platform**: LinkedIn, X/Twitter, or both?
- **Constraints**: Any specific angle the user wants?

If the request is vague ("find something interesting"), scan all three product lines and present options before proceeding.

## Phase 2: Exploration

Dispatch the `insight-architect` agent to explore the target repos. If doing manually:

1. **Map territory**: `git log --oneline -30` in target repos. Check branch names for feature work.
2. **Read gold mines first**:
   - `polymaxr/polymaxr-lite/.cursor/rules/common-bugs.mdc`
   - `polymaxr/polymaxr-mm-bot/.cursor/rules/common-bugs.mdc`
   - `polymaxr/polymaxr-lite-v2/risk/src/` (constants)
   - `megafi/server/src/common/` (infrastructure decisions)
   - `ai60/agentic-org/docs/AGENT-PATTERNS.md`
3. **Parallel mining**: When scanning multiple repos, dispatch concurrent reads. Don't scan sequentially when you can scan in parallel.

Do NOT proceed until you have at least 3 candidate insights with source references.

## Phase 3: Insight Extraction

For each candidate from Phase 2, apply the depth filter:

1. **What happened?** (1-2 sentences, factual)
2. **Why did it happen?** (first why)
3. **Why was that the case?** (second why, where depth lives)
4. **What's the structural principle?** (transferable lesson)
5. **What would surprise someone who hasn't built this?** (non-obvious part)

If questions 3-5 can't be answered, the insight is too shallow. Discard it.

Present the top 1-3 insights to the user with the depth filter answers. Get approval before drafting.

## Phase 4: Design

For the approved insight:

1. **Choose framework**: Apply `/copywriting` skill to select PAS/AIDA/BAB/4Ps/StoryBrand based on insight type.
2. **Outline structure**: Hook, body sections, closing statement.
3. **Identify the non-obvious moment**: Where in the post does the reader learn something they didn't expect?
4. **Identify the vulnerable moment**: Where do you admit something is hard, broken, or incomplete?

Present the outline to the user. Do NOT proceed to drafting without approval.

## Phase 5: Draft

Write the post following:
- The approved outline from Phase 4
- The chosen copywriting framework (applied invisibly)
- All rules from `.claude/rules/` (never-do, always-do, depth, voice)
- Platform formatting requirements (LinkedIn: 150-300 words; X: 280 chars)

Apply anti-AI constraints WHILE drafting, not after. Build the post clean from the start.

## Phase 6: Review

Run three review passes:

1. **Anti-AI Review**: Dispatch `anti-ai-reviewer` agent. If verdict is CONTAMINATED, fix all findings and re-run.
2. **Draft Review**: Dispatch `draft-reviewer` agent. If verdict is NEEDS WORK, fix all findings and re-run.
3. **Scoring Loop**: Run `/10-10-post` skill. If any criterion below 8, rewrite and re-score. Max 5 iterations.
4. **Humanizer Pass**: Run `/humanizer` skill. Apply the 3-pass system (detect, rewrite, final check).
5. **Final Verification**: Dispatch `post-verifier` agent. Must return VERIFIED.

Phase 6 is not complete until all five steps pass. If stuck after 3 full cycles, present the best version to the user with the remaining issues flagged.

## Phase 7: Completion

Deliver:
- **Final draft text** (ready to copy-paste)
- **Platform tag** (LinkedIn / X / Both)
- **Source reference** (repo, file path or commit SHA)
- **Content type** (bug story / architecture decision / platform quirk / agent lesson / performance story / rewrite story)

Log to memory:
```
[date] | [platform] | [content type] | [source repo] | [topic summary]
```

## Rules

- NEVER skip Phase 2 (Exploration). Insights without code exploration are shallow.
- NEVER skip Phase 3 (Insight Extraction). The depth filter is mandatory.
- NEVER draft before Phase 5. Design first.
- NEVER deliver before Phase 6 passes. Review is mandatory.
- If scope changes mid-pipeline (user wants a different angle), restart from Phase 3, not Phase 5.
- One post per pipeline run. Don't batch.
