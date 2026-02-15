# [Project Name: Enterprise Logging & Threat Hunting with Splunk]

## Executive Summary
**Objective:** To deploy a Tier-1 SIEM (Splunk Enterprise) to ingest system logs and identify brute-force authentication patterns.
**Outcome:** Successfully mapped raw syslog data to actionabe security intelligence, identifying a simulateedd attack via custom SPL queries.

## Environment & Tools
* **SIEM:** Splunk Enterprise (Linux Version 10.2.0)
* **Log Source:** /var/log/auth.log (Linux Security Events)
* **Query Language:** SPL (Splunk Processing Language)
* **Environment:** Isolated NAT Network via VirtualBox

## Step-by-Step Methodology
1. **Deployment:** Installed Splunk Enterprise on an Ubuntu server and optimized system limits (ulimit) for database performance.
2. **Data Ingestion:** Configured a local monitor input for the system's authentication log, setting the sourcetype to /var/log/auth.log for proper parsing.
3. **Brute Force Simulation:** Generated 10+ failed SSH login events tosimulate a password-spraying attack.
4. **Threat Hunting:** Developed an SPL query to aggregate failed login attempts by source IP and timestamp.

## Findings & Evidence
Splunk SPL:
index=main "Failed password"
| stats count as "Failed Attempts" by src_ip
| where "Failed Attempts" > 5

**Result:** The query successfully isolated the Attacker VM IP (10.0.2.13) as the source of the brute-force attempt.

## Remediation & Analysis
**The Problem:** Unmonitored SSH ports are primary targets for automated bots. Without log aggregation, these attempts go unnoticed until an account is compromised.
**The Solution:** 
 - Dashboarding: Created a real-time dashboard in Splunk to visualize "Logins by hour" to identify anomalies.
 - Security Hardening: Recommended teh implementation of Public Key Authentication and disabling password-based logins for all administrative accounts.
