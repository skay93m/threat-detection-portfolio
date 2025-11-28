# Writing Style Guide

## Non-Negotiable

- **Use plain British English** — colour, organisation, analyse, programme (not color, organization, analyze, program)
- **Use active voice** — "The rule detected the attack" not "The attack was detected by the rule"

---

## Blog Tone & Voice

These are technical posts demonstrating practical security work. Not tutorials or introductory guides.

This style guide is inspired by [The Economist Style Guide](https://www.economist.com/blogs/johnson/2015/07/english-language), adapted for technical documentation and threat detection narratives.

### Principles

- **Narrative-driven** — Tell the story of what you did and why. Use the active voice throughout; make the reader follow your investigation
- **Clear over clever** — Explain decisions, not just outcomes. Jargon confuses; clarity persuades
- **Thoughtful** — Show your reasoning, problem-solving approach, and learning. Admit what didn't work
- **Technical but accessible** — Assume the reader knows security basics; explain domain-specific choices and tool-specific decisions
- **Specific and concrete** — Use precise tool names, versions, rule identifiers, log formats, and metrics (not "we saw some alerts"; instead "the brute_force_5min rule triggered 47 times")

### Structure (Problem → Decision → Evidence)

#### 1. The Problem

- What were you trying to do?
- What was unclear, hard, or interesting about it?
- Why should the reader care?

#### 2. The Decision

- How did you approach it?
- What did you consider and reject?
- Why did you choose X over Y?
- What trade-offs did you accept?

#### 3. The Evidence

- What did you see? (logs, metrics, screenshots, configurations)
- Did it work? What broke?
- What did you learn? What surprised you?

### Tone

**Do use:**

- First person ("I discovered...", "I decided...", "I tested...")
- Honest reflection ("This didn't work because...", "I was wrong about...")
- Specific details — tool versions, rule names, log formats, confidence scores, false positive rates
- Shorter sentences. Punctuation is cheap. Use it
- Active verbs — investigate, detect, correlate, trigger, escalate (not: are investigated, is detected, are correlated)

**Avoid:**

- Step-by-step tutorials ("First, click the button...")
- Excessive jargon without explanation
- Hedging words: "obviously", "simply", "just", "merely" (things aren't obvious to everyone)
- Hype or marketing language ("game-changing", "innovative", "cutting-edge")
- Passive constructions — the rule found the threat, not the threat was found
- Vague adverbs — "quite", "rather", "somewhat" — choose precision instead

**Examples:**

| ❌ Avoid | ✅ Preferred |
|---------|-----------|
| "The malicious activity was identified by the SIEM rule." | "The rule detected 12 failed SSH logins from 192.168.1.100 in 5 minutes." |
| "It was observed that alerts were generated." | "The correlation rule triggered 3 alerts." |
| "Obviously, credentials should never be stored." | "Credentials in plaintext pose a direct attack surface." |
| "The configuration seems to work." | "The configuration reduced false positives by 31% and caught all test cases." |

### Style

**Headings:**

- Use sentence case (capitalize only first word and proper nouns)
- Make them specific: "Configuring Splunk field extractions for Suricata" not "Configuration"
- Keep them scannable

**Lists:**

- Use bullet points for options, components, or parallel ideas
- Use numbered lists only for sequential steps
- Parallel structure — if one item is a noun, all should be nouns

**Examples and evidence:**

- Include log snippets, alert outputs, rule configurations
- Show what success looks like and what failure looks like
- Reference metrics: "5 false positives per week", "92% detection rate on the test dataset"

**Links:**

- Link to related documentation and external resources (with specific page titles, not "click here")
- Reference relevant SIEM rules, detection logic, or lab configurations by name and location

---

## Internal Documentation

Internal docs (day-logs, results compilation, notes) follow the same principles but are less narrative:

- Use **clear headings** and **bullet points** for scannability
- Keep files **focused** (one topic per file)
- Link to related docs
- Date entries in day-logs: `YYYY-MM-DD.md`
- Use tables for comparisons (metrics, test results, configuration options)

---

## Markdown Standards

Follow the **[markdown-lint formatter](https://github.com/DavidAnson/markdownlint)** as configured in this workspace (see `.markdownlintrc` or VS Code linter settings for rules). Key principles:

- H1 for file title (one per file)
- H2 for main sections
- H3 for subsections
- Blank lines before and after headings and code blocks
- Code blocks with language labels where applicable
- Links relative to repo root where possible

The linter will catch style violations automatically.

---

**Goal:** Write so that anyone reading understands exactly what you did, why you made those decisions, and what you learned. The focus is on clear technical communication, active voice, and honest reflection on your work.
