# NIST CSF Incident Response — ICMP Flood DoS

> Google Cybersecurity Professional Certificate — Portfolio Activity

## Overview

This activity involved analyzing a simulated **ICMP flood Denial-of-Service (DoS) attack** and applying the **NIST Cybersecurity Framework (CSF)** to improve the organization’s network security.

The attack disrupted internal network services for approximately two hours after a malicious actor flooded the network with ICMP packets through an improperly configured firewall.

---

## Scenario

During the incident, internal network services became unavailable because the network was overwhelmed by incoming ICMP traffic.

The incident response team contained the attack by:

* Blocking incoming ICMP packets
* Taking non-critical services offline
* Restoring critical network services

The investigation later identified an improperly configured firewall as the main weakness that allowed the ICMP flood to reach the internal network.

---

## NIST CSF Analysis

| Function     | Action                                                                                                                              |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| **Identify** | Review firewall configurations, network assets, and security controls regularly to identify vulnerabilities and configuration gaps. |
| **Protect**  | Apply ICMP rate limiting, source IP verification, secure firewall rules, and network hardening controls.                            |
| **Detect**   | Use network monitoring and IDS/IPS tools to identify abnormal ICMP traffic patterns and generate alerts.                            |
| **Respond**  | Block malicious traffic, contain affected services, investigate the incident, and prioritize restoration of critical systems.       |
| **Recover**  | Restore affected services, verify network stability, review the incident, and improve security controls and recovery procedures.    |

---

## Security Improvements

Following the incident, the organization implemented:

* Firewall rules to limit incoming ICMP traffic
* Source IP verification to identify spoofed traffic
* Network monitoring for abnormal traffic patterns
* IDS/IPS filtering for suspicious ICMP traffic

---

## Root Cause and Impact

**Root cause:** An improperly configured firewall allowed unrestricted ICMP traffic into the network.

**Impact:** The ICMP flood overwhelmed network resources and caused internal services to become unavailable for approximately two hours.

---

## Skills Demonstrated

* NIST Cybersecurity Framework application
* Incident response planning
* DoS attack analysis
* Firewall security concepts
* IDS/IPS and network monitoring concepts
* Root-cause analysis
* Security remediation planning

---

## Reflection

This activity reinforced that incident response does not end when an attack is contained. Security teams must also identify why the incident was successful, improve preventive and detective controls, restore affected systems, and use lessons learned to reduce the likelihood of recurrence.

The NIST CSF provides a structured way to connect these activities through **Identify, Protect, Detect, Respond, and Recover**.

---

## Key Takeaway

`ICMP Flood → Network Disruption → Containment → Investigation → Security Improvements`

A successful incident response should both restore normal operations and strengthen the organization against similar attacks in the future.

---

## Artifact

The accompanying NIST CSF analysis contains the full incident response plan and security recommendations.

> This activity was completed as part of the Google Cybersecurity Professional Certificate using a simulated cybersecurity incident.
