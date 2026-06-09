# claude-skills

Personal Claude Code skill library.

## Installation

```bash
git clone https://github.com/tobilobaajimosun-dev/claude-skills.git
cp -r claude-skills/.claude/commands/* ~/.claude/commands/
```

Or symlink so updates pull automatically:

```bash
git clone https://github.com/tobilobaajimosun-dev/claude-skills.git ~/claude-skills
ln -sf ~/claude-skills/.claude/commands/figma-design-audit.md ~/.claude/commands/figma-design-audit.md
ln -sf ~/claude-skills/.claude/commands/design-system-guardian.md ~/.claude/commands/design-system-guardian.md
```

---

## Skills

### `/figma-design-audit`

**Senior Product Designer + Design System Engineer**

Analyzes Figma screens and extracts reusable component specs, design tokens, responsive layout patterns, and flags missing components.

**Usage**

```
/figma-design-audit https://www.figma.com/file/your-file-id/...
```

If no URL is passed the skill will prompt for one before starting.

**Output**

- Structured component specs (name, variants, states, responsive, Angular API, a11y)
- Missing component reports
- Design token table (colors, typography, spacing, radius, shadow, icons)
- Responsive layout analysis per screen

---

### `/design-system-guardian`

**Pre-implementation component audit gate**

Scans your project's component inventory, compares it against what you're about to build, and reports what exists, what's partial, what's missing, and what risks duplication. Stops before any code is written.

**Usage**

```
/design-system-guardian checkout flow
/design-system-guardian table, filter bar, status badge, empty state
```

If no argument is passed the skill will ask what you're about to build.

**Output**

```
COMPONENT AUDIT
━━━━━━━━━━━━━━━
Existing:       ✓ components already in the library
Partial:        ◑ components that need a new variant
Missing:        ✗ net-new components required
Duplicate Risk: ⚠ same function, different name
Reuse:          → composition opportunities
VERDICT:        SAFE TO BUILD | REVIEW REQUIRED | BLOCKED
```

---

## Adding a new skill

1. Create `.claude/commands/<skill-name>.md`
2. Add an entry to this README
3. Push — the symlink picks up changes automatically
