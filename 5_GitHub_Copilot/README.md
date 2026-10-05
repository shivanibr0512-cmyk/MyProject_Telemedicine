
# 5 — GitHub Copilot Generated Code

Evidence of using **GitHub Copilot** to generate code for the **Telemedicine Slot Booking & Prescription Portal**.

## What this folder needs

| Item | Status |
|---|---|
| Screenshot of Copilot generating code in the editor | Added |
| Link to the repository containing the generated code | To be added below |
| Short note on what was generated and what was changed by hand | Added |

## Suggested screenshots

Name them in order so they read as a sequence:

| # | Filename | What it should show |
|---|---|---|
| 1 | `01-copilot-prompt.png` | The prompt given to GitHub Copilot |
| 2 | `02-copilot-suggestion.png` | Copilot generating the requested function |
| 3 | `03-generated-code.png` | The generated code in the editor |
| 4 | `04-code-running.png` | The code executing or showing the booking result |

## Generated code repository

The generated code is included as part of this project repository.

**Repository:** `MyProject_Telemedicine`

## What was generated

GitHub Copilot was used to generate a simple Python function for booking a telemedicine consultation.

The function accepts:

- Patient name
- Doctor name
- Consultation slot

It returns a booking confirmation message.

### Generated functionality

The generated function follows this logic:

1. Accept the patient name.
2. Accept the doctor name.
3. Accept the consultation slot.
4. Generate a booking confirmation message.
5. Return the confirmation to the user.

## Copilot task

The prompt given to GitHub Copilot was:

> Create a simple Python function for a Telemedicine Slot Booking & Prescription Portal. The function should take patient name, doctor name and consultation slot as inputs and return a booking confirmation message.

## Generated Code
def book_consultation(patient_name, doctor_name, consultation_slot):
    return (
        f"Booking confirmed for {patient_name} with Dr. {doctor_name} "
        f"at {consultation_slot}."
    )
| Requirement | Copilot Demonstration |
|---|---|
| FR-001 | Digital prescription functionality can be developed as a future extension of the portal. |
| FR-002 | Doctor and specialty information can be integrated into the booking workflow. |
| FR-003 | The demonstrated `book_consultation()` function represents the basic consultation booking operation. |
| FR-004 | A secure consultation-room link can be integrated into the booking workflow. |
| FR-005 | Prescription download functionality can be integrated after consultation. |
| NFR-001 | Security requirements such as TLS 1.3 and AES-256 would be handled during system implementation. |
| NFR-002 | Slot-loading performance would be evaluated during implementation and testing. |
