# agents

Portable instructions for AI coding agents. Tool-agnostic markdown, one file per
concern.

These are the source of truth. Installing them into a specific tool is a separate
concern, handled by my dotfiles rather than here.

## Files

| File | Purpose |
| --- | --- |
| [writing-style.md](writing-style.md) | Prose register for chat and for written artifacts: Jira comments, PRs, commits, docs. |

## Conventions

- Plain markdown. No vendor-specific frontmatter or syntax.
- One concern per file. Each file stands alone and doesn't overlap the others,
  so they can be concatenated in any combination.
- Nothing work-specific, nothing secret. Project context belongs in that
  project's own `AGENTS.md`.

## Using these

Point a tool at whichever files apply. Global instruction locations differ by
tool and haven't converged:

| Tool | Global location |
| --- | --- |
| Copilot CLI | `~/.copilot/copilot-instructions.md` |
| Claude Code | `~/.claude/CLAUDE.md` |
| Codex | `~/.codex/AGENTS.md` |
| Cursor | User Rules, in app settings |

For project-level instructions, `AGENTS.md` at the repo root is read by most
tools directly.
