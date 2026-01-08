# Cursor Efficiency Guide

## Rules
- Define project-specific rules in `.cursor/rules/`
- Use glob patterns to apply rules by file type
- Keep rules modular and focused (one concern per file)
- Reference existing patterns from codebase
- Can refer rule file in another rule file

## Planning
- Draft plan with free tools (GPT/Gemini) first
- Let Cursor refine the approach
- Break into phases: design → implement → test
- Validate plan before coding starts

## Context Management
- Attach only relevant files, not folders
- Use screenshots for UI-specific tasks
- Link API docs/URLs when needed
- Remove stale context between tasks, use new agent

## Browser Integration
- Use browser tab for live UI testing
- Inspect elements, tweak CSS, apply to code
- Take screenshots to compare before/after

## Agent Modes

### Single Agent
- Works on local copy directly
- Review changes incrementally
- Undo/redo as needed

### Multiple Agents
- Use git worktrees for parallel agents
- Apply individual agent's change, review, follow-up, undo-apply
- Assign different models by task complexity
- Compare outputs across models for same task
- Disabled in multiple root workspaces

## Token Optimization
| Task Type | Recommended Approach |
|-----------|---------------------|
| Simple CSS/refactor | Cheaper models or autocomplete |
| Complex logic | Premium models |
| Boilerplate | Free tools (GPT/Gemini) |

### Best Practices
- Start new chat when context grows large
- Be specific in prompts—avoid vague requests
- Use `@file` references over pasting code
- Ask for diffs, not full file rewrites
- Batch related changes in single request
- Use autocomplete for repetitive edits

## Composer vs Chat
- **Composer**: Multi-file changes, refactoring across codebase
- **Chat**: Single-file edits, Q&A, debugging
- Use Composer for coordinated changes, Chat for focused edits

## Codebase Search
- Use semantic search (`@codebase`) for "how does X work?" questions
- Search specific directories to narrow scope
- Review search results before attaching to context

## References & Context
- `@codebase` for semantic understanding
- `@docs` for documentation lookup
- `@web` for external research
- `@folder` sparingly—prefer specific files
- Use `.cursorignore` to exclude node_modules, build outputs, etc.

## Prompt Engineering
- Structure: Goal → Context → Constraints → Expected output
- One task per prompt for clarity
- Iterate: refine based on output, don't rewrite entire prompt
- Use examples when pattern matching is needed

## Workflow Tips
- Review changes before accepting (especially multi-file)
- Test incrementally—don't wait for "complete" solution
- Use git commits between major changes for easy rollback
- Manual edits for trivial fixes save tokens
- Let Cursor generate boilerplate, you handle business logic
