---
name: git-summary
description: Generates a concise summary of recent git activity — commits, changed files, and a plain-English overview of what changed and why. Useful for standups, PR descriptions, or catching up after time away.
---

# Git Summary Skill

Produces a clear, human-readable summary of recent git activity in the current repository.

## When to use

Invoke this skill when the user asks things like:
- "What changed recently?"
- "Summarize the last N commits"
- "What did we work on this week?"
- "Give me a standup summary"

## Workflow

### Step 1: Gather git history

```
Run: git log --oneline -20
Run: git diff HEAD~N..HEAD --stat   (where N = number of commits to summarize)
```

### Step 2: Inspect notable changes

For files with significant diffs, read the actual diff:

```
Run: git show <commit> --stat
Run: git diff HEAD~N..HEAD -- <important-file>
```

### Step 3: Produce the summary

Structure the output as:

1. **Overview** — 1-2 sentences: what was the theme of recent work?
2. **Commits** — bullet list of commit messages with author and date
3. **Files changed** — group by area (e.g., frontend, backend, config)
4. **Notable changes** — highlight anything non-obvious (refactors, breaking changes, new dependencies)
5. **Next steps** — if discernible from commit messages or TODO comments

## Output format

```
## Git Summary — last N commits

**Overview**: [plain English summary]

**Commits**
- abc1234 — [message] (Author, date)
- ...

**Files changed**
- src/: [brief description]
- tests/: [brief description]

**Notable**: [anything worth calling out]
```

## Tips

- Keep the overview jargon-free — write for someone who hasn't seen the code
- If commits reference tickets (e.g., JIRA-123), mention them
- Flag any commits with "fix", "hotfix", or "revert" as potentially important
- If the range is large (>20 commits), summarize by week or feature area instead of per-commit
