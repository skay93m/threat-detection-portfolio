# Instructions to Self

## Purpose of This Repo

This is a **capability lab**, not a tutorial. It documents real security work building SOC analyst expertise through hands-on practice. The portfolio demonstrates:

- Practical threat detection and analysis work
- Decision-making in alert tuning and rule development
- Technical writing based on actual lab experience

## How I Work with Claude

I use Claude Code as my primary engineering/scripting agent. Claude handles:

- Setting up directory structures and automation
- Writing and refining scripts
- Compiling research into structured documents
- Helping frame blog posts from lab work

I use a separate Claude instance for deep research, analysis, and writing feedback.

All script additions go through Sourcery AI code review before committing.

## Daily Log Workflow (Using GitHub Issues + Day-Log Files)

This portfolio uses a **dual documentation system** to capture lab work:

### Lab Session Issues

Each week, create a new GitHub issue using the **Lab Session** template:

**How to create:**
1. Go to Issues → New Issue → Select "Lab Session" template
2. Title: `Lab Session: YYYY-MM-DD` (date you're starting the session)
3. Fill out template sections:
   - **Session Overview:** What's the goal for this work?
   - **What I Did:** Key actions, experiments, configurations
   - **What I Learned:** Insights, discoveries, gotchas
   - **Blockers/Challenges:** What went wrong or got stuck?
   - **Next Steps:** What's the follow-up work?
   - **Evidence/Links:** Links to screenshots, logs, configs, and day-log file

**Purpose:** GitHub issue is a _summary view_ of the week's work. Quick reference.

### Day-Log Files

For detailed, chronological notes of what you did and when:

**File location:** `docs/03-implementation/day-logs/YYYY-MM-DD.md`

**Create when:** You start a significant block of lab work

**What goes in:**
- **Chronological notes** of commands run, settings changed, observations
- **Timestamps** if doing multi-hour sessions
- **Screenshots/evidence filenames** with descriptions
- **Error messages** and how you resolved them
- **Configuration snippets** showing what you changed
- **Quick learnings** as you discover them

**Template:**
```markdown
# Lab Work: YYYY-MM-DD

## Session Goal
[What are you trying to accomplish?]

## Work Log

### Morning / Phase 1
- 10:15 — Did X, result was Y
- 10:45 — Tested Z, screenshot: [filename]
- Blocker: [What went wrong]

### Afternoon / Phase 2
- 14:00 — Changed configuration
- 14:30 — Ran test, output in [log filename]

## Key Learnings
- Discovery 1
- Discovery 2
- What to try next time

## Evidence
- Screenshots: [filenames in assets/]
- Logs: [filenames]
- Configs: [which config files in config/]
```

**Why separate files?**
- Issues are public-facing summaries; day-logs are your detailed working notes
- Day-logs stay in repo for future reference without cluttering GitHub Issues
- Easier to search and grep through day-logs than GitHub history

## Weekly Workflow

1. **Plan** — Define what I'm testing/building this week
2. **Lab** — Capture screenshots, logs, configurations + write day-log
3. **Log** — Day-log updated as you work; create Lab Session issue at week-end
4. **Compile** — Summarize findings from day-log into docs/04-results/
5. **Write** — Draft blog post if milestone reached
6. **Review** — Share with Claude (research) for feedback
7. **Publish** — Finalize and post to Substack (if ready)

## What Constitutes "Done" for a Session

A lab session is complete when:

- [ ] I have a day-log entry (format: `YYYY-MM-DD.md`)
- [ ] Evidence is captured (logs, screenshots, configs)
- [ ] At least one new thing is documented in lessons-learned.md
- [ ] Metrics are updated if applicable
- [ ] Next steps are clear

If I'm writing a blog post that week, it's done when:

- [ ] First draft is in docs/05-blog-posts/draft-XXX.md
- [ ] Claude (research) has reviewed it
- [ ] Final edits are complete and it's ready for publishing
- [ ] It's moved to docs/05-blog-posts/published/
