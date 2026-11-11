# Blue Health Mock Risk Assessment Workbook

> **Training exercise only.** Blue Health, its people, vendors, systems, and events are fictional. This workbook is for practice; it is not legal advice or a substitute for a real HIPAA Security Rule risk analysis.

## Workbook cover sheet

**Analyst:** ____________________________________  
**Assessment sponsor:** Chief Operating Officer  
**System:** BluePortal patient portal and supporting services  
**Assessment date / period:** ____________________  
**Workbook status:** ☐ In progress  ☐ Preliminary  ☐ Complete with limitations  
**Version:** __________

### Your assignment

You are the GRC Analyst supporting Blue Health, a fictional regional outpatient care provider with four clinics, approximately 28,000 patients, and 145 employees. Leadership has asked you to assess security risks to ePHI handled by BluePortal, a vendor-hosted patient portal.

Complete the worksheets in order. Separate confirmed facts from assumptions and vendor claims. Do not treat a written policy or an unverified statement as proof that a control operates effectively. Your goal is a defensible preliminary risk analysis and a clear set of decisions and evidence requests—not a legal-compliance determination.

**Suggested time:** 60–90 minutes.

---

# Worksheet 1 — Scenario and evidence packet

Read the following case materials before filling in the worksheets.

## 1.1 System description

BluePortal allows patients to view visit summaries and lab results, send non-urgent messages, and request appointments. Patients authenticate with an email address and password. Staff access portal messages through the cloud-hosted EHR. The portal and EHR exchange patient and appointment data through a vendor-managed integration.

Blue Health also uses email and a small on-premises office network. The EHR as a whole, medical devices, and unrelated corporate systems are not part of the proposed technical assessment, but dependencies that could affect BluePortal ePHI should be considered.

## 1.2 Interview notes

### IT Manager
- Staff use individual EHR accounts. The portal administration console has two named administrator accounts and a shared `portal-support` account used by three IT staff.
- The vendor says administrator MFA is supported. IT believes it was enabled last year, but configuration evidence has not been supplied.
- EHR offboarding disables staff accounts. It is not known whether this removes portal-console access automatically.
- The vendor applies application updates; Blue Health does not receive regular change reports.
- A monthly access review is planned, but the last completed review cannot be located.
- IT receives some portal alerts by email. The logged event types and retention period are unknown.

### Privacy Officer
- About six weeks ago, a patient reported receiving a portal notification that appeared to show another patient's first name. Staff believe it was a display error, but no documented investigation or breach assessment has been provided for this exercise.
- The general incident log does not consistently name the affected system or include technical findings.
- Portal messages may contain symptoms, medication questions, and appointment details. Patients are told not to use the portal for emergencies.

### Clinic operations lead
- Staff sometimes print portal messages to discuss during a visit. Printouts are supposed to be put in the patient's paper chart or securely destroyed, but there is no written portal-specific procedure.
- A prolonged portal outage would delay non-urgent communications. Urgent care has a phone-based fallback.

## 1.3 Inventory and data-flow notes

| Item | Current understanding | Evidence status |
|---|---|---|
| BluePortal | Vendor-hosted web service, accessible on mobile; supports registration, messages, appointment requests, visit summaries, and lab results | Vendor overview only |
| ePHI | Patient identifiers and contact details, appointment information, messages, visit summaries, and lab results | Product description; data-flow diagram not supplied |
| EHR integration | Vendor-managed interface exchanges patient and appointment data; exact fields, direction, and frequency unknown | Interview statement; technical specification requested |
| Staff access | Staff use managed clinic workstations to access the EHR; remote access arrangements undocumented | Partially confirmed |
| Portal administrators | Two named accounts and one shared support account | Interview statement; account export not supplied |
| Backup and recovery | Vendor says backups are performed; frequency, restoration testing, recovery objectives, and Blue Health responsibilities unknown | Unverified vendor statement |
| Subprocessors | Vendor overview refers to hosting and messaging providers; names and data handling details not supplied | Evidence gap |
| Retention and deletion | Messages are visible in the portal; retention, archival, and deletion rules unknown | Evidence gap |

## 1.4 Policy, vendor, change, and incident notes

