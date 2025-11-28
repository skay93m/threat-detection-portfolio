# Workflow

## Quick Reference

```txt
┌─────────────────────────────────────────────────────────────────┐
│                   Weekly Lab Session Rhythm                     │
└─────────────────────────────────────────────────────────────────┘

    Plan              Lab Work           Log & Compile          Blog
   (Week Start)      (Mid-Week)         (Week End)          (Milestone)
        │                 │                   │                  │
        ▼                 ▼                   ▼                  ▼
    ┌────────┐       ┌──────────┐      ┌────────────┐      ┌─────────┐
    │ Define │       │ Run Expt │      │Write Log   │      │ Draft   │
    │ Goals  │──────▶│ Capture  │─────▶│ Compile    │─────▶│ Post    │
    │ & Plan │       │ Evidence │      │ Results    │      │ Refine  │
    └────────┘       └──────────┘      └────────────┘      └─────────┘
                            │                   │                │
                            └───────────────────┘                │
                          (Screenshots, Logs,              (Move to
                           Configs, Insights)            Published)
```

**Key outputs:**

- Day-logs: `docs/03-implementation/day-logs/YYYY-MM-DD.md`
- Results: `docs/04-results/{lessons-learned,metrics,test-cases}.md`
- Blog drafts: `docs/05-blog-posts/draft-XXX-topic.md`

---

## Weekly Lab Session Rhythm

1. **Plan (Start of Week)**
   - Define what you're testing/building this week
   - Identify what you want to learn or prove
   - Set up lab environment if needed

2. **Lab Work (Mid-Week)**
   - Run experiments, create rules, investigate alerts
   - Capture **evidence**: screenshots, logs, configurations
   - Note observations and decisions as you go

3. **Log & Compile (End of Week)**
   - Write a day-log entry: `docs/03-implementation/day-logs/YYYY-MM-DD.md`
   - Move evidence into appropriate folder (`configs/`, `screenshots/`, etc.)
   - Update `docs/04-results/lessons-learned.md` with new insights
   - Update `docs/04-results/metrics.md` if you have measurements

4. **Blog Post (When a Milestone Hits)**
   - Start draft: `docs/05-blog-posts/draft-XXX-topic-name.md`
   - Follow [WRITING-STYLE-GUIDE.md](WRITING-STYLE-GUIDE.md)
   - Share with Claude (research) for feedback
   - Refine based on feedback
   - Move to `docs/05-blog-posts/published/` when ready
   - Update README.md with link to post

## Logging Work

### Day-Log Format

File: `docs/03-implementation/day-logs/YYYY-MM-DD.md`

```markdown
# Lab Work: YYYY-MM-DD

## What I Did
- Set up X
- Tested Y
- Analyzed Z

## What I Learned
- Key insight 1
- Key insight 2
- Blocker or challenge

## Evidence
- Screenshots: [filename]
- Logs: [filename]
- Configs: [filename]

## Next Steps
- What's the next thing to try?
```

## Compiling Results

After completing a logical section (e.g., "Set up first SIEM rules"), compile into:

- **docs/04-results/lessons-learned.md** — What you discovered
- **docs/04-results/metrics.md** — Measurements if applicable (alert volume, false positives, etc.)
- **docs/04-results/test-cases.md** — If you ran formal tests

## Publishing a Blog Post

1. **Draft** in `docs/05-blog-posts/draft-XXX.md`
   - Structure: Problem → Decision → Evidence
   - Include code snippets, screenshots, logs

2. **Get Feedback**
   - Ask Claude for structural/clarity feedback
   - Ask Claude (research) for flow and argument review

3. **Finalize**
   - Make edits based on feedback
   - Spell-check and proofread

4. **Publish**
   - Move to `docs/05-blog-posts/published/YYYY-MM-DD-title.md`
   - Post to Substack
   - Update README.md with link

## Updating Changelog

When you make **structural changes** (new folders, new sections), update `CHANGELOG.md`:

```markdown
## [Unreleased]

### Added
- New section: X
- New script: Y

### Changed
- Reorganised docs/

### Fixed
- Fixed Z
```

---

**Key Principle:** Capture evidence **as you work**. Waiting until the end to document makes you forget important details.
