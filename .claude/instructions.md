# Claude Code Project Instructions

> **Purpose:** Guide all Claude Code sessions to maintain project standards
> **Status:** Active - Read this file at the start of every session
> **Last Updated:** YYYY-MM-DD

---

## File Documentation System

This project uses **three separate documentation files** at the root level:

### 1. **TODO.md** - Active Work Items
- Current bugs and issues
- Future work items
- Critical rules and checklists (condensed version)
- **Update when:** Adding new tasks, marking items complete, discovering new issues
- **Keep it:** Clean and minimal - only active items

### 2. **DONE.md** - Completed Work Log
- Chronological history of all completed features and fixes
- Implementation details and file changes
- Bug fixes and their root causes
- **Update when:** Completing significant work, fixing bugs, implementing features
- **Format:** Add new entries at the top with date header

### 3. **LESSONS_LEARNED.md** - Critical Patterns & Anti-Patterns
- Detailed failure modes and their solutions
- Correct vs. wrong patterns with code examples
- Why certain bugs are "invisible" (silent failures)
- Prevention checklists
- **Update when:** Discovering a new class of bug, finding invisible failure modes, establishing new patterns
- **Keep it:** Detailed with examples - this is the knowledge base

---

## Mandatory Actions for Every Session

### When Starting Work:
1. **Read TODO.md** - Understand current active items and critical rules
2. **Scan LESSONS_LEARNED.md** - Review patterns relevant to your current work
3. **Follow KISS and DRY principles:**
   - **KISS (Keep It Simple, Stupid):** Only add what's requested or clearly necessary
   - **DRY (Don't Repeat Yourself):** Extract common patterns, use shared utilities

### During Development:
1. **Follow the Critical Rules** in TODO.md (they exist to prevent recurring bugs)
2. **Check LESSONS_LEARNED.md** before working in areas with documented pitfalls
3. **Test edge cases** mentioned in lessons learned

### When Completing Work:
1. **Update TODO.md:**
   - Mark completed items
   - Remove or update stale entries
   - Add new issues discovered

2. **Update DONE.md:**
   - Add entry at the top with date header
   - Include: issue description, root cause, fix summary, files modified
   - Keep it concise but complete

3. **Update LESSONS_LEARNED.md (if applicable):**
   - Add new pattern if you discovered an "invisible" bug
   - Include: problem description, root cause, correct pattern, wrong pattern, prevention checklist, why it's invisible
   - Use code examples

---

## Code Quality Standards

### KISS (Keep It Simple, Stupid)
- Only implement what's requested
- Keep solutions minimal and focused
- Trust internal code and framework guarantees
- Don't add features not requested
- Don't refactor code you're not changing
- Don't add error handling for impossible scenarios
- Don't create abstractions for one-time operations

### DRY (Don't Repeat Yourself)
- Extract common patterns to shared functions
- Use configuration files for repeated values
- Create utilities for repeated operations
- Don't copy-paste code blocks
- Don't duplicate logic across modules
- Don't hardcode values in multiple places

---

## Documentation Update Templates

### TODO.md Entry:
```markdown
### Known Issues
- [ ] **Brief description:** Detailed explanation of the issue
```

### DONE.md Entry:
```markdown
## YYYY-MM-DD - Feature/Fix Name
- **Issue:** Description of what was wrong
- **Root cause:** Why it happened
- **Fix:** What was changed
- **Impact:** Result of the fix
- **Files modified:** List of changed files
```

### LESSONS_LEARNED.md Entry:
```markdown
## Pattern Name

**Problem:** What goes wrong

**Root Cause:** Why it happens

**Correct Pattern:**
\`\`\`language
// Good code example
\`\`\`

**Wrong Pattern:**
\`\`\`language
// Bad code example
\`\`\`

**Prevention Checklist:**
- Step 1
- Step 2

**Why it's invisible:** Explanation of silent failure mode
```

---

## Emergency: How to Fix Common Issues

<!-- Add project-specific emergency fixes here -->
<!-- Example: -->
<!-- ### "My change isn't being saved to the database" -->
<!-- -> Check TODO.md Rule 1 - probably missing field in schema or endpoint -->

---

## Remember

- **These files exist to prevent wasted time** on recurring bugs
- **Update them diligently** - future Claude sessions depend on them
- **KISS and DRY are not optional** - they're project standards
- **Read before you code** - the lessons were learned the hard way

---

> **This file is read by every Claude Code session**
> **Keep it updated and concise**
> **Your future self (and other Claude sessions) will thank you**
> **Note:** `AGENTS.md` exists for non-Claude tools -- this file is Claude Code specific
