## **1. Patient Profile**

- **Patient ID:** PAT-FIN-000091
    
- **UHID:** UHID-2025-007889
    
- **Full Name:** Mr. Vinod Sharma
    
- **Age / DOB:** 41 years / 1983-06-22
    
- **Gender:** Male
    
- **Contact Number:** +91-98XXXXXXXX
    
- **Address:** Electronic City, Bengaluru, Karnataka
    
- **ID Proof:** Aadhaar (Last 4 digits: 5561)
    
- **Marital Status:** Married
    
- **Blood Group:** B+
    
- **Insurance:** No (Self-Pay)
    

---

## **2. Entry Point**

- **Date:** 2025-03-15
    
- **Care Context:** OPD → Diagnostics
    
- **Department:** Orthopedics OPD
    
- **Reason for Visit:** Acute knee pain after fall
    

---

## **3. Timeline of Events (Step-by-Step)**

### **09:20 AM – OPD Registration & Visit Creation**

- Patient registered at OPD counter.
    
- UHID verified (existing patient).
    
- OPD visit created.
    

**System Actions:**

- `OPDVisit` created
    
- Status: **Registered**
    

---

### **09:28 AM – OPD Consultation**

- **Consultant:** Dr. Harish Bhat (MS – Orthopedics)
    
- Clinical examination suggests ligament injury.
    
- MRI Knee advised.
    

**System Actions:**

- `ClinicalEncounter` created
    
- Investigation recommendation recorded
    

---

### **09:40 AM – Billing: Diagnostic Invoice Generated**

- MRI Knee billed.
    

**Invoice Details:**

- MRI Knee – ₹6,000
    

**System Actions:**

- `BillingInvoice` created
    
- Invoice status: **Unpaid**
    

---

### **09:42 AM – Partial Payment Collected**

- Patient expresses inability to pay full amount.
    
- Pays ₹3,500 upfront.
    

**Payment Details:**

- Payment Mode: Cash
    
- Amount Paid: ₹3,500
    

**System Actions:**

- `PaymentTransaction` created
    
- Invoice status → **Partially Paid**
    
- Outstanding balance auto-calculated
    

---

### **09:43 AM – Pending Balance Recorded**

- Pending amount: ₹2,500
    
- Due type: **Patient Pending**
    
- Payment due date: Same day (policy-configured)
    

**System Actions:**

- `OutstandingBalance` created
    
- Ledger updated
    

---

### **09:45 AM – Diagnostics Policy Enforcement**

- MRI marked as **On Hold** due to pending balance.
    
- Patient informed of balance requirement before imaging.
    

**System Actions:**

- `ServiceHoldFlag` applied to Investigation Order
    

---

### **11:30 AM – Patient Requests Deferment**

- Patient requests MRI to be done next day.
    
- Front desk reschedules MRI.
    

**System Actions:**

- Investigation order status → **Deferred**
    
- Pending balance retained
    

---

### **Next Day – 10:05 AM – Balance Payment**

- Patient returns and pays remaining ₹2,500 via UPI.
    

**System Actions:**

- Second `PaymentTransaction` created
    
- Invoice status → **Paid in Full**
    
- Outstanding cleared
    

---

### **10:07 AM – Diagnostics Released**

- MRI investigation released and performed.
    

**System Actions:**

- Service hold removed
    
- Investigation status → **Completed**
    

---

## **4. Modules Touched**

- Patient Master
    
- OPD
    
- Doctor EMR
    
- Diagnostics
    
- Billing
    
- Payments
    
- Accounts / Ledger
    
- Notifications
    

---

## **5. Data That Must Exist in System (Tables / Entities)**

- `Patient`
    
- `OPDVisit`
    
- `ClinicalEncounter`
    
- `BillingInvoice`
    
- `BillingLineItem`
    
- `PaymentTransaction`
    
- `OutstandingBalance`
    
- `LedgerEntry`
    
- `InvestigationOrder`
    
- `ServiceHoldFlag`
    
- `Document`
    

---

## **6. Status Changes (With Reason)**

|Entity|From Status|To Status|Reason|
|---|---|---|---|
|Billing Invoice|Draft|Partially Paid|Partial payment received|
|Billing Invoice|Partially Paid|Paid|Balance cleared|
|Investigation|Ordered|On Hold|Pending balance|
|Investigation|On Hold|Completed|Full payment received|

---

## **7. Exit Summary**

- **Exit Type:** Financial Closure After Partial Payment
    
- **Service Delay:** Yes (policy enforced)
    
- **Pending Duration:** 1 day
    
- **Final Outcome:** Services completed after full payment
    

---

## **8. Documents Generated**

- Diagnostic Invoice
    
- Partial Payment Receipt
    
- Outstanding Balance Statement
    
- Final Payment Receipt
    
- MRI Report
    

(All documents time-stamped and ledger-linked)

---

## **9. Final Billing Summary**

|Description|Amount (₹)|
|---|---|
|MRI Knee|6,000|
|Amount Paid (Day 1)|3,500|
|Amount Paid (Day 2)|2,500|
|**Total Paid**|**6,000**|
|Pending Balance|₹0|

---

## **10. Edge Cases / Validations Tested**

1. Partial payment allowed on diagnostic invoice
    
2. Accurate outstanding balance calculation
    
3. Invoice status transition (Draft → Partial → Paid)
    
4. Service hold enforcement on unpaid balance
    
5. Multiple payments against single invoice
    
6. Ledger reconciliation across payment dates
    
7. Deferred service handling
    
8. Audit trail for financial overrides
    
9. Prevention of duplicate invoices
    
10. Receipt generation per payment transaction