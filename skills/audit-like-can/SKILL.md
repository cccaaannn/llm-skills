---
name: audit-like-can
description: Strict audit of the whole repo (or the given paths or globs) against Can's laws. Runs review-like-can on every line in scope, marks every violation, then adds a summary. Needs a clean working tree so every marker shows in git and is revertable.
disable-model-invocation: true
argument-hint: "[path or glob ...]"
license: MIT
metadata:
  source: https://github.com/cccaaannn/llm-skills skills/audit-like-can
---

1. Run `git status --porcelain`. If it prints anything, stop: tell the user the working tree must be clean (commit or stash first) and do nothing else.
2. Call the Skill tool with "review-like-can" and follow it exactly, with one change to its scope: review every line of every tracked file, as it is now, in these paths or globs: `$ARGUMENTS` (the whole repo when this is empty). Read "changed line" and "changed file" in it as "line in scope" and "file in scope".
3. After its report and verdict, add a summary: the number of violations per law in law order, then the 10 files with the most violations.
