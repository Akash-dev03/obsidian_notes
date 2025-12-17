## **1. Patient Profile**

- **Patient ID:** PAT-OPD-000145
    
- **UHID:** UHID-2025-000981
    
- **Full Name:** Mr. Ramesh Kumar
    
- **Age / DOB:** 38 years / 1987-03-12
    
- **Gender:** Male
    
- **Contact Number:** +91-9XXXXXXXXX
    
- **Address:** Whitefield, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 4821)
    
- **Marital Status:** Married
    
- **Blood Group:** O+
    
- **Known Allergies:** None
    
- **Existing Conditions:** None
    
- **Insurance:** Not applicable (Self-pay OPD)
    

---

## **2. Entry Point**

- **Date:** 2025-01-14
    
- **Time:** 09:12 AM
    
- **Entry Mode:** Walk-in
    
- **Department:** OPD Registration Counter
    
- **Reason for Visit:** Fever and sore throat for 2 days
    

---

## **3. Timeline of Events (Step-by-Step)**

### **09:12 AM – Patient Registration**

- Front desk executive searches patient by mobile number.
    
- Patient not found → **New patient registration initiated**.
    
- UHID auto-generated.
    
- Demographic details captured.
    
- Registration fee not collected yet (bundled with consultation).
    

**System Actions:**

- `Patient` record created
    
- `UHID` generated
    
- Visit marked as **OPD**
    

---

### **09:18 AM – OPD Visit Creation**

- OPD visit created under:
    
    - **Department:** General Medicine
        
    - **Consulting Doctor:** Dr. Ananya Rao (MD – General Medicine)
        
- Visit type: **New Consultation**
    
- Token number auto-generated: **GM-023**
    

**System Actions:**

- `OPDVisit` record created
    
- Status: **Registered**
    
- Queue position updated
    

---

### **09:25 AM – Billing: OPD Consultation Fee**

- Consultation fee auto-applied: ₹500
    
- Bill generated before consultation (hospital policy)
    

**System Actions:**

- `BillingInvoice` created
    
- Line Item:
    
    - OPD Consultation – ₹500
        
- Payment Mode: UPI
    
- Payment status: **Paid**
    

---

### **09:34 AM – Patient Called for Consultation**

- Nurse marks patient as **Arrived**
    
- Vital signs recorded:
    
    - Temperature: 99.8°F
        
    - BP: 124/80 mmHg
        
    - Pulse: 82 bpm
        
    - SpO₂: 98%
        

**System Actions:**

- `Vitals` record created
    
- OPD Visit status updated to **In Consultation**
    

---

### **09:40 AM – Doctor Consultation**

- Doctor reviews vitals and patient complaints.
    
- Clinical notes recorded:
    
    - Mild pharyngeal congestion
        
    - No respiratory distress
        
- Provisional diagnosis:
    
    - **Acute Viral Pharyngitis**
        

**Clinical Decisions:**

- No lab investigations required
    
- No imaging required
    
- Symptomatic treatment advised
    

**Prescription:**

- Paracetamol 650 mg – SOS
    
- Warm saline gargles
    
- Hydration advice
    

**System Actions:**

- `ClinicalEncounter` created
    
- `Diagnosis` saved
    
- `Prescription` generated
    

---

### **09:52 AM – Doctor Completes Consultation**

- Doctor marks consultation as complete.
    
- Follow-up advice:
    
    - Review after 3 days if symptoms persist
        

**System Actions:**

- OPD Visit status updated to **Completed**
    

---

### **09:55 AM – Patient Exit**

- No additional services required.
    
- Discharge summary auto-generated for OPD.
    
- Patient exits hospital.
    

---

## **4. Modules Touched**

- Patient Master
    
- Registration
    
- OPD
    
- Doctor EMR
    
- Billing
    
- Payments
    
- Pharmacy (Prescription only, no dispensing)
    
- Reports / Documents
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientAddress`
    
- `PatientIdentification`
    
- `OPDVisit`
    
- `Doctor`
    
- `Department`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `Diagnosis`
    
- `Prescription`
    
- `BillingInvoice`
    
- `BillingLineItem`
    
- `PaymentTransaction`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|OPD Visit|Created|Registered|Visit initiated|
|OPD Visit|Registered|In Consultation|Patient entered doctor room|
|OPD Visit|In Consultation|Completed|Doctor finalized consultation|
|Billing Invoice|Draft|Paid|Payment received|

---

## **7. Exit Summary**

- **Exit Type:** OPD Completed – Walkout
    
- **Condition at Exit:** Stable
    
- **Admission Required:** No
    
- **Referral Required:** No
    
- **Follow-up:** Optional (3 days if symptoms persist)
    

---

## **8. Documents Generated**

- OPD Registration Slip
    
- OPD Consultation Bill (Paid)
    
- OPD Prescription
    
- OPD Visit Summary
    

(All documents stored in `Document` module and downloadable as PDF)

---

## **9. Final Billing Summary**

|Item|Amount (₹)|
|---|---|
|OPD Consultation|500|
|Diagnostics|0|
|Pharmacy|0|
|**Total**|**₹500**|
|Payment Mode|UPI|
|Payment Status|Paid|

---
