Below is a **complete, end-to-end HMS patient journey story** authored from a **hospital domain expert and HMS QA architect perspective**, structured for **inpatient (IPD) medical admission with diagnostics and discharge**, covering **clinical workflow, diagnostics turnaround, billing, and discharge governance**.

> **Interpretation note (domain-standard):**
> “PD” is interpreted as **IPD (In-Patient Department)**, as PD is not a standard care context in HMS workflows.

---

## **Scenario Code:** TC-IPD-02

## **Scenario Name:** IPD → Diagnostics → Discharge

---

## **1. Patient Profile**

* **Patient ID:** PAT-IPD-000366
* **UHID:** UHID-2025-004951
* **Full Name:** Mr. Rajesh Iyer
* **Age / DOB:** 52 years / 1972-01-11
* **Gender:** Male
* **Contact Number:** +91-97XXXXXXXX
* **Address:** Basavanagudi, Bengaluru, Karnataka
* **ID Proof:** Aadhaar (Last 4 digits: 4419)
* **Marital Status:** Married
* **Blood Group:** O+
* **Known Allergies:** None
* **Existing Conditions:**

  * Hypertension (controlled)
* **Insurance:** Yes

  * **Payer:** Star Health Insurance
  * **Policy Type:** Individual Mediclaim
  * **Policy Number:** STAR-IND-992184

---

## **2. Entry Point**

* **Admission Type:** Planned / Medical IPD
* **Source:** OPD referral (General Medicine)
* **Admission Date & Time:** 2025-02-11, 02:40 PM
* **Department:** General Medicine
* **Reason for Admission:** Evaluation of persistent fever of unknown origin (5 days)

---

## **3. Timeline of Events (Step-by-Step)**

### **02:40 PM – IPD Admission**

* Patient reports to IPD admission desk with OPD referral.
* UHID verified.
* Insurance pre-auth initiated for medical admission.

**System Actions:**

* `IPDAdmission` created
* Admission type: **Planned – Medical**
* Status: **Admitted**

---

### **02:48 PM – Bed Allocation**

* Ward: Semi-Private Ward
* Bed No: SPW-07

**System Actions:**

* `Bed` marked **Occupied**

---

### **03:00 PM – Admission Nursing Assessment**

* Baseline vitals recorded:

  * BP: 126/82 mmHg
  * Pulse: 88 bpm
  * Temperature: 100.6°F
  * SpO₂: 98%

**System Actions:**

* `Vitals` created
* `NursingAssessment` completed

---

### **03:20 PM – Consultant Evaluation**

* **Consultant:** Dr. Raghavendra Rao (MD – General Medicine)
* Detailed history and physical examination performed.

**Provisional Diagnosis:**

* **Fever – Under Evaluation (PUO)**

**Clinical Decision:**

* Inpatient diagnostic workup required.

---

### **03:30 PM – Diagnostics Ordered**

**Laboratory Investigations:**

* CBC
* ESR
* CRP
* Blood Culture
* LFT
* RFT

**Imaging:**

* Chest X-Ray

**System Actions:**

* `InvestigationOrder` created
* IPD status → **Under Investigation**

---

### **04:00 PM – Sample Collection**

* Blood samples collected at bedside.
* Patient escorted for X-Ray.

**System Actions:**

* `LabSample` created
* `RadiologyOrder` initiated

---

### **Day 1 Evening – Initial Results**

**Results:**

* CBC: Mild leukocytosis
* CRP: Elevated
* Chest X-Ray: Normal

**System Actions:**

* Partial `LabResult` entries created
* Status: **Partially Reported**

---

### **Day 2 – Continued Observation & Final Reports**

#### **09:30 AM – Final Diagnostics**

* Blood culture: No growth
* LFT/RFT: Normal

**Final Diagnosis:**

* **Acute Viral Febrile Illness**

**System Actions:**

* `Diagnosis` finalized
* Investigation status → **Completed**

---

### **10:00 AM – Treatment & Monitoring**

* Supportive treatment continued:

  * Antipyretics
  * IV fluids (stopped once afebrile)
* Patient afebrile for 24 hours.

**System Actions:**

* `MedicationAdministration`
* `DailyProgressNote`

---

### **Day 2 – Discharge Day**

#### **11:30 AM – Discharge Order**

* Patient clinically stable.
* No further inpatient care required.

**System Actions:**

* `DischargeOrder` created

---

#### **12:15 PM – Final Billing**

* Final IPD bill generated.
* Insurance claim initiated.

**System Actions:**

* `BillingInvoice` finalized
* `InsuranceClaim` created

---

#### **01:00 PM – Discharge**

* Discharge summary explained.
* Follow-up advised after 5 days (OPD).

**System Actions:**

* `DischargeSummary` generated
* IPD status → **Discharged**

---

## **4. Modules Touched**

* Patient Master
* OPD (Referral)
* IPD Admission
* Bed Management
* Nursing
* Doctor EMR
* Diagnostics (Lab & Radiology)
* Pharmacy
* Billing
* Insurance
* Discharge

---

## **5. Data That Must Exist in System (Tables / Entities)**

* `Patient`
* `PatientInsurance`
* `IPDAdmission`
* `Bed`
* `Vitals`
* `NursingAssessment`
* `ClinicalEncounter`
* `InvestigationOrder`
* `LabSample`
* `LabResult`
* `RadiologyReport`
* `Diagnosis`
* `MedicationAdministration`
* `DailyProgressNote`
* `BillingInvoice`
* `InsuranceClaim`
* `DischargeOrder`
* `DischargeSummary`
* `Document`

---

## **6. Status Changes (With Reason)**

| Entity        | From Status         | To Status           | Reason                |
| ------------- | ------------------- | ------------------- | --------------------- |
| IPD Admission | Admitted            | Under Investigation | Diagnostics initiated |
| Investigation | Ordered             | Completed           | All reports available |
| IPD Admission | Under Investigation | Discharge Planned   | Diagnosis finalized   |
| IPD Admission | Discharge Planned   | Discharged          | Patient stable        |
| Bed           | Occupied            | Available           | Patient discharged    |

---

## **7. Exit Summary**

* **Exit Type:** IPD Medical Discharge
* **Patient Condition:** Stable, afebrile
* **Length of Stay:** 2 days
* **Follow-up:** General Medicine OPD – 5 days
* **Discharge Mode:** With advice

---

## **8. Documents Generated**

* IPD Admission Slip
* Diagnostic Reports (Lab + X-Ray)
* Daily Progress Notes
* Final Discharge Summary
* Final Bill
* Insurance Claim Intimation

---

## **9. Final Billing Summary**

| Category           | Amount (₹)  |
| ------------------ | ----------- |
| Room Charges       | 12,000      |
| Diagnostics        | 9,500       |
| Pharmacy           | 3,200       |
| Nursing & Misc     | 2,300       |
| **Total Bill**     | **₹27,000** |
| Insurance Approved | ₹25,000     |
| Patient Payable    | ₹2,000      |
