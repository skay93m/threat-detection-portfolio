# Coding Style Guide

## General Principles

Scripts in this repo should be:

- **Documented** — Clear README or docstring explaining what it does
- **Simple** — Solve the specific problem, not a general class of problems
- **Safe** — No hardcoded credentials, IPs, or sensitive data
- **Tested** — Works in the lab environment (or documented failure modes)

## Coding Principles for SOC Lab

### DRY — Don't Repeat Yourself

**Purpose:** Reduce redundancy to improve maintainability and reduce bugs.

**In the SOC lab context:**

- **Reusable parsers:** Create shared functions for common log formats (Syslog, CEF, JSON) instead of duplicating parsing logic in multiple scripts

  ```python
  # Good: Shared function
  def parse_syslog_message(raw_log):
      """Extract timestamp, hostname, process, and message from syslog."""
      # Parsing logic
      return parsed

  # Bad: Duplicated in multiple alert scripts
  # parse logic repeated 5 times
  ```

- **Configuration constants:** Extract lab setup values (SIEM URLs, ports, thresholds) into a shared config file rather than hardcoding across scripts
- **Alert rules:** If multiple SIEM rules detect similar patterns, document the shared detection logic and reference it
- **Test data:** Create reusable datasets for sandbox testing instead of generating new test logs for each script

**When NOT to apply DRY in labs:**

- Quick proof-of-concept scripts meant to be discarded are acceptable as one-offs
- Use judgment: optimize for clarity if the code is unlikely to be reused

### Clean Code Principles

#### Meaningful Names

Use clear, intent-revealing variable names that describe what the data represents.

```python
# Good
suspicious_inbound_connections = [c for c in connections if c.port in [445, 3389]]

# Bad
x = [c for c in conn_list if c.p in dangerous_ports]
```

Function names should describe the action: `detect_brute_force()`, `extract_indicators()`, `build_alert_summary()`.

#### Small Functions (Single Responsibility)

Each function should do one thing well.

```python
# Good: Separate concerns
def read_log_file(filepath):
    with open(filepath) as f:
        return f.readlines()

def parse_log_entries(raw_lines):
    return [parse_syslog_message(line) for line in raw_lines]

def filter_alerts(entries, threshold):
    return [e for e in entries if e.confidence >= threshold]

# Bad: Multiple responsibilities
def process_everything(filepath, threshold):
    with open(filepath) as f:
        lines = f.readlines()
    parsed = [parse(line) for line in lines]
    filtered = [p for p in parsed if p.confidence >= threshold]
    for alert in filtered:
        send_to_siem(alert)
    return filtered
```

#### Avoid Magic Numbers

Define constants with meaningful names.

```python
# Good
BRUTE_FORCE_THRESHOLD = 5  # Failed logins within 5 minutes = brute force
SIEM_TIMEOUT_SECONDS = 30
CRITICAL_CONFIDENCE = 0.95

# Bad
if failed_logins > 5:
    # Why 5? What does this mean?
```

#### Comments Should Explain WHY, Not WHAT

Code shows what it does; comments should explain the reasoning.

```python
# Good: Explains reasoning
# Use 5-minute window: most brute force tools try multiple times within this timeframe
brute_force_attempts = [
    login for login in logins
    if login.timestamp - first_attempt.timestamp <= 300
]

# Bad: Explains what code does (redundant)
# Loop through logins and filter by timestamp
for login in logins:
    if login.timestamp - first_attempt.timestamp <= 300:
```

#### Error Handling

Don't silently fail; explicitly handle and log errors.

```python
# Good
try:
    alert_data = json.loads(raw_alert)
except json.JSONDecodeError as e:
    logger.error(f"Failed to parse alert: {e}")
    continue

# Bad
try:
    alert_data = json.loads(raw_alert)
except:
    pass  # Silent failure
```

### Defensive Programming for Detection Engineering

#### Input Validation

Assume external data (logs, API responses, user input) may be malformed.

```python
def extract_source_ip(log_entry):
    if not log_entry or 'source_ip' not in log_entry:
        logger.warning(f"Missing source_ip in entry: {log_entry}")
        return None
    return log_entry['source_ip']
```

#### Fail Safely

Log and skip bad data rather than crashing the detection pipeline.

```python
for log_line in log_stream:
    try:
        parsed = parse_log_line(log_line)
        detections.extend(check_for_attacks(parsed))
    except Exception as e:
        logger.error(f"Skipping malformed log: {log_line} | Error: {e}")
        continue
```

### SOLID Principles (Adapted for Lab Scripts)

#### S — Single Responsibility Principle

Each script/module handles one detection type or operation:

