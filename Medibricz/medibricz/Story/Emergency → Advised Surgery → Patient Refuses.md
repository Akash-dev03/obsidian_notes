Below is a **complete, end-to-end HMS patient journey story** authored from a **hospital domain expert and HMS QA architect perspective**, structured for **clinical safety, consent/refusal governance, ER–surgery coordination, and medico-legal audit**.

---

## **Scenario Code:** TC-ER-04

## **Scenario Name:** Emergency → Advised Surgery → Patient Refuses

---

## **1. Patient Profile**

- **Patient ID:** PAT-ER-000238
    
- **UHID:** UHID-2025-004126
    
- **Full Name:** Mr. Deepak Rao
    
- **Age / DOB:** 47 years / 1977-10-19
    
- **Gender:** Male
    
- **Contact Number:** +91-95XXXXXXXX
    
- **Address:** Yelahanka, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 7718)
    
- **Marital Status:** Married
    
- **Blood Group:** O+
    
- **Known Allergies:** None
    
- **Existing Conditions:** Hypertension (on medication)
    
- **Insurance:** Yes
    
    - **Payer:** Star Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** STAR-IND-882741
        

---

## **2. Entry Point**

- **Date:** 2025-02-05
    
- **Time:** 01:42 AM
    
- **Entry Mode:** Walk-in (assisted by relative)
    
- **Department:** Emergency Room (ER)
    
- **Chief Complaint:** Severe right lower abdominal pain with vomiting (8 hours)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **01:42 AM – Emergency Arrival & Triage**

- Patient received at ER triage bay.
    
- Immediate triage performed prior to full registration.
    

**Triage Findings:**

- Severe abdominal pain (VAS 8/10)
    
- Nausea and vomiting
    
- Guarding present
    

**Triage Category:** **Priority II – Urgent**

**System Actions:**

- `EmergencyVisit` created (temporary)
    
- Triage timestamp captured
    
- Status: **Under Triage**
    

---

### **01:45 AM – Emergency Registration**

- Minimal demographics captured.
    
- Temporary ER number generated.
    
- UHID created and mapped.
    

**System Actions:**

- `Patient` created
    
- `UHID` generated
    
- ER visit linked to UHID
    
- Status → **Registered**
    

---

### **01:48 AM – Initial Vitals & Monitoring**

- Vitals recorded:
    
    - BP: 138/86 mmHg
        
    - Pulse: 104 bpm
        
    - SpO₂: 98%
        
    - Temperature: 100.2°F
        

**System Actions:**

- `Vitals` created
    
- ER Visit status → **Under Treatment**
    

---

### **01:52 AM – Emergency Doctor Assessment**

- **Attending Doctor:** Dr. Anil Deshmukh (MD – Emergency Medicine)
    
- Focused abdominal examination performed.
    

**Provisional Diagnosis:**

- **Suspected Acute Appendicitis**
    

**Clinical Decision:**

- Emergency diagnostics required.
    

**Investigations Ordered:**

1. CBC
    
2. Ultrasound Abdomen
    

**System Actions:**

- `ClinicalEncounter` created
    
- `InvestigationOrder` created
    
- ER Visit status → **Awaiting Diagnostics**
    

---

### **02:05 AM – Diagnostics & Results**

- Blood sample collected.
    
- Ultrasound performed.
    

**Results:**

- CBC: Elevated WBC (15,800/mm³)
    
- USG Abdomen: Inflamed, non-compressible appendix
    

**System Actions:**

- `LabResult` created
    
- `RadiologyReport` created
    
- Status: **Completed**
    

---

### **02:18 AM – Surgical Consultation**

- **On-call Surgeon:** Dr. Vivek Shetty (MS – General Surgery)
    
- Reviews clinical findings and reports.
    

**Final Diagnosis:**

- **Acute Appendicitis**
    

---

### **02:22 AM – Emergency Surgery Advice**

- Surgeon advises:
    
    - **Emergency Appendectomy**
        
    - Explains risks: perforation, peritonitis, sepsis
        
    - Explains benefits and urgency
        
- Recommended admission:
    
    - IPD – Emergency
        
    - OT booking required
        

**System Actions:**

- `ProcedureRecommendation` created
    
- `SurgeryAdvice` documented
    
- ER Visit status → **Surgery Advised (Emergency)**
    

---

### **02:30 AM – Patient Counseling**

- Patient and attendant counseled extensively.
    
- Concerns raised:
    
    - Fear of surgery
        
    - Financial concerns despite insurance
        

---

### **02:35 AM – Surgery Refusal**

- Patient **refuses surgery against medical advice**.
    
- Surgeon documents:
    
    - Nature of emergency explained
        
    - High-risk consequences explained
        
    - Patient decision recorded
        

**Consent / Refusal Handling:**

- **Emergency Surgery Refusal Form** digitally signed by patient and witness.
    

**System Actions:**

- `TreatmentRefusal` record created
    
- Refusal reason: **Patient decision (Emergency refusal)**
    
- ER Visit status → **Completed – Surgery Refused**
    

---

### **02:42 AM – ER Discharge (Against Medical Advice)**

- Patient discharged **LAMA (Left Against Medical Advice)**.
    
- Discharge advice provided:
    
    - Return immediately if pain worsens
        
    - Written risk warning handed over
        

**System Actions:**

- `DischargeSummary` created
    
- ER Visit status → **LAMA Discharged**
    

---

## **4. Modules Touched**

- Emergency / ER
    
- Triage
    
- Patient Registration
    
- Doctor EMR
    
- Diagnostics (Lab & Radiology)
    
- Surgery / OT Advisory
    
- Consent & Refusal Management
    
- Insurance (view-only)
    
- Documents
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `EmergencyVisit`
    
- `TriageAssessment`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `InvestigationOrder`
    
- `LabResult`
    
- `RadiologyReport`
    
- `Diagnosis`
    
- `ProcedureRecommendation`
    
- `TreatmentRefusal`
    
- `ConsentDocument`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|ER Visit|Created|Under Triage|Emergency assessment|
|ER Visit|Under Triage|Registered|Demographics captured|
|ER Visit|Registered|Under Treatment|Clinical care started|
|ER Visit|Under Treatment|Awaiting Diagnostics|Investigations ordered|
|ER Visit|Awaiting Diagnostics|Surgery Advised (Emergency)|Appendicitis confirmed|
|ER Visit|Surgery Advised|Completed – Surgery Refused|Patient declined|
|ER Visit|Completed|LAMA Discharged|Left against advice|

---

## **7. Exit Summary**

- **Exit Type:** LAMA (Emergency Surgery Refused)
    
- **Patient Condition at Exit:** Symptomatic, unstable risk
    
- **Admission Required:** Yes (declined)
    
- **Risk Explained:** Yes (documented)
    
- **Legal Safeguard:** Refusal consent obtained
    

---

## **8. Documents Generated**

- ER Triage Sheet
    
- ER Clinical Notes
    
- Lab & Ultrasound Reports
    
- Emergency Surgery Advice Note
    
- **Emergency Surgery Refusal / LAMA Consent Form**
    
- ER Discharge Summary (LAMA)
    

(All documents time-stamped and witness-linked)

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|ER Consultation|1,000|
|Diagnostics (CBC + USG)|1,200|
|Surgery|Not billed|
|**Total Payable**|**₹2,200**|
|Payment Status|Pending / Collected at exit (as per policy)|
