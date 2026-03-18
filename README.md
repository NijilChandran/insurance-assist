# Insurance Assistant — Inba

> An AI-powered chatbot to help insurance policyholders in India understand claim deductions, challenge improper TPA repudiations, and navigate their policy with confidence.

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Hosted%20on-GitHub%20Pages-222?logo=github)](https://nijilchandran.github.io/insurance-assist/)
[![Powered by](https://img.shields.io/badge/Powered%20by-DigitalOcean%20GenAI-0080FF?logo=digitalocean)](https://www.digitalocean.com/products/ai-agents)

**Live site:** [https://nijilchandran.github.io/insurance-assist/](https://nijilchandran.github.io/insurance-assist/)

---

## What is Inba?

**Inba** is a virtual insurance assistant built on Digital Ocean's GenAI Agent framework. It is specifically trained to help insured individuals in India understand why their claims were partially or fully rejected by Third Party Administrators (TPAs), and whether those deductions are valid under IRDAI regulations and their policy terms.

Inba grounds every answer in three knowledge bases:
- 📋 **Corporate Insurance Policy** — a reference policy document covering covered treatments, exclusions, and limits
- 📜 **IRDAI Circulars** — regulatory guidelines from the Insurance Regulatory and Development Authority of India
- ❌ **TPA Rejection Mapping** — a structured catalogue of common TPA deduction/repudiation codes and whether they are contestable

---

## Features that Chatbot can perform

### 🔍 Deduction Analysis
Inba identifies whether a deduction made by a TPA is legitimate or contestable. It cross-references the rejection reason against IRDAI Standardization Guidelines, flagging cases such as:
- **Double billing** (e.g. monitoring charges deducted when room rent is already paid)
- **Non-payable items** applied incorrectly
- **Excess deduction** beyond the policy limit

### 📋 Claims Guidance
Step-by-step walkthrough of the insurance claim process — from admission to final settlement — including what documents to collect, timelines to expect, and whom to contact at each stage.

### 📜 IRDAI Regulatory Reference
Inba uses official IRDAI circulars to back its answers. When contesting a deduction, it cites the specific circular, annexure, and item number, giving policyholders a factual basis for escalation.

### 📄 Policy Interpretation
Plain-language explanations of:
- Coverage limits and sub-limits
- Waiting period clauses
- Exclusions and what "not covered" actually means
- Renewal terms and portability rights

### ❌ TPA Rejection Mapping
Using the TPA Rejection Mapping knowledge base, Inba can:
- Identify the rejection code or reason cited by the TPA
- Explain whether the rejection aligns with policy terms
- Suggest whether it is worth contesting and how

### ✉️ Escalation Drafting
On request, Inba can help draft a formal objection or grievance letter to send to the TPA or insurer, citing relevant IRDAI circulars and policy clauses.


## Future Features

### Scraping from IRDAI Circulars
Scraping from IRDAI Circulars to update the knowledge base on regular basis.

### 🌐 Multilingual Awareness
Inba currently responds only in English but could be extended to other languages in the future.

### Policy upload
Allow users to upload their policy documents to the knowledge base to get customized responses based on their policy.

### Whatsapp Integration
Inba could be integrated with Whatsapp to provide a more seamless experience for users.

### 📊 Analytics and Insights
 Inba could be extended to provide analytics on the most common TPA rejection codes and reasons. Create Awareness among public for the larger issue of TPA rejection.
---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML5, CSS3 (zero dependencies) |
| Chatbot Widget | Digital Ocean GenAI Agent — embedded via `<script>` tag |
| AI Agent | Digital Ocean Agent Framework (RAG over knowledge bases) |
| Hosting | GitHub Pages (static, free) |
| CI/CD | Git push to `main` → auto-deploy |

---

## Repository Structure

```
insurance-assist/
├── index.html              # Landing page + chatbot widget embed
├── chatbot.js              # DO widget script tag (reference copy)
├── LICENSE                 # MIT License
├── SAFETY.md               # Security guidelines for contributors
├── .gitignore
│
├── agent/
│   ├── agent_instructions.md   # Inba's persona, scope, and tone
│   └── build_steps.md          # How the agent and site were built
│
└── knowledge_base/
    ├── README.md               # KB content guidelines
    ├── policy/                 # Corporate insurance policy document
    ├── irdai/                  # IRDAI circulars
    └── TPA/                    # TPA rejection mapping
```

---

## Running Locally

Do **not** open `index.html` by double-clicking — the chatbot widget requires an HTTP server:

```powershell
# Python (recommended)
python -m http.server 8080
```

Then open: [http://localhost:8080](http://localhost:8080)

---

## Security & Safety

This is a **public, open source repository**. Before contributing any files, read [`SAFETY.md`](SAFETY.md). Key rules:
- Never commit API tokens, passwords, or private keys
- Never commit customer PII (names, policy numbers, claim IDs)
- The `data-agent-id` and `data-chatbot-id` in `chatbot.js` are public widget embed keys — safe to commit

---

## Disclaimer

Inba provides information for **educational and guidance purposes only**. It is not a substitute for professional legal or financial advice. For formal grievances, use the [IRDAI Bima Bharosa portal](https://bimabharosa.irdai.gov.in/) or contact your insurer directly.

---

## License

[MIT](LICENSE) © 2026 Nijil Chandran
