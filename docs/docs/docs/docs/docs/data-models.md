Data Models
1. Overview
The system uses a set of structured data models to support:
patient requests
drug identity refinement
pharmacy clarifications
acceptance workflow
paywall logic
move‑list notifications
reimbursement tracking
All models are designed to be simple, explicit, and compatible with a queue‑based architecture (no inventory API required).
2. DrugProduct Model
Represents the refined drug identity used across the entire system.
Fields
drugName
strength
dosageForm
manufacturer
ndc (optional)
quantityRequested
Purpose
Standardizes medication identity for:
queue filtering
clarification
acceptance
move‑list matching
3. PatientRequest Model
Represents a patient’s request for a medication.
Fields
requestId
patientId
drugProduct (DrugProduct model)
createdAt
status
pending
clarifying
accepted
rejected
awaitingPayment
completed
clarificationHistory (array of PharmacyClarification)
acceptedByPharmacyId (nullable)
Purpose
Tracks the full lifecycle of a request from creation → clarification → acceptance → paywall → completion.
4. PharmacyClarification Model
Represents a structured clarification sent by a pharmacy.
Fields
clarificationId
pharmacyId
requestId
timestamp
fieldsClarified
manufacturer
strength
dosageForm
quantity
isAcceptedByPatient (boolean)
Purpose
Captures the refinement work pharmacies perform before acceptance and reimbursement.
5. PharmacyAcceptance Model
Represents a pharmacy’s acceptance of a request.
Fields
acceptanceId
pharmacyId
requestId
timestamp
drugProductConfirmed (DrugProduct model)
requiresPayment (boolean)
isIdentityUnlocked (boolean)
Purpose
Triggers the paywall and signals that inventory is available.
6. PaywallTransaction Model
Represents the patient’s payment to unlock pharmacy identity.
Fields
transactionId
requestId
patientId
pharmacyId
amount
timestamp
status
initiated
successful
failed
Purpose
Controls identity unlock and reimbursement eligibility.
7. MoveListItem Model
Represents a drug product a pharmacy wants to move.
Fields
moveListItemId
pharmacyId
drugProduct (DrugProduct model)
createdAt
Purpose
Triggers priority notifications when patient requests match internal move‑list items.
8. ReimbursementEvent Model
Represents a completed clarification‑led acceptance eligible for reimbursement.
Fields
eventId
pharmacyId
requestId
clarificationId (nullable if acceptance occurred without clarification)
acceptanceId
paywallTransactionId
timestamp
status
pending
paid
Purpose
Provides a transparent ledger for pharmacy payouts.
9. Pharmacy Model
Represents a pharmacy in the network.
Fields
pharmacyId
name
address
phone
licenseNumber
moveList (array of MoveListItem)
routingPriorityScore
Purpose
Supports queue filtering, move‑list logic, and routing optimization.
10. Patient Model
Represents a patient using the app.
Fields
patientId
name
contactInfo
createdAt
Purpose
Supports request creation and post‑paywall identity unlock.
11. Summary
These models form the backbone of the system:
DrugProduct standardizes identity
PatientRequest drives the workflow
PharmacyClarification captures refinement
PharmacyAcceptance triggers paywall
PaywallTransaction unlocks identity
MoveListItem powers internal prioritization
ReimbursementEvent ensures fair compensation
Together, they support a compliant, queue‑based, no‑inventory‑API architecture.
