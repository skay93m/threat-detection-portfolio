# Entry-Level Cybersecurity SOC Analyst Requirements Research

## Overview

This document serves as the compass for the SOC lab design. It extracts essential and desirable skills from entry-level cybersecurity postings to inform what capabilities need to be built and demonstrated.

---

## Existing Foundation & Transferable Skills

### Current Certifications

- **Microsoft Azure Fundamentals (AZ-900)** — Passed June 2025
- **Microsoft Security, Compliance, and Identity Fundamentals (SC-900)** — Passed November 2025

### Technical Skills Already Held

- **Programming:** C and Python (2016 MPharm research project)
- **Data Analysis:** Extracted and analysed data from complex systems (SLAM NHS Trust: electronic medical records, clinical trial databases, adverse event coding)
- **Systems Learning:** Rapid onboarding to unfamiliar platforms (SLAM: PMR system, prescribing systems, proprietary data analysis software)
- **IT Fundamentals:** Operating systems, system navigation, command-line basics
- **Professional Software:** Advanced Excel, SQL-adjacent queries, data visualization

### Transferable Skills from Non-Security Roles

- **Attention to detail:** Clinical pharmacy demands precision; incident response demands the same rigor
- **Pattern recognition:** Identifying medication interactions and clinical anomalies transfers directly to identifying suspicious log patterns
- **Communication to stakeholders:** Explaining clinical decisions to patients and healthcare teams transfers to explaining security findings to non-technical stakeholders
- **Process documentation:** GPhC standards compliance and incident reporting align with security incident documentation requirements
- **Quick learning:** Demonstrated ability to master new systems under pressure

---

## Industry Standards & Frameworks

Understanding these frameworks is essential for SOC operations. This lab will align detection rules and incident response workflows with these standards.

### NIST Cybersecurity Framework (CSF)

- **Identify:** Know what assets and risks exist in your environment
- **Protect:** Implement safeguards to prevent or minimize impact
- **Detect:** Identify when a cybersecurity event occurs
- **Respond:** Act immediately to contain and remediate
- **Recover:** Restore systems to normal operation

**Relevance to SOC Lab:** Detection and response components form the core of SOC operations. This lab demonstrates alignment with NIST identify/detect/respond functions.

### MITRE ATT&CK Framework

- Comprehensive matrix of adversary tactics and techniques based on real-world observations
- Organises attack patterns by: Initial Access → Execution → Persistence → Privilege Escalation → Defense Evasion → Credential Access → Discovery → Lateral Movement → Collection → Command & Control → Exfiltration → Impact
- Used by defenders to build detection rules and response procedures
- Industry standard for threat modelling and attack simulation

**Relevance to SOC Lab:** This lab tests detection of common MITRE ATT&CK techniques (SSH brute-force = Initial Access, command execution = Execution, and so on). Detection rules map directly to specific techniques.

### CIS Controls (Critical Security Controls)

- 18 prioritised security controls based on frequency and severity of attacks
- Top controls: Inventory of authorized/unauthorized assets, secure configuration, access control, security training, incident response
- Actionable guidance for security operations

**Relevance to SOC Lab:** This lab demonstrates logging and monitoring aligned with CIS Control #6 (Maintenance and Monitoring of Security Technology) and #8 (Audit Log Monitoring).

### ISO/IEC 27001:2022 & 27002:2022

- Information Security Management System (ISMS) standards
- 27001: Requirements for implementing information security
- 27002: Implementation guidance (14 domains including access control, cryptography, physical/environmental security, incident management)
- Annex A.12: Operations security (logging, monitoring, system administration)

**Relevance to SOC Lab:** Log retention, event logging standards, and incident response documentation align with ISO 27002 Annex A.12 requirements.

### NIST Special Publication 800-61: Computer Security Incident Handling Guide

- Standard incident response lifecycle: Preparation → Detection and Analysis → Containment, Eradication, and Recovery → Post-Incident Activity
- Defines roles, procedures, tools, and metrics for incident response
- Industry standard for incident response workflows

**Relevance to SOC Lab:** Incident response playbooks and documentation follow NIST 800-61 structure.

### Cyber Kill Chain (Lockheed Martin)

- Sequential stages of a cyber attack: Reconnaissance → Weaponization → Delivery → Exploitation → Installation → Command & Control → Actions on Objectives
- Helps defenders understand attack progression and design detection at each stage

**Relevance to SOC Lab:** Detection rules target specific kill chain stages (for example, command execution detection = Installation stage, network anomalies = C2 stage).

---

## Essential Criteria (Must Have)

- Experience of SIEM alerting and monitoring procedures
- Ability to inspect security logs, identify log sources, communicate findings to stakeholders
- Involvement in correlation and triage of security incidents
  - Understanding of investigation, analysis, and response techniques
  - Post-incident activity and reporting
- Firm understanding of core principles in vulnerability scanning
- Awareness of vulnerability scanning tooling
- Solid technical foundation in IT
  - Knowledge of operating systems
  - Network topology
  - Security concepts

---

## Desirable Criteria (Nice to Have)

