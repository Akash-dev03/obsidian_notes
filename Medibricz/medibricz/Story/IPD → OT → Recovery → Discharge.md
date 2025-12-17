## **1. Patient Profile**

- **Patient ID:** PAT-IPD-000412
    
- **UHID:** UHID-2025-005214
    
- **Full Name:** Mr. Karthik Reddy
    
- **Age / DOB:** 39 years / 1985-07-09
    
- **Gender:** Male
    
- **Contact Number:** +91-90XXXXXXXX
    
- **Address:** HSR Layout, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 6284)
    
- **Marital Status:** Married
    
- **Blood Group:** B+
    
- **Known Allergies:** None
    
- **Existing Conditions:** None
    
- **Insurance:** Yes
    
    - **Payer:** Star Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** STAR-IND-551239
        

---

## **2. Entry Point**

- **Admission Type:** Planned IPD (Elective Surgery)
    
- **Source:** OPD – Orthopedics
    
- **Admission Date & Time:** 2025-02-15, 07:40 AM
    
- **Department:** Orthopedics
    
- **Reason for Admission:** Elective Arthroscopic ACL Reconstruction (Right Knee)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **Day 1 – Admission Day**

#### **07:40 AM – IPD Admission**

- Patient reports to IPD admission desk.
    
- UHID and insurance verified.
    
- Insurance pre-auth already **Approved** (₹3,00,000).
    

**System Actions:**

- `IPDAdmission` created
    
- Admission type: **Planned – Surgical**
    
- Status: **Admitted**
    

---

#### **07:48 AM – Bed Allocation**

- Ward: Private Ward
    
- Bed No: PW-06
    

**System Actions:**

- `Bed` marked **Occupied**
    

---

#### **08:05 AM – Admission Nursing Assessment**

- Baseline vitals recorded:
    
    - BP: 120/78 mmHg
        
    - Pulse: 76 bpm
        
    - Temperature: 98.1°F
        
    - SpO₂: 99%
        

**System Actions:**

- `Vitals` created
    
- `NursingAssessment` completed
    

---

#### **08:25 AM – Surgeon Review & Consent**

- **Surgeon:** Dr. Arvind Menon (MS – Orthopedics)
    
- Surgical plan reconfirmed.
    
- Risks, benefits, and alternatives explained.
    
- Informed surgical consent obtained.
    

**System Actions:**

- `ClinicalEncounter` created
    
- `ConsentDocument` verified and locked
    

---

### **Pre-Operative Phase**

#### **09:00 AM – Pre-Op Diagnostics & Clearance**

- Pre-op checklist completed.
    
- Investigations reviewed:
    
    - CBC, RFT, ECG – Within normal limits
        
- Anesthesia clearance obtained.
    

**System Actions:**

- `PreOpAssessment` completed
    
- `AnesthesiaClearance` recorded
    

---

### **OT Phase**

#### **10:15 AM – Transfer to OT**

- Patient shifted to Operation Theatre.
    
- Surgical safety checklist initiated.
    

**System Actions:**

- `OTSchedule` status → **In Progress**
    
- Bed status → **On Leave (OT)**
    

---

#### **10:30 AM – Surgery Start**

- Procedure: **Arthroscopic ACL Reconstruction – Right Knee**
    
- Anesthesia: Spinal
    
- Duration: 1 hour 45 minutes
    

**System Actions:**

- `ProcedureRecord` created
    
- `AnesthesiaNotes` captured
    
- `OTNotes` updated
    

---

#### **12:15 PM – Surgery Completion**

- No intra-operative complications.
    
- Patient shifted to recovery room.
    

**System Actions:**

- `OTSchedule` status → **Completed**
    

---

### **Recovery Phase**

#### **12:20 PM – Post-Anesthesia Recovery**

- Patient monitored in PACU.
    
- Vitals stable.
    

**System Actions:**

- `RecoveryNotes` created
    
- Pain score documented
    

---

#### **01:10 PM – Shift Back to Ward**

- Patient shifted back to IPD bed.
    
