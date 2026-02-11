# AGENTS.md

This file provides guidance to AI coding agents working with code in this repository.
It follows the [AGENTS.md open standard](https://github.com/anthropics/agent-guidelines) supported by Codex CLI, OpenClaw, Cursor, Aider, Google Jules, Gemini CLI, Windsurf, Devin, and many other tools.

> **Claude Code users:** See `CLAUDE.md` for Claude Code specific instructions.
> **Codex CLI users:** See `.codex/config.toml` for project-level Codex configuration.

---

## Project Overview

<!-- Describe your project in 2-3 sentences -->
**Project Name** - Brief description of what the project does.

### Architecture

<!-- Describe your system architecture. Examples: -->
<!-- - Monolith, microservices, serverless, etc. -->
<!-- - Key components and their responsibilities -->
<!-- - Technology stack for each component -->

### Key Integration Points

<!-- Document how components communicate -->
<!-- Example: -->
<!-- - **Backend <-> Database**: ORM with connection pooling -->
<!-- - **Backend <-> Frontend**: REST API + WebSocket -->
<!-- - **Backend <-> Workers**: Message queue -->

---

## Development Commands

<!-- Document commands for each component of your project -->

### Setup

```bash
# Initial setup steps
```

### Development

```bash
# How to run the project locally
```

### Testing

```bash
# How to run tests
```

### Code Quality

```bash
# Linting, formatting, type checking commands
```

---

## Architecture Deep Dive

<!-- Add detailed documentation about key subsystems -->
<!-- Only add sections that are relevant to your project -->

### Database Layer
<!-- Schema overview, migration strategy, connection details -->

### Configuration System
<!-- How config is loaded, env vars, runtime vs startup config -->

### Authentication
<!-- Auth flow, token management, session handling -->

---

## Critical Development Rules

These rules prevent recurring bugs documented in `TODO.md` and `LESSONS_LEARNED.md`:

<!-- Add project-specific rules as you discover them. Examples: -->

<!-- ### 1. Rule Name -->
<!-- Description of what to do/avoid and why. -->

### 1. KISS and DRY

- **KISS**: Only add what's requested or clearly necessary. No premature optimization or abstraction.
- **DRY**: Extract common patterns to shared functions. Use config files for repeated values.

### 2. Windows Platform Compatibility

**NEVER use Unix-specific shell patterns on Windows**:
- `> /dev/null` -> `> NUL` (Windows null device)
- `2> /dev/null` -> `2> NUL` (Windows stderr redirect)
- Or use cross-platform solutions when possible

---

## Testing

<!-- Document your testing strategy -->

### Running Tests

```bash
# Commands to run tests
```

### Manual Testing

<!-- Steps for manual integration testing if applicable -->

---

## Common Pitfalls

<!-- Document project-specific pitfalls as they are discovered -->
<!-- Each pitfall should have: Symptom, Fix -->

<!-- Example: -->
<!-- ### Problem Name -->
<!-- **Symptom**: What the developer observes -->
<!-- **Fix**: How to resolve it -->

---

## Project Documentation Files

**Active Development**:
- `TODO.md` - Active bugs and future work
- `DONE.md` - Completed work log (chronological)
- `LESSONS_LEARNED.md` - Critical patterns and anti-patterns

**Tool-Specific Configuration**:
- `CLAUDE.md` - Claude Code specific instructions (read automatically by Claude Code)
- `.claude/instructions.md` - Claude Code session instructions
- `.codex/config.toml` - Codex CLI project configuration

**Update These Files**:
- After completing work -> Add to `DONE.md`
- After discovering invisible bugs -> Add pattern to `LESSONS_LEARNED.md`
- When adding/changing tasks -> Update `TODO.md`

---

## Default Credentials

<!-- Document any default credentials for development -->
<!-- IMPORTANT: Always note to change defaults in production -->

---

## Security Notes

<!-- Document security-relevant configuration and practices -->

---

## Additional Resources

<!-- Links to other documentation, external resources, etc. -->
