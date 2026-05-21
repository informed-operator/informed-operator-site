---
title: "Business Continuity & Disaster Recovery Plan"
summary: "A full BCP/DRP with ransomware threat modeling, asset classification, recovery objectives, and incident response structure — developed as graduate coursework."
category: "Security & Forensics"
tags: [Incident Response, Threat Modeling, Documentation]
featured: true
---

## Overview

This Business Continuity and Disaster Recovery Plan was developed as a capstone project for the Security Management course in the M.S. Information Science program at the University of Pittsburgh. The plan covers a mid-sized fictional professional services firm and is structured to meet NIST SP 800-34 guidelines.

## Scope

The plan addresses three primary threat scenarios:

- **Ransomware attack** targeting file servers and backup infrastructure
- **Extended power outage** affecting primary datacenter operations
- **Key personnel loss** during an active incident

## Key Components

### Asset Classification

Critical systems were classified by recovery priority:

| Tier | Systems | RTO | RPO |
|------|---------|-----|-----|
| 1 — Critical | Authentication, email, VPN | 4 hrs | 1 hr |
| 2 — Important | File storage, CRM | 24 hrs | 4 hrs |
| 3 — Standard | Internal wikis, reporting | 72 hrs | 24 hrs |

### Ransomware Threat Analysis

The ransomware scenario draws on the MITRE ATT&CK framework to model the attack chain: initial access via phishing, lateral movement, privilege escalation, and deployment. The plan addresses the specific failure modes that allowed the 2021 Colonial Pipeline and Kaseya attacks to succeed — particularly the gap between air-gapped backup assumptions and actual backup network segmentation.

### Incident Response Structure

The IR structure defines roles, escalation paths, and communication protocols for the first 72 hours of a ransomware incident — including the containment/eradication/recovery sequence and the decision criteria for ransom payment consideration vs. recovery from backup.

## Takeaways

The most instructive part of this exercise was modeling the backup infrastructure attack surface. Many BCP/DRP documents assume backups are safe because they exist. The ransomware scenarios that actually succeed — Maze, REvil, BlackCat — specifically target backup systems first. A plan that doesn't account for that failure mode is a plan that won't survive the incident it was written for.
