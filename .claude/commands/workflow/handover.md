# Handover

Generate a comprehensive handover document for the current session so the next Claude instance can continue seamlessly.

## Purpose

When ending a session or switching contexts, create a handover document that captures everything needed for continuity. This prevents the "AI amnesia" problem where context is lost between sessions.

## Output Format

Create/update `HANDOVER.md` in the project root with:

```markdown
# Session Handover

**Generated:** [timestamp]
**Last Working On:** [current task/feature]

## Context Summary
[2-3 sentence overview of what this project is and current state]

## Current Status

### Completed This Session
- [x] Task 1
- [x] Task 2

### In Progress
- [ ] Task currently being worked on
  - Current state: [where we left off]
  - Next step: [immediate next action]

### Blocked/Pending
- [ ] Task waiting on [dependency/decision]

## Key Decisions Made
1. **[Decision]** — [Why we chose this approach]
2. **[Decision]** — [Tradeoffs considered]

## Code Changes
- `path/to/file.ts` — [what changed and why]
- `path/to/other.ts` — [what changed and why]

## Things That Didn't Work
- Tried [approach] but [why it failed]
- [Approach] seemed promising but [issue discovered]

## Environment Notes
- [Any setup, config, or environment details]
- [Commands that need to be run]

## For Next Session
1. [First priority task]
2. [Second priority task]
3. [Nice-to-have if time]

## Open Questions
- [Unresolved question needing human input]
- [Technical uncertainty to investigate]
```

## Instructions

1. Review the conversation history
2. Check `git diff` and `git log` for recent changes
3. Identify incomplete work and blockers
4. Document decisions and their rationale
5. Note anything that didn't work (saves time later)
6. Prioritize next steps clearly

## When to Use

- End of work session
- Before `/clear` or `/compact`
- Switching to different task
- Before closing Claude Code
- When context is getting long

## Pro Tip

Combine with `/compact` for optimal workflow:
1. Run `/handover` to save context
2. Run `/compact` to reduce token usage
3. Next session: "Read HANDOVER.md and continue"