- Oral intake initiated gradually.
    

**System Actions:**

- Bed status → **Occupied**
    
- `PostOpOrders` activated
    

---

### **Post-Operative Inpatient Care (Day 1–2)**

- IV antibiotics and analgesics administered.
    
- Physiotherapy initiated on Day 2.
    
- Daily surgeon rounds documented.
    

**System Actions (Daily):**

- `MedicationAdministration`
    
- `PhysiotherapyNotes`
    
- `DailyProgressNote`
    

---

### **Day 3 – Discharge Day**

#### **10:00 AM – Discharge Order**

- Patient ambulating with support.
    
- Surgical wound clean and dry.
    

**System Actions:**

- `DischargeOrder` created
    

---

#### **11:00 AM – Final Billing**

- Final IPD bill generated.
    
- Insurance claim initiated.
    

**System Actions:**

- `BillingInvoice` finalized
    
- `InsuranceClaim` created
    

---

#### **12:00 PM – Discharge**

- Discharge summary explained.
    
- Physiotherapy and follow-up instructions provided.
    

**System Actions:**

- `DischargeSummary` generated
    
- IPD status → **Discharged**
    
- Bed status → **Available**
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD (Referral)
    
- IPD Admission
    
- Bed Management
    
- Nursing
    
- Doctor EMR
    
- OT / Surgery
    
- Anesthesia
    
- Recovery / PACU
    
- Physiotherapy
    
- Pharmacy
    
- Billing
    
- Insurance
    
- Discharge
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientInsurance`
    
- `IPDAdmission`
    
- `Bed`
    
- `Vitals`
    
- `NursingAssessment`
    
- `ClinicalEncounter`
    
- `PreOpAssessment`
    
- `AnesthesiaClearance`
    
- `OTSchedule`
    
- `ProcedureRecord`
    
- `OTNotes`
    
- `RecoveryNotes`
    
- `MedicationAdministration`
    
- `PhysiotherapyNotes`
    
- `DailyProgressNote`
    
- `BillingInvoice`
    
- `InsuranceClaim`
    
- `DischargeOrder`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|IPD Admission|Admitted|Pre-Op|Surgery preparation|
|Bed|Occupied|On Leave (OT)|Patient in OT|
|OT Schedule|Scheduled|Completed|Surgery finished|
|IPD Admission|Post-Op|Recovery|PACU monitoring|
|IPD Admission|Recovery|Discharge Planned|Clinical stability|
|IPD Admission|Discharge Planned|Discharged|Treatment completed|
|Bed|Occupied|Available|Patient discharged|

---

## **7. Exit Summary**

- **Exit Type:** Planned Surgical Discharge
    
- **Patient Condition:** Stable, ambulatory
    
- **Length of Stay:** 3 days
    
- **Follow-up:** Orthopedics OPD after 10 days
    
- **Discharge Mode:** With advice and physiotherapy plan
    

---

## **8. Documents Generated**

- IPD Admission Slip
    
- Insurance Pre-Auth Approval
    
- Surgical Consent
    
- OT & Anesthesia Notes
    
- Post-Op Care Sheet
    
- Physiotherapy Instructions
    
- Final Discharge Summary
    
- Final Bill & Insurance Claim Form
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|Room Charges|36,000|
|OT & Surgeon Fees|1,20,000|
|Anesthesia|25,000|
|Diagnostics|10,000|
|Pharmacy|14,000|
|Physiotherapy|5,000|
|**Total Bill**|**₹2,10,000**|
|Insurance Approved|₹2,00,000|
|Patient Payable|₹10,000|

---

## **10. Edge Cases / Validations Tested**

1. Planned IPD surgical admission
    
2. Pre-op clearance enforcement
    
3. OT checklist compliance
    
4. Bed leave handling during OT
    
5. PACU recovery documentation
    
6. Post-op physiotherapy initiation
    
7. Discharge only after surgeon clearance
    
8. Insurance claim post-surgery
    
9. Final bill lock after discharge
    
10. Complete medico-legal audit trail