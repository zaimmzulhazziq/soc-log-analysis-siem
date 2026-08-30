# SOC Log Analysis & SIEM Project

## 🎯 Objective
Practice a core SOC L1 skill: ingest raw logs into a SIEM, write detection searches to spot suspicious activity, and document findings the way a real analyst would report them.

## 🛠️ Tools & Dataset
- **SIEM:** Splunk Free (Splunk Enterprise free license, local install)
- **Dataset:** Public security log samples from [SecRepo](https://www.secrepo.com/) (Apache access logs with scan/attack traffic) — no real/private data used.

## 📋 Steps
1. Install Splunk Free locally and get it running on `localhost:8000`.
2. Download and ingest the sample dataset as a new index.
3. Write SPL searches to detect:
   - Repeated failed requests / brute-force-like patterns
   - Suspicious user agents (scanners, known attack tools)
   - Possible SQL injection or path traversal attempts in request strings
   - Unusual spikes in error status codes (4xx/5xx)
4. Build one simple dashboard panel summarizing the top findings.
5. Document findings, screenshots, and lessons learnt below.

See [docs/SETUP_GUIDE.md](docs/SETUP_GUIDE.md) for the full step-by-step walkthrough.

## 🔍 Findings
> 🚧 To be filled in after hands-on analysis.

## 📸 Screenshots
> 🚧 To be added.

## 📚 Lessons Learnt
> 🚧 To be filled in.
