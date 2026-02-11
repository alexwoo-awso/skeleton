# Skeleton Setup Guide

> **Purpose:** Bootstrap a new project with the Claude Code documentation system
> **Usage:** Copy the contents of this directory into a new project root

---

## What's Included

```
.skeleton/
├── .claude/
│   └── instructions.md      # Session-level instructions for Claude Code
├── .skills/
│   └── skill-creator/       # Universal skill for creating new skills
│       ├── SKILL.md
│       ├── license.txt
│       └── scripts/
│           ├── init_skill.py
│           ├── package_skill.py
│           └── quick_validate.py
├── CLAUDE.md                 # Project-level instructions (customize heavily)
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
├── .skills/
│   └── skill-creator/
├── CLAUDE.md
├── TODO.md
├── DONE.md
└── LESSONS_LEARNED.md
```

### 2. Customize CLAUDE.md

This is the most important file. Fill in:
- Project overview and architecture
- Development commands (setup, run, test, lint)
- Key integration points
- Architecture deep dive (database, config, auth, etc.)
- Default credentials
- Security notes

### 3. Update TODO.md

Add your initial critical rules and work items. Rules accumulate as you discover recurring bugs.

### 4. Update .claude/instructions.md

Add project-specific emergency fixes and quick-reference patterns to the bottom sections.

### 5. Start Working

The system is self-maintaining: Claude Code reads these files at session start and updates them as work progresses. `DONE.md` and `LESSONS_LEARNED.md` will grow organically.

## The System

### How It Works

1. **`CLAUDE.md`** - Read by Claude Code automatically. Contains project architecture, commands, and rules.
2. **`.claude/instructions.md`** - Session instructions. Tells Claude to read/update the other files.
3. **`TODO.md`** - Living checklist of bugs, rules, and work items. Condensed and actionable.
4. **`DONE.md`** - Append-only log. New entries at top. Provides implementation history.
5. **`LESSONS_LEARNED.md`** - Knowledge base of failure modes. Prevents repeating mistakes across sessions.
6. **`.skills/`** - Modular skill packages. Each skill has a `SKILL.md` and optional resources.

### Why It Works

- **Cross-session memory**: Claude Code sessions are stateless. These files persist knowledge.
- **Bug prevention**: Critical rules in `TODO.md` prevent recurring bugs before they happen.
- **Pattern library**: `LESSONS_LEARNED.md` documents invisible failures with code examples.
- **Audit trail**: `DONE.md` tracks what was done, why, and what files changed.
- **Extensibility**: `.skills/` adds domain-specific capabilities without bloating main docs.

### Principles

- **KISS**: Only add what's needed. Templates have placeholders, not boilerplate.
- **DRY**: Common patterns go in shared files. Rules reference lessons, not duplicate them.
- **Progressive disclosure**: Start minimal, grow as the project grows.

## Delete This File

Once you've set up your project, delete `SETUP.md`. It's only needed during initial setup.
