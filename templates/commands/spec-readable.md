---
description: Convert spec-simple.md into properly-readable spec-readable.md following writing rules
---

User input:

$ARGUMENTS

This command converts your working notes in `spec-simple.md` into a clean, properly-formatted `spec-readable.md` that you can show to co-workers.

**Workflow:**

1. Find the current feature directory by checking the git branch name (format: `###-feature-name`) or looking in `specs/` for the most recent feature
2. Read `spec-simple.md` from the feature directory (your informal working notes)
3. Read `.specify/templates/readable-spec-rules.md` for complete writing rules and structure
4. Convert the simple notes into a properly-formatted readable spec following ALL the rules in the template
5. Write the result to `spec-readable.md` in the same feature directory
6. Report completion with section count and any areas that needed interpretation

**Key Rules from Template:**
- Follow the exact structure defined in readable-spec-rules.md
- No buzzwords ("seamless", "robust", "leverages", "paradigm", "revolutionary")
- No vague terms like "natural" or "intuitive" without explanation
- Use plain English, active voice, short paragraphs
- Include concrete examples with specific values
- Clean up informal notes and TODOs
- Make it presentable for stakeholders

If $ARGUMENTS is provided, use it as additional context for the conversion.
