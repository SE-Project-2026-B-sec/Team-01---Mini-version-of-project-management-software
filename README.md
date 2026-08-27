[README.md](https://github.com/user-attachments/files/31505512/README.md)
# Lab 1: Requirements Engineering & UML Use-Case Modelling

**Smart Lab Equipment & Slot Reservation Portal**

A scheduling system for engineering lab facilities that prevents double-booking of high-value hardware (oscilloscopes, logic analyzers, FPGA boards), verifies equipment calibration status before allowing reservations, and enforces late-return disciplinary rules.

## Actors

- **Student** — views equipment availability, reserves and cancels slots
- **Lab Technician** — manages equipment status, records returns, applies disciplinary restrictions
- **Authentication Service** — authenticates users before granting access

## Repository Contents

| File | Description |
|---|---|
| `Requirements_Table.docx` | 5 Functional Requirements (FR-001–FR-005) and 2 Non-Functional Requirements (NFR-001–NFR-002), each with ID, Type, Description, Priority, Acceptance Criteria, and Rationale |
| `Smart_Lab_Use_Case_Diagram.drawio` | Editable UML use-case diagram source (draw.io) |
| `UML_UseCase_Diagram.pdf` | Exported UML use-case diagram — actors, use cases, system boundary, «include» and «extend» relationships |
| `UseCase_Flow_ReserveSlot.docx` | One-page use-case flow for UC-02: Reserve Equipment Slot — preconditions, postconditions, main success scenario, and two alternate flows |
| `Lab1_Combined.pdf` | All three documents merged into a single PDF for easy review |

## Use Cases

- UC-01: View Equipment Availability
- UC-02: Reserve Equipment Slot *(«include»s Check Equipment Availability)*
- UC-03: Cancel Reservation
- UC-04: Manage Equipment Status
- UC-05: Record Equipment Return *(extended by Flag Late Return)*
- Authenticate User
- Check Equipment Availability
- Flag Late Return
- Apply Disciplinary Restriction

## Key Design Decisions

- **FR-003** (equipment status management) gates **FR-001** (reservation) — a student cannot reserve equipment marked uncalibrated, under maintenance, or unavailable.
- **NFR-001** (200ms concurrent processing with DB-level locking) is what the "Slot Already Locked" alternate flow in the use-case flow document demonstrates.
- **Check Equipment Availability** is factored out as an included use case rather than duplicated, since both UC-01 and UC-02 depend on it.
- **Flag Late Return** is modeled as an `extend` (not `include`) of UC-05 because it only applies conditionally — when a return is late — not on every equipment return.

## Tools Used

draw.io (UML diagram) · Microsoft Word (requirements table and use-case flow)
