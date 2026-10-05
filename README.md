

**Project:** Telemedicine Slot Booking & Prescription Portal  
**Problem Statement:** #11 — Healthcare & Telemedicine
**SRN:PES1UG24CS439**

## 1. Project Overview

The **Telemedicine Slot Booking & Prescription Portal** is a software system designed to support online medical consultations.

The system allows patients to view doctors and their specializations, check available consultation slots, book video consultations, access a secure consultation room, and download digitally signed prescriptions.

The project focuses on making the telemedicine consultation process simple, secure, and efficient.

---

## 2. Problem Statement

Traditional medical consultations may require patients to physically visit hospitals or clinics, which can be inconvenient and time-consuming.

The Telemedicine Slot Booking & Prescription Portal provides a digital platform where patients can book available consultation slots and receive prescriptions electronically after consultation.

The system also focuses on security of medical information and efficient loading of available consultation slots.

---

## 3. Objectives

The main objectives of the project are:

- To allow patients to view doctors and their specializations.
- To allow patients to view available video consultation slots.
- To provide online consultation slot booking.
- To provide a secure consultation room link.
- To allow patients to download digitally signed prescriptions.
- To protect patient and prescription information.
- To provide fast access to available consultation slots.

---

## 4. Key Features

### Patient Features

- View available doctors.
- View doctor specializations.
- View available consultation slots.
- Book a video consultation.
- Access a secure consultation room.
- Download digitally signed prescriptions.

### Security Features

- TLS 1.3 for data transmission.
- AES-256 encryption for stored data.

### Performance

- Available consultation slots should load within 3 seconds.

---

## 5. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-001 | The system shall provide digital prescriptions. | High |
| FR-002 | The system shall allow users to view doctors and their specialties. | High |
| FR-003 | The system shall allow users to view and book available video consultation slots. | High |
| FR-004 | The system shall provide a secure consultation room link. | High |
| FR-005 | The system shall allow users to download digitally signed prescriptions. | High |

---

## 6. Non-Functional Requirements

| ID | Requirement |
|----|-------------|
| NFR-001 | Data in transit shall use TLS 1.3 and stored data shall use AES-256 encryption. |
| NFR-002 | Available consultation slots shall load within 3 seconds. |

---

## 7. System Workflow

The basic workflow of the system is:

1. Patient accesses the telemedicine portal.
2. Patient views available doctors and specialties.
3. Patient checks available consultation slots.
4. Patient selects a suitable slot.
5. Patient books the consultation.
6. The system provides a secure consultation room link.
7. Patient attends the online consultation.
8. Doctor provides a digital prescription.
9. Patient downloads the digitally signed prescription.

---

## 8. System Actors

The main actor involved in the system is:

### Patient

The patient can:

- View doctors.
- View specialties.
- View available slots.
- Book consultations.
- Access the consultation room.
- Download prescriptions.

The system also interacts with the doctor/medical consultation process for consultation and prescription generation.

---

## 9. Project Management

The project was planned and managed using Agile project management concepts.

The following Jira activities were performed:

- Kanban Board
- Scrum Project
- Epic creation
- User Stories
- Tasks and Subtasks
- Backlog management
- Bug Tracking
- Scrum Reports

The project requirements were converted into user stories and tasks for planning and tracking.

---

## 10. Requirements Engineering

The project includes:

- Functional Requirements
- Non-Functional Requirements
- Requirements Traceability Matrix (RTM)
- Requirement prioritization
- Acceptance criteria
- Requirement rationale

The requirements were documented and organized before system design and development activities.

---

## 11. System Architecture

The system follows a layered architecture consisting of:

- Presentation / Frontend Layer
- Application / Backend Layer
- Database Layer
- External Services

The architecture supports communication between the user interface, application logic, database, and required external services.

---

## 12. GitHub Copilot

GitHub Copilot was used to generate a simple Python function related to telemedicine slot booking.

Example functionality:

```python
def book_consultation(patient_name, doctor_name, consultation_slot):
    return (
        f"Booking confirmed for {patient_name} with Dr. {doctor_name} "
        f"at {consultation_slot}."
    )
## 10. Software Testing Tools

Software testing activities are carried out using the software testing repository provided for the course.

The testing process includes:

- Understanding the given application.
- Executing the provided 4 test cases.
- Identifying the reported bug.
- Using vibe coding / AI assistance to fix the bug.
- Applying the required patch.
- Retesting the application after the fix.
- Documenting the testing and bug-fixing process.
- Sharing the testing repository link.

The testing repository and related test results will be added to this section as instructed by the course faculty.
