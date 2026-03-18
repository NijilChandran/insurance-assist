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

## Phase 3 — Chatbot Creation from the Agent

Once the agent is deployed, create a **Chatbot** from it to generate a publicly embeddable widget.

### 3.1 — Open Chatbot Settings
1. In the agent dashboard, select your deployed agent (`inba-deductionhelper`)
2. Click **Chatbots** → **Create Chatbot**

### 3.2 — Make the Endpoint Public
1. Under **Access**, set visibility to **Public**
   - This allows the widget to be embedded on any web page without authentication
   - The endpoint URL will be: `https://<agent-domain>/static/chatbot/widget.js`


### 3.3 — Customise Appearance
Fill in the branding fields:

| Field | Value used | Attribute in script tag |
|---|---|---|
| **Chatbot Name** | `inba-deductionhelper Chatbot` | `data-name` |
| **Primary Color** | `#031B4E` (dark navy) | `data-primary-color` |
| **Secondary Color** | `#E5E8ED` (light grey) | `data-secondary-color` |
| **Button Background** | `#0061EB` (bright blue) | `data-button-background-color` |
| **Default / Starting Message** | `Hello! I'm Inba. How can I help you with your insurance claim today?` | `data-starting-message` |
| **Logo** | Default agent SVG from DO | `data-logo` |

### 3.4 — Set Allowed Origin Domains
1. Under **Allowed Origins**, add your GitHub Pages domain:
   ```
   https://nijilchandran.github.io
   ```
2. This restricts the widget so it only loads from your authorised domain — prevents others from embedding your chatbot on their sites
3. For local testing also add: `http://localhost:8080`



### 3.5 — Save and Copy the Embed Script
1. Click **Save Chatbot**
2. Click **Embed** → copy the generated `<script>` tag:
   ```html
   <script async
     src="https://<agent-domain>/static/chatbot/widget.js"
     data-agent-id="<AGENT_ID>"
     data-chatbot-id="<CHATBOT_ID>"
     data-name="inba-deductionhelper Chatbot"
     data-primary-color="#031B4E"
     data-secondary-color="#E5E8ED"
     data-button-background-color="#0061EB"
     data-starting-message="Hello! I'm Inba. How can I help you with your insurance claim today?"
     data-logo="https://<agent-domain>/static/chatbot/icons/default-agent.svg">
   </script>
   ```
3. Save a copy as `chatbot.js` in the repository root (reference only)
4. Paste the script tag at the bottom of `<body>` in `index.html`

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

