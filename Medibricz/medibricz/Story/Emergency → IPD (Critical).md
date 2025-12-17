## **1. Patient Profile**

- **Patient ID:** PAT-ER-000209
    
- **UHID:** UHID-2025-003912
    
- **Full Name:** Mr. Mohammed Irfan
    
- **Age / DOB:** 61 years / 1963-02-09
    
- **Gender:** Male
    
- **Contact Number:** +91-94XXXXXXXX
    
- **Address:** Shivajinagar, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 8894)
    
- **Marital Status:** Married
    
- **Blood Group:** B+
    
- **Known Allergies:** None known
    
- **Existing Conditions:**
    
    - Hypertension (10 years)
        
    - Type 2 Diabetes Mellitus (8 years)
        
- **Insurance:** Yes
    
    - **Payer:** ICICI Lombard
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** ICICI-IND-441982
        

---

## **2. Entry Point**

- **Date:** 2025-02-02
    
- **Time:** 03:26 AM
    
- **Entry Mode:** Brought by ambulance
    
- **Department:** Emergency Room (ER)
    
- **Chief Complaint:** Sudden onset severe chest pain with sweating and breathlessness (45 minutes)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **03:26 AM – Emergency Arrival & Triage**

- Ambulance handover completed at ER bay.
    
- Immediate triage initiated before formal registration.
    

**Triage Findings:**

- Severe chest pain (VAS 9/10)
    
- Diaphoretic, anxious
    
- Altered sensorium intermittently
    

**Triage Category:** **Priority I – Resuscitation (Critical)**

**System Actions:**

- `EmergencyVisit` created (temporary)
    
- Triage timestamp captured
    
- Status: **Under Triage**
    

---

### **03:28 AM – Rapid ER Registration**

- Minimal demographics captured from attendant.
    
- Temporary ER number generated.
    
- UHID created and mapped post-stabilization.
    

**System Actions:**

- `Patient` created
    
- `UHID` generated
    
- ER visit linked to UHID
    
- Status → **Registered**
    

---

### **03:30 AM – Immediate Vitals & Monitoring**

- Continuous cardiac monitoring initiated.
    
- Initial vitals:
    
    - BP: 86/58 mmHg
        
    - Pulse: 122 bpm (irregular)
        
    - SpO₂: 91% (room air)
        
    - RR: 28/min
        

**System Actions:**

- `Vitals` recorded
    
- ER Visit status → **Under Treatment**
    
- Monitor data linked to encounter
    

---

### **03:32 AM – Emergency Physician Assessment**

- **Attending Doctor:** Dr. Prakash Nair (MD – Emergency Medicine)
    
- ECG performed at bedside.
    

**ECG Findings:**

- ST elevation in leads II, III, aVF
    

**Provisional Diagnosis:**

- **Acute Inferior Wall Myocardial Infarction (STEMI)**
    

**Critical Decision:**

- Immediate escalation to critical care.
    
- Activate cardiology and ICU team.
    

**System Actions:**

- `ClinicalEncounter` created
    
- `Diagnosis` (provisional, critical) recorded
    
- **Code STEMI** triggered
    

---

### **03:35 AM – Emergency Stabilization**

- Interventions initiated:
    
    - Oxygen via non-rebreather mask
        
    - IV access ×2
        
    - Aspirin + Clopidogrel administered
        
    - IV fluids cautiously
        
- Thrombolysis preparedness initiated.
    

**System Actions:**

- `MedicationAdministration` logged
    
- Resuscitation notes captured
    

---

### **03:38 AM – Emergency Diagnostics (Bedside)**

- Point-of-care tests ordered:
    
    - Cardiac Troponin-I
        
    - ABG
        
    - RBS
        

**System Actions:**

- `InvestigationOrder` created
    
- Samples collected in ER
    

---

### **03:45 AM – Cardiology Review**

- **Consultant:** Dr. Sandeep Kulkarni (DM – Cardiology)
    
- Confirms STEMI with cardiogenic shock risk.
    