- `detect_brute_force.py` — only brute force detection
- `correlate_iocs.py` — only IOC correlation
- Not one giant script doing everything

#### O — Open/Closed Principle

Scripts should be easy to extend without modifying core logic.

```python
# Good: Easy to add new detection rules
DETECTION_RULES = [
    BruteForceDetector(),
    SuspiciousFileAccessDetector(),
    UnusualNetworkActivityDetector(),
]
for rule in DETECTION_RULES:
    alerts.extend(rule.check(logs))

# Bad: Hard to extend without editing the main function
if rule_type == 'brute_force':
    # brute force logic
elif rule_type == 'file_access':
    # file access logic
# Need to edit here to add new rules
```

#### L — Liskov Substitution Principle

If building detector classes, all should behave consistently.

```python
class Detector:
    def check(self, log_entry) -> List[Alert]:
        raise NotImplementedError

class BruteForceDetector(Detector):
    def check(self, log_entry) -> List[Alert]:
        # Implementation

class DnsAnomalyDetector(Detector):
    def check(self, log_entry) -> List[Alert]:
        # Implementation
```

#### I — Interface Segregation Principle

Don't require scripts to implement methods they don't need.

```python
# Good: Specific interfaces
class LogParser:
    def parse(self, raw_log): pass

class AlertGenerator:
    def generate_alert(self, event): pass

# Bad: One bloated interface
class AllInOne:
    def parse(self): pass
    def generate_alert(self): pass
    def send_to_siem(self): pass
    def visualize_graph(self): pass
    # Scripts only need some of these
```

#### D — Dependency Inversion Principle

Depend on abstractions, not concrete implementations.

```python
# Good
def process_alerts(alert_source: AlertSource):
    for alert in alert_source.fetch():
        handle_alert(alert)

process_alerts(FileBasedAlertSource('alerts.json'))
process_alerts(SIEMAPIAlertSource(siem_client))

# Bad
def process_alerts_from_file(filepath):
    # Tightly coupled to file format
    with open(filepath) as f:
        alerts = json.load(f)
```

### Practical Lab-Specific Guidelines

#### Detection Logic Clarity

Make detection thresholds and logic explicit and testable.

```python
def is_brute_force_attack(login_attempts, window_seconds=300, threshold=5):
    """
    Detect brute force by counting failed logins in a time window.

    Args:
        login_attempts: List of failed login events with timestamp
        window_seconds: Time window to analyze (default: 300 = 5 min)
        threshold: Number of failures to trigger alert (default: 5)

    Returns:
        True if >= threshold failures within window_seconds
    """
    if not login_attempts:
        return False

    first_attempt_time = login_attempts[0].timestamp
    last_attempt_time = login_attempts[-1].timestamp
    time_diff = (last_attempt_time - first_attempt_time).total_seconds()

    return time_diff <= window_seconds and len(login_attempts) >= threshold
```

#### Correlation and Enrichment

When correlating events, make the join logic clear.

```python
# Good: Explicit correlation logic
def correlate_failed_login_to_access_attempt(failed_login, access_attempt):
    """Check if same user/host attempted unauthorized access after failed login."""
    return (
        failed_login.username == access_attempt.username and
        failed_login.source_ip == access_attempt.source_ip and
        access_attempt.timestamp - failed_login.timestamp < 60  # Within 1 minute
    )
```

#### Lab Documentation vs Production

In lab scripts, include example runs and expected outputs.

```python
"""
Example:
    python3 detect_brute_force.py auth.log --threshold 5

Output:
    [Alert] Brute force detected: user=admin, source=192.168.1.100, attempts=7
"""
```

---

**Summary:** Write code as if colleagues need to understand your threat detection logic quickly, maintain it without your help, and extend it with new detection rules. Clarity enables faster analysis and better threat hunting.

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
- **Lab-specific** — Add actual configs during lab setup, not as pre-seeded templates

Example structure (add during lab setup):

```yaml
# environment-config.yml - DO NOT COMMIT REAL CREDENTIALS
siem:
  hostname: "CHANGEME_SIEM_HOSTNAME"
  port: 8089
  # Auth: Use local .env file
```

## Naming Conventions

- **Lab scripts:** `analyse_*.py`, `setup_*.sh`, `parse_*.py`
- **Day-log files:** `YYYY-MM-DD.md`
- **Blog drafts:** `draft-001-topic-name.md`, `draft-002-...`
- **Config files:** Snake_case, descriptive names

## Code Review

All scripts are reviewed by **Sourcery AI** before committing. Flag in PR or mention to Claude.

---

**Priority:** Clarity and maintainability over optimization. This is a portfolio, not production code.
