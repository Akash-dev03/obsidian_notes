## **1. Patient Profile**

- **Patient ID:** PAT-OPD-000688
    
- **UHID:** UHID-2025-007114
    
- **Full Name:** Mr. Ashok Kulkarni
    
- **Age / DOB:** 62 years / 1962-01-17
    
- **Gender:** Male
    
- **Contact Number:** +91-95XXXXXXXX
    
- **Address:** Sadashivanagar, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 7741)
    
- **Marital Status:** Married
    
- **Blood Group:** O+
    
- **Known Allergies:** None
    
- **Existing Conditions:**
    
    - Type 2 Diabetes Mellitus (15 years)
        
    - Hypertension (12 years)
        
    - Ischemic Heart Disease (history of PTCA)
        
- **Insurance:** Yes
    
    - **Payer:** Star Health Insurance
        
    - **Policy Type:** Senior Citizen Mediclaim
        
    - **Policy Number:** STAR-SEN-882915
        

---

## **2. Entry Point**

- **Date:** 2025-03-10
    
- **Time:** 09:30 AM
    
- **Initial Entry:** OPD – General Medicine
    
- **Chief Complaint:** Fever, cough, and breathlessness for 3 days
    

---

## **3. Timeline of Events (Step-by-Step)**

### **09:30 AM – OPD Registration**

- Patient arrives at OPD front desk.
    
- UHID found (existing patient).
    
- Demographics and insurance verified.
    

**System Actions:**

- `OPDVisit` created
    
- Status: **Registered**
    

---

### **09:38 AM – Billing: OPD Consultation**

- Consultation fee: ₹700.
    
- Invoice generated and paid (Card).
    

**System Actions:**

- `BillingInvoice` created
    
- Status: **Paid**
    

---

### **09:45 AM – OPD Vitals & Screening**

- Vitals recorded:
    
    - BP: 146/88 mmHg
        
    - Pulse: 98 bpm
        
    - Temperature: 101.2°F
        
    - SpO₂: 94% (room air)
        

**System Actions:**

- `Vitals` created
    
- Mild hypoxia flagged
    

---

### **09:52 AM – OPD Doctor Consultation**

- **Consultant:** Dr. Pranav Joshi (MD – General Medicine)
    
- Chest examination suggests lower respiratory infection.
    

**Provisional Diagnosis:**

- **Community Acquired Pneumonia**
    

**Decision:**

- Planned medical IPD admission for IV antibiotics and monitoring.
    

**System Actions:**

- `ClinicalEncounter` created
    
- OPD Visit status → **Referred to IPD**
    

---

### **10:05 AM – Planned IPD Admission**

- Patient admitted from OPD.
    
- Admission type: **Planned – Medical**
    

**System Actions:**

- `IPDAdmission` created
    
- Status: **Admitted**
    

---

### **10:12 AM – Ward Bed Allocation**

- Ward: Semi-Private Ward
    
- Bed No: SPW-21
    

**System Actions:**

- `Bed` marked **Occupied**
    

---

### **10:30 AM – Admission Assessment**

- Nursing assessment completed.
    
- Baseline vitals:
    
    - BP: 150/92 mmHg
        
    - Pulse: 96 bpm
        
    - SpO₂: 93%
        

**System Actions:**

- `NursingAssessment`
    
- `Vitals` recorded
    

---

### **11:00 AM – Inpatient Treatment Started**

- IV antibiotics initiated.
    
- Blood cultures and labs sent.
    

**System Actions:**

- `MedicationAdministration`
    
- `InvestigationOrder` created
    

---

## **Day 2 – Sudden Deterioration in IPD**

### **02:20 AM – Acute Clinical Deterioration**

- Patient develops:
    
    - Sudden severe breathlessness
        
    - SpO₂ drops to 82% on oxygen
        
    - Altered sensorium
        

**System Actions:**

- Emergency vitals captured
    
- `ClinicalAlert` triggered
    

---

