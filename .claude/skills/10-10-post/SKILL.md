---
name: 10-10-post
description: |
  Iterative scoring loop for post drafts. Evaluate on 5 criteria, fix weak
  areas, re-score until all criteria hit 8+. Max 5 iterations.
  Triggers: "score this post", "10/10", "rate this draft", "is this good enough".
user-invocable: true
---

# 10/10 Post

Iterate on a post draft using structured evaluation until it scores 8+ on every criterion.

## The Loop

### Step 1: Evaluate

Score the draft on 5 criteria (each 1-10):

| Criterion | What to Assess | 8+ Means |
|-----------|---------------|----------|
| **Depth** | Is there a structural insight beyond the surface story? Does "why" go 2+ levels deep? Is there a broader principle? | Reader learns something about engineering, not just about what happened |
| **Specificity** | Real numbers from real code? Exact values, not rounded? Details that only come from reading the source? | Post could only be written by someone with access to this codebase |
| **Non-obvious** | Would this surprise someone who builds similar systems? Is there a "why behind the why"? | Reader's reaction is "I wouldn't have thought of that" |
| **Human voice** | Contractions present (5+)? Sentence lengths varied? Vulnerable moment? Parenthetical aside? Sounds like a person? | You'd believe a human typed this on their phone |
| **Anti-AI** | Zero em dashes? Zero AI vocabulary? No negative parallelisms? No synonym cycling? No closing question? Varied structure? | A skeptic scanning for AI tells finds nothing |

### Step 2: Identify Weaknesses

For each criterion scoring below 8:
- Name the specific element that's weak
- Quote the exact text that needs fixing
- Describe what "8+" looks like for this specific post

### Step 3: Fix

Make targeted fixes for each weakness:
- **Depth below 8**: Add the second "why." Add the structural principle. Connect to a broader engineering lesson.
- **Specificity below 8**: Go back to the source file. Find the exact number, the exact config value, the exact timing. Replace vague language with it.
- **Non-obvious below 8**: Ask: "What would someone assume about this situation? How is reality different?" Add that contrast.
- **Human voice below 8**: Add contractions. Break a long sentence into a short burst. Add a parenthetical aside. Add a moment of honesty.
- **Anti-AI below 8**: Scan for em dashes, AI vocabulary, negative parallelisms, synonym cycling. Fix every instance found.

Make 1-3 targeted changes per criterion. Don't overhaul everything at once.

### Step 4: Re-evaluate

Go back to Step 1. Score the fixed draft on all 5 criteria.

## Stop Condition

Stop when ALL 5 criteria score 8+.

## Escape Hatch

If after 5 iterations a criterion is stuck below 8:
- Flag which criterion is stuck and why
- Present the best version to the user with the limitation noted
- Suggest what additional source material might help (e.g., "if we had the actual latency numbers from the monitoring dashboard, Specificity would jump to 9")

## Output Format

### Per Iteration

```
=== Iteration [N] ===

| Criterion | Score | Notes |
|-----------|-------|-------|
| Depth | X/10 | [specific assessment] |
| Specificity | X/10 | [specific assessment] |
| Non-obvious | X/10 | [specific assessment] |
| Human voice | X/10 | [specific assessment] |
| Anti-AI | X/10 | [specific assessment] |

Weaknesses: [list what needs fixing]
Fixes applied: [list what was changed]
```

### Final

```
=== 10/10 Post Result ===
Iterations: [N]
Final scores: Depth [X] | Specificity [X] | Non-obvious [X] | Human [X] | Anti-AI [X]
Status: ALL 8+ | STUCK ON [criterion]
```

## Rules

- Be honest in scoring. Inflated scores defeat the purpose.
- A 7 is not an 8. Close doesn't count.
- Score against the rules in `.claude/rules/`, not against your own preferences.
- One fix at a time per criterion. Don't rewrite the entire post each iteration.
- Max 5 iterations. If not 10/10 by then, ship the best version with notes.
