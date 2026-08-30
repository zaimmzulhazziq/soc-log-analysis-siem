# SOC Log Analysis & SIEM Project

## 🎯 Objective
Practice a core SOC L1 skill: ingest raw logs into a SIEM, write detection rules/searches to spot suspicious activity, and document findings the way a real analyst would report them.

## 🛠️ Tools & Dataset
- **SIEM:** [Wazuh](https://wazuh.com/) (free, open-source SIEM/XDR) — deployed locally via Docker (single-node stack: indexer + manager + dashboard)
- **Dataset:** Public security log samples from [SecRepo](https://www.secrepo.com/) (Apache access logs with scan/attack traffic) — no real/private data used.

## 📋 Steps
1. Install Docker Desktop and deploy the Wazuh single-node Docker stack locally.
2. Log in to the Wazuh dashboard and get familiar with the interface.
3. Ingest the sample log dataset for analysis.
4. Write searches/rules in the Wazuh dashboard to detect:
   - Repeated failed requests / brute-force-like patterns
   - Suspicious user agents (scanners, known attack tools)
   - Possible SQL injection or path traversal attempts in request strings
   - Unusual spikes in error status codes (4xx/5xx)
5. Build one simple dashboard panel summarizing the top findings.
6. Document findings, screenshots, and lessons learnt below.

See [docs/SETUP_GUIDE.md](docs/SETUP_GUIDE.md) for the full step-by-step walkthrough.

## 🔍 Findings
> 🚧 To be filled in after hands-on analysis.

## 📸 Screenshots
> 🚧 To be added.

## 📚 Lessons Learnt
> 🚧 To be filled in.
