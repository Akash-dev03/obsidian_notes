## **1. Patient Profile**

- **Patient ID:** PAT-OPD-000487
    
- **UHID:** UHID-2025-002314
    
- **Full Name:** Mr. Sunil Verma
    
- **Age / DOB:** 56 years / 1968-05-04
    
- **Gender:** Male
    
- **Contact Number:** +91-97XXXXXXXX
    
- **Address:** Jayanagar, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 6639)
    
- **Marital Status:** Married
    
- **Blood Group:** A+
    
- **Known Allergies:** None
    
- **Existing Conditions:** Type 2 Diabetes Mellitus (on oral medication)
    
- **Insurance:** Yes
    
    - **Payer:** Star Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** SHI-IND-98231477
        

---

## **2. Entry Point**

- **Date:** 2025-01-20
    
- **Time:** 08:55 AM
    
- **Entry Mode:** Walk-in
    
- **Department:** OPD Registration
    
- **Chief Complaint:** Progressive shortness of breath and chest discomfort on exertion (5 days)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **08:55 AM – Patient Registration**

- Patient searched using UHID (existing patient).
    
- Demographics verified and updated.
    
- Insurance details validated and marked as **Active**.
    

**System Actions:**

- `Patient` retrieved
    
- `InsurancePolicy` linked to patient
    
- Visit context set as OPD
    

---

### **09:02 AM – OPD Visit Creation**

- OPD visit created:
    
    - **Department:** Cardiology
        
    - **Consulting Doctor:** Dr. Nikhil Iyer (DM – Cardiology)
        
- Visit type: **Follow-up OPD**
    
- Token generated: **CARD-012**
    

**System Actions:**

- `OPDVisit` created
    
- Status: **Registered**
    

---

### **09:08 AM – Billing: OPD Consultation**

- Consultation fee applied: ₹800
    
- Invoice generated.
    

**System Actions:**

- `BillingInvoice` created
    
- Payment Mode: Insurance (cashless OPD not applicable)
    
- Patient pays upfront: Cash
    
- Status: **Paid**
    

---

### **09:15 AM – Pre-Consultation Vitals**

- Vitals recorded:
    
    - BP: 146/92 mmHg
        
    - Pulse: 96 bpm
        
    - SpO₂: 95% (room air)
        

**System Actions:**

- `Vitals` recorded
    
- OPD Visit status → **In Consultation**
    

---

### **09:22 AM – Doctor Consultation**

- Detailed cardiac examination performed.
    
- ECG reviewed (done previously).
    
- Provisional diagnosis:
    
    - **Suspected Stable Angina / Coronary Artery Disease**
        

**Clinical Decision:**

- Planned admission required for:
    
    - Coronary angiography
        
    - Cardiac monitoring
        
    - Optimization of comorbidities
        

**Admission Type Decision:**

- **IPD – Planned (Elective)**
    

**System Actions:**

- `ClinicalEncounter` saved
    
- `Diagnosis` (provisional) recorded
    
- OPD Visit status → **Referred to IPD**
    

---

### **09:38 AM – Planned IPD Admission Request**

- Doctor raises IPD admission request:
    
    - Admission date: Same day
        
    - Ward preference: Cardiac Ward – Twin Sharing
        
    - Expected LOS: 3–4 days
        

**System Actions:**

- `IPDAdmissionRequest` created
    
- Status: **Pending Bed Allocation**
    

---

### **09:45 AM – Insurance Pre-Authorization Initiated**

- Insurance desk initiates cashless pre-auth.
    
- Documents uploaded:
    
    - OPD notes
        
    - Provisional diagnosis
        
    - Admission recommendation
        

**System Actions:**

- `InsurancePreAuth` created
    
- Status: **Sent to Insurance**
    

---

### **10:05 AM – Bed Allocation**

- Bed manager allocates bed:
    
    - Ward: Cardiac Ward
        
    - Bed No: CW-12
        

**System Actions:**

- `Bed` marked as **Reserved**
    
- `IPDAdmission` created
    
- Admission status: **Admitted (Planned)**
    

---

### **10:15 AM – OPD Closure**

- OPD visit formally closed.
    
- IPD number generated and linked to same UHID.
    

**System Actions:**

- OPD Visit status → **Converted to IPD**
    
- OPD workflow ends
    

---

## **4. Modules Touched**

- Patient Master
    
- Registration
    
- OPD
    
- Doctor EMR
    
- Billing
    
- Insurance
    
- IPD Admission
    
- Bed Management
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientInsurance`
    
- `OPDVisit`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `Diagnosis`
    
- `BillingInvoice`
    
- `PaymentTransaction`
    
- `IPDAdmissionRequest`
    
- `IPDAdmission`
    
- `Bed`
    
- `InsurancePreAuth`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From|To|Reason|
|---|---|---|---|
|OPD Visit|Created|Registered|Visit initiated|
|OPD Visit|Registered|In Consultation|Patient called|
|OPD Visit|In Consultation|Referred to IPD|Planned admission decision|
|IPD Request|Created|Pending Bed|Awaiting allocation|
|Bed|Available|Reserved|Planned admission|
|IPD Admission|Draft|Admitted|Bed assigned|
|OPD Visit|Referred to IPD|Closed|Converted to IPD|

---

## **7. Exit Summary**

- **Exit Type:** OPD Converted to IPD
    
- **Admission Nature:** Planned / Elective
    
- **Patient Condition:** Stable
    
- **Continuity of Care:** Shifted to IPD without discharge
    
- **OPD Closure Reason:** Admission required
    

---

## **8. Documents Generated**

- OPD Registration Slip
    
- OPD Consultation Bill
    
- OPD Clinical Notes
    
- IPD Admission Request
    
- Insurance Pre-Authorization Form
    
- Bed Allotment Slip
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|OPD Consultation|800|
|Diagnostics (OPD)|0|
|IPD Charges|Not yet billed|
|**Total Paid (OPD)**|**₹800**|
|IPD Billing|To start post-admission|

---

## **10. Edge Cases / Validations Tested**

1. OPD to IPD planned conversion
    
2. Same-day admission workflow
    
3. Insurance pre-auth initiation from OPD
    
4. Bed reservation before admission
    
5. OPD closure without patient exit
    
6. Single UHID across OPD and IPD
    
7. Prevention of OPD billing post conversion
    
8. Audit trail for referral decision
    
9. Admission request vs admission creation
    
10. Handling elective (non-emergency) IPD flow