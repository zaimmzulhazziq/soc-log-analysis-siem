# Setup Guide — SOC Log Analysis & SIEM Project

This guide walks through the full hands-on setup, from installing the SIEM to writing the first detection searches.

## 1. Install Splunk Free
1. Go to https://www.splunk.com/en_us/download/splunk-enterprise.html and download the macOS installer (free license, no credit card needed).
2. Run the installer, accept the license, set an admin username/password when prompted.
3. Start Splunk (the installer usually offers to start it, or run `splunk start` from the install directory).
4. Open http://localhost:8000 in your browser and log in with the admin account you created.

## 2. Get sample security log data
1. Go to https://www.secrepo.com/ (public repository of security-relevant sample logs, safe to use — no real/private data).
2. Download an Apache access log sample (these include normal traffic plus scan/attack patterns, which makes them useful for detection practice).
3. In Splunk: **Settings → Add Data → Upload**, select the downloaded log file, and create a new index, e.g. `soc_lab`.

## 3. Example SPL searches to try
Run these in the Splunk Search bar (adjust the index name to match what you created):

```spl
# Top source IPs by request count
index=soc_lab | stats count by clientip | sort -count | head 10

# Requests with 4xx/5xx errors, grouped by IP
index=soc_lab status>=400 | stats count by clientip, status | sort -count

# Look for common attack patterns in the request URI (SQLi / path traversal)
index=soc_lab (uri="*union*select*" OR uri="*../*" OR uri="*<script*") 
| table _time clientip uri status

# Suspicious / scanner-like user agents
index=soc_lab useragent="*nikto*" OR useragent="*sqlmap*" OR useragent="*nmap*"
| stats count by clientip, useragent
```

## 4. Build a simple dashboard
1. Save 2–3 of your searches as reports.
2. Create a new Dashboard and add each report as a panel (e.g. "Top Source IPs", "Error Status Spikes", "Suspicious User Agents").
3. Take a screenshot of the finished dashboard for the portfolio.

## 5. Document your findings
Back in the main README.md:
- Fill in **Findings** — what did you actually discover in the sample data? (e.g. "IP X made 400+ requests with SQLi patterns in a 5-minute window")
- Add your dashboard/search **screenshots** to a `screenshots/` folder and reference them.
- Fill in **Lessons Learnt** — what was new, what was tricky, what you'd do differently in a real SOC.

## Notes
- All data used here is public sample data from SecRepo — safe to commit and share publicly.
- Keep any real/personal log data out of this repo.
