# drug-location-engine
The app helps patients find pharmacies that have their medication in stock. AI only refines the drug product. Pharmacies can clarify or reject; accepted clarifications earn reimbursement. Patients pay only when a pharmacy confirms inventory, then connect directly to that pharmacy
Prescription Drug Location Tool
A real‑time medication availability system consisting of a patient‑facing mobile app and a pharmacy‑facing mobile/web app. The platform helps patients locate pharmacies that have their medication in stock. AI is used only to refine the drug product identity — name, strength, dosage form, and manufacturer — based on patient input. It does not interpret SIG, directions, or prescriber intent.
Overview
Patients often struggle to find pharmacies that carry the medication they need. Pharmacies, meanwhile, receive unclear product descriptions, manufacturer mismatches, and unnecessary callbacks.
This tool solves both problems by sending standardized medication availability requests to pharmacies. Pharmacies can clarify or reject the request. If a clarification leads to a successful acceptance, the pharmacy receives reimbursement for that clarification. Patients pay only when a pharmacy confirms they have the medication.
After acceptance, the patient is connected directly to the pharmacy that confirmed inventory. The app does not guarantee readiness or pickup timing — it only confirms availability and provides a communication path.
No inventory API or integration is required. Pharmacies simply filter the request queue.
Two‑Part App Architecture
Patient Mobile App
Enter medication name, description, or pill photo
AI refines drug product identity only
View request status
Pay only after a pharmacy accepts
Connect to the pharmacy that confirmed inventory
Pharmacy Mobile/Web App
View incoming patient requests
Filter by drug name, strength, form, manufacturer
Clarify or reject requests
Accept when inventory is available
Receive reimbursement for accepted clarifications
Maintain an optional internal “move list” for priority notifications
Optional Pharmacy “Move List” (Internal Only)
Pharmacies may list drugs they want to move — such as slow‑moving inventory, high‑cost items, or short‑dated stock.
This list is not visible to consumers.
When a patient request matches an item on the move list, the pharmacy receives a priority notification. This helps pharmacies dispense inventory they prefer to move without exposing stock levels to patients and without requiring any inventory API.
Paywall & Communication Rules
The paywall ensures pharmacies and patients only connect after acceptance.
Before acceptance, communication is restricted to structured clarification prompts that refine the drug product only. No identifying information is shared. Pharmacies cannot send their name, phone number, address, or pickup instructions, and patients cannot contact them.
After the patient pays, the app unlocks the pharmacy’s identity and enables direct connection. This prevents bypassing the paywall and keeps pre‑acceptance communication compliant and standardized.
How It Works
Patient enters medication or uploads pill photo
AI refines drug product identity only
Request enters pharmacy queue
Pharmacies filter, clarify, or reject
Accepted clarifications are reimbursed
Patient pays only after acceptance
Patient connects to pharmacy confirming inventory
AI Clarification Rules
AI may refine:
drug name
strength
dosage form
manufacturer
AI may not refine:
SIG
directions
prescriber intent
clinical judgment
Limitations
App confirms inventory, not readiness
No SIG interpretation
No clinical decision-making
Roadmap
Automated routing
Pharmacy dashboards
Patient notification system
Internal move‑list optimization
Optional inventory listing tools
Pharmacy performance metrics
License
MIT License recommended.