- Blue Health's general security policy requires unique user IDs, least privilege, workforce training, incident reporting, and periodic access review.
- A general contingency plan exists, but BluePortal is not named in the system recovery table.
- A vendor agreement is on file. The team has not reviewed whether it covers relevant business associate terms, security responsibilities, incident notification expectations, and subcontractor flow-downs.
- The vendor security overview claims encryption in transit and at rest, vulnerability scanning, and a security incident response process. Technical settings, test results, incident-notification timeline, and independent assurance evidence have not been supplied.
- There is no portal-specific risk register or documented risk acceptance for the shared administrator account.
- Lab-result viewing was added three months ago. The change ticket says “vendor configuration update” and has no attached privacy/security impact review.
- The reported notification issue occurred after the feature was introduced, but timing alone does not establish a cause. No confirmed unauthorized access or exfiltration is established from the information provided.
- The vendor has not yet answered Blue Health's request for details about the notification issue or relevant logs.

---

# Worksheet 2 — Assessment frame

## 2.1 Purpose and boundary

**Purpose of this assessment:**  
____________________________________________________________________________  
____________________________________________________________________________

**Proposed in-scope items** (confirm, revise, or add):
- [ ] Patient-facing portal and administrative console
- [ ] Vendor-hosted portal services and vendor-to-EHR integration
- [ ] Blue Health staff accounts and endpoints used to access portal messages
- [ ] Identity, authentication, logging, backup, incident response, and support processes relevant to the portal
- [ ] Relevant vendor services and subcontractors, subject to evidence availability
- [ ] Other: _________________________________________________________________

**Out of scope / dependencies to note:**  
____________________________________________________________________________  
____________________________________________________________________________

**Assessment period or point-in-time date:** __________________________________

## 2.2 Assumptions and limitations

| ID | Assumption or limitation | Why it matters | How to validate or reduce uncertainty |
|---|---|---|---|
| A1 | | | |
| A2 | | | |
| A3 | | | |

## 2.3 Stakeholder plan

| Stakeholder / role | What you need to understand | Interview or evidence requested | Status |
|---|---|---|---|
| IT Manager | | | ☐ To do ☐ Done |
| Privacy Officer | | | ☐ To do ☐ Done |
| Clinic operations lead | | | ☐ To do ☐ Done |
| Vendor security / account lead | | | ☐ To do ☐ Done |
| Other: | | | ☐ To do ☐ Done |

---

# Worksheet 3 — ePHI inventory and data-flow map

## 3.1 Data lifecycle

For each stage, identify the ePHI, system/person, transfer or storage location, safeguard, and evidence gap. Use “unknown” rather than guessing.

| Stage | Data / activity | System, person, or third party | Safeguard known today | Unknowns / evidence needed |
|---|---|---|---|---|
| Patient registration / entry | | | | |
| Portal storage and processing | | | | |
| Vendor-to-EHR exchange | | | | |
| Staff viewing and response | | | | |
| Patient notifications | | | | |
| Printing / paper handling | | | | |
| Backup / recovery | | | | |
| Retention / archival / deletion | | | | |
| Support / troubleshooting | | | | |

## 3.2 Draw the data flow

Sketch the main data flow and trust boundaries. Include patients, BluePortal, vendor hosting and subprocessors, the integration, EHR, staff, email/SMS notifications if applicable, and printed material. Mark uncertain flows with `?`.

```text
[Patient] ---> [                         ] ---> [                         ]
                   ?                         ?

[                         ] ---> [                         ] ---> [Staff]

Other flows / trust boundaries:
____________________________________________________________________________
____________________________________________________________________________
```

## 3.3 Asset and dependency list

| Asset / dependency | Owner | ePHI or security function | Criticality / rationale | Evidence status |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |
| | | | | |

---

# Worksheet 4 — Evidence request tracker

Prioritize evidence that could materially change the risk assessment. Request the least sensitive artifact that adequately answers the question, and use approved secure channels.

