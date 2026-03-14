---
description: Configure Veto server connection
---

Help the user configure their Veto connection step by step.

IMPORTANT: Do NOT use AskUserQuestion for the API key. The "Other" text input does not work well for pasting keys.

Step 1 - Use AskUserQuestion to ask for the fail policy:

Question 1 - Fail policy:
- header: "Fail policy"
- question: "What should happen if the Veto server is unreachable?"
- options: "closed — deny tool calls (Recommended)" and "open — allow tool calls"

Step 2 - Ask for the API key as a plain text message (NOT AskUserQuestion):
Say: "Please paste your Veto API key (find it in the Veto dashboard under Settings > API Keys). Or type 'skip' for local development without an API key."
Wait for the user to reply with their key or "skip".

Step 3 - After collecting all answers:

1. Create the config directory if it doesn't exist:
   Run: `mkdir -p ~/.veto`

2. Edit if it already exist or Write the config file using the Write tool to `~/.veto/config.json`
   Content: {"api_key": "...", "fail_policy": "...", "timeout": 25}
   Use the fail_policy value from the user's answer in Step 1 ("open" or "closed").
   If the user skipped the API key, set "api_key": ""

3. Report success or failures
