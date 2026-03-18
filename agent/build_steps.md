# How the Chatbot Was Built — Step-by-Step

> Documents the process of creating the **inba-deductionhelper** chatbot on Digital Ocean's GenAI Agent framework and embedding it as a static GitHub Pages site.

---

## Phase 1 — Digital Ocean Agent Setup

1. Log in to [cloud.digitalocean.com](https://cloud.digitalocean.com)
2. Navigate to **AI** → **Agents** → **Create Agent**
3. Configure:
   - **Name:** `inba-deductionhelper`
   - **Model:** (select preferred LLM, e.g. GPT-4o or Llama 3)
   - **Instructions:** Paste content from `agent/agent_instructions.md`
4. Attach Knowledge Base (see Phase 2)
5. Click **Deploy Agent**
6. Copy the generated **Agent ID** and **Chatbot ID** from the agent details page

---

## Phase 2 — Knowledge Base Upload

1. In the agent dashboard, go to **Knowledge Bases** → **Create Knowledge Base**
2. Upload files from the `knowledge_base/` folder in this repository
3. Create 3 different knowledge bases for Policy, IRDAI Circulars and TPA Rejection mapping. 
3. Wait for indexing to complete (green ✅ status)
4. Link the knowledge base to the agent under **Agent Settings → Knowledge Bases**

---

## Phase 3 — Widget Embed Code (`chatbot.js`)

1. In the agent dashboard, click **Embed** or **Share**
2. Copy the `<script>` tag — it looks like:
   ```html
   <script async
     src="https://<agent-domain>/static/chatbot/widget.js"
     data-agent-id="<AGENT_ID>"
     data-chatbot-id="<CHATBOT_ID>"
     ...>
   </script>
   ```
3. Save this as `chatbot.js` in the repository (for reference — the actual embed goes in `index.html`)
4. Customise colors using the `data-primary-color`, `data-secondary-color`, and `data-button-background-color` attributes to match branding

---

## Phase 4 — Static Site (`index.html`)

1. Create `index.html` with:
   - Responsive CSS Grid layout (2-column card grid)
   - Brand header with shield icon
   - Four feature cards (Claims, Deductions, Policy, Instant Answers)
   - The DO widget `<script>` tag at the bottom of `<body>`
2. No external JS libraries — vanilla HTML/CSS only (per spec)

---

## Phase 5 — GitHub Pages Deployment

1. Push repository to GitHub (public repo)
2. Settings → Pages → Source: `main` branch, root `/`
3. Site live at: `https://NijilChandran.github.io/insurance-assist/`

---

## Key IDs (non-secret, public embed keys)

| Key | Value |
|---|---|
| Agent ID | `71c8fc0d-227e-11f1-b074-4e013e2ddde4` |
| Chatbot ID | `iTabyc1nI15PjUFWZXPu8Bo1tEsRaCdu` |
| Agent Domain | `dou3ota6tj4frnt5zfltu2fv.agents.do-ai.run` |

> ⚠️ These are **public widget embed keys** — they identify the widget but do not grant API access. Your actual DO API tokens must never be committed. See `SAFETY.md`.
