# Lab 3: Component Modelling & Architectural Pattern Selection

**Course**: Software Engineering  
**Institution**: PES University  
**Student SRN**: PES1UG24CS453  
**Topic**: Municipal Solid Waste Route Optimizer

---

## Deliverables Summary

This directory contains the deliverables for Lab 3:

| File | Format | Description |
|---|---|---|
| `architecture_justification.pdf` | PDF Document | Exactly 1-page PDF export of the architectural justification and pattern comparison table. |
| `component_diagram.png` | PNG Image | High-resolution UML 2.0 Component Architecture Diagram with `<<component>>` stereotypes, ball-and-socket assembly connectors, protocols, and data flow. |
| `BUGTRACKER_PES1UG24CS453.pdf` | PDF Document | Bug tracking report. |
| `KANBAN_PES1UG24CS453.pdf` | PDF Document | Kanban board report. |
| `SCRUM_PES1UG24CS453.pdf` | PDF Document | Scrum agile sprint report. |

---

## Scenario Overview

The **Municipal Solid Waste Route Optimizer** is a city sanitation portal designed to:
- Ingest ultrasonic fill-level telemetry from 10,000 smart trash bins across the city.
- Plan dynamic collection routes including **only bins over 80% full**.
- Achieve recalculation for **50 garbage trucks across 10,000 bins in under 45 seconds**.
- Track citizen complaints for missed waste pickups.
- **Actors**: Sanitation Supervisor (Fleet Operations), Truck Driver (In-Cab Navigation), Citizen (Public User), Smart Trash Bins (Ultrasonic Sensors).
