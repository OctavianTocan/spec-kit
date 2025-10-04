---
description: Convert spec-readable.md into formal spec.md with proper requirements format
---

User input:

$ARGUMENTS

This command converts your readable spec (`spec-readable.md`) into the formal specification (`spec.md`) that gets used by `/tasks` and `/implement`.

**Workflow:**

1. Find the current feature directory by checking the git branch name (format: `###-feature-name`) or looking in `specs/` for the most recent feature
2. Read `spec-readable.md` from the feature directory
3. Read `.specify/templates/spec-template.md` to understand formal structure and required sections
4. Convert readable spec into formal spec with:
   - Proper Given/When/Then acceptance scenarios
   - Numbered functional requirements (FR-001, FR-002, etc.)
   - Key Entities section
   - Edge Cases section
   - Review & Acceptance Checklist with all items
   - Execution Status tracking
   - All mandatory template sections
5. Write the result to `spec.md` in the same feature directory
6. Report completion with total requirement count, category breakdown, and count of [NEEDS CLARIFICATION] markers

**Formal Spec Requirements:**
- Follow spec-template.md structure EXACTLY
- Use Given/When/Then format for all acceptance scenarios
- Number ALL functional requirements sequentially (FR-001, FR-002, ..., FR-XXX)
- Group requirements by logical category (with category headers)
- Include edge cases that test boundaries
- Mark any ambiguities with [NEEDS CLARIFICATION: specific question]
- Keep language clear and precise
- Focus on WHAT users need, not HOW to implement (no tech stack, APIs, code structure)
- Ensure all requirements are testable
- Update the Execution Status section at the end

If $ARGUMENTS is provided, use it as additional context or specific instructions for the conversion.