**Clinical Decision:**

- Immediate **ICU admission**
    
- Plan for thrombolysis followed by coronary angiography
    

**Admission Type:**

- **IPD – Emergency / Critical**
    
- **Level of Care:** ICU
    

**System Actions:**

- `IPDAdmissionRequest` created
    
- Priority marked **Critical**
    
- ER Visit status → **Referred to IPD (Critical)**
    

---

### **03:48 AM – Insurance Emergency Intimation**

- Insurance desk initiates **emergency cashless intimation**.
    
- Pre-auth flagged as **Post-Admission Approval** (as per policy).
    

**System Actions:**

- `InsurancePreAuth` created
    
- Status: **Emergency Intimation Sent**
    

---

### **03:50 AM – ICU Bed Allocation**

- ICU bed allocated:
    
    - **Unit:** Medical ICU
        
    - **Bed No:** MICU-03
        

**System Actions:**

- `Bed` marked **Occupied**
    
- `IPDAdmission` created
    
- Admission status: **Admitted – Critical**
    

---

### **03:55 AM – ER to ICU Handover**

- Structured SBAR handover completed:
    
    - Situation, Background, Assessment, Recommendation
        
- Patient transferred to ICU with monitoring.
    

**System Actions:**

- ER Visit status → **Closed (Converted to IPD)**
    
- ICU care plan initiated
    

---

## **4. Modules Touched**

- Emergency / ER
    
- Triage
    
- Patient Registration
    
- Doctor EMR
    
- Vitals & Monitoring
    
- Diagnostics (Point-of-Care)
    
- IPD Admission
    
- ICU / Critical Care
    
- Bed Management
    
- Insurance
    
- Billing (Deferred for emergency)
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `EmergencyVisit`
    
- `TriageAssessment`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `Diagnosis`
    
- `MedicationAdministration`
    
- `InvestigationOrder`
    
- `LabSample`
    
- `LabResult`
    
- `IPDAdmissionRequest`
    
- `IPDAdmission`
    
- `Bed`
    
- `InsurancePreAuth`
    
- `HandoverNote`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|ER Visit|Created|Under Triage|Immediate critical assessment|
|ER Visit|Under Triage|Registered|Minimal demographics captured|
|ER Visit|Registered|Under Treatment|Resuscitation started|
|ER Visit|Under Treatment|Referred to IPD (Critical)|STEMI diagnosed|
|IPD Admission|Draft|Admitted – Critical|ICU bed assigned|
|Bed|Available|Occupied|ICU allocation|
|ER Visit|Referred to IPD|Closed|Converted to IPD|

---

## **7. Exit Summary**

- **Exit Type:** ER Converted to IPD (Critical)
    
- **Patient Condition at Transfer:** Hemodynamically unstable but stabilized for transfer
    
- **Level of Care:** ICU
    
- **Continuity:** Seamless ER → ICU handover
    
- **ER Discharge:** Not applicable
    

---

## **8. Documents Generated**

- Emergency Triage Sheet
    
- ER Clinical Notes
    
- ECG Report
    
- Emergency Medication Sheet
    
- ICU Admission Note
    
- Insurance Emergency Intimation
    
- ER–ICU Handover Document
    

(All documents time-stamped for medico-legal audit)

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|ER Services|Deferred|
|Diagnostics|Deferred|
|ICU Billing|Initiated post-admission|
|**Total at ER Stage**|**₹0 (Emergency Override)**|

_(Emergency policy allows treatment before payment; billing starts in IPD.)_

---

## **10. Edge Cases / Validations Tested**

1. Priority I triage handling
    
2. Treatment before full registration
    
3. ER to ICU emergency conversion
    
4. Critical flag propagation across modules
    
5. Emergency insurance intimation without pre-auth
    
6. Deferred billing in life-threatening cases
    
7. ICU bed allocation under emergency
    
8. Structured ER–IPD handover documentation
    
9. Single UHID across ER and IPD
    
10. Complete medico-legal audit trail for critical care