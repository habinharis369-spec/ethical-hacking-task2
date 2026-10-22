# Ethical Hacking Task 2 — Local Reconnaissance and Attack Surface Map

## Scope
- Target: OWASP Juice Shop running locally at `http://127.0.0.1:3000`
- Environment: local Docker lab owned/installed by the learner
- Testing window: [enter date and start/end time]
- Allowed methods: manual browser inspection and low-rate HTTP requests to localhost only
- Out of scope: public IPs, third-party services/accounts, destructive testing, denial of service, credential attacks, persistence, phishing, and accessing real personal data

## Contents
- `report.md` — reconnaissance report and findings
- `inventory.csv` — structured attack-surface inventory
- `evidence/http-head-headers.txt` — captured HTTP response headers from the learner's terminal
- `evidence/observations.md` — observed browser behavior and remaining work

## Before submitting
1. Fill in your name and testing window in `report.md`.
2. Add a screenshot of the browser Network tab if you collect it; redact cookies, tokens, and personal data.
3. Complete the pending observations in the inventory. Do not mark a vulnerability confirmed unless you have evidence.
4. Add your signed authorization statement to `report.md`.
5. Upload this folder/repository to GitHub or share a view-only Drive folder, then submit one link.

This package intentionally distinguishes observed facts from hypotheses. It does not claim untested vulnerabilities.

## Next reconnaissance step
Use `evidence/network-tab-checklist.md` to inspect the local app's browser requests. Record actual observations in `evidence/network-observations.md`; do not invent evidence or include cookies/tokens.
