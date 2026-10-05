
# 1 — Requirements Engineering

Requirements elicitation and analysis for **Problem Statement #11 — Telemedicine Slot Booking & Prescription Portal**.

## Contents

| File | Contents |
|---|---|
| `Requirements_FR_NFR.md` | 5 functional and 2 non-functional requirements for the Telemedicine Portal, with priority, acceptance criteria and rationale. |
| `RTM.md` | Requirements Traceability Matrix for the Telemedicine Portal. |
| `UseCase_Diagram.png` | UML use-case diagram for the Telemedicine Slot Booking & Prescription Portal. |
| `UseCase_Diagram.drawio` | Editable source of the Telemedicine UML use-case diagram. |
| `UseCase_Flow_BookConsultation.md` | Detailed flow for booking a video consultation. |
| `Alternate_and_Exception_Flows.md` | Alternative and exception flows for consultation booking and prescription access. |

## Summary

| Item | Details |
|---|---|
| Functional Requirements | 5 (FR-001 to FR-005) |
| Non-Functional Requirements | 2 (NFR-001 to NFR-002) |
| Main Actor | Patient |
| Core Use Case | Book Video Consultation |
| Security Requirement | TLS 1.3 and AES-256 |
| Performance Requirement | Available consultation slots load within 3 seconds |

# Alternate Flows and Exception Flows

**Problem Statement #11 — Telemedicine Slot Booking & Prescription Portal**

Extension of the main use case: Book Video Consultation

---

## 1. Alternate flow vs exception flow

| | Alternate Flow | Exception Flow |
|---|---|---|
| **What causes it** | A valid situation that can occur during normal system operation but follows a different path from the main flow. | A failure in the system, network, database, or an external service. |
| **Whose fault** | Nobody's. The system is working correctly. | The system or an external dependency has failed. |
| **Outcome** | The use case continues through another valid path or ends without completing the booking. | The system fails safely and informs the patient without creating incomplete or invalid booking data. |
| **Example here** | The patient selects a slot that becomes unavailable and chooses another slot. | The booking service fails while saving the appointment. |

**The practical test:** if the situation can occur even when all system components are working correctly, it is an alternate flow. If something has failed, it is an exception flow.

---

## 2. Reference — main success scenario

The main success scenario for the **Book Video Consultation** use case is:

1. Patient logs into the telemedicine portal.
2. Patient views available doctors and their specializations.
3. Patient selects a doctor or specialty.
4. System displays available video consultation slots.
5. Patient selects a suitable consultation slot.
6. Patient confirms the booking.
7. System verifies that the selected slot is still available.
8. System creates the consultation booking.
9. System provides a secure consultation room link.
10. Patient attends the online consultation.
11. Doctor provides a digital prescription.
12. Patient downloads the digitally signed prescription.

The following alternate and exception flows refer to these steps.

---

# 3. Alternate Flows

## AF-1 — No doctor available for the selected specialty [FR-002]

- **2a.** The patient selects a medical specialty for which no doctor is currently available.
- **2a1.** The system displays a "No doctors available" message.
- **2a2.** The system allows the patient to view other available specialties.
- **2a3.** The patient selects another specialty or exits the process.
- The use case ends without a consultation booking.

---

## AF-2 — Doctor available but no consultation slots are available [FR-003]

- **4a.** The selected doctor has no available video consultation slots.
- **4a1.** The system informs the patient that no slots are currently available.
- **4a2.** The system displays other available doctors or future available slots.
- **4a3.** The patient selects another doctor or another available slot.
- **4a4.** The booking process resumes from slot selection.

---

## AF-3 — Selected slot becomes unavailable during booking [FR-003]

- **5a.** The patient selects an available consultation slot.
- **5a1.** Another patient books the same slot before the current patient confirms the booking.
- **5a2.** The system detects that the selected slot is no longer available.
- **5a3.** The system informs the patient that the selected slot is no longer available.
- **5a4.** The system refreshes the doctor's available slots.
- **5a5.** The patient selects another available slot.
- The flow resumes from slot selection.

---

## AF-4 — Patient selects a different available slot [FR-003]

- **5b.** The patient decides not to continue with the initially selected slot.
- **5b1.** The patient returns to the available slot list.
- **5b2.** The system displays the currently available slots.
- **5b3.** The patient selects another slot.
- **5b4.** The booking continues with the newly selected slot.

---

## AF-5 — Patient cancels the booking before confirmation [FR-003]

- **6a.** The patient decides not to book the selected consultation.
- **6a1.** The patient cancels the booking process.
- **6a2.** The system does not create a consultation booking.
- **6a3.** The selected slot remains available.
- The use case ends without a booking.

---

## AF-6 — Patient changes the selected doctor [FR-002, FR-003]

- **3a.** The patient decides to consult a different doctor.
- **3a1.** The patient returns to the doctor list.
- **3a2.** The system displays available doctors and their specialties.
- **3a3.** The patient selects another doctor.
- **3a4.** The system displays the selected doctor's available consultation slots.
- The flow resumes at slot selection.

---

## AF-7 — Patient cannot attend the selected consultation [FR-003]

The patient decides that the selected consultation time is not suitable.

1. The patient cancels or changes the scheduled consultation according to the available booking options.
2. The system releases the selected slot if the booking is cancelled.
3. The system displays available alternative slots.
4. The patient may select another consultation slot.
5. The booking is updated or cancelled accordingly.

---

## AF-8 — Prescription is not immediately available after consultation [FR-001]