### **02:25 AM – Ward Emergency Call**

- Rapid Response Team activated.
    
- Patient shifted to Emergency Room for resuscitation.
    

**System Actions:**

- `IPDToERTransfer` logged
    
- IPD status → **Emergency Escalation**
    

---

### **02:30 AM – Emergency Triage (From IPD)**

- ER triage performed immediately.
    

**Triage Category:** **Priority I – Resuscitation**

**System Actions:**

- `EmergencyVisit` created (source: IPD)
    
- Status: **Under Treatment**
    

---

### **02:32 AM – Emergency Stabilization**

- High-flow oxygen started.
    
- ABG sent.
    
- Vasopressor support initiated.
    

**Provisional Diagnosis Update:**

- **Severe Pneumonia with Septic Shock**
    

**System Actions:**

- `ClinicalEncounter` updated
    
- `MedicationAdministration` logged
    

---

### **02:40 AM – ICU Escalation Decision**

- Intensivist reviews patient.
    
- Decision for immediate ICU admission with ventilatory support.
    

**System Actions:**

- `ICUTransferRequest` created
    
- ER status → **Referred to ICU**
    

---

### **02:45 AM – ICU Bed Allocation**

- ICU: Medical ICU
    
- Bed No: MICU-08
    

**System Actions:**

- `ICUAdmission` created
    
- ICU bed marked **Occupied**
    
- ER visit closed (converted)
    

---

### **02:50 AM – ICU Admission**

- Patient intubated.
    
- Mechanical ventilation started.
    

**System Actions:**

- `VentilationRecord`
    
- `ICUProgressNotes` initiated
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD
    
- IPD Admission
    
- Ward Management
    
- Emergency / ER
    
- ICU / Critical Care
    
- Bed Management
    
- Diagnostics
    
- Pharmacy
    
- Billing
    
- Insurance
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `OPDVisit`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `BillingInvoice`
    
- `IPDAdmission`
    
- `Bed`
    
- `NursingAssessment`
    
- `MedicationAdministration`
    
- `InvestigationOrder`
    
- `EmergencyVisit`
    
- `ICUAdmission`
    
- `VentilationRecord`
    
- `ICUProgressNotes`
    
- `InsurancePreAuth`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|OPD Visit|Registered|Referred to IPD|Pneumonia|
|IPD Admission|Admitted|Emergency Escalation|Sudden deterioration|
|ER Visit|Created|Under Treatment|Resuscitation|
|ER Visit|Under Treatment|Referred to ICU|Septic shock|
|ICU Admission|Draft|Admitted|Ventilatory support|
|Ward Bed|Occupied|Available|ICU transfer|

---

## **7. Exit Summary**

- **Exit Type:** OPD → IPD → ER → ICU Conversion
    
- **Patient Condition at ICU Admission:** Critical, ventilated
    
- **Level of Care:** ICU
    
- **OPD/IPD Exit:** Converted, not discharged
    
- **Continuity:** Single UHID across all stages
    

---

## **8. Documents Generated**

- OPD Consultation Note
    
- IPD Admission Note
    
- Emergency Escalation Record
    
- ER Treatment Sheet
    
- ICU Admission & Ventilation Notes
    
- Emergency–ICU Handover Document
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|OPD Consultation|700|
|IPD (Ward)|Interim|
|ER Services|Deferred|
|ICU Billing|Initiated post-admission|
|**Total Collected Pre-ICU**|**₹700**|

_(Emergency escalation allows deferred billing.)_

---

## **10. Edge Cases / Validations Tested**

1. Planned IPD deterioration handling
    
2. Ward → ER emergency escalation
    
3. ICU admission originating from IPD
    
4. Single UHID across OPD, IPD, ER, ICU
    
5. Real-time bed release and ICU allocation
    
6. Emergency vitals override normal workflow
    
7. Deferred billing during life-threatening event
    
8. Insurance escalation handling
    
9. Audit trail for deterioration timing
    
10. Prevention of duplicate admissions