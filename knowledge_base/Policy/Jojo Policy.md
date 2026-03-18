# This detailed Policy Document is for a  fictional organization called **JoJo Enterprises**. 

# It is designed as a "Technical Master Policy," structured to serve as the ground-truth dataset for you insurance assist rules engine.

# Replace JoJo Enterprises with the actual organization name and policy document.
+  In the future, application can allow policy document upload and extract the policy details for customization of rules engine.

# JoJo Enterprises: Group Health Insurance Master Policy (FY 2026-27)

| Policy Detail | Specification |
| :--- | :--- |
| **Policyholder** | JoJo Enterprises Pvt. Ltd. |
| **Insurer** | The New India Assurance Co. Ltd. |
| **TPA Partner** | Medi Assist Insurance TPA Pvt. Ltd. |
| **Policy Version** | 2026.1.0-IT-SERVICES |
| **Jurisdiction** | Republic of India |

---

## 1. Benefit Table (The Logic Baseline)

| Clause | Silver Plan (Default) | Platinum Plan (Optional) |
| :--- | :--- | :--- |
| **Base Sum Insured** | ₹4,00,000 | ₹10,00,000 |
| **Family Definition** | 1+3 (Self, Spouse, 2 Children) | 1+5 (Includes Parents/In-laws) |
| **Room Rent Limit** | Shared AC Room (No Cap on Value) | Single Private AC Room (No Cap) |
| **ICU Charges** | No Limit (At Actuals) | No Limit (At Actuals) |
| **Maternity Limit** | ₹50,000 (N) / ₹75,000 (C) | ₹1,00,000 (N) / ₹1,25,000 (C) |
| **PED Waiting Period** | **0 Days** (Day 1 Cover) | **0 Days** (Day 1 Cover) |
| **Corporate Buffer** | ₹1,00,000 (Critical Illness) | ₹5,00,000 (Critical Illness) |

---

## 2. Definitive Coverage & IRDAI Overrides

### 2.1 The "Unbundling" Protection (IRDAI List II)
As per **IRDAI/HLT/REG/CIR/193/07/2020**, the following expenses are considered **Subsumed into Room Rent** and cannot be deducted as separate line items if Room Rent is charged to JoJo Enterprises employees:
* **Nursing & Service Charges:** Item 102 (Nursing), Item 105 (Admission).
* **Housekeeping & Admin:** Item 108 (Water/Electricity), Item 122 (Housekeeping).
* **Monitoring Services:** Item 117 (Pulse Oximeter/Vitals Monitoring).
* **RMO Fees:** Item 103 (Duty Doctor/Resident Surgeon fees).

### 2.2 Proportionate Deduction Logic (2024 Update)
If an employee stays in a category higher than their eligibility:
* **Applicability:** Proportionate deductions apply ONLY to Associate Medical Expenses (Surgeon, OT, Anesthesia).
* **Explicit Exemptions:** No deductions shall be applied to:
    1.  Cost of Medicines and Consumables.
    2.  Medical Devices and Implants.
    3.  Diagnostics and Lab Tests.
    4.  **ICU Stay:** ICU charges are considered fixed and exempt from room-category proportionality.

---

## 3. Specific IT-Sector Extensions

### 3.1 Modern Treatment Clauses
Coverage up to **50% of Sum Insured** for:
* Uterine Artery Embolization and HIFU.
* Balloon Sinuplasty.
* **Robotic Surgeries** (Medically necessary).
* Stereotactic Radio Surgeries.
* Intra Vitreal Injections.

### 3.2 Mental Healthcare Benefit
In compliance with the **Mental Healthcare Act, 2017**, any JoJo Enterprises employee hospitalized for mental illness shall be treated identically to physical illness. 
* **OPD Counseling:** Reimbursable up to **₹15,000** under the "Mental Wellness" bouquet.

---

## 4. Moratorium & Claims Redressal

### 4.1 The 5-Year Moratorium (2026 Mandate)
After **five years of continuous coverage** under the JoJo Enterprises group plan (including portability from previous employers), no claim can be contested by the TPA/Insurer on the grounds of "Non-Disclosure of PED" or "Misrepresentation," except in cases of proven fraud.

### 4.2 Escalation Matrix for Wrongful Deductions
If a claim is short-settled by Medi Assist:
1.  **Stage 1:** Internal Appeal via **Medi Assist Portal** (Turnaround: 48 hours).
2.  **Stage 2:** Escalation to **JoJo HR Benefits Helpdesk**.
3.  **Stage 3:** Official complaint on **Bima B भरोसा (IGMS)**.
4.  **Stage 4:** Filing with the **Insurance Ombudsman** (Relevant for deductions >₹10,000).

---

## 5. Standard Exclusions (Non-Payable)
The following are strictly excluded per **IRDAI List I**:
* External durable medical equipment (Hearing aids, Crutches).
* Personal comfort items (Tissues, Mouthwash, Hand sanitizer).
* Aesthetic treatments (Lasik for power <7.5D, Cosmetic hair transplant).
* Intentional self-injury or alcohol-related hospitalizations.