| Priority | Evidence / interview | Requested from | Why it matters | What finding could change the rating? | Status / date |
|---|---|---|---|---|---|
| 1 | Incident timeline, relevant notification details, logs, and documented investigation | Vendor + Privacy Officer | | | |
| 1 | Portal administrator and user access export, including shared-account use | IT + vendor | | | |
| 1 | MFA and authentication configuration evidence | Vendor + IT | | | |
| 1 | Integration data-flow / field specification | Vendor + EHR owner | | | |
| 2 | Vendor assurance report and scope/period, plus remediation summary | Vendor | | | |
| 2 | Subprocessor list and relevant contract / responsibility terms | Vendor + Privacy / Legal | | | |
| 2 | Logging coverage, retention, alerting, and investigation responsibilities | Vendor + IT | | | |
| 2 | Backup, restore-test evidence, recovery objectives, and responsibility matrix | Vendor + IT / continuity lead | | | |
| 2 | Change record and security/privacy review for lab-results launch | Vendor + Blue Health | | | |
| 3 | Portal data retention, archival, export, and deletion schedule | Vendor + Privacy / Records | | | |
| 3 | Staff procedures and training for portal messages and printouts | Operations + HR / Privacy | | | |
| Other | | | | | |

---

# Worksheet 5 — Risk scoring method

Use this exercise scale unless your instructor has provided another one. Explain your reasoning; scores support prioritization and do not replace judgment.

## Likelihood

| Score | Meaning |
|---|---|
| 1 — Rare | Conceivable, but little reason to expect it under current conditions. |
| 2 — Unlikely | Could occur, but evidence suggests it is not expected in normal conditions. |
| 3 — Possible | Plausible; relevant exposure, weakness, or uncertainty exists. |
| 4 — Likely | Expected to occur or recur absent corrective action. |

## Impact

| Score | Meaning |
|---|---|
| 1 — Limited | Limited disruption or low potential effect on ePHI confidentiality, integrity, or availability. |
| 2 — Moderate | Meaningful disruption or potential harm affecting a limited set of records or users. |
| 3 — Major | Significant ePHI exposure, patient impact, or interruption of an important care-supporting service. |
| 4 — Severe | Broad or highly sensitive ePHI exposure, substantial patient harm, or prolonged loss of a critical service. |

## Rating bands

**Risk score = Likelihood × Impact** (range 1–16).

| Score | Rating |
|---|---|
| 1–3 | Low |
| 4–7 | Moderate |
| 8–11 | High |
| 12–16 | Critical |

Rate inherent risk before safeguards. Rate residual risk after considering only safeguards evidenced as operating. If control operation is unverified, explain how you treat the uncertainty. Identify confidentiality (C), integrity (I), availability (A), or multiple dimensions.

**Calibration notes / local methodology differences:**  
____________________________________________________________________________

---

# Worksheet 6 — Risk register

Complete at least five distinct scenarios. Cover privileged/shared access, the notification issue, vendor/subprocessor assurance, logging and investigation, backup/recovery/retention, and workforce/offboarding or print handling. A risk scenario must state what could happen, why, which asset/ePHI is affected, and the consequence. “No MFA” by itself is a condition, not a complete risk scenario.

## Risk entry template — duplicate for each risk

### Risk ID / title: ______________________________  **Priority:** ☐ 1 ☐ 2 ☐ 3

**Asset, process, and ePHI affected:**  
____________________________________________________________________________

**Threat event and plausible cause (what could happen, and why?):**  
____________________________________________________________________________  
____________________________________________________________________________

**Potential consequence to patients, Blue Health, or ePHI:**  
____________________________________________________________________________

**Existing safeguards and evidence** (distinguish implemented/evidenced from policy or claim):  
____________________________________________________________________________  
____________________________________________________________________________

**Evidence gaps / assumptions:**  
____________________________________________________________________________

**Inherent likelihood:** ___ / 4  **Impact:** ___ / 4  **Score:** ___ / 16  **Rating:** __________

**Rationale for inherent likelihood and impact:**  
____________________________________________________________________________  
____________________________________________________________________________

**Risk dimension:** ☐ Confidentiality  ☐ Integrity  ☐ Availability  ☐ Multiple

**Residual likelihood:** ___ / 4  **Impact:** ___ / 4  **Score:** ___ / 16  **Rating:** __________

**Rationale for residual rating and treatment of unverified controls:**  
____________________________________________________________________________  
____________________________________________________________________________

**Recommended response:** ☐ Mitigate  ☐ Share/transfer  ☐ Avoid  ☐ Accept (with rationale)

**Treatment action(s), including interim safeguards:**  
____________________________________________________________________________  
____________________________________________________________________________

**Accountable owner:** ____________________  **Target milestone/date:** ____________________

**Validation evidence and closure criteria:**  
____________________________________________________________________________

**Risk acceptance decision-maker (if applicable):** ____________________

