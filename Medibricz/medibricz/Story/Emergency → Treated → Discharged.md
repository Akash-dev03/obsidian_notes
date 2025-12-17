## **1. Patient Profile**

- **Patient ID:** PAT-ER-000118
    
- **UHID:** UHID-2025-003104
    
- **Full Name:** Mr. Arun Prakash
    
- **Age / DOB:** 34 years / 1990-11-02
    
- **Gender:** Male
    
- **Contact Number:** +91-96XXXXXXXX
    
- **Address:** BTM Layout, Bengaluru, Karnataka
    
- **ID Proof:** Driving License (Last 4 digits: 7742)
    
- **Marital Status:** Married
    
- **Blood Group:** O−
    
- **Known Allergies:** None
    
- **Existing Conditions:** None
    
- **Insurance:** No (Emergency Self-Pay)
    

---

## **2. Entry Point**

- **Date:** 2025-01-27
    
- **Time:** 06:42 PM
    
- **Entry Mode:** Walk-in (assisted by bystander)
    
- **Department:** Emergency Room (ER)
    
- **Chief Complaint:** Acute chest pain and anxiety episode (30 minutes duration)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **06:42 PM – Emergency Arrival & Triage**

- Patient brought to ER reception.
    
- Immediate triage initiated before registration.
    

**Triage Assessment:**

- Chest pain present
    
- Conscious, oriented
    
- No trauma
    

**Triage Category:** **Priority II (Urgent)**

**System Actions:**

- `EmergencyVisit` created (temporary)
    
- Triage timestamp captured
    
- Status: **Under Triage**
    

---

### **06:45 PM – Emergency Registration**

- Minimal demographics captured.
    
- Temporary ER number generated and later mapped to UHID.
    

**System Actions:**

- `Patient` created
    
- `UHID` generated
    
- ER visit linked to UHID
    
- Status → **Registered**
    

---

### **06:48 PM – Initial Vitals & Monitoring**

- ER nurse records vitals:
    
    - BP: 138/88 mmHg
        
    - Pulse: 104 bpm
        
    - SpO₂: 97%
        
    - RR: 22/min
        

**System Actions:**

- `Vitals` created
    
- ER Visit status → **Under Treatment**
    

---

### **06:50 PM – Emergency Doctor Assessment**

- **Attending Doctor:** Dr. Meera Joshi (MD – Emergency Medicine)
    
- ECG performed immediately.
    

**ECG Findings:**

- Normal sinus rhythm
    
- No ischemic changes
    

**Provisional Diagnosis:**

- **Acute Anxiety / Panic Attack**
    
- Cardiac event ruled out clinically
    

**System Actions:**

- `ClinicalEncounter` created
    
- `Diagnosis` (provisional) recorded
    

---

### **06:56 PM – Emergency Treatment**

- Oxygen via nasal cannula (2 L/min)
    
- Inj. Diazepam (low dose) administered IV
    
- Patient reassured and monitored
    

**System Actions:**

- `MedicationAdministration` logged
    
- Treatment notes saved
    

---

### **07:15 PM – Observation Period**

- Patient observed in ER observation bay.
    
- Repeat vitals:
    
    - Pulse: 84 bpm
        
    - BP: 124/80 mmHg
        
- Chest pain resolved.
    

**System Actions:**

- Observation notes added
    
- Status remains **Under Treatment**
    

---

### **07:28 PM – Reassessment & Discharge Decision**

- Doctor reassesses patient.
    
- No ongoing symptoms.
    
- No admission required.
    

**Final Diagnosis:**

- **Acute Anxiety Episode (Non-Cardiac Chest Pain)**
    

**Discharge Decision:** ER Discharge (Stable)

---

### **07:32 PM – Billing Initiation**

- Emergency bill generated.
    

**Billing Items:**

- ER Consultation – ₹1,200
    
- ECG – ₹400
    
- Emergency Medications – ₹300
    

**System Actions:**

- `BillingInvoice` created
    
- Total: ₹1,900
    
- Payment Mode: Cash
    
- Status: **Paid**
    

---

### **07:40 PM – Emergency Discharge**

- Discharge instructions provided:
    
    - Stress management advice
        
    - Avoid caffeine
        
    - OPD psychiatry follow-up if recurrent
        
- Emergency discharge summary generated.
    

**System Actions:**

- ER Visit status → **Discharged**
    
- Visit closed
    

---

## **4. Modules Touched**

- Emergency / ER
    
- Triage
    
- Patient Registration
    
- Doctor EMR
    
- Vitals & Monitoring
    
- Billing
    
- Payments
    
- Documents
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `EmergencyVisit`
    
- `TriageAssessment`
    
- `Vitals`
    
- `ClinicalEncounter`
    
- `Diagnosis`
    
- `MedicationAdministration`
    
- `BillingInvoice`
    
- `BillingLineItem`
    
- `PaymentTransaction`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|ER Visit|Created|Under Triage|Immediate assessment|
|ER Visit|Under Triage|Registered|Demographics captured|
|ER Visit|Registered|Under Treatment|Doctor started care|
|ER Visit|Under Treatment|Discharged|Patient stabilized|
|Billing Invoice|Draft|Paid|Payment received|

---

## **7. Exit Summary**

- **Exit Type:** Emergency Discharge
    
- **Patient Condition:** Stable
    
- **Admission Required:** No
    
- **Referral:** Optional OPD Psychiatry
    
- **Risk at Exit:** Low
    

---

## **8. Documents Generated**

- Emergency Registration Slip
    
- ECG Report
    
- Emergency Treatment Sheet
    
- Emergency Discharge Summary
    
- Emergency Bill & Receipt
    

(All documents stored with ER timestamps for audit)

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|ER Consultation|1,200|
|ECG|400|
|Medications|300|
|**Total Paid**|**₹1,900**|
|Payment Mode|Cash|
|Outstanding|₹0|

---

## **10. Edge Cases / Validations Tested**

1. Triage before full registration
    
2. Temporary ER number mapping to UHID
    
3. Emergency diagnostics before billing
    
4. Observation without admission
    
5. ER discharge without IPD conversion
    
6. Emergency medication administration logging
    
7. Mandatory reassessment before discharge
    
8. Non-cardiac chest pain handling
    
9. Billing consolidation for ER services
    
10. Complete medico-legal audit trail