- **11a.** The doctor completes the consultation but the digital prescription is not yet available.
- **11a1.** The system informs the patient that the prescription is being prepared.
- **11a2.** The prescription is made available after it is generated and digitally signed.
- **11a3.** The patient can return later to access the prescription.
- The consultation itself remains completed.

---

# 4. Exception Flows

Each exception flow represents a system, database, network, security, or external-service failure.

The system must fail safely and must not create a partially completed consultation booking.

---

## EF-1 — Doctor/slot information service unavailable [FR-002, FR-003]

The system cannot retrieve doctors or available consultation slots.

1. The system detects that the required service is unavailable.
2. The system does not display incorrect or outdated availability as confirmed availability.
3. The patient receives a message that the information is temporarily unavailable.
4. The failure is logged for investigation.
5. The patient is asked to retry later.

---

## EF-2 — Database failure during booking [FR-003]

The booking information cannot be saved to the database.

1. The system detects the database failure.
2. The booking is not treated as successful.
3. The selected slot is not incorrectly marked as permanently booked.
4. The patient receives a booking failure message.
5. The error is logged for troubleshooting.
6. The patient can retry the booking after the service becomes available.

---

## EF-3 — Slot availability cannot be verified [FR-003]

The system cannot verify whether the selected slot is still available.

1. The system does not confirm the consultation.
2. The patient is informed that availability could not be verified.
3. The system requests the patient to refresh the available slots.
4. The patient can select another slot.
5. No incomplete booking is created.

---

## EF-4 — Secure consultation room link cannot be generated [FR-004]

The system successfully creates the booking but cannot generate the secure consultation room link.

1. The system records the link-generation failure.
2. The system does not provide an invalid or incomplete link.
3. The patient is informed that the consultation room link could not be generated.
4. The system attempts to generate the secure link again.
5. If the problem continues, the issue is logged for administrator/support action.
6. The patient is not given an unsecured consultation link.

---

## EF-5 — Video consultation service unavailable [FR-004]

The external video consultation service becomes unavailable.

1. The system detects that the consultation service cannot be accessed.
2. The patient is informed that the consultation room is temporarily unavailable.
3. The system keeps the consultation booking information safely stored.
4. The system provides the patient with appropriate retry information.
5. The failure is logged for troubleshooting.

---

## EF-6 — Digital prescription generation fails [FR-001]

The doctor completes the consultation but the digital prescription cannot be generated.

1. The system records the prescription-generation failure.
2. The patient is informed that the prescription is temporarily unavailable.
3. The system does not provide an incomplete prescription.
4. The system attempts to generate the prescription again.
5. If the failure continues, the issue is logged for administrator/support action.

---

## EF-7 — Prescription download fails [FR-005]

The patient attempts to download the digitally signed prescription but the download fails.

1. The system keeps the prescription safely stored.
2. The patient receives a download failure message.
3. The system allows the patient to retry the download.
4. The system does not delete or modify the prescription because of the failed download.
5. The failure is logged if repeated.

---

## EF-8 — Network connection lost during booking [FR-003]

The patient's internet connection is lost while booking a consultation.

1. The system cannot complete the current request.
2. The patient is informed that the connection was interrupted.
3. The system does not display a false booking confirmation.
4. The patient is asked to reconnect and check the booking status.
5. The patient can retry after the connection is restored.

---

## EF-9 — Security/TLS connection failure [NFR-001]

A secure TLS 1.3 connection cannot be established.

1. The system refuses to transmit sensitive medical information through an insecure connection.
2. The consultation or related transaction is not continued over an unsecured connection.
3. The patient receives a connection/security error.
4. The failure is logged for investigation.
5. The system allows the operation to be retried after secure communication is restored.

---

## EF-10 — Slot information takes longer than 3 seconds to load [NFR-002]

The available consultation slots do not load within the required 3-second performance target.

1. The system continues loading or reports that the request is taking longer than expected.
2. The patient is not shown incomplete availability as final availability.
3. The performance issue is recorded for monitoring.
4. The patient can retry or refresh the slot list.

---

# 5. What-if questions raised by these flows

Working through the alternate and exception flows raises several questions that may require additional decisions before complete system implementation:

- What happens if two patients attempt to book the same consultation slot at exactly the same time?
- What happens if a patient loses internet connectivity immediately after clicking the booking button?
- What happens if the booking is created but the secure consultation link cannot be generated?
- What happens if a doctor becomes unavailable after a patient has already booked a consultation?
- What happens if the video consultation service becomes unavailable shortly before the appointment?
- What happens if a doctor completes a consultation but does not generate the prescription?
- How long should a digitally signed prescription remain available for download?
- What happens if a patient repeatedly fails to download a prescription?
- What happens if the patient's device does not support the secure consultation room?
- What happens if available slot information is temporarily outdated?
- What happens if a patient's consultation slot is cancelled because of a doctor-side issue?
- What happens if the prescription-generation service is unavailable for an extended period?

---

## Effect on the Requirements

The alternate and exception flows identify situations that are not completely described by the basic functional requirements.

In particular:

- **Slot conflict handling** should define how simultaneous booking attempts are handled.
- **Consultation cancellation/rescheduling** should define what happens when an already booked appointment is changed.
- **Prescription availability** should define when a prescription becomes available after consultation.
- **Video service failure** should define how patients are handled when the consultation service is unavailable.
- **Prescription failure and retry** should define how prescription-generation failures are recovered.

These points can be considered for additional functional requirements in a future revision of the specification.
