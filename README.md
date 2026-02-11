# Skeleton

A project scaffolding template that bootstraps new repositories with a **Claude Code documentation system** -- persistent cross-session memory, structured task tracking, and extensible skill packages.

## Why

Claude Code sessions are stateless. Every new session starts from zero, re-discovering architecture, repeating past mistakes, and losing context from previous work. This skeleton solves that with a lightweight file-based system that gives Claude Code persistent memory across sessions.

## What's Included

```
skeleton/
├── .claude/
│   └── instructions.md          # Session-level Claude Code instructions
├── .skills/
│   └── skill-creator/           # Built-in skill for creating new skills
│       ├── SKILL.md
│       ├── license.txt
│       └── scripts/
│           ├── init_skill.py
│           ├── package_skill.py
│           └── quick_validate.py
├── CLAUDE.md                    # Project-level instructions (customize per project)
├── TODO.md                      # Active bugs, rules, and work items
├── DONE.md                      # Completed work log (chronological)
├── LESSONS_LEARNED.md           # Patterns and anti-patterns knowledge base
└── SETUP.md                     # Setup guide (delete after bootstrapping)
```

### File Purposes

| File | Role | Updated When |
|------|------|-------------|
| `CLAUDE.md` | Project architecture, commands, rules. Read automatically by Claude Code. | Project setup, architecture changes |
| `.claude/instructions.md` | Session instructions. Tells Claude to read/update the other files. | Rarely -- mostly stable |
| `TODO.md` | Living checklist. Condensed and actionable. | Adding tasks, discovering issues |
| `DONE.md` | Append-only log. Newest entries at the top. | Completing work |
| `LESSONS_LEARNED.md` | Knowledge base of failure modes with code examples. | Discovering invisible bugs |
| `.skills/` | Modular skill packages that extend Claude Code capabilities. | Adding new skills |

## Quick Start

### 1. Create a new repo from this template

Click **"Use this template"** on GitHub, or clone and copy manually:

```bash
git clone https://github.com/alexwoo-awso/skeleton.git my-project
cd my-project
rm -rf .git
git init
```

### 2. Customize `CLAUDE.md`

This is the most important file. Fill in:

- Project name and description
- Architecture overview
- Development commands (setup, run, test, lint)
- Key integration points
- Critical rules specific to your project

### 3. Update `TODO.md`

Add your initial work items and any project-specific rules.

### 4. Update `.claude/instructions.md`

Add project-specific emergency fixes and quick-reference patterns.

### 5. Delete `SETUP.md`

It's only needed during initial setup.

### 6. Start working

The system is self-maintaining. Claude Code reads these files at session start and updates them as work progresses. `DONE.md` and `LESSONS_LEARNED.md` grow organically.

## How It Works

```
Session Start                    During Work                     Session End
─────────────                    ───────────                     ───────────
Read CLAUDE.md          ──>      Follow rules from TODO.md  ──> Update TODO.md
Read TODO.md            ──>      Check LESSONS_LEARNED.md   ──> Append to DONE.md
Scan LESSONS_LEARNED.md ──>      Use .skills/ as needed     ──> Update LESSONS_LEARNED.md
```

**Cross-session memory**: Files persist knowledge between stateless Claude Code sessions.

**Bug prevention**: Critical rules in `TODO.md` catch recurring bugs before they happen.

**Pattern library**: `LESSONS_LEARNED.md` documents invisible failures with code examples.

**Audit trail**: `DONE.md` tracks what was done, why, and which files changed.

**Extensibility**: `.skills/` adds domain-specific capabilities without bloating the main docs.

## Skills System

Skills are modular, self-contained packages that extend Claude Code with specialized knowledge, workflows, and tools. Each skill lives in `.skills/<skill-name>/` and contains a `SKILL.md` plus optional scripts, references, and assets.

The included **skill-creator** skill can bootstrap new skills:

```bash
python .skills/skill-creator/scripts/init_skill.py my-skill --path .skills --resources scripts,references
```

See `.skills/skill-creator/SKILL.md` for full documentation on creating skills.

## Design Principles

- **KISS** -- Only add what's needed. Templates have placeholders, not boilerplate.
- **DRY** -- Common patterns go in shared files. Rules reference lessons, not duplicate them.
- **Progressive disclosure** -- Start minimal, grow as the project grows.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

The skill-creator component (`.skills/skill-creator/`) includes its own Apache 2.0 license.
