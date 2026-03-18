# Knowledge Base

This folder contains the documents uploaded to the Digital Ocean Agent's knowledge base.  
The agent uses these files for **Retrieval-Augmented Generation (RAG)** — it searches them to ground its answers in factual content rather than relying solely on the base LLM.

---

## What to put here

| File type | Examples |
|---|---|
| Policy FAQs | `health_insurance_faq.md`, `motor_claims_faq.md` |
| Claim procedures | `claim_process_steps.md` |
| Coverage terms | `exclusions_and_limits.md` |
| Deduction tables | `deductible_reference.md` |
| Escalation contacts | `helpline_numbers.md` |

---

## Format recommendations

- **Markdown (`.md`)** — best for structured text; headings help the agent chunk content cleanly
- **Plain text (`.txt`)** — acceptable for simple lists or notes
- **PDF** — supported by DO, but markdown is preferred for version control readability

---

## ⚠️ Before adding any file, check `SAFETY.md`

Do **not** add files containing:
- Customer names, policy numbers, or claim IDs
- Any Personally Identifiable Information (PII)
- Internal pricing or commission structures marked confidential
