# Local Reconnaissance and Attack Surface Map

**Track:** Ethical Hacking  
**Level:** Beginner-friendly  
**Learner:** [Enter your name]  
**Date:** 22 October 2026 (edit if needed)  
**Testing window:** [Enter start time and end time, local time]

## 1. Scope and authorisation

- **Target:** `http://127.0.0.1:3000`
- **Application:** OWASP Juice Shop
- **Environment:** local Docker lab; container previously identified as `juice-shop`
- **Network boundary:** localhost only
- **Purpose:** enumerate visible application surfaces and record observations with risk hypotheses.
- **Out of scope:** public systems/IPs, EdVyro, other students, third-party accounts, denial of service, credential stuffing, phishing, malware, persistence, destructive payloads, and real personal data.

**Authorisation statement — sign before submission:**  
“I confirm that the target documented in this report is a local lab that I own or am explicitly authorised to test. I performed only the activities within the stated scope and testing window, and did not intentionally target third-party systems or access real personal data.”

Name: ____________________  
Signature: ____________________  
Date: ____________________

## 2. Methodology

1. Confirmed the local web application responded at `127.0.0.1:3000`.
2. Requested HTTP response headers using `curl.exe -I http://127.0.0.1:3000`.
3. Manually inspected the application’s product listing and navigation.
4. Entered the ordinary search term `apple` and recorded the returned results.
5. Further route/network inspection remains pending; no vulnerability is confirmed by the observations below.

## 3. Findings

### F-01 — HTTP response headers observed

**Affected component:** HTTP response from the local application  
**Evidence:** `evidence/http-head-headers.txt`

Observed response:
- Status: `HTTP/1.1 200 OK`
- `Access-Control-Allow-Origin: *`
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: SAMEORIGIN`
- `Feature-Policy: payment 'self'`
- `X-Recruiting: /#/jobs`
- `Content-Type: text/html; charset=UTF-8`

**Interpretation:** The server responded successfully. `nosniff` and `SAMEORIGIN` are present. The wildcard CORS header is worth checking against specific endpoints and intended cross-origin requirements, but this header alone does not prove a vulnerability. The custom `X-Recruiting` header reveals a jobs-related route; this is an observation, not necessarily a security issue.

**Impact:** No adverse impact demonstrated during this header check.  
**Reproducible steps:**
1. Start the local Juice Shop lab.
2. Open PowerShell.
3. Run `curl.exe -I http://127.0.0.1:3000`.
4. Compare the returned headers with the evidence file.

**Remediation:** No change is justified solely from this initial observation. Review CORS configuration against the application’s intended cross-origin access and restrict it where appropriate.  
**Retest result:** Initial header capture returned HTTP 200. Further endpoint-specific verification is pending.  
**Severity:** Undetermined; no confirmed vulnerability.

### F-02 — Product search returns matching products

**Affected component:** Product search and result display  
**Evidence:** Learner entered the ordinary term `apple`; the app returned:
- Apple Juice (1000ml) — `1.99¤`
- Apple Pomace — `0.89¤`
- Pineapple Juice (1000ml) — `2.99¤`

**Impact:** No adverse impact demonstrated. The normal search behavior worked.  
**Reproducible steps:**
1. Open `http://127.0.0.1:3000`.
2. Open the search bar using the magnifying-glass icon.
3. Enter `apple`.
4. Observe the listed matching products.

**Risk hypothesis:** Input handling and result rendering may be reviewed if later evidence suggests a weakness. The normal search result does not demonstrate injection or another vulnerability.  
**Remediation:** None indicated by this observation alone.  
**Retest result:** Normal search returned three matching products.

## 4. Attack-surface inventory

See `inventory.csv`. Current coverage includes the HTTP response, product search, product listing, account entry point, basket controls, and application routes. Items marked “pending” have not been technically verified.

## 5. Limitations

- This is an initial reconnaissance report, not a full security assessment.
- The browser Network-tab inspection and additional route/service enumeration are pending. Follow `evidence/network-tab-checklist.md` and add only actual observations.
- No vulnerability should be reported as confirmed without reproducible supporting evidence.
- No real user data or credentials were intentionally accessed.

## 6. Retest summary

- Local target availability: Passed (HTTP 200 observed).
- Header collection: Completed.
- Normal product search: Passed.
- Endpoint-specific CORS verification: Pending.
- Network/request inventory: Pending.
- Account and basket behavior: Not tested beyond visible UI observation.

## 7. Submission checklist

- [ ] Replace learner name placeholder.
- [ ] Fill in the testing window.
- [ ] Sign the authorisation statement.
- [ ] Add a redacted Network-tab screenshot or request notes.
- [ ] Review and update pending items using actual observations.
- [ ] Upload the package to a repository/folder and submit one viewable link.
