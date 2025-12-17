## **1. Patient Profile**

- **Patient ID:** PAT-ER-000302
    
- **UHID:** UHID-2025-006742
    
- **Full Name:** Mr. Ajay Deshpande
    
- **Age / DOB:** 54 years / 1970-12-06
    
- **Gender:** Male
    
- **Contact Number:** +91-93XXXXXXXX
    
- **Address:** Kothrud, Pune, Maharashtra
    
- **ID Proof:** Aadhaar (Last 4 digits: 4612)
    
- **Marital Status:** Married
    
- **Blood Group:** O+
    
- **Known Allergies:** None known
    
- **Existing Conditions:**
    
    - Type 2 Diabetes Mellitus (10 years)
        
    - Dyslipidemia
        
- **Insurance:** Yes
    
    - **Payer:** Star Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** STAR-IND-771920
        

---

## **2. Entry Point**

- **Date:** 2025-03-03
    
- **Time:** 11:48 PM
    
- **Entry Mode:** Ambulance (108)
    
- **Department:** Emergency Room (ER)
    
- **Chief Complaint:** Severe abdominal pain, distension, vomiting, and fever (12 hours)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **11:48 PM – Emergency Arrival & Triage**

- Ambulance handover completed.
    
- Immediate triage performed before registration.
    

**Triage Findings:**

- Severe abdominal pain (VAS 9/10)
    
- Hypotension, tachycardia
    
- Guarding and rigidity
    

**Triage Category:** **Priority I – Resuscitation (Critical)**

**System Actions:**

- `EmergencyVisit` created (temporary)
    
- Triage timestamp captured
    
- Status: **Under Triage**
    

---

### **11:50 PM – Rapid Emergency Registration**

- Minimal demographics captured from attendant.
    
- Temporary ER number generated.
    
- UHID created and mapped.
    

**System Actions:**

- `Patient` created
    
- `UHID` generated
    
- ER visit linked
    
- Status → **Registered**
    

---

### **11:52 PM – Immediate Stabilization**

- ER team initiates resuscitation.
    
- Vitals recorded:
    
    - BP: 82/54 mmHg
        
    - Pulse: 124 bpm
        
    - SpO₂: 92%
        
    - Temperature: 101.8°F
        

**Interventions:**

- Oxygen via non-rebreather mask
    
- Two IV lines secured
    
- IV fluids bolus
    
- Broad-spectrum antibiotics started
    

**System Actions:**

- `Vitals` recorded
    
- `MedicationAdministration` logged
    
- ER status → **Under Treatment**
    

---

### **11:58 PM – Emergency Physician Assessment**

- **ER Consultant:** Dr. Kunal Mehra (MD – Emergency Medicine)
    
- Provisional diagnosis:
    
    - **Suspected Perforation Peritonitis with Septic Shock**
        

**Clinical Decision:**

- Immediate ICU admission for stabilization prior to surgery.
    

**System Actions:**

- `ClinicalEncounter` created
    
- `Diagnosis` (critical, provisional) recorded
    
- ER status → **Referred to ICU**
    

---

### **12:05 AM – ICU Admission (Emergency)**

- **ICU:** Surgical ICU
    
- **Bed:** SICU-02
    

**System Actions:**

- `ICUAdmission` created
    
- Bed marked **Occupied**
    
- ER visit status → **Closed (Converted to ICU)**
    

---

### **12:10 AM – ICU Stabilization**

- Central line placed.
    
- Vasopressor support initiated.
    
- Arterial blood gas and labs sent.
    

**System Actions:**

- `ICUProgressNotes`
    
- `VentilationRecord` (non-invasive)
    
- `InvestigationOrder` created
    

---

### **12:35 AM – Diagnostics Review**

**Results:**

- ABG: Metabolic acidosis
    
- CBC: WBC 19,600
    
- X-Ray Abdomen: Free air under diaphragm
    

**Final Diagnosis:**

- **Hollow Viscus Perforation with Septic Shock**
    

---

### **12:45 AM – Emergency Surgery Decision**

- **On-call Surgeon:** Dr. Suresh Patankar (MS – General Surgery)
    
- Surgery advised:
    
    - **Emergency Exploratory Laparotomy**
        

**Consent:**

- High-risk emergency consent obtained from spouse.
    

**System Actions:**

- `ProcedureRecommendation` created
    
- `ConsentDocument` captured
    
- ICU status → **Planned for OT**
    

---

### **12:55 AM – Insurance Emergency Intimation**

- Cashless emergency intimation sent.
    
- Pre-auth flagged **Post-Admission / Post-Surgery**.
    

**System Actions:**

- `InsurancePreAuth` created
    
- Status: **Emergency Intimation Sent**
    

---

### **01:05 AM – Transfer from ICU to OT**

- Patient shifted with full monitoring.
    

**System Actions:**

