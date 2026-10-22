
# Ethical Hacking Task 2: Local Reconnaissance and Attack Surface Map

## Project Overview

This project documents an authorised reconnaissance exercise conducted against a locally running OWASP Juice Shop application. The objective is to identify the application's visible attack surface, inspect HTTP response headers, observe browser network requests, and document findings using a structured security assessment report.

All testing was restricted to the local lab environment.

## Objectives

- Verify that the local OWASP Juice Shop application is accessible.
- Collect and document HTTP response headers.
- Observe product search functionality and application navigation.
- Inspect browser network requests using Chrome Developer Tools.
- Create an attack-surface inventory.
- Document evidence, potential risks, limitations, and remediation considerations.
- Follow responsible and authorised security testing practices.

## Scope and Rules of Engagement

**Target:** `http://127.0.0.1:3000`

**Application:** OWASP Juice Shop

**Environment:** Local testing environment

Testing was limited to the locally running application. Public IP addresses, third-party systems, other students' accounts, and external services were outside the authorised scope.

The assessment did not intentionally involve denial of service, credential stuffing, phishing, malware, persistence, destructive payloads, or access to real personal data.

## Methodology

1. Checked local application availability using `curl.exe -I http://127.0.0.1:3000`.
2. Recorded the observed HTTP response headers.
3. Inspected the product listing and application navigation in the browser.
4. Used the search feature with the term `apple`.
5. Opened Chrome Developer Tools and inspected the Network tab.
6. Recorded visible request metadata for the application-configuration endpoint.
7. Organised the collected observations into a report and attack-surface inventory.

## Key Observations

### 1. HTTP Response Headers

The initial HTTP request returned `200 OK`.

The observed response included:

- `Access-Control-Allow-Origin: *`
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: SAMEORIGIN`
- `Content-Type: text/html; charset=UTF-8`

The wildcard CORS header is recorded for further review against the application's intended cross-origin access requirements. This observation alone does not establish a vulnerability.

### 2. Product Search

Searching for `apple` displayed matching products, including Apple Juice, Apple Pomace, and Pineapple Juice.

This demonstrated normal search functionality. No search-related vulnerability was confirmed by this test.

### 3. Browser Network Inspection

Chrome Developer Tools showed requests including:

- `application-configuration`
- `Quantity/`
- `search?q=`
- Socket.IO polling requests

The selected application-configuration request showed:

- **Method:** GET
- **Status:** 304 Not Modified
- **Local address:** `127.0.0.1:3000`
- **Endpoint:** `/rest/admin/application-configuration`

A `304 Not Modified` response is cache-related and is not itself a vulnerability. The endpoint's response contents and access permissions require further verification.

## Repository Contents

- `README.md` — Project overview, scope, methodology, and observations.
- `report.md` — Detailed reconnaissance report, findings, limitations, and retest summary.
- `inventory.csv` — Structured attack-surface inventory.
- `evidence/http-head-headers.txt` — Captured HTTP response headers.
- `evidence/browser-observations.md` — Browser and network observations.
- `evidence/network-observations.csv` — Recorded network request metadata.
- `evidence/authorization-statement.txt` — Authorisation statement to complete and sign.

## Results and Limitations

The local application responded successfully, normal product search worked, and initial browser network requests were observed.

This was an initial reconnaissance exercise, not a complete security assessment. Endpoint-specific CORS behaviour, configuration response contents, and access controls have not been fully verified. No confirmed vulnerability is claimed based on the evidence collected so far.

## Responsible Testing Statement

Testing must be conducted only on systems owned by the tester or explicitly authorised for assessment. All activity should remain within the written scope and testing window. Secrets, credentials, session tokens, and personal information must not be published.

**Authorisation statement:** Before submission, the tester must confirm that the target was owned or explicitly authorised and complete the required signature and date.

## Conclusion

This exercise demonstrates the initial stages of a structured web application security assessment: target verification, HTTP header collection, functional observation, browser network inspection, evidence documentation, and attack-surface inventory creation.

Further authorised verification is required before any potential security weakness can be classified as a confirmed vulnerability.
