## **1. Patient Profile**

- **Patient ID:** PAT-IPD-000341
    
- **UHID:** UHID-2025-004782
    
- **Full Name:** Mrs. Anjali Mehta
    
- **Age / DOB:** 45 years / 1979-04-16
    
- **Gender:** Female
    
- **Contact Number:** +91-98XXXXXXXX
    
- **Address:** Koramangala, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 5932)
    
- **Marital Status:** Married
    
- **Blood Group:** A+
    
- **Known Allergies:** Sulfa drugs
    
- **Existing Conditions:**
    
    - Symptomatic uterine fibroids
        
- **Insurance:** Yes
    
    - **Payer:** HDFC ERGO Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** HDFC-IND-774521
        

---

## **2. Entry Point**

- **Admission Type:** Planned / Elective IPD
    
- **Source:** OPD referral (Gynecology)
    
- **Planned Admission Date:** 2025-02-08
    
- **Actual Admission Date & Time:** 2025-02-08, 09:10 AM
    
- **Department:** Obstetrics & Gynecology
    
- **Reason for Admission:** Elective Total Abdominal Hysterectomy (TAH)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **Day 0 – Pre-Admission (OPD, Prior Day)**

**2025-02-07 | 04:20 PM**

- Gynecologist confirms surgery plan during OPD visit.
    
- Planned admission created for next day.
    

**System Actions:**

- `IPDAdmissionRequest` created
    
- Surgery planned date captured
    
- Insurance pre-auth initiated
    

---

### **Day 1 – Admission Day**

#### **09:10 AM – IPD Admission**

- Patient reports to admission desk.
    
- Identity verified using UHID.
    
- Insurance pre-auth status: **Approved** (₹2,50,000 limit).
    

**System Actions:**

- `IPDAdmission` created
    
- Admission type: **Planned**
    
- Status: **Admitted**
    

---

#### **09:18 AM – Bed Allocation**

- Ward: General Ward – Female
    
- Bed No: GW-F-18
    

**System Actions:**

- `Bed` status → **Occupied**
    

---

#### **09:30 AM – Admission Assessment**

- Duty nurse completes admission checklist.
    
- Baseline vitals recorded.
    

**Vitals:**

- BP: 118/76 mmHg
    
- Pulse: 78 bpm
    
- Temperature: 98.2°F
    

**System Actions:**

- `Vitals` created
    
- `NursingAssessment` saved
    

---

#### **10:00 AM – Consultant Review**

- **Consultant:** Dr. Shilpa Deshpande (MS – OBG)
    
- Confirms surgical plan.
    
- Informed consent revalidated.
    

**System Actions:**

- `ClinicalEncounter` created
    
- `ConsentDocument` verified
    

---

#### **11:30 AM – Pre-Op Diagnostics**

- Blood tests and ECG completed.
    

**System Actions:**

- `InvestigationOrder`
    
- `LabResult` + `ECGReport`
    

---

### **Day 1 – Surgery Day**

#### **02:00 PM – OT Transfer**

- Patient shifted to OT.
    
- OT checklist completed.
    

**System Actions:**

- `OTSchedule` started
    
- Bed temporarily marked **On Leave (OT)**
    

---

#### **02:20 PM – Surgery Performed**

- Procedure: **Total Abdominal Hysterectomy**
    
- Duration: 2 hours
    
- No intra-operative complications.
    

**System Actions:**

- `ProcedureRecord` created
    
- `OTNotes` saved
    

---

#### **04:45 PM – Post-Op Recovery**

- Patient shifted to recovery, then ward.
    
- Vitals stable.
    

**System Actions:**

- `PostOpNotes`
    
- Bed status → **Occupied**
    

---

### **Day 2–4 – Inpatient Stay**

- Daily doctor rounds recorded.
    
- Pain management, antibiotics, IV fluids administered.
    
- Diet advanced gradually.
    

**System Actions (Daily):**

- `DailyProgressNote`
    
- `MedicationAdministration`
    
- `NursingNotes`
    

---

### **Day 5 – Discharge Day**

#### **10:30 AM – Discharge Order**

- Patient clinically stable.
    
- Fit for discharge.
    

**System Actions:**

- `DischargeOrder` created
    

---

#### **11:15 AM – Final Billing**

- Final bill generated.
    
- Insurance claim initiated.
    

**System Actions:**

- `IPDBillingInvoice` finalized
    
- `InsuranceClaim` created
    

---

#### **12:00 PM – Discharge**

- Discharge summary explained.
    
- Follow-up appointment given.
    

**System Actions:**

- `DischargeSummary` generated
    
- IPD status → **Discharged**
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD (Referral)
    
- IPD Admission
    
- Bed Management
    
- Nursing
    
- Doctor EMR
    
- Diagnostics
    
- OT / Surgery
    
- Pharmacy
    
- Billing
    
- Insurance
    
- Discharge
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientInsurance`
    
- `IPDAdmissionRequest`
    
- `IPDAdmission`
    
- `Bed`
    
- `Vitals`
    
- `NursingAssessment`
    
- `ClinicalEncounter`
    
- `InvestigationOrder`
    
- `LabResult`
    
- `OTSchedule`
    
- `ProcedureRecord`
    
- `MedicationAdministration`
    
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
|IPD Admission|Requested|Admitted|Planned admission|
|Bed|Available|Occupied|Patient admitted|
|Surgery|Scheduled|Completed|Procedure done|
|Insurance Claim|Initiated|Submitted|Final bill raised|
|IPD Admission|Admitted|Discharged|Treatment completed|

---

## **7. Exit Summary**

- **Exit Type:** Planned IPD Discharge
    
- **Patient Condition:** Stable
    
- **Length of Stay:** 5 days
    
- **Follow-up:** OPD review after 10 days
    
- **Discharge Mode:** With advice
    

---

## **8. Documents Generated**

- IPD Admission Slip
    
- Insurance Pre-Auth Approval
    
- OT Notes
    
- Surgery Consent
    
- Daily Progress Notes
    
- Final Discharge Summary
    
- Final Bill & Insurance Claim Form
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|Room Charges|45,000|
|OT & Surgeon Fees|80,000|
|Diagnostics|12,000|
|Pharmacy|18,000|
|Nursing & Misc|10,000|
|**Total Bill**|**₹1,65,000**|
|Insurance Approved|₹1,65,000|
|Patient Payable|₹0|

---

## **10. Edge Cases / Validations Tested**

1. Planned admission vs emergency admission
    
2. Insurance pre-auth before admission
    
3. Bed blocking prior to arrival
    
4. OT scheduling and bed leave handling
    
5. Daily clinical documentation
    
6. Post-op care workflow
    
7. Discharge order vs actual discharge timing
    
8. Insurance claim generation post-discharge
    
9. Final bill lock after discharge
    
10. Complete medico-legal audit trail