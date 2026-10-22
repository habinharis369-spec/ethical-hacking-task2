# Network-tab evidence collection (to complete locally)

This checklist guides the next authorised reconnaissance step against your own local OWASP Juice Shop only.

1. Open `http://127.0.0.1:3000` in Chrome.
2. Press `F12` and select **Network**.
3. Select **Fetch/XHR** if available, then reload the page with `Ctrl+R`.
4. If the list is empty, select **All** and reload once.
5. Record only request **Name**, **Method**, **Status**, and **Type**. You may note a route/path if it contains no tokens or personal data.
6. Do not copy or share Cookie, Authorization, Set-Cookie, session IDs, tokens, or personal data.
7. Save a screenshot as `evidence/network-tab.png` with sensitive values hidden, or enter the observations in `evidence/network-observations.md`.

## Results template

| Request name/path (redacted) | Method | Status | Type | Purpose / observation |
|---|---|---|---|---|
| [fill from your browser] | | | | |

Do not invent request results. If no requests appear, note the selected filter and whether the page was reloaded.