**Status:** ☐ Open  ☐ In progress  ☐ Pending evidence  ☐ Accepted  ☐ Closed

---

## Risk entry 1

Use the template above. Suggested theme: shared portal administrator/support account and uncertain MFA/access review.

## Risk entry 2

Use the template above. Suggested theme: patient notification or data-isolation error; investigate the reported event without assuming cause or outcome.

## Risk entry 3

Use the template above. Suggested theme: vendor assurance, subcontractors, contract responsibilities, or integration boundaries.

## Risk entry 4

Use the template above. Suggested theme: logging, detection, incident investigation, and vendor cooperation.

## Risk entry 5

Use the template above. Suggested theme: backup/recovery, downtime, data retention, staff offboarding, or printed messages.

## Additional risk entries

Add more entries if your data-flow analysis identifies additional material scenarios.

---

# Worksheet 7 — Treatment plan

Choose practical actions for the highest-priority risks. Owners should be accountable roles, not just “IT.” Include interim safeguards and objective proof of completion and ongoing effectiveness.

| Priority / risk ID | Treatment action | Response type | Accountable owner | Target milestone | Interim safeguard | Completion / effectiveness evidence | Status |
|---|---|---|---|---|---|---|---|
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |

### Treatment planning prompts

- Which actions can begin immediately while vendor evidence is pending?
- What is the plan for the shared administrator account? How will individual accountability be demonstrated?
- Who owns fact-finding and follow-up for the reported notification issue?
- What assurance, configuration, contract, and incident-cooperation evidence is appropriate to request from the vendor?
- How will Blue Health validate integration scope, logging, restore capability, and account termination?
- Which residual risks require explicit leadership acceptance, and at what point?

**Leadership decisions / resources needed:**  
____________________________________________________________________________  
____________________________________________________________________________

---

# Worksheet 8 — Executive readout

Write a short, decision-focused briefing for the COO. Clearly label preliminary judgments and distinguish confirmed facts from unverified claims.

## Executive summary

**Overall assessment status:** ☐ Preliminary  ☐ Complete with limitations

**Scope and key exclusions:**  
____________________________________________________________________________  
____________________________________________________________________________

**Top three risks and why they matter:**

1. _________________________________________________________________________
2. _________________________________________________________________________
3. _________________________________________________________________________

**Most important immediate actions:**  
____________________________________________________________________________  
____________________________________________________________________________

**Decisions or resources requested from leadership:**  
____________________________________________________________________________  
____________________________________________________________________________

**Material uncertainties that prevent a confident final rating:**  
____________________________________________________________________________  
____________________________________________________________________________

---

# Worksheet 9 — Analyst quality check and sign-off

Before submitting, confirm each item:

- [ ] Purpose, assessment boundary, period, assumptions, and limitations are explicit.
- [ ] ePHI creation, receipt, maintenance, transmission, printing, retention, and deletion have been considered.
- [ ] Relevant vendor, integration, and subprocessors are included as dependencies.
- [ ] Confirmed safeguards are separated from policy statements, vendor claims, and unverified assumptions.
- [ ] Risks are written as plausible events with causes and consequences—not merely missing controls.
- [ ] Inherent and residual ratings are reasoned consistently using the defined scale.
- [ ] Confidentiality, integrity, and availability are considered.
- [ ] Owners, milestones, interim safeguards, and evidence-based closure criteria are assigned.
- [ ] The reported notification issue is escalated for appropriate fact-finding; neither breach nor benign defect is presumed.
- [ ] Risk acceptance is explicit and assigned to an appropriate decision-maker.
- [ ] Leadership's decisions and unresolved evidence gaps are documented.

**Analyst conclusion:**  
____________________________________________________________________________  
____________________________________________________________________________

**Analyst name / date:** ____________________________________

**Reviewer / date:** ____________________________________

---

# Optional stretch challenge

The vendor responds with a SOC 2 report under NDA, a portal administrator export, and a technical description of the EHR integration.

1. What scope, period, system boundaries, exceptions, and complementary customer controls would you review in the assurance report?
2. What would you validate in the administrator export, including account ownership, privilege, MFA, and last use?
3. What fields, direction, frequency, authentication, error handling, and monitoring would you examine in the integration description?
4. What evidence could change your likelihood or residual-risk ratings? What uncertainty would remain?
5. Why does the existence of an assurance report not by itself prove that every Blue Health responsibility is satisfied?
