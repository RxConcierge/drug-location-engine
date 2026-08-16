System Architecture Overview
The Prescription Drug Location Tool is built as a two‑part application:
Patient‑Facing Mobile App
Pharmacy‑Facing Mobile/Web App
Both apps communicate with a shared backend that manages:
request queue
AI drug identity refinement
clarification workflow
paywall
pharmacy acceptance
move‑list notifications
No inventory API is required.
1. Patient‑Facing Mobile App
The patient app handles:
medication entry
pill photo upload
AI drug identity refinement
request creation
paywall
post‑acceptance connection to pharmacy
Key Modules
Drug Input Module
AI Identity Refinement Module
Request Creation Module
Paywall Module
Pharmacy Connection Module
2. Pharmacy‑Facing Mobile/Web App
The pharmacy app handles:
queue filtering
clarification
rejection
acceptance
reimbursement tracking
optional move‑list management
Key Modules
Queue Viewer
Clarification Engine
Acceptance Workflow
Reimbursement Tracker
Move‑List Manager (internal only)
3. Backend Services
The backend is composed of several independent services:
Queue Service
Manages all incoming patient requests.
Pharmacies filter by drug identity — no inventory API required.
AI Refinement Service
Refines drug identity only:
name
strength
dosage form
manufacturer
Never refines SIG or prescriber intent.
Clarification Engine
Handles structured prompts from pharmacies.
No identity exchange allowed pre‑paywall.
Paywall Service
Locks identity until payment.
Unlocks pharmacy + patient identity after payment.
Move‑List Notification Service
Pharmacies list drugs they want to move.
This list is not visible to consumers.
It only triggers internal priority notifications.
Notification Service
Sends:
acceptance alerts
clarification alerts
move‑list triggers
paywall unlock notifications
4. Data Models
Core models include:
DrugProduct
PatientRequest
PharmacyClarification
PharmacyAcceptance
MoveListItem
PaywallTransaction
See: Data Models
5. Workflow Summary
Patient enters medication
AI refines drug identity
Request enters queue
Pharmacy filters
Pharmacy clarifies or rejects
Accepted clarifications earn reimbursement
Patient pays
Identity unlocks
Patient connects to pharmacy
See: Workflow
6. Security & Privacy
No identity exchange pre‑paywall
No inventory API
No SIG interpretation
No clinical decision-making
Structured prompts only
7. Roadmap
routing optimization
pharmacy dashboards
patient notifications
move‑list analytics
optional inventory upload (internal only)