- `OTSchedule` → **In Progress**
    
- ICU bed marked **On Leave (OT)**
    

---

### **01:20 AM – Surgery Performed**

- **Procedure:** Exploratory Laparotomy + Perforation Repair
    
- Duration: 2 hours 10 minutes
    
- Intra-op findings: Duodenal perforation
    

**System Actions:**

- `ProcedureRecord` created
    
- `OTNotes`
    
- `AnesthesiaNotes`
    

---

### **03:30 AM – Post-Operative Recovery (ICU)**

- Patient shifted back to ICU for post-op ventilation.
    

**System Actions:**

- `OTSchedule` → **Completed**
    
- ICU bed → **Occupied**
    
- `PostOpICUNotes` created
    

---

### **Day 2–3 – ICU Care**

- Ventilator weaning.
    
- Vasopressors tapered.
    
- Hemodynamics stabilized.
    

**System Actions (Daily):**

- `ICUProgressNotes`
    
- `MedicationAdministration`
    

---

### **Day 4 – Transfer to IPD Ward**

- Patient extubated and stable.
    

**Clinical Decision:**

- Shift to surgical ward.
    

**System Actions:**

- `ICUTransferOutOrder`
    
- Ward Bed Allocated: **Surgical Ward – SW-14**
    
- `IPDAdmission` (ward care) continued
    

---

### **Day 4–7 – Ward Recovery**

- Oral diet initiated.
    
- Wound care and mobilization.
    
- Daily surgeon rounds.
    

**System Actions:**

- `DailyProgressNote`
    
- `NursingNotes`
    

---

### **Day 7 – Discharge Day**

#### **11:00 AM – Discharge Order**

- Patient clinically stable.
    

#### **12:00 PM – Final Billing**

- ICU + OT + IPD consolidated bill generated.
    
- Insurance claim initiated.
    

#### **01:00 PM – Discharge**

- Discharge summary explained.
    
- Follow-up advised after 7 days.
    

**System Actions:**

- `DischargeSummary`
    
- IPD status → **Discharged**
    
- Bed status → **Available**
    

---

## **4. Modules Touched**

- Emergency / ER
    
- Triage
    
- ICU / Critical Care
    
- OT / Surgery
    
- Anesthesia
    
- IPD (Ward)
    
- Bed Management
    
- Diagnostics
    
- Pharmacy
    
- Billing
    
- Insurance
    
- Discharge
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `EmergencyVisit`
    
- `TriageAssessment`
    
- `ICUAdmission`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `Diagnosis`
    
- `MedicationAdministration`
    
- `InvestigationOrder`
    
- `LabResult`
    
- `ProcedureRecommendation`
    
- `ConsentDocument`
    
- `OTSchedule`
    
- `ProcedureRecord`
    
- `AnesthesiaNotes`
    
- `ICUProgressNotes`
    
- `IPDAdmission`
    
- `Bed`
    
- `BillingInvoice`
    
- `InsurancePreAuth`
    
- `InsuranceClaim`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|ER Visit|Under Treatment|Referred to ICU|Septic shock|
|ICU Admission|Admitted|Planned for OT|Surgery required|
|OT Schedule|In Progress|Completed|Surgery done|
|ICU Admission|Post-Op ICU|Stable|Clinical improvement|
|IPD Admission|ICU|Ward|Step-down care|
|IPD Admission|Ward|Discharged|Recovery completed|

---

## **7. Exit Summary**

- **Exit Type:** IPD Discharge after ICU + Surgery
    
- **Condition at Exit:** Stable
    
- **Total LOS:** 7 days
    
- **ICU Stay:** 3 days
    
- **Follow-up:** Surgical OPD – 7 days
    

---

## **8. Documents Generated**

- ER Triage & Treatment Sheet
    
- ICU Admission & Progress Notes
    
- Emergency Surgery Consent
    
- OT & Anesthesia Notes
    
- ICU–Ward Transfer Note
    
- Final Discharge Summary
    
- Insurance Claim Documents
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|ICU Charges|90,000|
|OT & Surgeon Fees|1,40,000|
|Anesthesia|30,000|
|Diagnostics|22,000|
|Ward Charges|25,000|
|Pharmacy|28,000|
|**Total Bill**|**₹3,35,000**|
|Insurance Approved|₹3,00,000|
|Patient Payable|₹35,000|

---

## **10. Edge Cases / Validations Tested**

1. Emergency to ICU without delay
    
2. ICU stabilization before OT
    
3. Emergency surgery consent handling
    
4. ICU → OT → ICU bed leave logic
    
5. Post-op ICU mandatory stay
    
6. Step-down from ICU to ward
    
7. Consolidated ICU + OT + IPD billing
    
8. Emergency insurance post-auth workflow
    
9. Critical audit trail continuity
    
10. No duplicate admissions across units