# agents

Instructions and skills for AI coding agents.

Two kinds of thing live here, under different rules.

**Instructions** are portable, tool-agnostic markdown — one file per concern, at
the repo root.

**Skills** are executable procedures for a specific tool, under `skills/`. They
carry vendor frontmatter and can span several files. They are not portable, and
that's the point.

These are the source of truth. Installing them into a specific tool is a separate
concern, handled by my dotfiles rather than here.

## Instructions

| File | Purpose |
| --- | --- |
| [writing-style.md](writing-style.md) | Prose register for chat and for written artifacts: Jira comments, PRs, commits, docs. |

### Conventions

- Plain markdown. No vendor-specific frontmatter or syntax.
- One concern per file. Each file stands alone and doesn't overlap the others,
  so they can be concatenated in any combination.
- Nothing work-specific, nothing secret. Project context belongs in that
  project's own `AGENTS.md`.

### Using these

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

## Skills

| Skill | Tool | Purpose |
| --- | --- | --- |
| [start-journal](skills/start-journal/) | Claude Code | Build a START (STAR + Tomorrow) journal entry in the Obsidian vault, through context capture, per-stage rinse, and consolidation. |
| [jira](skills/jira/) | Claude Code | Work with Jira Cloud through the official Atlassian CLI (`acli`): authentication, JQL search, and work item operations. |

### Conventions

- One directory per skill. `SKILL.md` is the entry point; longer reference
  material goes in `reference/`.
- Vendor frontmatter is expected. These target a named tool.
- A skill may hardcode paths on my machine. Portability is not a goal here —
  if it needs to run elsewhere, that's a fork, not a parameter.
- Still nothing secret, and nothing work-specific. Examples inside a skill are
  invented. Real content stays in the vault or repo the skill operates on.
- No snapshots of what a skill operates on — no inventories, vocabularies, file
  listings or quoted prose lifted from the target. They go stale, and this repo
  is public. A skill needing that detail reads it at runtime.

### Installing

Symlink into the tool's skill directory rather than copying, so the repo stays
the only copy:

```sh
ln -s ~/Documents/agents/skills/start-journal \
      /path/to/project/.claude/skills/start-journal
```

Claude Code reads project skills from `<project>/.claude/skills/` and user-wide
skills from `~/.claude/skills/`. Project-scoped is the default here — a skill
that operates on one vault or repo shouldn't load everywhere else.
