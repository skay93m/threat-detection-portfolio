# Coding Style Guide

## General Principles

Scripts in this repo should be:
- **Documented** — Clear README or docstring explaining what it does
- **Simple** — Solve the specific problem, not a general class of problems
- **Safe** — No hardcoded credentials, IPs, or sensitive data
- **Tested** — Works in the lab environment (or documented failure modes)

## Script Documentation

Each script in `/scripts/` should have:
- A **shebang** line (e.g., `#!/usr/bin/env python3`)
- A **docstring** at the top explaining:
  - What the script does
  - What inputs it expects
  - What it outputs or does
  - Any dependencies
- **Comments** for non-obvious logic

Example:
```python
#!/usr/bin/env python3
"""
Parses SIEM logs and extracts alerts above confidence threshold.

Usage:
    python3 parse_alerts.py <logfile> <threshold>

Output:
    CSV of alerts with source, destination, rule name, confidence
"""
```

## Configuration Files

Config files in `/config/` should be:
- **Sanitised** — No real IPs, hostnames, API keys, or passwords
- **Documented** — Comments explaining each section
- **Templated** — Use placeholders like `CHANGEME_SERVER_IP` if needed

Example:
```yaml
# vm-specs.yml - DO NOT COMMIT REAL CREDENTIALS
siem:
  hostname: "CHANGEME_SIEM_HOSTNAME"
  port: 8089
  # Auth: Use local .env file
```

## Naming Conventions

- **Lab scripts:** `analyze_*.py`, `setup_*.sh`, `parse_*.py`
- **Day-log files:** `YYYY-MM-DD.md`
- **Blog drafts:** `draft-001-topic-name.md`, `draft-002-...`
- **Config files:** Snake_case, descriptive names

## Code Review

All scripts are reviewed by **Sourcery AI** before committing. Flag in PR or mention to Claude.

---

**Priority:** Clarity and maintainability over optimization. This is a portfolio, not production code.
