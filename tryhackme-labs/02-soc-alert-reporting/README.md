# TryHackMe — Alert Reporting and Escalation

## Overview

This room focused on how SOC analysts document security incidents and determine when an alert should be escalated for further investigation.

The exercises involved analyzing alert context, writing concise incident reports using the **Five Ws**, identifying suspicious activity, and preparing escalation notes for L2 analysts.

---

## Skills Practiced

`Alert Reporting` `SOC Escalation` `Phishing Analysis` `Process Tree Analysis` `Active Directory Discovery` `Incident Documentation`

---

## 1. Phishing Alert Reporting

A phishing alert involved an email claiming to be from Microsoft Support and informing the recipient of an urgent Microsoft Teams pricing increase.

### Indicators Reviewed

* Failed SPF authentication
* Failed DKIM authentication
* Urgent social-engineering language
* Unexpected `.rar` attachment
* Sender impersonating Microsoft Support

### Five Ws

| Question  | Finding                                                          |
| --------- | ---------------------------------------------------------------- |
| **Who**   | Eddie Huffman, IT Manager                                        |
| **What**  | Received a suspicious email containing `REPORT.rar`              |
| **When**  | March 27, 2025 at 19:25                                          |
| **Where** | Corporate email account                                          |
| **Why**   | Failed sender authentication, urgency, and suspicious attachment |

### Assessment

The failed SPF and DKIM checks, combined with the suspicious attachment and social-engineering content, supported a phishing classification.

**Verdict: True Positive**

---

## 2. Suspicious Active Directory Discovery

Another alert detected several discovery commands being executed on a Microsoft Exchange server.

### Observed Commands

```text
hostname
whoami /priv
net group "Domain Admins" /domain
nltest /dclist:tryhackme.thm
```

### Process Chain

```text
w3wp.exe
   ↓
revshell.exe
   ↓
cmd.exe
```

The IIS worker process `w3wp.exe` spawned `revshell.exe`, which then launched `cmd.exe` under `NT AUTHORITY\SYSTEM`.

The commands were used to:

* identify the compromised host
* enumerate current privileges
* identify Domain Admin accounts
* locate domain controllers

### Assessment

The combination of a reverse-shell process, SYSTEM-level execution, and Active Directory discovery activity was consistent with post-compromise reconnaissance.

**Verdict: True Positive**

---

## 3. L2 Escalation

The Active Directory discovery alert required escalation because the activity indicated that a highly privileged server may have been compromised.

### Escalation Summary

`DMZ-MSEXCHANGE-2013` showed suspicious post-compromise behavior. The IIS worker process spawned a reverse-shell executable, which launched `cmd.exe` as `NT AUTHORITY\SYSTEM`. Multiple commands were then executed to enumerate privileges, Domain Admin accounts, and domain controllers.

The activity was escalated for further investigation and containment.

### Recommended Follow-Up

* Investigate how `w3wp.exe` spawned the reverse shell
* Review network activity associated with `revshell.exe`
* Identify additional commands or payloads executed on the host
* Check for lateral movement
* Review authentication activity involving privileged accounts
* Preserve relevant host and network evidence

---

## Key Takeaways

* Alert reports should clearly explain **who, what, when, where, and why**.
* Authentication failures such as SPF and DKIM failures should be evaluated together with other indicators.
* Process ancestry can provide critical context during endpoint investigations.
* Legitimate Windows commands can become suspicious depending on the process, user, host, and surrounding activity.
* L1 analysts should escalate alerts when the available evidence suggests a compromise requires deeper investigation or containment.

---

## Artifacts

Supporting screenshots and sanitized lab evidence are available in the [`artifacts/`](./artifacts/) directory.

---

## Platform

**TryHackMe — Alert Reporting and Escalation**

> This write-up documents my own analysis and learning from a guided TryHackMe SOC exercise. Challenge flags and direct task answers are intentionally excluded.
