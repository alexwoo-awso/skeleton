# Skeleton Setup Guide

> **Purpose:** Bootstrap a new project with the AI agent documentation system
> **Usage:** Copy the contents of this directory into a new project root

---

## What's Included

```
skeleton/
├── .claude/
│   └── instructions.md      # Session-level instructions for Claude Code
├── .codex/
│   └── config.toml          # Project-level config for Codex CLI
├── .skills/
│   └── skill-creator/       # Universal skill for creating new skills
│       ├── SKILL.md
│       ├── license.txt
│       └── scripts/
│           ├── init_skill.py
│           ├── package_skill.py
│           └── quick_validate.py
├── AGENTS.md                 # Universal AI agent instructions (open standard)
├── CLAUDE.md                 # Claude Code specific instructions
├── TODO.md                   # Active work items and critical rules
├── DONE.md                   # Completed work log
├── LESSONS_LEARNED.md        # Patterns and anti-patterns knowledge base
└── SETUP.md                  # This file (delete after setup)
```

## How to Use

### 1. Copy to New Project

Copy everything except `SETUP.md` into your project root:

```
your-project/
├── .claude/
│   └── instructions.md
├── .codex/
│   └── config.toml
├── .skills/
│   └── skill-creator/
├── AGENTS.md
├── CLAUDE.md
├── TODO.md
├── DONE.md
└── LESSONS_LEARNED.md
```

### 2. Customize Your Instruction Files

**`AGENTS.md`** (for Codex CLI, OpenClaw, Cursor, Aider, and other AGENTS.md-compatible tools):
- Project overview and architecture
- Development commands (setup, run, test, lint)
- Key integration points
- Critical development rules

**`CLAUDE.md`** (for Claude Code):
- Same sections as AGENTS.md, tailored for Claude Code conventions
- References `.claude/instructions.md` for session-level instructions

Both files share the same structure. Fill in the same project information in each.

### 3. Configure Your Tool

**Claude Code:**
- Edit `.claude/instructions.md` for session-specific instructions
- Add project-specific emergency fixes and quick-reference patterns

**Codex CLI:**
- Edit `.codex/config.toml` to set your preferred model, approval policy, and sandbox mode
- All options are commented out by default -- uncomment what you need

**OpenClaw / Other AGENTS.md tools:**
- `AGENTS.md` is all you need -- these tools read it automatically
- Tool-specific config lives in each tool's own config location

### 4. Update TODO.md

Add your initial critical rules and work items. Rules accumulate as you discover recurring bugs.

### 5. Start Working

The system is self-maintaining: your AI agent reads these files at session start and updates them as work progresses. `DONE.md` and `LESSONS_LEARNED.md` will grow organically.

## The System

### How It Works

1. **`AGENTS.md`** - Read by Codex CLI, OpenClaw, Cursor, Aider, and 20+ other tools. Contains project architecture, commands, and rules.
2. **`CLAUDE.md`** - Read by Claude Code automatically. Same content, Claude Code specific conventions.
3. **`.claude/instructions.md`** - Claude Code session instructions. Tells Claude to read/update the doc files.
4. **`.codex/config.toml`** - Codex CLI project configuration. Model, approval policy, sandbox settings.
5. **`TODO.md`** - Living checklist of bugs, rules, and work items. Condensed and actionable.
6. **`DONE.md`** - Append-only log. New entries at top. Provides implementation history.
7. **`LESSONS_LEARNED.md`** - Knowledge base of failure modes. Prevents repeating mistakes across sessions.
8. **`.skills/`** - Modular skill packages. Each skill has a `SKILL.md` and optional resources.

### Why It Works

- **Cross-session memory**: AI agent sessions are stateless. These files persist knowledge.
- **Bug prevention**: Critical rules in `TODO.md` prevent recurring bugs before they happen.
- **Pattern library**: `LESSONS_LEARNED.md` documents invisible failures with code examples.
- **Audit trail**: `DONE.md` tracks what was done, why, and what files changed.
- **Extensibility**: `.skills/` adds domain-specific capabilities without bloating main docs.

### Principles

- **KISS**: Only add what's needed. Templates have placeholders, not boilerplate.
- **DRY**: Common patterns go in shared files. Rules reference lessons, not duplicate them.
- **Progressive disclosure**: Start minimal, grow as the project grows.

## Trim for Your Tool

If you only use one AI tool, you can remove the files you don't need:

| You use | Keep | Can remove |
|---------|------|------------|
| **Claude Code only** | `CLAUDE.md`, `.claude/` | `AGENTS.md`, `.codex/` |
| **Codex CLI only** | `AGENTS.md`, `.codex/` | `CLAUDE.md`, `.claude/` |
| **OpenClaw / Cursor / Aider / etc.** | `AGENTS.md` | `CLAUDE.md`, `.claude/`, `.codex/` |
| **Multiple tools** | All files | Nothing -- they coexist without conflict |

## Delete This File

Once you've set up your project, delete `SETUP.md`. It's only needed during initial setup.
