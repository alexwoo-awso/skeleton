# Skeleton

A universal AI agent scaffolding template that bootstraps new repositories with persistent cross-session memory, structured task tracking, and extensible skill packages -- compatible with **Claude Code**, **OpenAI Codex CLI**, **OpenClaw**, and any tool that supports the **AGENTS.md** open standard.

## Why

AI coding agent sessions are stateless. Every new session starts from zero, re-discovering architecture, repeating past mistakes, and losing context from previous work. This skeleton solves that with a lightweight file-based system that gives any AI agent persistent memory across sessions.

## Supported Tools

| Tool | Reads | Config |
|------|-------|--------|
| **Claude Code** | `CLAUDE.md` | `.claude/instructions.md` |
| **OpenAI Codex CLI** | `AGENTS.md` | `.codex/config.toml` |
| **OpenClaw** | `AGENTS.md` | Global config (user home) |
| **Cursor, Aider, Jules, Gemini CLI, Windsurf, Devin, etc.** | `AGENTS.md` | Varies by tool |

Both `CLAUDE.md` and `AGENTS.md` are included and self-contained. Each is tailored to its tool ecosystem while sharing the same structural template.

## What's Included

```
skeleton/
├── .claude/
│   └── instructions.md          # Claude Code session instructions
├── .codex/
│   └── config.toml              # Codex CLI project config (sample)
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
├── .skills/
│   └── skill-creator/           # Built-in skill for creating new skills
│       ├── SKILL.md
│       ├── license.txt
│       └── scripts/
│           ├── init_skill.py
│           ├── package_skill.py
│           └── quick_validate.py
├── AGENTS.md                    # Universal AI agent instructions (open standard)
├── CLAUDE.md                    # Claude Code specific instructions
├── TODO.md                      # Active bugs, rules, and work items
├── DONE.md                      # Completed work log (chronological)
├── LESSONS_LEARNED.md           # Patterns and anti-patterns knowledge base
├── SETUP.md                     # Setup guide (delete after bootstrapping)
├── README.md                    # Project documentation
├── CONTRIBUTING.md              # Contribution guidelines
├── CODE_OF_CONDUCT.md           # Code of conduct
├── SECURITY.md                  # Security policy
├── LICENSE                      # MIT license
└── .gitignore
```

### File Purposes

| File | Role | Updated When |
|------|------|-------------|
| `AGENTS.md` | Universal agent instructions. Read by Codex, OpenClaw, Cursor, Aider, and 20+ other tools. | Project setup, architecture changes |
| `CLAUDE.md` | Claude Code specific instructions. Read automatically by Claude Code. | Project setup, architecture changes |
| `.claude/instructions.md` | Claude Code session instructions. Tells Claude to read/update the doc files. | Rarely -- mostly stable |
| `.codex/config.toml` | Codex CLI project configuration (model, approval policy, sandbox). | Per-project Codex setup |
| `TODO.md` | Living checklist. Condensed and actionable. | Adding tasks, discovering issues |
| `DONE.md` | Append-only log. Newest entries at the top. | Completing work |
| `LESSONS_LEARNED.md` | Knowledge base of failure modes with code examples. | Discovering invisible bugs |
| `.skills/` | Modular skill packages that extend agent capabilities. | Adding new skills |

## Quick Start

### 1. Create a new repo from this template

Click **"Use this template"** on GitHub, or clone and copy manually:

```bash
git clone https://github.com/alexwoo-awso/skeleton.git my-project
cd my-project
rm -rf .git
git init
```

### 2. Customize the instruction files

**For Claude Code** -- edit `CLAUDE.md`:
- Project name and description
- Architecture overview
- Development commands (setup, run, test, lint)
- Key integration points
- Critical rules specific to your project

**For Codex / OpenClaw / other tools** -- edit `AGENTS.md`:
- Same sections as above, using tool-agnostic language
- Both files share the same structure and can be kept in sync

**For Codex CLI** -- edit `.codex/config.toml`:
- Uncomment and set your preferred model, approval policy, and sandbox mode

### 3. Update `TODO.md`

Add your initial work items and any project-specific rules.

### 4. Trim for your tool (optional)

If you only use one tool, you can remove the files you don't need:
- **Claude Code only:** Remove `AGENTS.md` and `.codex/`
- **Codex / OpenClaw only:** Remove `CLAUDE.md` and `.claude/`
- **Multiple tools:** Keep both -- they coexist without conflict

### 5. Delete `SETUP.md`

It's only needed during initial setup.

### 6. Start working

The system is self-maintaining. Your AI agent reads these files at session start and updates them as work progresses. `DONE.md` and `LESSONS_LEARNED.md` grow organically.

## How It Works

```
Session Start                    During Work                     Session End
─────────────                    ───────────                     ───────────
Read instruction file   ──>      Follow rules from TODO.md  ──> Update TODO.md
Read TODO.md            ──>      Check LESSONS_LEARNED.md   ──> Append to DONE.md
Scan LESSONS_LEARNED.md ──>      Use .skills/ as needed     ──> Update LESSONS_LEARNED.md
```

**Cross-session memory**: Files persist knowledge between stateless agent sessions.

**Bug prevention**: Critical rules in `TODO.md` catch recurring bugs before they happen.

**Pattern library**: `LESSONS_LEARNED.md` documents invisible failures with code examples.

**Audit trail**: `DONE.md` tracks what was done, why, and which files changed.

**Extensibility**: `.skills/` adds domain-specific capabilities without bloating the main docs.

## Skills System

Skills are modular, self-contained packages that extend your AI agent with specialized knowledge, workflows, and tools. Each skill lives in `.skills/<skill-name>/` and contains a `SKILL.md` plus optional scripts, references, and assets.

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
