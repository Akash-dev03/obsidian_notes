## **1. Patient Profile**

- **Patient ID:** PAT-IPD-000458
    
- **UHID:** UHID-2025-005846
    
- **Full Name:** Mr. Srinivas Rao
    
- **Age / DOB:** 58 years / 1966-03-28
    
- **Gender:** Male
    
- **Contact Number:** +91-96XXXXXXXX
    
- **Address:** Malleshwaram, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 9026)
    
- **Marital Status:** Married
    
- **Blood Group:** A−
    
- **Known Allergies:** None
    
- **Existing Conditions:**
    
    - Type 2 Diabetes Mellitus (12 years)
        
    - Hypertension (8 years)
        
- **Insurance:** Yes
    
    - **Payer:** ICICI Lombard Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** ICICI-IND-667420
        

---

## **2. Entry Point**

- **Admission Type:** Planned Medical IPD
    
- **Source:** OPD – General Medicine
    
- **Admission Date & Time:** 2025-02-18, 06:20 PM
    
- **Department:** General Medicine
    
- **Reason for Admission:** Community-acquired pneumonia with uncontrolled diabetes
    

---

## **3. Timeline of Events (Step-by-Step)**

### **Day 1 – IPD Admission**

#### **06:20 PM – IPD Admission**

- Patient arrives with OPD referral.
    
- UHID and insurance verified.
    
- Insurance pre-auth initiated for medical admission.
    

**System Actions:**

- `IPDAdmission` created
    
- Admission type: **Planned – Medical**
    
- Status: **Admitted**
    

---

#### **06:28 PM – Bed Allocation (Ward)**

- Ward: Semi-Private Ward
    
- Bed No: SPW-11
    

**System Actions:**

- `Bed` marked **Occupied**
    

---

#### **06:45 PM – Admission Assessment**

- Nursing assessment and baseline vitals recorded:
    
    - BP: 144/90 mmHg
        
    - Pulse: 102 bpm
        
    - Temperature: 101.4°F
        
    - SpO₂: 93% (room air)
        

**System Actions:**

- `Vitals` created
    
- `NursingAssessment` completed
    

---

#### **07:10 PM – Consultant Review**

- **Consultant:** Dr. Mahesh Gowda (MD – General Medicine)
    
- Confirms diagnosis and starts IV antibiotics, insulin infusion.
    

**System Actions:**

- `ClinicalEncounter` created
    
- `MedicationOrders` initiated
    

---

### **Day 2 – Clinical Deterioration & ICU Transfer**

#### **02:15 AM – Acute Deterioration**

- Patient develops:
    
    - Increased breathlessness
        
    - SpO₂ drops to 86% on oxygen
        
    - Altered sensorium
        

**System Actions:**

- Emergency vitals captured
    
- `ClinicalAlert` triggered
    

---

#### **02:25 AM – ICU Escalation Decision**

- Consultant and intensivist review.
    
- Diagnosis updated:
    
    - **Severe Pneumonia with Sepsis**
        

**Clinical Decision:**

- Immediate ICU transfer for ventilatory support.
    

**System Actions:**

- `ICUTransferRequest` created
    
- IPD status → **Escalated to ICU**
    

---

#### **02:35 AM – ICU Bed Allocation**

- ICU: Medical ICU
    
- Bed No: MICU-05
    

**System Actions:**

- ICU `Bed` marked **Occupied**
    
- Ward bed released
    
- `ICUAdmission` created
    

---

#### **02:45 AM – ICU Admission**

- Patient shifted with monitoring.
    
- Non-invasive ventilation started.
    

**System Actions:**

- `ICUNotes` initiated
    
- `VentilationRecord` created
    

---

### **Day 2–3 – ICU Stay**

- Continuous monitoring.
    
- IV antibiotics escalated.
    
- Glycemic control optimized.
    
- Gradual improvement in oxygenation.
    

**System Actions (Daily):**

- `ICUProgressNotes`
    
- `MedicationAdministration`
    
- `VentilationLogs`
    

---

### **Day 4 – Step-Down to Ward**

#### **10:30 AM – ICU Downgrade Decision**

