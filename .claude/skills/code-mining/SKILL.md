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

Scan target repos. Default: scan all three product lines in parallel. Scan in tier order: docs first, then source files, then git log last.

**Tier 1 - Doc files first (WHY things exist):**

Doc files explain WHY decisions were made. They contain design rationale, tradeoff reasoning, and evolution context that commits alone cannot provide. Read these first to build context before scanning code.

```
# Project-level context
**/CLAUDE.md
**/README.md

# Architecture and design specs
**/.claude/specs/*.md
**/ARCHITECTURE.md
**/DESIGN.md

# Implementation plans and knowledge transfer
**/docs/KNOWLEDGE_TRANSFER.md
**/docs/*PLAN*.md
**/docs/POST_RUN_ANALYSIS.md
```

If no doc files are found in a repo, note it and move to Tier 2. A repo with no docs is itself an insight (documentation debt).

**Tier 2 - Gold mine source files (WHAT happened):**
```
# Documented bugs (richest source for failure stories)
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

**Tier 3 - Git log for timeline context (not primary insight source):**

Use git log to understand WHEN things changed and the order of evolution, not as the primary source of insight. Cross-reference commits with doc files to find the reasoning behind changes.

```bash
git log --oneline -30    # Recent commits
git log --grep="fix" --oneline -15    # Bug fixes
git log --grep="refactor" --oneline -10    # Structural changes
git branch -a --sort=-committerdate | head -20    # Active branches
```

Pass criteria:
- At least 2 repos scanned successfully
- At least 30 commits visible across repos
- At least 2 gold mine source files read
- At least 3 doc files read across repos
- At least 1 doc file that explains design rationale (not just a README listing commands)

## Step 2: Trace Paths

For the most interesting findings from Step 1:

1. **Read the actual source files** touched by interesting commits. Don't stop at the commit message.
2. **Look for constants with comments** explaining "why." The number isn't the insight. The reason behind the number is.
3. **Look for edge cases in conditionals.** `if balance < threshold` tells you something went wrong at that threshold.
4. **Look for error handling patterns.** Retry logic, fallback chains, circuit breakers all encode production lessons.
5. **Look for TODO/FIXME/HACK comments.** These are honest admissions of known limitations.
6. **Cross-reference**: Did the same pattern or fix appear in multiple repos?
7. **Follow references from docs to code.** If a doc mentions a specific component, threshold, or design decision, read the actual implementation file. The insight lives in the gap between what the doc planned and what the code actually does.
8. **Look for design rationale in prose.** Architecture docs, knowledge transfer docs, and implementation plans contain tradeoff reasoning, rejected alternatives, and evolution context that source files don't capture.

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

Universal principle: [the engineering principle anyone building software would recognize. No internal code references. This is the LEAD.]
What I encountered: [1-2 sentences, factual, in terms any engineer would understand]
First why: [why it happened]
Second why: [why that was the case]
Non-obvious part: [what would surprise someone who builds similar systems]
External hook: [one line a non-technical person could understand]
Post angle: [for someone who will NEVER see the codebase. Must pass Code Leak Check.]
Depth score: [1-10]
```

### Code Leak Check

Before finalizing any insight brief, verify the Post angle:
- Contains file names? Reframe.
- Contains function names? Reframe.
- Contains framework names (NestJS, Tokio, etc.)? Reframe.
- Contains internal project structure? Reframe.
- References git commands or branch names? Reframe.
- Could someone who has never seen the codebase understand it? If not, reframe.

Post angle must describe engineering BEHAVIOR, not engineering ARTIFACTS.

BAD: "Fill detection across 4 files broke because of async settlement"
GOOD: "When your system trusts an API that hasn't settled yet, absence looks like cancellation"

BAD: "Circuit breaker opens at 50% in contracts.service.ts"
GOOD: "Why we trip the breaker at half-failure, not full-failure"

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
- Every Post angle passes the Code Leak Check
- Every insight has an External hook a non-engineer could parse
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
