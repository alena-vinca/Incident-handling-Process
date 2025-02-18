# Incident-handling-Process
---

# HTB - Incident Handling Process

## Table of Contents
- [Incident Handling](#incident-handling)
  - [Definition & Scope](#definition--scope)
  - [Value of Incident Handling](#value-of-incident-handling)
  - [Incident Prioritization](#incident-prioritization)
  - [Incident Manager Role](#incident-manager-role)
- [Cyber Kill Chain](#cyber-kill-chain)
  - [Stages](#stages)
  - [Key Points](#key-points)
  - [Question](#question)
- [Incident Handling Process Overview](#incident-handling-process-overview)
  - [Main Activities](#main-activities)
  - [Key Points](#key-points-1)
  - [Question](#question-1)
- [Preparation Stage (Part 1)](#preparation-stage-part-1)
  - [Preparation Goals](#preparation-goals)
  - [Preparation Essentials](#preparation-essentials)
  - [Key Documentation](#key-documentation)
  - [Reporting Capability](#reporting-capability)
  - [Independent Systems](#independent-systems)
  - [Questions](#questions)
- [Preparation Stage (Part 2)](#preparation-stage-part-2)
  - [Protective Measures Overview](#protective-measures-overview)
  - [Recommended Protections](#recommended-protections)
  - [Questions](#questions-1)
- [Detection & Analysis Stage (Part 1)](#detection--analysis-stage-part-1)
  - [Sources of Detection](#sources-of-detection)
  - [Detection Layers](#detection-layers)
  - [Initial Investigation](#initial-investigation)
  - [Incident Severity & Extent](#incident-severity--extent)
  - [Confidentiality & Communication](#confidentiality--communication)
  - [Question](#question-2)
- [Detection & Analysis Stage (Part 2)](#detection--analysis-stage-part-2)
  - [Investigation Goal](#investigation-goal)
  - [Three-Step Cyclic Process](#three-step-cyclic-process)
  - [Creation & Usage of IOCs](#creation--usage-of-iocs)
  - [Identifying New Leads & Impacted Systems](#identifying-new-leads--impacted-systems)
  - [Data Collection & Analysis](#data-collection--analysis)
  - [Question](#question-3)
- [Containment, Eradication, & Recovery Stage](#containment-eradication--recovery-stage)
  - [Containment](#containment)
  - [Eradication](#eradication)
  - [Recovery](#recovery)
  - [Question](#question-4)
- [Post-Incident Activity Stage](#post-incident-activity-stage)
  - [Purpose](#purpose)
  - [Reporting](#reporting)
  - [Lessons Learned & Improvements](#lessons-learned--improvements)
  - [Question](#question-5)

---

## Incident Handling

### Definition & Scope
- **Event:** Any action in a system or network.
- **Incident:** An event with a negative impact.
- **IT Security Incident:** An event intentionally causing harm to a computer system.

### Value of Incident Handling
- Minimizes information theft and service disruption.  
- Ensures a systematic, trained response to reduce impact.  
- Effective decisions before, during, and after an incident significantly affect the outcome.

### Incident Prioritization
- Different incidents have different impacts.  
- High-severity incidents need immediate focus and resources.  
- Lower-priority incidents might still require initial checks to confirm if they are genuine security incidents.

### Incident Manager Role
- Often a SOC Manager, CISO/CIO, or trusted third-party.  
- Has authority to assign tasks and direct other teams.  
- Manages overall communication and tracks actions taken during the incident.

---

## Cyber Kill Chain

### Stages
1. **Recon (Information Gathering)**
   - Attacker chooses a target and gathers data (e.g., social media, company websites, job ads, scans).
   - Goal: Learn about the target’s environment and security tools.

2. **Weaponize (Prepare the Attack)**
   - Attacker creates or customizes malware and embeds it into an exploit/payload.
   - Often designed to bypass antivirus or EDR.
   - Main focus: Gain remote access and ensure persistence.

3. **Delivery (Send the Payload)**
   - Attacker gets the exploit/payload to the target (e.g., phishing emails, malicious links, USB drives).

4. **Exploitation (Execution of Malicious Code)**
   - Triggering the exploit or payload on the victim’s system.
   - Aim: Execute code that grants attacker control/access.

5. **Installation (Malware Takes Root)**
   - Malware is installed on the compromised system.
   - Ensures long-term access and hides attacker’s presence.

6. **Command and Control (Remote Control)**
   - Attacker establishes a communication channel with compromised machines.
   - Can download additional scripts or tools as needed.

7. **Actions/Objectives (Final Goal)**
   - Could be data theft, ransomware, financial fraud, etc.
   - May involve seeking highest-level access for a broader impact.
   - Ransomware encrypts data; paying ransom is not recommended.

### Key Points
- Process isn’t strictly linear—attackers may revisit earlier stages.
- **Goal:** Detect and stop attackers as early as possible.

### Question
> **Q:** In which stage of the cyber kill chain is malware developed?  
> **A:** Weaponize

---

## Incident Handling Process Overview

- **Incident Handling Process (NIST) Stages**  
  1. Preparation  
  2. Detection & Analysis  
  3. Containment, Eradication & Recovery  
  4. Post-Incident Activity

### Main Activities
- **Investigation:** Find "patient zero," build a timeline, identify tools/malware used, and note what systems were compromised.  
- **Recovery:** Develop and implement a recovery plan; resume normal operations once contained.

### Key Points
- The process is **cyclical** (not purely linear).  
- Don’t skip steps—fully address all affected systems before moving on.  
- After handling the incident, create a **report** and perform **lessons learned** to prevent similar incidents.

### Question
> **Q:** True or False: Incident handling contains two main activities. These are investigating and reporting.  
> **A:** False

---

## Preparation Stage (Part 1)

### Preparation Goals
- Establish/maintain an incident handling capability.  
- Implement protective measures.

### Preparation Essentials
- **Skilled Team:** In-house or outsourced, but with basic in-house understanding.  
- **Trained Workforce:** Security awareness for all staff.  
- **Policies/Documentation:** Up-to-date contact info, IR plan, asset inventory, network diagrams.  
- **Tools & Hardware:** Forensic workstations, software, network equipment, “jump bag” for quick response.

### Key Documentation
- Contact info (legal, management, IT support, law enforcement).  
- Incident response policy, plan, and procedures.  
- System/network baselines (clean states).  
- Rapid procurement process for urgent tool purchases.

### Reporting Capability
- Document steps and evidence (who, what, where, why, how).  
- Keep notes with timestamps, actions taken, results, and responsible person.

### Independent Systems
- Use a separate, secure system for investigation documentation and communication.  
- Assume the organization’s main environment may be compromised.

### Questions
> **Q:** What should we have prepared and always ready to ‘grab and go’?  
> **A:** Jump bag  
>
> **Q:** True or False: Using baselines, we can discover deviations from the golden image, which aids in discovering suspicious or unwanted changes.  
> **A:** True

---

## Preparation Stage (Part 2)

### Protective Measures Overview
- Protective actions aren’t solely the incident team’s job but crucial for effective response.  
- Knowledge of these measures helps responders understand entry points and artifacts.

### Recommended Protections
- **DMARC:** Prevents email spoofing; requires careful testing.  
- **Endpoint Hardening & EDR:**
  - Use CIS/Microsoft baselines.  
  - Disable/limit harmful services (LLMNR, PowerShell, etc.).  
  - Enforce least privilege (LAPS, remove admin rights).  
  - Whitelist execution if possible (block scripts in user-writable folders).  
  - Deploy EDR that integrates with AMSI.  
- **Network Protection:**
  - Segment critical systems; minimize connections.  
  - Use IDS/IPS with SSL interception.  
  - Restrict network access to approved devices (802.1x, Conditional Access).  
- **Privilege Identity Management / MFA / Passwords:**
  - Strong passphrases over simple complex passwords.  
  - MFA for all administrative access.  
- **Vulnerability Scanning:**
  - Scan continuously; address high/critical issues quickly.  
  - Segment unpatched systems if you cannot remediate.  
- **User Awareness Training:**
  - Train users to spot/report suspicious behavior.  
  - Conduct regular tests (phishing, dropped USB sticks, etc.).  
- **Active Directory Security Assessment:**
  - Check for misconfigurations, known AD exploit paths.  
  - Conduct regular assessments or bring in external experts if needed.  
- **Purple Team Exercises:**
  - Combine red team (attackers) and blue team (defenders).  
  - Identify gaps in logging, detection, and response.  
  - Strengthen incident team readiness.

### Questions
> **Q:** What can we use to block phishing emails pretending to originate from our mail server?  
> **A:** DMARC  
>
> **Q:** True or False: “Summer2021!” is a complex password.  
> **A:** True

---

## Detection & Analysis Stage (Part 1)

### Sources of Detection
- Employees noticing unusual behavior.  
- Alerts from security tools (EDR, IDS, etc.).  
- Threat hunting activities.  
- Third-party notifications.

### Detection Layers
1. **Perimeter:** Firewalls, DMZ, external IDS/IPS.  
2. **Internal Network:** Local firewalls, host IDS/IPS.  
3. **Endpoints:** Antivirus, EDR.  
4. **Applications:** App/service logs, monitoring.

### Initial Investigation
- Gather info (date/time, who reported, type of incident).  
- Identify impacted systems (location, owner, current state).  
- Document actions so far (ongoing or stopped?).  
- Build an incident timeline (events sorted by time, note source of evidence).

### Incident Severity & Extent
- Assess impact, exploitation requirements, and effect on business-critical systems.  
- Check number of systems affected, exploit prevalence, worm-like behavior.  
- High-impact incidents require immediate response/escalation.

### Confidentiality & Communication
- Keep incident details on a need-to-know basis.  
- Communication often handled by legal or appointed personnel.  
- Set investigation goals; update management on progress/changes.

### Question
> **Q:** True or False: Can a third-party vendor be a source of detecting a compromise?  
> **A:** True

---

## Detection & Analysis Stage (Part 2)

### Investigation Goal
- Understand **how** the incident happened and **which** systems/data were impacted.  
- If root cause is unknown, attackers can return the same way.

### Three-Step Cyclic Process
1. **Create & Use IOCs** (Indicators of Compromise)  
2. **Identify New Leads & Impacted Systems**  
3. **Collect & Analyze Data** from identified systems

### Creation & Usage of IOCs
- IOCs = signs that an incident has occurred (IPs, file hashes, etc.).  
- Standards like OpenIOC or Yara structure and share IOCs.  
- Use caution when connecting to compromised systems—avoid caching privileged credentials (PsExec nuances).

### Identifying New Leads & Impacted Systems
- IOC hits can reveal additional compromised devices or false positives.  
- Prioritize systems offering high potential for new evidence.

### Data Collection & Analysis
- Choose **live response** (collect data while running) or **system shutdown** (risk losing memory artifacts).  
- Analyze malware, disk forensics, memory forensics.  
- Maintain **chain of custody** for legal admissibility.

### Question
> **Q:** During an investigation, we discovered a malicious file with an MD5 hash of `b40…24a`. How do we usually call such a hash value in investigations? (Abbreviation)  
> **A:** IOC

---

## Containment, Eradication, & Recovery Stage

### Containment
- **Goal:** Prevent further damage/spread after the investigation reveals scope.  
- **Short-Term Containment:**
  - Quick actions with minimal system changes (isolate systems, pull cables).
  - Preserves evidence and allows for deeper planning.  
- **Long-Term Containment:**
  - More permanent measures (password changes, patching, firewall rules).
  - Coordinate with stakeholders and business teams.

### Eradication
- **Goal:** Completely remove the root cause and all remnants of the incident.  
- Typical actions: Remove malware, rebuild/restore systems from clean backups, apply patches/hardening.

### Recovery
- **Goal:** Safely return systems to normal operation while monitoring for reinfection or attacker return.  
- Verify system functionality and data integrity before reintroducing to production.  
- **Monitoring Post-Recovery:** Watch for unusual logons, processes, or registry changes.  
- Larger incidents may need **phased** recovery: quick wins first, long-term improvements later.

### Question
> **Q:** True or False: Patching a system is considered a short-term containment.  
> **A:** False

---

## Post-Incident Activity Stage

### Purpose
- Document the incident, analyze team performance, and improve future capabilities.  
- Reflect on what happened, how it was handled, and how to strengthen defenses.

### Reporting
- Final report answers:
  - What happened? When?  
  - Team performance vs. plans/procedures  
  - Business collaboration (response time, info provided)  
  - Containment & eradication actions  
  - Preventive measures for similar incidents  
  - Needed tools/resources for better detection/analysis  
- Reports measure incident impact, time spent, and actions taken.  
- Serve as references for future incidents or legal proceedings.

### Lessons Learned & Improvements
- Conduct a meeting with all stakeholders soon after the incident.  
- Evaluate and update plans, playbooks, policies, and procedures if necessary.  
- Check team readiness, tools, and training requirements.  
- Provide training opportunities by reviewing the incident with new members.

### Question
> **Q:** True or False: We should train junior team members as part of post-incident activities.  
> **A:** True

---