- Patient stable:
    
    - SpO₂ 97% on nasal cannula
        
    - Hemodynamically stable
        

**Clinical Decision:**

- Transfer from ICU to ward.
    

**System Actions:**

- `ICUTransferOutOrder` created
    

---

#### **11:00 AM – Ward Bed Reallocation**

- Ward: Semi-Private Ward
    
- Bed No: SPW-09
    

**System Actions:**

- Ward `Bed` marked **Occupied**
    
- ICU bed released
    

---

### **Day 4–6 – Ward Recovery Phase**

- Oral antibiotics started.
    
- Insulin shifted to subcutaneous.
    
- Chest physiotherapy continued.
    

**System Actions (Daily):**

- `DailyProgressNote`
    
- `PhysiotherapyNotes`
    
- `NursingNotes`
    

---

### **Day 6 – Discharge Day**

#### **10:00 AM – Discharge Order**

- Patient afebrile for 48 hours.
    
- Respiratory status stable.
    

**System Actions:**

- `DischargeOrder` created
    

---

#### **11:15 AM – Final Billing & Insurance**

- Consolidated IPD + ICU bill generated.
    
- Insurance claim initiated.
    

**System Actions:**

- `BillingInvoice` finalized
    
- `InsuranceClaim` created
    

---

#### **12:30 PM – Discharge**

- Discharge summary explained.
    
- Follow-up and medication instructions provided.
    

**System Actions:**

- `DischargeSummary` generated
    
- IPD status → **Discharged**
    
- Bed status → **Available**
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD (Referral)
    
- IPD Admission
    
- Ward Management
    
- ICU / Critical Care
    
- Bed Management
    
- Nursing
    
- Doctor EMR
    
- Pharmacy
    
- Physiotherapy
    
- Billing
    
- Insurance
    
- Discharge
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientInsurance`
    
- `IPDAdmission`
    
- `Bed`
    
- `ICUAdmission`
    
- `Vitals`
    
- `NursingAssessment`
    
- `ClinicalEncounter`
    
- `ICUProgressNotes`
    
- `VentilationRecord`
    
- `MedicationAdministration`
    
- `DailyProgressNote`
    
- `PhysiotherapyNotes`
    
- `BillingInvoice`
    
- `InsuranceClaim`
    
- `DischargeOrder`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|IPD Admission|Admitted (Ward)|ICU Escalation|Clinical deterioration|
|ICU Admission|Admitted|Stable|Response to treatment|
|IPD Admission|ICU|Ward|Step-down care|
|IPD Admission|Ward|Discharge Planned|Recovery achieved|
|IPD Admission|Discharge Planned|Discharged|Treatment completed|
|Bed|Occupied|Available|Patient discharged|

---

## **7. Exit Summary**

- **Exit Type:** IPD Discharge after ICU Step-Down
    
- **Patient Condition:** Stable
    
- **Total Length of Stay:** 6 days
    
- **ICU Stay:** 2 days
    
- **Follow-up:** General Medicine OPD – 7 days
    
- **Discharge Mode:** With advice
    

---

## **8. Documents Generated**

- IPD Admission Slip
    
- ICU Admission & Progress Notes
    
- ICU–Ward Transfer Note
    
- Daily Ward Progress Notes
    
- Final Discharge Summary
    
- Final Bill
    
- Insurance Claim Intimation
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|Ward Charges|30,000|
|ICU Charges|60,000|
|Diagnostics|18,000|
|Pharmacy|22,000|
|Physiotherapy|5,000|
|**Total Bill**|**₹1,35,000**|
|Insurance Approved|₹1,25,000|
|Patient Payable|₹10,000|

---

## **10. Edge Cases / Validations Tested**

1. ICU escalation from ward
    
2. Real-time bed release and reallocation
    
3. ICU to ward downgrade governance
    
4. Mixed ICU + ward billing consolidation
    
5. Insurance coverage for ICU days
    
6. Medication continuity across care levels
    
7. Ventilation record lifecycle
    
8. Discharge only after ICU clearance
    
9. Correct LOS calculation across units
    
10. Complete medico-legal audit trail