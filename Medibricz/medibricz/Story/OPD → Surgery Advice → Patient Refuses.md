## **1. Patient Profile**

- **Patient ID:** PAT-OPD-000529
    
- **UHID:** UHID-2025-002689
    
- **Full Name:** Ms. Kavita Nair
    
- **Age / DOB:** 42 years / 1982-08-21
    
- **Gender:** Female
    
- **Contact Number:** +91-99XXXXXXXX
    
- **Address:** Marathahalli, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 3147)
    
- **Marital Status:** Married
    
- **Blood Group:** AB+
    
- **Known Allergies:** None
    
- **Existing Conditions:** Hypothyroidism (on medication)
    
- **Insurance:** Yes
    
    - **Payer:** HDFC ERGO Health Insurance
        
    - **Policy Type:** Family Floater
        
    - **Policy Number:** HDFC-FAM-556278
        

---

## **2. Entry Point**

- **Date:** 2025-01-24
    
- **Time:** 11:05 AM
    
- **Entry Mode:** Walk-in
    
- **Department:** OPD Registration
    
- **Chief Complaint:** Recurrent right upper abdominal pain after meals (3 months)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **11:05 AM – Patient Registration**

- Patient searched using UHID (existing patient).
    
- Demographics and insurance validity confirmed.
    

**System Actions:**

- `Patient` retrieved
    
- Insurance marked **Active**
    
- OPD context initialized
    

---

### **11:12 AM – OPD Visit Creation**

- OPD visit created under:
    
    - **Department:** General Surgery
        
    - **Consulting Doctor:** Dr. Rajeev Kulkarni (MS – General Surgery)
        
- Visit type: **New Consultation**
    
- Token generated: **GS-019**
    

**System Actions:**

- `OPDVisit` created
    
- Status: **Registered**
    

---

### **11:18 AM – Billing: OPD Consultation**

- Consultation fee: ₹700
    
- Invoice generated and paid (UPI).
    

**System Actions:**

- `BillingInvoice` created
    
- Status: **Paid**
    

---

### **11:25 AM – Pre-Consultation Vitals**

- Vitals recorded:
    
    - BP: 122/78 mmHg
        
    - Pulse: 84 bpm
        
    - Temperature: 98.4°F
        
    - SpO₂: 99%
        

**System Actions:**

- `Vitals` entry created
    
- OPD Visit status → **In Consultation**
    

---

### **11:32 AM – Doctor Consultation**

- Detailed abdominal examination performed.
    
- Ultrasound report from prior visit reviewed.
    

**Findings:**

- Multiple gallstones
    
- Thickened gallbladder wall
    

**Diagnosis:**

- **Chronic Calculous Cholecystitis**
    

---

### **11:40 AM – Surgery Advice**

- Doctor advises:
    
    - **Elective Laparoscopic Cholecystectomy**
        
    - Explains benefits, risks, recovery, and insurance coverage
        
- Expected admission:
    
    - IPD – Planned
        
    - Expected LOS: 2–3 days
        

**System Actions:**

- `ClinicalEncounter` updated
    
- `SurgeryAdvice` recorded
    
- `ProcedureRecommendation` created
    
- OPD Visit status → **Surgery Advised**
    

---

### **11:48 AM – Patient Counseling**

- Patient expresses concern regarding:
    
    - Fear of surgery
        
    - Family commitments
        
- Requests time to decide.
    

---

### **11:52 AM – Surgery Refusal**

- Patient explicitly refuses surgery **at this time**.
    
- Doctor documents:
    
    - Surgery explained in detail
        
    - Risks of delay explained
        
    - Patient refusal noted
        

**Consent Handling:**

- **Surgery Refusal Form** digitally acknowledged by patient.
    

**System Actions:**

- `TreatmentRefusal` record created
    
- Refusal reason captured (Patient Choice)
    
- OPD Visit status → **Completed – Surgery Refused**
    

---

### **11:58 AM – OPD Exit**

- Conservative management advised:
    
    - Dietary modification
        
    - Analgesics PRN
        
- Follow-up advised after 4 weeks or earlier if pain worsens.
    

---

## **4. Modules Touched**

- Patient Master
    
- Registration
    
- OPD
    
- Doctor EMR
    
- Billing
    
- Insurance (view-only)
    
- Consent / Refusal Management
    
- Documents
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientInsurance`
    
- `OPDVisit`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `Diagnosis`
    
- `ProcedureRecommendation`
    
- `TreatmentRefusal`
    
- `ConsentDocument`
    
- `BillingInvoice`
    
- `PaymentTransaction`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From|To|Reason|
|---|---|---|---|
|OPD Visit|Created|Registered|Visit initiated|
|OPD Visit|Registered|In Consultation|Patient called|
|OPD Visit|In Consultation|Surgery Advised|Surgical intervention recommended|
|OPD Visit|Surgery Advised|Completed – Surgery Refused|Patient declined surgery|
|Billing Invoice|Draft|Paid|Consultation fee settled|

---

## **7. Exit Summary**

- **Exit Type:** OPD Completed – Surgery Refused
    
- **Patient Condition:** Stable
    
- **Admission Required:** No (declined)
    
- **Risk Explained:** Yes
    
- **Follow-up:** Planned OPD review in 4 weeks
    

---

## **8. Documents Generated**

- OPD Registration Slip
    
- OPD Consultation Bill
    
- OPD Clinical Notes
    
- Surgery Advice Summary
    
- **Surgery Refusal / Informed Decline Consent**
    
- OPD Visit Summary
    

(All documents stored with patient acknowledgment and timestamp)

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|OPD Consultation|700|
|Diagnostics|0|
|Surgery|Not billed|
|**Total Paid**|**₹700**|
|Outstanding|₹0|

---

## **10. Edge Cases / Validations Tested**

1. Surgery advice without forced admission
    
2. Explicit patient refusal capture
    
3. Mandatory refusal reason entry
    
4. Legal consent/refusal documentation
    
5. OPD completion despite surgical recommendation
    
6. Prevention of IPD admission creation after refusal
    
7. Insurance not triggered without admission
    
8. Audit trail for counseling and refusal
    
9. Multiple advice entries allowed per OPD visit
    
10. Follow-up scheduling after refusal