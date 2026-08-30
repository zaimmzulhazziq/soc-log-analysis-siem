# Setup Guide — SOC Log Analysis & SIEM Project (Wazuh)

This guide walks through the full hands-on setup, from deploying the SIEM to writing the first detection searches.

## ⚠️ Check your Mac's specs first
The Wazuh single-node Docker stack officially recommends **16 GB RAM** and **~50 GB free disk space**. Check via  → About This Mac. If your Mac has less RAM, the stack may run slowly or the indexer may fail to start — in that case, come back and we can switch to a lighter option (ELK) or the Python-only route instead.

## 1. Install prerequisites
1. Install **Docker Desktop** for Mac (Apple Silicon build): https://www.docker.com/products/docker-desktop/
2. Make sure **Git** is installed (`git --version` in Terminal; macOS usually prompts to install Xcode Command Line Tools if missing).
3. Open Docker Desktop and make sure it's running (whale icon in the menu bar).

## 2. Clone the Wazuh Docker repo
In Terminal:
```bash
git clone https://github.com/wazuh/wazuh-docker.git -b v4.14.7
cd wazuh-docker/single-node/
```

## 3. Generate certificates
```bash
docker compose -f generate-indexer-certs.yml run --rm generator
```

## 4. Start the stack
```bash
docker compose up -d
```
First startup takes about a minute while the indexer initializes. Check status with:
```bash
docker compose ps
```

## 5. Log in to the dashboard
- URL: https://localhost (port 443, self-signed cert — your browser will warn, that's expected for a local lab; proceed anyway)
- Default credentials are set during certificate/config generation — check the `config.yml` / generated credentials output from step 3, or the repo's own README, for the exact admin username and password. Do **not** commit real credentials to this repo.

## 6. Get sample security log data
1. Go to https://www.secrepo.com/ (public repository of security-relevant sample logs, safe to use — no real/private data).
2. Download an Apache access log sample (includes normal traffic plus scan/attack patterns — useful for detection practice).
3. In the Wazuh dashboard, use the log ingestion / custom log source options to load the sample file for analysis (Wazuh is agent-based by default, but for a local lab you can also explore its log analysis and rule-testing tools directly on an uploaded sample).

## 7. Things to look for / detections to write
- Repeated failed requests from the same IP (brute-force-like pattern)
- Suspicious user agents (scanners, known attack tools like nikto, sqlmap, nmap)
- Possible SQL injection or path traversal attempts in the request URI
- Unusual spikes in 4xx/5xx error status codes

## 8. Build a simple dashboard
1. Save 2–3 of your searches/visualizations.
2. Add them to a dashboard (e.g. "Top Source IPs", "Error Status Spikes", "Suspicious User Agents").
3. Take a screenshot of the finished dashboard for the portfolio.

## 9. Document your findings
Back in the main README.md:
- Fill in **Findings** — what did you actually discover in the sample data?
- Add your dashboard/search **screenshots** to the `screenshots/` folder and reference them.
- Fill in **Lessons Learnt** — what was new, what was tricky, what you'd do differently in a real SOC.

## Notes
- All data used here is public sample data from SecRepo — safe to commit and share publicly.
- Keep any real/personal log data, and any real credentials, out of this repo.
- When done experimenting, you can stop the stack with `docker compose down` (add `-v` to also remove data volumes) from the `wazuh-docker/single-node/` folder.
