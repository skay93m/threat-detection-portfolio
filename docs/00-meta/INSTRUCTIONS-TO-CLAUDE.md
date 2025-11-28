# Instructions to Claude

This is a **portfolio and capability lab**, not a tutorial or course repo.

## Your Role

When helping with this project, you should:

### ✅ Do

- Help with repo structure, automation, and scripting
- Review and refine scripts before they're committed (or flag for Sourcery review)
- Compile research documents with clear structure
- Provide research points for blog posts (with citations, structure, evidence links)
- Suggest improvements to documentation organisation
- Provide feedback on technical decisions

### ❌ Don't

- Write step-by-step tutorials or "how-to" guides
- Create sample data or dummy configs
- Add excessive comments or docstrings (keep code lean)
- Assume this is an educational resource for others (it's a personal portfolio)

## When Providing Feedback

- Reference the **[WRITING-STYLE-GUIDE.md](/docs/00-meta/WRITING-STYLE-GUIDE.md)** for tone and structure
- Reference the **[CODING-STYLE-GUIDE.md](/docs/00-meta/CODING-STYLE-GUIDE.md)** for script standards
- Link to relevant docs in this repo when suggesting changes
- Keep feedback actionable and specific

## Key Files to Check

- `docs/00-meta/AI-AGENT-POLICY.md` — How we use AI responsibly
- `docs/00-meta/WRITING-STYLE-GUIDE.md` — Tone, voice, structure
- `docs/00-meta/CODING-STYLE-GUIDE.md` — Script standards
- `CHANGELOG.md` — Track structural changes here

## Changelog Workflow

**When to update:** Before every commit that includes changes to the project (new files, docs, scripts, structure).

**What to include:**

- **Added:** New features, files, or documentation sections
- **Changed:** Modifications to existing content or structure
- **Fixed:** Bug fixes or corrections

**How it's enforced:** A git pre-commit hook (`.git/hooks/pre-commit`) will block commits unless `CHANGELOG.md` is staged. This ensures changes are always documented.

**If you need to bypass:** Use `git commit --no-verify` (rare—only for emergency commits)

**Reference:** See `CHANGELOG.md` for the format and examples.

## Blog Post Workflow

Blog posts are **your writing**, based on **my research support**:

1. **I provide:** Research points with structure (Problem → Decision → Evidence)
   - Each point includes: explanation, relevant citations, evidence gathered from your lab work
   - Source citations included verbatim

2. **You write:** The actual narrative and analysis
   - You synthesize the research points into a coherent post
   - You frame the story and add your own reflection
   - You incorporate evidence, logs, screenshots into the narrative

3. **Iteration:** We refine together
   - I check for clarity and structure
   - A separate Claude instance (research) provides writing feedback
   - You finalize and move to `docs/05-blog-posts/published/`

This approach keeps you as the author and decision-maker, with AI as research and structural support.

---

When in doubt, ask me to clarify what I need. This repo will evolve, so flexibility is key.
