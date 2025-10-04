# Readable Spec Writing Rules

This document defines how to convert informal notes from `spec-simple.md` into a clean, presentable `spec-readable.md`.

## Purpose

The readable spec is for **sharing with co-workers** who need to understand what you're building without wading through formal requirements. It should be:

- Easy to skim and understand quickly
- Free of buzzwords and jargon
- Practical with real-world examples
- Well-organized and visually clean
- Conversational but professional

## Structure

Use this exact structure:

```markdown
# [Feature Name] - Overview

**What This Is**: [One sentence describing what the system is]

**Why We're Building This**: [One sentence explaining the goal, not the benefits]

---

## How It Works

[Explain the main parts/components and how they interact. Use numbered lists or sections for different modules.]

### [Component 1 Name]
[What it does, when it runs, what it produces]

### [Component 2 Name]
[What it does, when it runs, what it produces]

---

## Key Features

[List the most important capabilities. Group by theme if needed.]

### [Feature Category 1]
[Details about related features]

### [Feature Category 2]
[Details about related features]

---

## How [Main Action] Gets Done

[Step-by-step explanation of the primary workflow from start to finish]

1. **[Step]**: [What happens]
2. **[Step]**: [What happens]

---

## Technical Details

[Important technical information organized by topic]

### [Topic 1]
[Details]

### [Topic 2]
[Details]

---

## Example Use Cases

[Real scenarios showing how someone would use this. Use bold for the scenario name, then explain.]

**[Scenario Name]**:
[Concrete example with specific details]

---

## [Component/Module] Breakdown

[Detailed breakdown of each part if needed]

### [Module Name]
- **Where**: [Editor/Runtime/etc]
- **What**: [Purpose]
- **Input**: [What it takes]
- **Output**: [What it produces]

---

## What You Can Customize

[List of things users can control, with brief explanations]

---

## Error Handling

[How the system handles common errors]

---

## Workflow Summary

[Quick numbered list of the overall process from start to finish]
```

## Writing Rules

### Language Style

**DO:**
- Use plain English
- Write like you're explaining to a teammate
- Use active voice ("The system extracts curves" not "Curves are extracted")
- Be specific ("adjusts weapon bounce intensity" not "modifies parameters")
- Use concrete examples
- Explain "why" something exists, not just "what" it does

**DON'T:**
- Use buzzwords: "seamless", "robust", "leverages", "holistic", "synergy", "paradigm"
- Use vague terms: "natural", "intuitive", "powerful", "flexible" (unless you explain what you mean)
- Use hype language: "revolutionary", "game-changing", "cutting-edge"
- Use overly formal language: "utilize" instead of "use", "facilitate" instead of "help"
- Repeat "experience" excessively (e.g., "shooter experience" → "shooter")
- Use passive voice when active is clearer

### Formatting

- Use **bold** for emphasis on important terms (first use only)
- Use `code formatting` for file names, bone names, parameter names
- Use bullet lists for features
- Use numbered lists for workflows/steps
- Use horizontal rules (`---`) to separate major sections
- Keep paragraphs short (2-4 sentences max)

### Examples

**Good**: "Right-click on any animation sequence in the editor to open the extraction tool."

**Bad**: "Users can leverage the seamless right-click workflow to extract motion data from animation sequences in a robust and intuitive manner."

---

**Good**: "With default settings, the motion looks exactly like the original animation. Change the settings and you get different behavior."

**Bad**: "The system provides a flexible paradigm that facilitates both faithful reproduction of original animations and highly customizable procedural motion generation depending on configuration parameters."

---

**Good**: "You've got an idle animation for your assault rifle, but the bounce feels too subtle. Extract the curves, crank up the 'Bounce Intensity' parameter while playing, find the sweet spot, save it."

**Bad**: "In scenarios where the default idle animation lacks sufficient amplitude, the system enables developers to dynamically adjust motion parameters to achieve optimal gameplay feel."

### Technical Details

- Include file formats when relevant (e.g., "FCurveDataAsset")
- Mention platform targets if important (e.g., "PC and consoles")
- Specify editor vs runtime clearly
- Name modules/components consistently
- Explain what "additive" or "procedural" means the first time you use it

### Examples Section

Each example should:
1. Start with a bold scenario name
2. Set the context (what you have)
3. Explain the problem or goal
4. Show the solution using the system
5. Use concrete values ("15 frames", "Bounce Intensity", not "various parameters")

## Conversion Process

When converting from `spec-simple.md`:

1. **Clean up informal notes**: Remove todos, questions to yourself, incomplete thoughts
2. **Organize by structure**: Rearrange content to match the template
3. **Expand abbreviations**: Write out anything that's shorthand
4. **Add examples**: If simple notes lack examples, create realistic ones
5. **Format consistently**: Apply markdown formatting rules
6. **Remove redundancy**: Say things once clearly instead of multiple times vaguely
7. **Verify completeness**: Every major component/feature should be covered

## What to Keep vs. Remove

**Keep:**
- Core functionality descriptions
- Component breakdowns
- Workflow explanations
- Technical specifications
- Use cases and examples
- Error handling
- Customization options

**Remove:**
- Personal notes to yourself
- Incomplete sentences
- Questions you haven't answered yet
- Implementation details (unless they affect user understanding)
- Debates about design choices
- TODOs and open questions

## Tone Examples

### "What This Is" Section
- Good: "A plugin that lets game developers adjust weapon animations in-engine without being an animator."
- Bad: "An innovative solution that revolutionizes the animation workflow paradigm."

### "Why We're Building This" Section
- Good: "To give developers a highly customizable gameplay feel that's extremely beginner-friendly."
- Bad: "To empower users with a seamless, robust toolset for enhancing their creative vision."

### Feature Descriptions
- Good: "Changes show up immediately - no restart needed."
- Bad: "The system facilitates real-time iterative workflow optimization."

## Final Checklist

Before considering the readable spec complete:

- [ ] Can a co-worker read this in 5 minutes and understand what you're building?
- [ ] Are all buzzwords removed or replaced with specific language?
- [ ] Do examples use concrete values and realistic scenarios?
- [ ] Is every major component/feature explained?
- [ ] Are technical terms defined on first use?
- [ ] Is the structure clean and easy to navigate?
- [ ] Would you be comfortable sharing this with stakeholders?
