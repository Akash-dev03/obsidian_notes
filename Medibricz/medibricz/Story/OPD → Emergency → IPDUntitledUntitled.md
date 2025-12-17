## **1. Patient Profile**

- **Patient ID:** PAT-OPD-000614
    
- **UHID:** UHID-2025-006128
    
- **Full Name:** Mr. Praveen Kumar
    
- **Age / DOB:** 49 years / 1975-09-03
    
- **Gender:** Male
    
- **Contact Number:** +91-94XXXXXXXX
    
- **Address:** Rajajinagar, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 1186)
    
- **Marital Status:** Married
    
- **Blood Group:** B+
    
- **Known Allergies:** None
    
- **Existing Conditions:**
    
    - Hypertension (7 years)
        
- **Insurance:** Yes
    
    - **Payer:** HDFC ERGO Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** HDFC-IND-998341
        

---

## **2. Entry Point**

- **Date:** 2025-02-22
    
- **Time:** 10:05 AM
    
- **Entry Mode:** Walk-in
    
- **Initial Department:** OPD – General Medicine
    
- **Chief Complaint:** Giddiness, palpitations, and mild chest discomfort since morning
    

---

## **3. Timeline of Events (Step-by-Step)**

### **10:05 AM – OPD Registration**

- Patient registers at OPD front desk.
    
- UHID found (existing patient); demographics verified.
    
- OPD visit created.
    

**System Actions:**

- `OPDVisit` created
    
- Status: **Registered**
    

---

### **10:12 AM – Billing: OPD Consultation**

- Consultation fee applied: ₹600.
    
- Invoice generated and paid (UPI).
    

**System Actions:**

- `BillingInvoice` created
    
- Status: **Paid**
    

---

### **10:18 AM – Pre-Consultation Vitals**

- OPD nurse records vitals:
    
    - BP: 168/102 mmHg
        
    - Pulse: 112 bpm (irregular)
        
    - SpO₂: 96%
        
- Nurse flags abnormal vitals.
    

**System Actions:**

- `Vitals` created
    
- Clinical alert raised
    

---

### **10:22 AM – OPD Doctor Assessment**

- **Consulting Doctor:** Dr. Ritu Malhotra (MD – General Medicine)
    
- Immediate ECG done in OPD.
    

**ECG Findings:**

- Atrial fibrillation with rapid ventricular rate
    

**Clinical Assessment:**

- Patient unstable for OPD management.
    

**Decision:**

- **Immediate transfer to Emergency Room**
    

**System Actions:**

- `ClinicalEncounter` created
    
- OPD Visit status → **Escalated to Emergency**
    

---

### **10:26 AM – OPD to Emergency Transfer**

- Patient shifted on wheelchair to ER.
    
- OPD formally hands over case to ER team.
    

**System Actions:**

- `OPDToERTransfer` logged
    
- OPD visit locked (no further OPD actions)
    

---

### **10:28 AM – Emergency Triage**

- ER triage performed.
    

**Triage Findings:**

- Symptomatic tachyarrhythmia
    
- BP labile
    

**Triage Category:** **Priority II – Urgent**

**System Actions:**

- `EmergencyVisit` created
    
- Status: **Under Triage**
    

---

### **10:30 AM – ER Stabilization**

- Continuous cardiac monitoring initiated.
    
- IV access secured.
    
- Rate control medication started.
    

**System Actions:**

- `MedicationAdministration` logged
    
- ER status → **Under Treatment**
    

---

### **10:38 AM – Emergency Physician Review**

- **ER Doctor:** Dr. Nilesh Patil (MD – Emergency Medicine)
    
- Diagnosis:
    
    - **New-onset Atrial Fibrillation with RVR**
        

**Decision:**

- Admission required for:
    
    - Cardiac monitoring
        
    - Rate/rhythm control
        
    - Anticoagulation initiation
        

**System Actions:**

- `Diagnosis` recorded
    
- ER status → **Referred to IPD**
    

---

### **10:45 AM – Emergency IPD Admission Request**

- Admission type: **Emergency – Medical**
    
- Level of care: HDU / monitored ward
    

**System Actions:**

- `IPDAdmissionRequest` created
    

---

### **10:50 AM – Insurance Emergency Intimation**

- Emergency cashless intimation sent.
    
- Pre-auth to be completed post-admission.
    

**System Actions:**

- `InsurancePreAuth` created
    
- Status: **Emergency Intimation Sent**
    

---

### **10:55 AM – Bed Allocation**

- Ward: Cardiac HDU
    
- Bed No: CHDU-04
    

**System Actions:**

- `Bed` marked **Occupied**
    
- `IPDAdmission` created
    
- Status: **Admitted (Emergency)**
    

---

### **11:00 AM – ER to IPD Handover**

- SBAR handover completed.
    
- Patient shifted to HDU with monitor.
    

**System Actions:**

- ER Visit status → **Closed (Converted to IPD)**
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD
    
- Doctor EMR
    
- Billing
    
- Emergency / ER
    
- Triage
    
- IPD Admission
    
- Bed Management
    
- Insurance
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `OPDVisit`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `BillingInvoice`
    
- `EmergencyVisit`
    
- `TriageAssessment`
    
- `MedicationAdministration`
    
- `Diagnosis`
    
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
|OPD Visit|Registered|Escalated to Emergency|Clinical instability|
|ER Visit|Created|Under Treatment|Stabilization started|
|ER Visit|Under Treatment|Referred to IPD|Admission required|
|IPD Admission|Draft|Admitted (Emergency)|Bed allocated|
|OPD Visit|Escalated|Closed|Converted to ER|
|ER Visit|Referred to IPD|Closed|Converted to IPD|

---

## **7. Exit Summary**

- **Exit Type:** OPD → ER → IPD Conversion
    
- **Patient Condition at Transfer:** Stabilized, monitored
    
- **Admission Nature:** Emergency Medical
    
- **Continuity of Care:** Single UHID across OPD, ER, IPD
    
- **OPD Exit:** Escalation, not discharge
    

---

## **8. Documents Generated**

- OPD Consultation Note
    
- OPD ECG Report
    
- ER Triage Sheet
    
- ER Treatment Record
    
- ER–IPD Handover Note
    
- Emergency Admission Slip
    
- Insurance Emergency Intimation
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|OPD Consultation|600|
|ER Services|Deferred|
|IPD Billing|To start post-admission|
|**Total Collected at OPD**|**₹600**|

_(Emergency/IPD billing initiated after admission as per policy.)_

---

## **10. Edge Cases / Validations Tested**

1. OPD escalation without patient discharge
    
2. Abnormal vitals triggering emergency transfer
    
3. OPD billing before escalation
    
4. Locking OPD visit after ER handoff
    
5. ER admission without duplicate UHID
    
6. Emergency admission from OPD
    
7. Insurance emergency intimation workflow
    
8. Bed allocation under emergency priority
    
9. Seamless OPD → ER → IPD status continuity
    
10. Complete audit trail for medico-legal safety