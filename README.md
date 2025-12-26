# n8n AI Web Security Scanner

This project is an AI-powered **web security scanner** built with **n8n** and **OpenAI**.

It mirrors a LLM security course lab I completed, but instead of running everything in code, I rebuilt the whole flow as a visual automation in n8n.

---

## What it does

Given a target URL (for example: `http://testphp.vulnweb.com`):

1. **Takes user input**
   - `target_url` – the site to assess  
   - `goal` – e.g. “High-level web security assessment focusing on missing security headers.”

2. **Fetches the site**
   - `HTTP Request` node pulls the HTML response.
   - I collect:
     - Status code  
     - Response headers  
     - HTML body

3. **Prepares AI-friendly data**
   - `Prepare for AI` node restructures the data into:
     - `headers`
     - `statusCode`
     - `html`

4. **Runs the AI security analysis**
   - `Basic LLM Chain` + OpenAI model
   - System prompt tells the model to act as a web security scanner.
   - User prompt includes:
     - Goal
     - Target URL
     - HTTP status
     - Headers
     - HTML body

5. **Returns a human-readable report**
   - `Analyze Security` / `Format Result` nodes shape the output as:
     - Summary
     - Missing / misconfigured security headers
     - Risks
     - Recommended next steps

---

## Tech & tools

- **n8n** – workflow automation / orchestration
- **OpenAI** – LLM for security analysis text
- **HTTP Request node** – pulls live HTTP responses
- **Manual trigger** – simple “run on click” execution

---

## How to run it yourself

1. Install or open n8n.
2. Export this repository and download  
   `AI Web Security Scanner (n8n).json`.
3. In n8n:
   - Go to **Workflows → Import from File**
   - Select the JSON file
4. Set your **OpenAI API credentials** in n8n.
5. Open the workflow, click **Execute workflow**, and use a test URL.

---

## Why I built this

I’m learning security, GRC, and AI tooling.  
This project helped me:

- Translate a **LLM/Python based security lab** into a **no-code/low-code workflow**.
- Understand how to orchestrate:
  - HTTP scanning
  - Data shaping
  - AI reasoning
- Build something that a security team could extend into:
  - Scheduled scans
  - Slack/Email alerts
  - Evidence collection for compliance.