- CompTIA Security+ Certification
- CompTIA Network+ Certification (currently in progress)
- Experience with cloud security platforms (Azure, AWS, and similar)
- Exposure to industry SIEM tools (Sentinel, Splunk, Wazuh, Elastic)
- Exposure to vulnerability scanning tools
- IT support or helpdesk experience
- Security certification (any level)

---

## Technical Capabilities Required for SOC Operations

### Log & Data Analysis

- Parse and understand security logs from multiple sources (Windows Event Logs, Linux syslog, network logs, application logs)
- Identify relevant log fields and correlate events across systems
- Filter noise and recognize significant events
- Understand log timestamps, event IDs, and severity levels
- Extract indicators of compromise (IoCs) from logs

### SIEM Operation

- Create, modify, and tune detection rules
- Set appropriate alert thresholds to minimize false positives
- Understand rule syntax and logic (AND, OR, NOT operators)
- Configure alert routing and escalation
- Build searches/queries to investigate incidents
- Use SIEM dashboards to monitor key metrics

### Incident Investigation

- Establish timeline of events during an incident
- Correlate multiple log sources to build complete picture
- Identify root cause of security events
- Document findings in clear, structured format
- Distinguish between suspicious activity and benign events

### Vulnerability Assessment

- Understand vulnerability severity ratings (CVSS)
- Interpret vulnerability scan results
- Prioritise vulnerabilities for remediation
- Communicate vulnerability findings to stakeholders
- Understand difference between active scanning and passive assessment

### Detection Rule Engineering

- Translate threat intelligence into detection logic
- Map attacks to MITRE ATT&CK techniques
- Write rules that detect attacks while minimizing false positives
- Test rules against known attack patterns
- Document rule purpose and detection logic

### Incident Response Procedures

- Follow structured incident response lifecycle (preparation → detection → containment → recovery → post-incident)
- Escalate incidents appropriately
- Document incident details: what happened, when, who was affected, impact
- Preserve evidence for post-incident review
- Participate in incident post-mortems

### Communication & Reporting

- Explain technical findings in clear, jargon-free language
- Create incident reports for non-technical stakeholders
- Present evidence and analysis concisely
- Answer follow-up questions about investigation methodology
- Document decisions and reasoning

### System & Network Knowledge

- Understand Windows and Linux operating system basics
- Recognise normal vs. abnormal system behaviour
- Understand network communication basics (ports, protocols, traffic patterns)
- Identify indicators of compromise specific to different systems
- Understand process execution and file system activity

---

## Core Responsibilities in SOC Analyst Roles

- Investigation and remediation of cyber incidents and alerts
- Correlation and triage of security incidents
- Cyber incident response planning and preparation
- Cyber incident detection, investigation, and analysis
- Cyber incident containment, eradication, and recovery
- Vulnerability scanning and reporting to stakeholders
- Improving detection capabilities within SIEM (tuning rules, reducing false positives)
- Assessment of security tooling and recommendations for improvements

---

## Common Industry Tools

- **SIEM Platforms:** Microsoft Sentinel, Splunk, Wazuh, Elastic Stack
- **Vulnerability Scanning:** Tenable Nessus, OpenVAS
- **Log Analysis & Collection:** Logstash, Fluentd, Splunk Universal Forwarder
- **Endpoint Detection:** Sysmon, EDR platforms (LimaCharlie, CrowdStrike, etc.)
- **IDS/IPS:** Suricata, Snort

---

## Key Insights for SOC Lab Design

### What Entry-Level SOC Roles Are NOT About

- Writing exploit code
- Advanced penetration testing
- Mastery of every security tool
- Deep networking knowledge
- Advanced cryptography

### What Entry-Level SOC Roles ARE About

- **Log literacy:** Reading security logs and understanding what happened
- **Alert triage:** Distinguishing signal from noise
- **Incident response workflow:** Understanding the detection → investigation → response lifecycle
- **Communication:** Explaining technical findings to non-technical stakeholders
- **Tool operation:** Using a SIEM to investigate incidents and improve detection
- **Attention to detail:** Spotting anomalies in system behaviour

---

## Success Criteria for This Lab

After completing this SOC lab, you should be able to credibly demonstrate:

- "I have built and tuned detection rules for common attack patterns aligned with MITRE ATT&CK and NIST frameworks"
- "I understand how to read and correlate logs from multiple sources (Windows, Linux, network) following NIST 800-61 incident response procedures"
- "I can distinguish between benign system activity and actual threats using industry-standard frameworks"
- "I've documented incident response workflows following NIST 800-61 and tested them against simulated attacks"
- "I understand tradeoffs between alert fidelity and operational burden"
- "I can explain my detection logic to both technical and non-technical audiences"
- "I understand how my detection work aligns with NIST CSF Detect and Respond functions"

---

## Research Methodology

I compiled this document with the assistance of Claude and GitHub Copilot by:

- Analysing entry-level SOC analyst job descriptions across multiple sectors and regions
- Reviewing industry standards for SOC operations (NIST CSF, MITRE ATT&CK, CIS Controls, ISO 27001/27002)
- Synthesising feedback from security professionals on what matters in practice
- Cross-referencing essential versus desirable criteria to identify genuine skill gaps

The goal: Build a lab that demonstrates these capabilities through evidence, aligned with industry standards, rather than relying on credentials alone.
