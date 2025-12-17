## **1. Patient Profile**

- **Patient ID:** PAT-FIN-000127
    
- **UHID:** UHID-2025-008245
    
- **Full Name:** Mrs. Pooja Malhotra
    
- **Age / DOB:** 36 years / 1988-02-14
    
- **Gender:** Female
    
- **Contact Number:** +91-97XXXXXXXX
    
- **Address:** Indiranagar, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 3906)
    
- **Marital Status:** Married
    
- **Blood Group:** O+
    
- **Known Allergies:** None
    
- **Insurance:** Yes
    
    - **Payer:** ICICI Lombard Health Insurance
        
    - **Policy Type:** Individual Mediclaim
        
    - **Policy Number:** ICICI-IND-554893
        
    - **Sum Insured Available:** ₹1,50,000
        
    - **Co-pay Clause:** 10% patient share
        

---

## **2. Entry Point**

- **Date:** 2025-03-18
    
- **Care Context:** Planned IPD Admission
    
- **Department:** General Surgery
    
- **Reason for Admission:** Elective Laparoscopic Cholecystectomy
    

---

## **3. Timeline of Events (Step-by-Step)**

### **Day −1 – Pre-Admission & Insurance Approval**

#### **04:00 PM – OPD Surgery Advice**

- Surgeon advises elective laparoscopic cholecystectomy.
    
- Planned IPD admission created for next day.
    

**System Actions:**

- `IPDAdmissionRequest` created
    
- Provisional estimate generated: ₹1,20,000
    

---

#### **04:30 PM – Insurance Pre-Authorization**

- Cashless pre-auth initiated.
    
- Documents uploaded:
    
    - OPD notes
        
    - Diagnosis
        
    - Estimated cost
        

**System Actions:**

- `InsurancePreAuth` created
    
- Status → **Approved**
    
- Approved amount: ₹1,00,000
    
- Co-pay: 10% applicable
    

---

## **Day 1 – Admission & Treatment**

### **09:10 AM – IPD Admission**

- Patient admitted as planned.
    
- Insurance approval verified at admission desk.
    

**System Actions:**

- `IPDAdmission` created
    
- Status: **Admitted**
    

---

### **09:18 AM – Bed Allocation**

- Ward: Private Room
    
- Bed No: PR-05
    

**System Actions:**

- `Bed` marked **Occupied**
    

---

### **09:40 AM – Financial Counseling**

- Billing desk explains:
    
    - Insurance approved: ₹1,00,000
        
    - Estimated patient share (co-pay + exclusions): ₹20,000
        

**System Actions:**

- `PatientLiabilityEstimate` generated
    

---

### **09:45 AM – Advance Cash Collection**

- Patient pays advance towards co-pay.
    

**Payment Details:**

- Amount: ₹15,000
    
- Mode: UPI
    

**System Actions:**

- `AdvancePayment` recorded
    
- Tagged as **Patient Share**
    

---

### **02:00 PM – Surgery Performed**

- Procedure: **Laparoscopic Cholecystectomy**
    
- No complications.
    

**System Actions:**

- `ProcedureRecord` created
    
- OT & anesthesia charges captured
    

---

## **Day 2 – Discharge & Mixed Billing**

### **10:30 AM – Discharge Order**

- Patient clinically stable.
    
- Fit for discharge.
    

**System Actions:**

- `DischargeOrder` created
    

---

### **11:15 AM – Final Billing Generation**

- Final bill prepared.
    

**Final Bill Breakdown:**

- Total Hospital Charges: ₹1,18,000
    

**Insurance Eligibility:**

- Approved by insurance: ₹1,00,000
    
- Non-payable (co-pay + uncovered items): ₹18,000
    

**System Actions:**

- `BillingInvoice` finalized
    
- Split tagged:
    
    - Insurance Payable
        
    - Patient Payable
        

---

### **11:25 AM – Insurance Claim Submission**

- Cashless claim submitted with final bill.
    

**System Actions:**

- `InsuranceClaim` created
    
- Status → **Submitted**
    

---

### **11:30 AM – Patient Final Settlement**

- Patient advance adjusted: ₹15,000
    
- Remaining balance: ₹3,000
    

**Payment Details:**

- Mode: Cash
    
- Amount: ₹3,000
    

**System Actions:**

- Second `PaymentTransaction` created
    
- Patient balance cleared
    

---

### **11:45 AM – Discharge**

- Discharge summary explained.
    
- Patient exits hospital.
    

**System Actions:**

- IPD status → **Discharged**
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD (Pre-admission advice)
    
- IPD Admission
    
- Bed Management
    
- OT / Surgery
    
- Billing
    
- Insurance
    
- Payments
    
- Discharge
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `PatientInsurance`
    
- `IPDAdmissionRequest`
    
- `InsurancePreAuth`
    
- `IPDAdmission`
    
- `Bed`
    
- `ProcedureRecord`
    
- `BillingInvoice`
    
- `BillingLineItem`
    
- `InsuranceClaim`
    
- `AdvancePayment`
    
- `PaymentTransaction`
    
- `LedgerEntry`
    
- `DischargeSummary`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|Insurance Pre-Auth|Created|Approved|Insurer approval|
|IPD Admission|Admitted|Discharged|Treatment completed|
|Insurance Claim|Created|Submitted|Final bill generated|
|Billing Invoice|Draft|Finalized|Discharge billing|
|Patient Balance|Pending|Cleared|Cash payment made|

---

## **7. Exit Summary**

- **Exit Type:** IPD Discharge (Mixed Payment)
    
- **Insurance Mode:** Cashless with co-pay
    
- **Patient Contribution:** Paid in full
    
- **Outstanding Balance:** ₹0
    

---

## **8. Documents Generated**

- Insurance Pre-Auth Approval
    
- Patient Liability Estimate
    
- Advance Payment Receipt
    
- Final IPD Bill
    
- Insurance Claim Submission
    
- Final Payment Receipt
    
- Discharge Summary
    

---

## **9. Final Billing Summary**

|Category|Amount (₹)|
|---|---|
|Total Hospital Charges|1,18,000|
|Insurance Payable|1,00,000|
|Patient Payable|18,000|
|Patient Paid (Advance + Final)|18,000|
|**Outstanding**|**₹0**|

---

## **10. Edge Cases / Validations Tested**

1. Insurance approval lower than estimate
    
2. Co-pay percentage enforcement
    
3. Advance payment tagged as patient share
    
4. Split billing (insurance vs patient)
    
5. Adjustment of advance at final bill
    
6. Multiple payment modes for patient share
    
7. Claim submission only after discharge
    
8. Blocking discharge if patient balance pending
    
9. Ledger reconciliation (insurance vs cash)
    
10. Complete financial audit trail