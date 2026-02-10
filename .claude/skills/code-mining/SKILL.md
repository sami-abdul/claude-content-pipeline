---
name: code-mining
description: |
  Scan repos for post-worthy code patterns, architectural decisions, bugs,
  and implementation insights. Produces structured insight briefs.
  Triggers: "mine code", "scan repos", "find insights", "what have we built".
user-invocable: true
---

# Code Mining

Scan project repositories for post-worthy insights. Uses git history, source files, documented bugs, and constants to find material that's grounded in real code.

## MANDATORY: Follow This Runbook Exactly

Execute all 3 steps in order. Do not skip steps or substitute your own approach.

## Step 1: Map Territory

Scan target repos. Default: scan all three product lines in parallel.

**For each repo, run:**
```bash
git log --oneline -30    # Recent commits
git log --grep="fix" --oneline -15    # Bug fixes
git log --grep="refactor" --oneline -10    # Structural changes
git branch -a --sort=-committerdate | head -20    # Active branches
```

**Priority files to read:**
```
# Documented bugs (richest source, scan first)
polymaxr/polymaxr-lite/.cursor/rules/common-bugs.mdc
polymaxr/polymaxr-mm-bot/.cursor/rules/common-bugs.mdc

# Constants with reasons
polymaxr/polymaxr-lite-v2/risk/src/circuit_breakers.rs
polymaxr/polymaxr-lite-v2/risk/src/timing_filter.rs
polymaxr/polymaxr-lite-v2/strategy/src/endgame.rs

# Infrastructure decisions
megafi/server/src/common/contracts/contracts.service.ts
megafi/server/src/common/price/price.service.ts
megafi/server/src/common/blockchain/gas.service.ts

# Agent deployment lessons
ai60/agentic-org/docs/AGENT-PATTERNS.md
ai60/agentic-org/agents/common/sam-upwork/deploy.sh
```

Pass criteria:
- At least 2 repos scanned successfully
- At least 30 commits visible across repos
- At least 2 priority files read

## Step 2: Trace Paths

For the most interesting findings from Step 1:

1. **Read the actual source files** touched by interesting commits. Don't stop at the commit message.
2. **Look for constants with comments** explaining "why." The number isn't the insight. The reason behind the number is.
3. **Look for edge cases in conditionals.** `if balance < threshold` tells you something went wrong at that threshold.
4. **Look for error handling patterns.** Retry logic, fallback chains, circuit breakers all encode production lessons.
5. **Look for TODO/FIXME/HACK comments.** These are honest admissions of known limitations.
6. **Cross-reference**: Did the same pattern or fix appear in multiple repos?

For each finding, note:
- Exact file path and line numbers
- The specific code or commit
- What the code actually does (not what you think it does)

Pass criteria:
- At least 5 findings with exact source references
- At least 2 findings that go beyond the commit message (required reading the actual code)

## Step 3: Produce Insight Brief

For each finding that passes the depth filter, produce:

```
## Insight: [title]
Source: [repo], [file:line or commit SHA]
Category: [bug story | architecture decision | platform quirk | agent lesson | performance story | rewrite story]

What happened: [1-2 sentences, factual]
First why: [why it happened]
Second why: [why that was the case]
Structural principle: [the transferable lesson]
Non-obvious part: [what would surprise someone]
Post angle: [how to frame for AI builders, no org names]
Depth score: [1-10]
```

Only include insights with depth score 7+.

**Final output:**
```
Code Mining Brief
Date: [today]
Repos scanned: [list]
Insights found: [count]

[Insight briefs, ranked by depth score]

Recommended for next post: [which insight and why]
```

Pass criteria:
- At least 3 insights with depth score 7+
- Each insight has all fields filled (no blanks)
- Recommendation is specific and justified

## Categories to Prioritize

1. **Production bugs with lessons**: Common-bugs.mdc entries, fix commits with non-obvious root causes
2. **Architecture decisions with tradeoffs**: Constants that encode hard-won knowledge
3. **Platform quirks nobody talks about**: API behaviors, precision requirements, settlement timing
4. **Cross-repo patterns**: Same lesson applied differently across products
5. **Rewrites and pivots**: v2 repos, branch history showing evolution
6. **Agent deployment lessons**: Context budgets, skill invocation, memory sync patterns

## Fallback Behavior

- If a repo has no recent activity, note it and focus on others.
- If common-bugs.mdc doesn't exist in a repo, use git log --grep="fix" as substitute.
- If fewer than 3 insights reach depth score 7+, lower threshold to 6+ and flag them as "needs depth work."
