# Spec Workflow

This document explains the three-stage spec workflow and how to use the commands.

## The Three Spec Files

### 1. `spec-simple.md` (Your Working Notes)
**Purpose**: Informal notes and brainstorming. This is where YOU work.

**Characteristics:**
- Not formatted properly
- Contains TODOs, questions, incomplete thoughts
- Not intended for others to read
- Never committed to GitHub
- Constantly edited, deleted, added to

**Example content:**
```markdown
# weapon animation thing

- extract curves from animations
- TODO: figure out how spring stuff works
- runtime editor? maybe?
- needs to be easy to use, no animation knowledge required
- additive layering (multiple motions stack)

Questions:
- do we need LOD?
- what about mobile?
```

### 2. `spec-readable.md` (Clean, Shareable)
**Purpose**: Properly-formatted spec you can show co-workers.

**Characteristics:**
- Follows writing rules from `.specify/templates/readable-spec-rules.md`
- Clean, organized, professional
- No buzzwords, clear language
- Includes practical examples
- Good for stakeholder communication

**Created by**: `/spec-readable` command

### 3. `spec.md` (Formal Specification)
**Purpose**: Formal requirements document used by `/tasks` and `/implement`.

**Characteristics:**
- Follows `.specify/templates/spec-template.md` structure exactly
- Given/When/Then acceptance scenarios
- Numbered functional requirements (FR-001, etc.)
- Review checklists
- Used by automation tools

**Created by**: `/spec-formal` command

## Workflow

```
┌─────────────────┐
│ spec-simple.md  │  ← You edit this (informal notes)
│ (working notes) │
└────────┬────────┘
         │
         │ /spec-readable
         ↓
┌─────────────────┐
│spec-readable.md │  ← Share with co-workers
│  (clean copy)   │
└────────┬────────┘
         │
         │ /spec-formal
         ↓
┌─────────────────┐
│    spec.md      │  ← Used by /tasks and /implement
│   (formal req)  │
└─────────────────┘
```

## Commands

### `/spec-readable`
Converts `spec-simple.md` → `spec-readable.md`

**What it does:**
1. Reads your working notes from `spec-simple.md`
2. Cleans up formatting
3. Removes informal notes and TODOs
4. Applies writing rules (no buzzwords, clear language)
5. Organizes into standard structure
6. Writes to `spec-readable.md`

**When to use:**
- After you've made significant changes to spec-simple.md
- Before sharing with a co-worker
- When you want to see your notes in clean format

**Example:**
```bash
/spec-readable
```

Or with additional instructions:
```bash
/spec-readable focus on the runtime editor features
```

### `/spec-formal`
Converts `spec-readable.md` → `spec.md`

**What it does:**
1. Reads the clean spec from `spec-readable.md`
2. Converts to formal Given/When/Then scenarios
3. Extracts and numbers functional requirements (FR-XXX)
4. Adds edge cases and review checklist
5. Writes formal spec to `spec.md`

**When to use:**
- After you and your co-workers agree spec-readable.md looks good
- Before running `/tasks` or `/implement`
- When you need the formal requirements document

**Example:**
```bash
/spec-formal
```

Or with additional instructions:
```bash
/spec-formal make sure to include all performance requirements
```

## Typical Session

### Step 1: Brainstorm in spec-simple.md
Open `specs/001-some-feature/spec-simple.md` and dump your thoughts:

```markdown
# new animation system

need:
- extract curves from animations (editor tool, right click menu)
- play them at runtime with springs
- easy to tweak during play

questions:
- how many motion types? at least idle, aim, firing
- what about blending multiple motions?

TODO:
- figure out data asset structure
```

### Step 2: Create readable version
```bash
/spec-readable
```

Claude converts your notes into:

```markdown
# Procedural Animation System - Overview

**What This Is**: A plugin that extracts motion from animations and lets you
adjust how they play at runtime using spring interpolation.

**Why We're Building This**: To give developers easy-to-tweak weapon motion
without animation knowledge.

## How It Works
...
```

### Step 3: Review with team
Share `spec-readable.md` with co-workers. Get feedback. Update `spec-simple.md` with changes. Re-run `/spec-readable`.

### Step 4: Create formal spec
Once everyone agrees the readable version is good:

```bash
/spec-formal
```

This creates `spec.md` with proper requirements:

```markdown
### Acceptance Scenarios

1. **Given** an animation sequence in the editor, **When** the developer
right-clicks and selects extract, **Then** the system creates a motion data file.

### Functional Requirements

#### Motion Extraction
- **FR-001**: System MUST extract location curves from animation sequences
- **FR-002**: System MUST extract rotation curves from animation sequences
...
```

### Step 5: Generate tasks
Now you can run:

```bash
/tasks
```

This reads `spec.md` and creates actionable tasks.

## File Locations

All three files live in the same feature directory:

```
specs/
  001-your-feature/
    spec-simple.md      ← Your working notes (edit freely)
    spec-readable.md    ← Clean version (generated)
    spec.md            ← Formal requirements (generated)
```

## Important Notes

### Don't Edit Generated Files Directly
- `spec-readable.md` and `spec.md` are generated from `spec-simple.md`
- If you edit them directly, changes will be lost on next generation
- Always edit `spec-simple.md`, then regenerate

### Iteration
You can iterate as many times as needed:

```
Edit spec-simple.md
→ /spec-readable
→ review
→ Edit spec-simple.md again
→ /spec-readable again
→ /spec-formal (only when ready)
```

### Version Control
- `spec-simple.md` - **Don't commit** (it's in .gitignore)
- `spec-readable.md` - Optional (good for documentation)
- `spec.md` - **Always commit** (required by /tasks)

## Templates

### Writing Rules
`.specify/templates/readable-spec-rules.md` - Complete rules for creating readable specs

Key rules:
- No buzzwords
- Plain English
- Short paragraphs
- Concrete examples
- Active voice

### Formal Template
`.specify/templates/spec-template.md` - Structure for formal specs

Includes:
- Acceptance scenarios format
- Functional requirements format
- Review checklist
- All required sections

## Helper Script

`.specify/scripts/bash/find-current-feature.sh` - Locates current feature directory

Usage:
```bash
.specify/scripts/bash/find-current-feature.sh --json
```

Returns:
```json
{
  "FEATURE_NAME": "001-some-feature",
  "FEATURE_DIR": "/full/path/to/specs/001-some-feature",
  "SPEC_FILE": "/full/path/to/specs/001-some-feature/spec.md",
  "SPEC_SIMPLE_FILE": "/full/path/to/specs/001-some-feature/spec-simple.md",
  "SPEC_READABLE_FILE": "/full/path/to/specs/001-some-feature/spec-readable.md"
}
```

## Quick Reference

| File | Purpose | Who Edits | Committed |
|------|---------|-----------|-----------|
| spec-simple.md | Working notes | You (manually) | No |
| spec-readable.md | Clean shareable | Generated | Optional |
| spec.md | Formal requirements | Generated | Yes |

| Command | Input | Output | When |
|---------|-------|--------|------|
| /spec-readable | spec-simple.md | spec-readable.md | After brainstorming |
| /spec-formal | spec-readable.md | spec.md | After team approval |
