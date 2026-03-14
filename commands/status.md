---
description: Check Veto server connection status and active rules
---

Check the Veto configuration at $HOME\.veto\config.json. If it exists, read the server_url (default: https://api.vetoapp.io) and api_key, then:

Step 1 - Health check:
Run: `powershell -Command "(Invoke-WebRequest -Uri '{server_url}/health' -UseBasicParsing).StatusCode"`

Step 2 - Rules check:
Run: `powershell -Command "Invoke-RestMethod -Uri '{server_url}/api/v1/rules' -Headers @{'Authorization'='Bearer {api_key}'}"`

Step 3 - Report: server URL, connection status (ok/unreachable), rule count, and fail policy.
