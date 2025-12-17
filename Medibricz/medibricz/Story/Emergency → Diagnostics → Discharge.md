## **1. Patient Profile**

- **Patient ID:** PAT-ER-000164
    
- **UHID:** UHID-2025-003487
    
- **Full Name:** Ms. Neha Kulkarni
    
- **Age / DOB:** 27 years / 1997-06-14
    
- **Gender:** Female
    
- **Contact Number:** +91-98XXXXXXXX
    
- **Address:** Banashankari, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 2056)
    
- **Marital Status:** Single
    
- **Blood Group:** B−
    
- **Known Allergies:** None
    
- **Existing Conditions:** None
    
- **Insurance:** No (Emergency Self-Pay)
    

---

## **2. Entry Point**

- **Date:** 2025-01-29
    
- **Time:** 09:18 PM
    
- **Entry Mode:** Walk-in
    
- **Department:** Emergency Room (ER)
    
- **Chief Complaint:** Sudden onset severe headache with nausea (2 hours)
    

---

## **3. Timeline of Events (Step-by-Step)**

### **09:18 PM – Emergency Arrival & Triage**

- Patient arrives at ER reception.
    
- Immediate triage performed prior to full registration.
    

**Triage Findings:**

- Severe headache (VAS 8/10)
    
- Nausea, no vomiting
    
- Conscious and oriented
    

**Triage Category:** **Priority II – Urgent**

**System Actions:**

- `EmergencyVisit` created (temporary)
    
- Triage timestamp recorded
    
- Status: **Under Triage**
    

---

### **09:21 PM – Emergency Registration**

- Minimal demographics captured.
    
- Temporary ER number generated.
    
- UHID created and mapped.
    

**System Actions:**

- `Patient` created
    
- `UHID` generated
    
- ER Visit linked to UHID
    
- Status → **Registered**
    

---

### **09:24 PM – Initial Vitals**

- ER nurse records vitals:
    
    - BP: 142/90 mmHg
        
    - Pulse: 98 bpm
        
    - SpO₂: 98%
        
    - Temperature: 98.6°F
        

**System Actions:**

- `Vitals` created
    
- ER Visit status → **Under Treatment**
    

---

### **09:27 PM – Emergency Doctor Assessment**

- **Attending Doctor:** Dr. Rohit Malhotra (MD – Emergency Medicine)
    
- Neurological exam performed.
    

**Provisional Diagnosis:**

- **Rule out Acute Migraine vs Intracranial Pathology**
    

**Clinical Decision:**

- Emergency diagnostics required before discharge decision.
    

**Investigations Ordered:**

1. CT Brain (Non-contrast)
    
2. CBC
    
3. Random Blood Sugar (RBS)
    

**System Actions:**

- `ClinicalEncounter` created
    
- `InvestigationOrder` created
    
- ER Visit status → **Awaiting Diagnostics**
    

---

### **09:35 PM – Billing: Emergency Diagnostics**

- Emergency diagnostics bill generated.
    

**Billing Items:**

- CT Brain – ₹2,500
    
- CBC – ₹350
    
- RBS – ₹150
    

**System Actions:**

- `BillingInvoice` created
    
- Total: ₹3,000
    
- Payment Mode: Card
    
- Status: **Paid**
    

---

### **09:42 PM – Sample Collection & Imaging**

- Blood samples collected in ER.
    
- Patient escorted to CT scan room.
    

**System Actions:**

- `LabSample` created (CBC, RBS)
    
- Sample status: **Collected**
    
- `RadiologyOrder` marked **In Progress**
    

---

### **10:05 PM – Diagnostics Processing**

- CT scan completed.
    
- Lab samples processed and validated.
    

**Results:**

- CT Brain: Normal study
    
- CBC: Within normal limits
    
- RBS: 102 mg/dL
    

**System Actions:**

- `LabResult` created
    
- `RadiologyReport` created
    
- Status: **Completed**
    

---

### **10:18 PM – Doctor Review of Reports**

- Doctor reviews all reports.
    
- No red flags identified.
    

**Final Diagnosis:**

- **Acute Migraine Headache**
    

**Treatment Administered:**

- IV analgesic
    
- Antiemetic
    

**System Actions:**

- `MedicationAdministration` logged
    
- Diagnosis finalized
    

---

### **10:30 PM – Observation & Stabilization**

- Patient observed for 15 minutes.
    
- Headache severity reduced to 2/10.
    

**System Actions:**

- Observation notes recorded
    
- ER Visit status remains **Under Treatment**
    

---

### **10:45 PM – Discharge Decision**

- Patient stable and symptomatically improved.
    
- No admission required.
    

---

### **10:48 PM – Emergency Discharge**

- Discharge instructions provided:
    
    - Avoid trigger factors
        
    - Adequate hydration
        
    - Neurology OPD follow-up if recurrent
        
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
    
- Diagnostics (Lab & Radiology)
    
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
    
- `InvestigationOrder`
    
- `LabSample`
    
- `LabResult`
    
- `RadiologyOrder`
    
- `RadiologyReport`
    
- `MedicationAdministration`
    
- `Diagnosis`
    
- `BillingInvoice`
    
- `BillingLineItem`
    
- `PaymentTransaction`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

| Entity          | From Status          | To Status            | Reason                |
| --------------- | -------------------- | -------------------- | --------------------- |
| ER Visit        | Created              | Under Triage         | Immediate assessment  |
| ER Visit        | Under Triage         | Registered           | Demographics captured |
| ER Visit        | Registered           | Under Treatment      | Clinical care started |
| ER Visit        | Under Treatment      | Awaiting Diagnostics | Tests ordered         |
| Lab Sample      | Created              | Collected            | Sample drawn          |
| Diagnostics     | In Progress          | Completed            | Reports validated     |
| ER Visit        | Awaiting Diagnostics | Under Treatment      | Review and treatment  |
| ER Visit        | Under Treatment      | Discharged           | Patient stabilized    |
| Billing Invoice | Draft                | Paid                 | Payment received      |

---

## **7. Exit Summary**

- **Exit Type:** Emergency Discharge
    
- **Patient Condition:** Stable
    
- **Admission Required:** No
    
- **Referral:** Neurology OPD (if recurrence)
    
- **Risk at Exit:** Low
    

---

## **8. Documents Generated**

- Emergency Registration Slip
    
- CT Brain Report
    
- Lab Reports (CBC, RBS)
    
- Emergency Treatment Sheet
    
- Emergency Discharge Summary
    
- Emergency Bill & Payment Receipt
    

(All documents time-stamped and audit-ready)

---

## **9. Final Billing Summary**

| Category       | Amount (₹) |
| -------------- | ---------- |
| CT Brain       | 2,500      |
| Lab Tests      | 500        |
| ER Medications | Included   |
| **Total Paid** | **₹3,000** |
| Payment Mode   | Card       |
| Outstanding    | ₹0         |

---

## **10. Edge Cases / Validations Tested**

1. Emergency diagnostics before admission decision
    
2. Radiology + lab integration within ER
    
3. Diagnostics billing prior to discharge
    
4. Blocking discharge until report review
    
5. ER observation without IPD admission
    
6. Temporary ER number to UHID mapping
    
7. Diagnostic turnaround time tracking
    
8. Reassessment after report availability
    
9. Consolidated ER diagnostic billing
    
10. Complete medico-legal audit trail