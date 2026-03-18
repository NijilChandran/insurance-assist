# Documents few common TPA Rejection reasons and the counter logic to be used.

TPA Rejection Code / Phrase,Real-World Meaning,"App Logic: Policy & IRDAI ""Counter-Attack"""
"""Non-Medical Expenses""","General bucket for deductions like gloves, masks, or monitoring.","Check IRDAI List II: If the item is ""Monitoring"" or ""Nursing,"" it must be subsumed in Room Rent. Cite IRDAI/HLT/REG/CIR/193/07/2020."

"""Proportionate Deduction Applied""","You stayed in a room higher than your ""Silver Plan"" limit.","Check IRDAI 2024 Master Circular: Verify if they deducted from Pharmacy/Consumables. If yes, flag as a violation; those are exempt from % cuts."

"""Unbundled Services""","Hospital billed separately for things that should be in a ""package.""","JoJo Policy Section III(2): Quote the ""Subsumed Charges"" clause. Argue that the hospital (Network) cannot bill these separately per the PPN agreement."

"""R&C (Reasonable & Customary) Charges""",The TPA thinks the hospital overcharged for the surgery.,"GHI Exception: In corporate plans for firms like JoJo Enterprises, if the hospital is a ""Network Hospital,"" R&C limits are often waived or pre-fixed. Check PPN rates."

"""Pre-Existing Disease (PED) Exclusion""",Claim rejected because you had the illness before joining.,"JoJo Policy Section I: Flag as ""Wrongful."" Corporate IT policies (TCS-style) almost always have a PED Waiver from Day 1."

"""Charges Not Payable as per List I""","Standard non-payable items (Tissues, Gowns, etc.).","Validation: Usually legitimate. However, cross-reference with List IV (Items that can be paid if part of a procedure)."


{
  "rule_metadata": {
    "source": "IRDAI/HLT/REG/CIR/193/07/2020",
    "category": "LIST_II_SUBSUMED_INTO_ROOM_CHARGES",
    "enforcement_date": "2020-10-01",
    "legal_action": "Challenge deduction if Room Rent is paid"
  },
  "subsumed_items": [
    {
      "item_id": "102",
      "official_name": "NURSING CHARGES",
      "keywords": ["nursing care", "nursing service", "nurse visit", "nursing station fee"],
      "is_payable_separately": false,
      "legal_ref": "IRDAI List II - Item 21/102"
    },
    {
      "item_id": "103",
      "official_name": "RMO / HOUSE SURGEON CHARGES",
      "keywords": ["rmo charges", "duty doctor fee", "resident doctor", "house surgeon"],
      "is_payable_separately": false,
      "legal_ref": "IRDAI List II"
    },
    {
      "item_id": "117",
      "official_name": "MONITORING CHARGES",
      "keywords": ["monitoring", "pulse oximeter charges", "patient monitoring", "vitals check"],
      "is_payable_separately": false,
      "legal_ref": "IRDAI List II - Item 37",
      "exception": "Payable if patient is in ICU/ICCU where room rent is not charged separately"
    },
    {
      "item_id": "122",
      "official_name": "HOUSEKEEPING CHARGES",
      "keywords": ["cleaning", "sanitation", "housekeeping", "waste management"],
      "is_payable_separately": false,
      "legal_ref": "IRDAI List II - Item 22"
    }
  ]
}