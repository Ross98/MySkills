---
name: handoff
description: Use when the user says "handoff", asks to save the current work state for a later session, or requests a resumable task summary in handoff.md.
---

# Handoff

Save a self-contained snapshot that lets a fresh Codex session continue the current task without rereading the conversation.

## Workflow

1. Treat the workspace root as the Git top-level directory. If no Git repository exists, use the current working directory.
2. Review the conversation, current plan, changed files, test results, and relevant tool output. Inspect repository state when needed.
3. Build the complete snapshot before writing.
4. Create or fully replace `<workspace-root>/handoff.md`. Never merely print the summary in chat. Use a safe file-editing method and do not modify unrelated files.
5. Confirm the absolute saved path and briefly name the next action.

## Required document shape

```markdown
# Task Handoff

## Goal
[Current objective and acceptance criteria]

## Completed
[Verified work already done]

## Current state
[What works, what is in progress, and exact blocker if any]

## Decisions
[Important decisions and reasons]

## Files
[Created or modified paths and what changed]

## Verification
[Commands run and observed results; say "Not run" when applicable]

## Next steps
1. [First concrete action]

## Continuation notes
[Exact commands, errors, risks, assumptions, and context a fresh session needs]
```

## Content rules

- Overwrite the previous snapshot; do not append history.
- Record verified facts. Clearly label assumptions and unverified claims.
- Keep exact file paths, commands, identifiers, and error messages verbatim.
- Include unresolved user requirements and pending decisions.
- Never include passwords, API keys, tokens, private keys, or unnecessary personal data.
- Prefer concise operational detail over conversation narrative.
