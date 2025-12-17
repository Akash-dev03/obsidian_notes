## **1. Patient Profile**

- **Patient ID:** PAT-OPD-000312
    
- **UHID:** UHID-2025-001742
    
- **Full Name:** Ms. Priya Sharma
    
- **Age / DOB:** 29 years / 1995-09-18
    
- **Gender:** Female
    
- **Contact Number:** +91-98XXXXXXXX
    
- **Address:** Indiranagar, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 9173)
    
- **Marital Status:** Single
    
- **Blood Group:** B+
    
- **Known Allergies:** Penicillin
    
- **Existing Conditions:** None
    
- **Insurance:** Not applicable (Self-pay OPD)
    

---

## **2. Entry Point**

- **Date:** 2025-01-16
    
- **Time:** 10:08 AM
    
- **Entry Mode:** Walk-in
    
- **Department:** OPD Registration
    
- **Chief Complaint:** Lower abdominal pain and nausea for 1 day
    

---

## **3. Timeline of Events (Step-by-Step)**

### **10:08 AM – Patient Registration**

- Front desk searches patient using mobile number.
    
- Patient not found → new registration created.
    
- UHID auto-generated.
    
- Demographics, allergy information recorded.
    

**System Actions:**

- `Patient` created
    
- `UHID` generated
    
- Registration marked as **OPD**
    

---

### **10:14 AM – OPD Visit Creation**

- OPD visit created under:
    
    - **Department:** General Medicine
        
    - **Consulting Doctor:** Dr. Suresh Menon (MD – Internal Medicine)
        
- Visit type: **New OPD Consultation**
    
- Token generated: **GM-041**
    

**System Actions:**

- `OPDVisit` created
    
- Status: **Registered**
    

---

### **10:18 AM – Billing: Consultation Fee**

- Consultation fee applied: ₹600
    
- Invoice generated.
    

**System Actions:**

- `BillingInvoice` created
    
- Line Item:
    
    - OPD Consultation – ₹600
        
- Payment Mode: Cash
    
- Status: **Paid**
    

---

### **10:26 AM – Pre-Consultation Vitals**

- Patient marked as arrived by OPD nurse.
    
- Vitals recorded:
    
    - BP: 118/76 mmHg
        
    - Pulse: 90 bpm
        
    - Temperature: 98.9°F
        
    - SpO₂: 99%
        

**System Actions:**

- `Vitals` entry created
    
- OPD Visit status → **In Consultation**
    

---

### **10:32 AM – Doctor Consultation**

- Doctor documents symptoms and performs abdominal examination.
    
- Provisional diagnosis:
    
    - **Suspected Urinary Tract Infection (UTI)**
        

**Clinical Decision:**

- Diagnostics required before final diagnosis.
    

**Investigations Ordered:**

1. Complete Urine Examination (CUE)
    
2. CBC (Complete Blood Count)
    

**System Actions:**

- `ClinicalEncounter` created
    
- `InvestigationOrder` generated
    
- OPD Visit status → **Awaiting Diagnostics**
    

---

### **10:38 AM – Billing: Diagnostic Charges**

- Diagnostics bill auto-generated.
    

**Billing Details:**

- CBC – ₹350
    
- Urine Routine – ₹150
    

**System Actions:**

- Diagnostic `BillingInvoice` created
    
- Total: ₹500
    
- Payment Mode: UPI
    
- Status: **Paid**
    

---

### **10:45 AM – Sample Collection**

- Patient reports to Diagnostic Lab.
    
- Phlebotomist collects blood and urine samples.
    

**System Actions:**

- `LabSample` created
    
- Sample status: **Collected**
    
- Barcode generated and mapped
    

---

### **11:20 AM – Lab Processing**

- Samples processed.
    
- Results validated by lab technician and pathologist.
    

**System Actions:**

- `LabResult` entries created
    
- Status: **Completed**
    

---

### **11:35 AM – Doctor Review of Reports**

- Patient recalled to OPD.
    
- Doctor reviews results:
    
    - Elevated WBC count
        
    - Urine shows pus cells
        

**Final Diagnosis:**

- **Uncomplicated Urinary Tract Infection**
    

**Treatment Plan:**

- Oral antibiotics (non-penicillin)
    
- Increased fluid intake
    
- No admission required
    

**Prescription Issued:**

- Nitrofurantoin 100 mg – BID for 5 days
    
- Paracetamol – SOS
    

**System Actions:**

- `Diagnosis` finalized
    
- `Prescription` generated
    
- OPD Visit status → **Completed**
    

---

### **11:48 AM – OPD Exit**

- Patient counseled.
    
- Follow-up advised after 5 days if symptoms persist.
    
- Patient exits hospital.
    

---

## **4. Modules Touched**

- Patient Master
    
- Registration
    
- OPD
    
- EMR / Doctor Notes
    
- Diagnostics (Lab)
    
- Billing
    
- Payments
    
- Reports / Documents
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientAllergy`
    
- `OPDVisit`
    
- `Doctor`
    
- `Department`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `InvestigationOrder`
    
- `LabSample`
    
- `LabResult`
    
- `Diagnosis`
    
- `Prescription`
    
- `BillingInvoice`
    
- `BillingLineItem`
    
- `PaymentTransaction`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

| Entity          | From                 | To                   | Reason              |
| --------------- | -------------------- | -------------------- | ------------------- |
| OPD Visit       | Created              | Registered           | Visit initiated     |
| OPD Visit       | Registered           | In Consultation      | Patient called      |
| OPD Visit       | In Consultation      | Awaiting Diagnostics | Tests ordered       |
| Lab Sample      | Created              | Collected            | Sample drawn        |
| Lab Sample      | Collected            | Completed            | Processing finished |
| OPD Visit       | Awaiting Diagnostics | Completed            | Diagnosis finalized |
| Billing Invoice | Draft                | Paid                 | Payment received    |

---

## **7. Exit Summary**

- **Exit Type:** OPD Completed – Diagnostic Closure
    
- **Patient Condition:** Stable
    
- **Admission Required:** No
    
- **Referral:** No
    
- **Follow-up:** Optional OPD review after 5 days
    

---

## **8. Documents Generated**

- OPD Registration Slip
    
- OPD Consultation Bill
    
- Diagnostic Bill
    
- Lab Reports (CBC, Urine Routine)
    
- OPD Prescription
    
- OPD Visit Summary
    

(All documents stored as PDFs under Document Management)

---

## **9. Final Billing Summary**

| Category         | Amount (₹) |
| ---------------- | ---------- |
| OPD Consultation | 600        |
| Diagnostics      | 500        |
| Pharmacy         | 0          |
| **Total Paid**   | **₹1,100** |
| Payment Modes    | Cash + UPI |
| Outstanding      | ₹0         |
