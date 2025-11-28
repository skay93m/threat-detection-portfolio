# Threat Detection Portfolio

A structured capability lab for developing SOC analyst skills through practical threat detection, incident response, and security operations work.

## Overview

This portfolio documents hands-on work building expertise in:

- **Threat Detection & Response:** Designing SIEM rules, hunting for anomalies, investigating alerts
- **Security Operations:** Building detection pipelines, managing false positives, tuning alerts
- **Analysis & Writing:** Converting lab work into clear, well-structured technical writing

This is a *capability lab*, not a tutorial repository. Each section documents real work done, decisions made, and evidence captured.

## Structure

```bash
📁 docs/
├── 00-meta/          → How I work, style guides, instructions
├── 01-research/      → Job descriptions, literature review, requirements
├── 02-design/        → Architecture, tool selection, threat scenarios
├── 03-implementation/ → Day logs, configurations, troubleshooting notes
├── 04-results/       → Test cases, evidence, metrics, lessons learned
└── 05-blog-posts/    → Draft and published blog posts

📁 config/            → Sanitised environment configs and rules (added during lab setup)
📁 scripts/           → Lab automation, analysis tools
📁 assets/            → Diagrams, screenshots
```

## Quick Links

- **[Research & Design](docs/01-research/)** — What I'm building and why
- **[Implementation Logs](docs/03-implementation/)** — Weekly lab session notes
- **[Blog Posts](docs/05-blog-posts/)** — Public writing (published on Substack)
- **[Changelog](CHANGELOG.md)** — Structural updates and milestones

## How to Navigate

1. **For structure & workflow:** See [docs/00-meta/](docs/00-meta/)
2. **For my current work:** Check [docs/03-implementation/day-logs/](docs/03-implementation/day-logs/)
3. **For what I've learned:** Read [docs/04-results/](docs/04-results/)
4. **For published writing:** See [docs/05-blog-posts/published/](docs/05-blog-posts/published/)

## Daily Log System

Lab work is tracked using **weekly GitHub issues** (summaries) and **daily log files** (detailed notes):

- **Lab Session Issue** (per week): Create at week-end using the [Lab Session template](.github/ISSUE_TEMPLATE/lab-session.md) to summarize the week's work and link to day-logs
- **Day-Log Files** (per day/session): `docs/03-implementation/day-logs/YYYY-MM-DD.md` — Chronological work notes with commands, evidence, blockers

See [INSTRUCTIONS-TO-SELF.md](docs/00-meta/INSTRUCTIONS-TO-SELF.md) for detailed instructions on creating and maintaining both.

## Tools & Environment

- **SIEM:** TBD
- **Lab VMs:** TBD
- **OS:** Windows/Linux (guest), macOS (host)
- **Scripting:** Python, Bash
- **Writing & Publishing:** Markdown + Substack
- **AI Assistance:** Transparent use of AI tools for research, structure, and automation (see [AI-AGENT-POLICY](docs/00-meta/AI-AGENT-POLICY.md))

## Status

🔄 **Foundation & Core Skills** (In Progress)

- [x] Repo structure
- [ ] Research & requirements mapping
- [ ] SIEM & lab environment setup
- [ ] First detection rules
- [ ] Blog post series begins

## License

Personal portfolio — documentation and code shared for educational purposes.

---

**Last Updated:** 2025-11-28
**Blog:** [Syafiq's Space](https://syafiqsspace.substack.com/)
