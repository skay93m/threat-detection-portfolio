# Writing Style Guide

## Blog Tone & Voice

These are technical posts demonstrating practical security work. Not tutorials or introductory guides.

### Principles
- **Narrative-driven:** Tell the story of what you did and why
- **Clear over clever:** Explain decisions, not just outcomes
- **Thoughtful:** Show your reasoning, problem-solving approach, and learning
- **Technical but accessible:** Assume reader knows security basics, explain any domain-specific choices

### Structure (Problem → Decision → Evidence)

1. **The Problem**
   - What were you trying to do?
   - What was unclear, hard, or interesting about it?

2. **The Decision**
   - How did you approach it?
   - What did you consider and reject?
   - Why did you choose X over Y?

3. **The Evidence**
   - What did you see? (logs, metrics, screenshots)
   - Did it work? What broke?
   - What did you learn?

### Tone

- Use **plain British English** (colour, organisation, etc.)
- Avoid:
  - Step-by-step tutorials ("First, click the button...")
  - Excessive jargon without explanation
  - "Obviously" or "simply" (things aren't obvious to everyone)
  - Hype or marketing language

- Do use:
  - First person ("I discovered...", "I decided...")
  - Honest reflection ("This didn't work because...")
  - Specific details (tool versions, rule names, log formats)

## Internal Documentation

- Use **clear headings** and **bullet points** for scannability
- Keep files **focused** (one topic per file)
- Link to related docs
- Date entries in day-logs: `YYYY-MM-DD.md`

## Markdown Standards

- H1 for file title (one per file)
- H2 for main sections
- H3 for subsections
- Code blocks with language labels
- Links to internal docs relative to repo root

---

**Goal:** Write so that anyone reading understands exactly what you did, why you made those decisions, and what you learned. The focus is on clear technical communication and honest reflection on your work.
