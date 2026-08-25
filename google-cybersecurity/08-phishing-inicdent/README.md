# Phishing Alert Triage — Malicious Attachment

> Google Cybersecurity Professional Certificate — Portfolio Activity

## Overview

This activity involved triaging a simulated phishing alert sent to an HR mailbox.

The email appeared to be a job application but contained a suspicious executable attachment, `bfsvc.exe`, and a known malicious SHA-256 hash.

## Key Findings

- Display name and sender identity did not match the name used in the message
- Subject line used an unusual `Re:` prefix
- Spelling and grammar errors were present
- Attachment was an `.exe` file instead of a resume or document
- Attachment was password-protected
- Provided SHA-256 hash was known malicious

## Verdict

**True Positive — Phishing with Malicious Attachment**

The executable attachment and known malicious hash provided strong evidence that the email was malicious.

## Skills Demonstrated

- Phishing email analysis
- SOC alert triage
- IOC identification
- True-positive determination
- Incident escalation

## Artifact

The full ticket contains the alert details, investigation notes, verdict, and recommended response.

> Simulated activity completed as part of the Google Cybersecurity Professional Certificate.