# Insurance Assistant — Inba
## Built on DigitalOcean Gradient™ AI Platform

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Hosted%20on-GitHub%20Pages-222?logo=github)](https://nijilchandran.github.io/insurance-assist/)
[![Powered by](https://img.shields.io/badge/Powered%20by-DigitalOcean%20Gradient%20AI-0080FF?logo=digitalocean)](https://docs.digitalocean.com/products/gradient-ai-platform/)

**Live site:** [https://nijilchandran.github.io/insurance-assist/](https://nijilchandran.github.io/insurance-assist/)

---

## Overview

**Inba** is a domain-specific AI chatbot built on the [DigitalOcean Gradient™ AI Platform](https://docs.digitalocean.com/products/gradient-ai-platform/) — a fully-managed platform for building AI agents with knowledge bases for Retrieval-Augmented Generation (RAG), serverless inference, and embedded chatbot widgets. Inba helps insurance policyholders in India understand, question, and contest TPA (Third Party Administrator) claim deductions using a regulated, fact-grounded AI agent.

The production deployment is a **zero-dependency static website** hosted free on GitHub Pages, demonstrating that enterprise-grade AI can be integrated into the simplest possible frontend.

---
## Platform: DigitalOcean Gradient™ AI

This project demonstrates end-to-end use of the Gradient AI Platform across six stages:

---

### Step 1 — Agent Instructions

**Feature:** [Agent Instructions Best Practices](https://docs.digitalocean.com/products/gradient-ai-platform/concepts/agent-instructions/)

Agent instructions define the agent's identity, objective, expertise, and restrictions — applied at every conversation turn.

| Section | Content |
|---|---|
| **Identity** | Inba — virtual assistant for Indian insurance claims |
| **Objective** | Help users understand and challenge TPA deductions |
| **Expertise** | Indian insurance policies, IRDAI circulars, TPA rejection patterns |
| **Restrictions** | English only; no opinions, speculation, or PII collection |
| **Limitations** | Transparent about knowledge gaps; escalates to IRDAI portal |
| **Response Style** | Brief, fact-based, citation-backed; clarifies ambiguous queries |

Stored in version control at [`agent/agent_instructions.md`](agent/agent_instructions.md).

---

### Step 2 — Knowledge Base Creation

**Feature:** [Create and Manage Knowledge Bases](https://docs.digitalocean.com/products/gradient-ai-platform/how-to/create-manage-agent-knowledge-bases/)

Three separate knowledge bases were created to keep retrieval focused and indexing costs predictable:

| Knowledge Base | Contents | Purpose |
|---|---|---|
| **Policy KB** | Corporate group insurance policy | Coverage limits, exclusions, sub-limits |
| **IRDAI Circulars KB** | IRDAI regulatory circulars | Regulatory grounding for contestation |
| **TPA Rejection Mapping KB** | Rejection code → contestability mapping | Validate or challenge TPA decisions |

**Embedding model** — selected once at KB creation; converts documents into vector embeddings stored in a managed **OpenSearch** database. Model was chosen based on the dashboard's pricing table (Dataset size → Token Count → Indexing Cost).

**Chunking strategy** — tested via the *Test and Update Chunking Strategy* panel to ensure IRDAI circular sections were preserved as coherent retrieval units.

**Data sources used:** File upload (`.md` documents). Gradient AI also supports Spaces buckets and web crawling (seed URL / sitemap) for future expansion.

---

### Step 3 — Agent Creation & Knowledge Base Attachment

**Feature:** [Use Agents in Your Applications](https://docs.digitalocean.com/products/gradient-ai-platform/how-to/use-agents/)

Agent `inba-deductionhelper` was created via the Control Panel with:
- Agent instructions from `agent_instructions.md`
- All three knowledge bases attached under **Agent Settings → Knowledge Bases**
- RAG enabled — every user query retrieves relevant chunks before LLM generation

---

### Step 4 — Model Selection via the Playground

**Feature:** [Agent Playground](https://docs.digitalocean.com/products/gradient-ai-platform/how-to/test-agents/) + [Foundation Models](https://docs.digitalocean.com/products/gradient-ai-platform/details/models/)

Gradient AI supports open source and commercial models:

| Family | Examples |
|---|---|
| **Anthropic** | Claude Sonnet 4.6, Claude Haiku 4.5, Claude Opus 4 |
| **Meta** | Llama 3 series |
| **Alibaba** | Qwen3-32B |
| **OpenAI** (BYOK) | GPT-4o via your own API key |

The **Playground** was used to test identical insurance queries across models without writing code — comparing accuracy of IRDAI citations, hallucination rate, verbosity, and per-token cost. A mid-tier model balancing citation accuracy and cost was selected.

---

### Step 5 — Chatbot Creation & Embed Configuration

**Feature:** Chatbot builder within the Agent dashboard

| Configuration | Detail |
|---|---|
| **Endpoint** | Set to Public; rate limits configured for cost control |
| **Branding** | Navy `#031B4E`, blue `#0061EB`, custom starting message |
| **Allowed Origins** | `https://nijilchandran.github.io` — blocks third-party embedding |
| **Embed** | `<script>` tag saved as `chatbot.js`; embedded in `index.html` |

---

### Step 6 — GitHub Pages Integration

**Stack:** Vanilla HTML5 + CSS3, zero JS dependencies

| Decision | Rationale |
|---|---|
| Static site | Gradient AI widget is fully client-side — no backend needed |
| GitHub Pages | Free HTTPS hosting; auto-deploys on `git push` to `main` |
| Zero libraries | Per spec — no jQuery, React, or Bootstrap |
| Open source (MIT) | Agent instructions and KB guidelines version-controlled publicly |

---

## Architecture

```
User (Browser)
    │
    ▼
GitHub Pages ── index.html (HTML/CSS, no JS framework)
    │
    │  <script async src="widget.js" ...>
    ▼
DigitalOcean Gradient™ AI Platform
    ├── Chatbot Widget       (UI layer, iframe)
    ├── Agent: inba-deductionhelper
    │       └── Agent Instructions (persona, scope, style)
    ├── RAG Pipeline
    │       ├── Knowledge Base: Policy
    │       ├── Knowledge Base: IRDAI Circulars
    │       └── Knowledge Base: TPA Rejection Mapping
    │               └── OpenSearch (managed vector store)
    └── Foundation Model (selected via Playground)
```

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
    ├── policy/                 # Corporate insurance policy
    ├── irdai/                  # IRDAI circulars
    └── TPA/                    # TPA rejection mapping
```

---

## Running Locally (WINDOWS)

Do **not** open `index.html` by double-clicking — the chatbot widget requires HTTP:

```powershell
python -m http.server 8080
```

Open: [http://localhost:8080](http://localhost:8080)

Note: Ensure you add `http://localhost:8080` to the allowed origins in the agent chat dashboard temporarily.
---

## Security

- Never commit API tokens, passwords, or private keys
- Never commit customer PII (names, policy numbers, claim IDs)
- `data-agent-id` and `data-chatbot-id` in `chatbot.js` are public widget embed keys — safe to commit

---

## References

- [Gradient AI Platform Docs](https://docs.digitalocean.com/products/gradient-ai-platform/)
- [Agent Instructions Best Practices](https://docs.digitalocean.com/products/gradient-ai-platform/concepts/agent-instructions/)
- [Knowledge Base How-To](https://docs.digitalocean.com/products/gradient-ai-platform/how-to/create-manage-agent-knowledge-bases/)
- [Foundation & Embedding Models](https://docs.digitalocean.com/products/gradient-ai-platform/details/models/)
- [Agent Playground](https://docs.digitalocean.com/products/gradient-ai-platform/how-to/test-agents/)

---

## Disclaimer

Inba provides information for educational and guidance purposes only. It is not a substitute for professional legal or financial advice. For formal grievances, use the [IRDAI Bima Bharosa portal](https://bimabharosa.irdai.gov.in/).

---

## License

[MIT](LICENSE) © 2026 Nijil Chandran
