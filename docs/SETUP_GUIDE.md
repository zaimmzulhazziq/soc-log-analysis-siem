# Setup Guide — SOC Alert Triage & Log Analysis Project (LetsDefend)

This guide walks through the full hands-on process, from creating an account to writing up your first incident report.

## Why LetsDefend?
Your Mac (MacBook Air M1, 8GB RAM) isn't enough to comfortably run a full local SIEM stack (Splunk/Wazuh/ELK all recommend 16GB+). LetsDefend solves this by hosting a real SIEM/EDR-style environment in the browser — no local resources needed, and it's a platform genuinely used by SOC training programs and referenced by recruiters.

## 1. Create your account
1. Go to https://letsdefend.io/
2. Sign up for a free account (this step is yours to do — account creation needs your own email/password).
3. Log in and open the main dashboard.

## 2. Get familiar with the platform
Explore these sections before diving in:
- **Monitoring** page — the alert queue, similar to a real SOC analyst's daily view
- **Log Management** — where you can search/inspect raw logs
- Any free/sample **case** or **alert** available on the free tier

## 3. Investigate 2–3 alerts
For each alert you pick, work through it like a real SOC L1 analyst would:
1. **What triggered it?** (rule name, source, severity)
2. **Gather context** — related logs, source/destination IPs, process info, timestamps
3. **Determine verdict** — true positive or false positive, and why
4. **Extract IOCs** — IPs, domains, file hashes, if any
5. **Decide next action** — escalate, contain, close as benign, etc. (as you would recommend to a team lead)

## 4. Write it up as a mini incident report
For each investigated alert, add an entry using this template (put these in the README.md **Findings** section, or as separate files under `docs/incident-reports/`):

```markdown
### Incident: <short title>
- **Date investigated:** YYYY-MM-DD
- **Alert/Rule:** <name>
- **Severity:** <low/medium/high/critical>
- **Summary:** What happened, in 2-3 sentences.
- **Analysis:** What you found in the logs/evidence.
- **IOCs:** IPs / domains / hashes involved (if any)
- **Verdict:** True positive / False positive
- **Recommended action:** What you'd do next as an analyst
```

## 5. Screenshots
Take screenshots of:
- The alert queue / dashboard overview
- At least one full investigation (evidence you reviewed)
- Your completed case/report view

Save them in the `screenshots/` folder and reference them from the README.

## 6. Document your findings
Back in the main README.md:
- Fill in **Findings** with your 2–3 incident write-ups (using the template above)
- Add your **screenshots** and reference them
- Fill in **Lessons Learnt** — what was new, what was tricky, what you'd do differently in a real SOC

## Notes
- Everything here happens inside LetsDefend's own environment — no real/private data or credentials should ever go into this repo.
- If you later get access to a more powerful machine, the Wazuh (Docker) or ELK route is worth revisiting for a deeper "I deployed my own SIEM" project.
