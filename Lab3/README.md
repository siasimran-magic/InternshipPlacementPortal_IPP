# Lab 3: Component Modelling & Architectural Pattern Selection

**Course**: Software Engineering  
**Institution**: PES University  
**Topic**: Municipal Solid Waste Route Optimizer

---

## Deliverables Summary

This directory contains the complete deliverables for Lab 3:

| File | Format | Description |
|---|---|---|
| `component_diagram.png` | PNG Image | High-resolution UML 2.0 Component Architecture Diagram with `<<component>>` stereotypes, ball-and-socket assembly connectors, protocols, and data flow. |
| `component_diagram.pdf` | PDF Document | Single-page vector PDF export of the component diagram. |
| `component_diagram.puml` | PlantUML Source | Source code for reproducing and rendering the component diagram. |
| `architecture_justification.docx` | Word Document | 1-page structured architectural justification selecting Microservices Architecture. |
| `architecture_justification.pdf` | PDF Document | Exactly 1-page PDF export of the architectural justification and pattern comparison table. |

---

## Scenario Overview

The **Municipal Solid Waste Route Optimizer** is a city sanitation portal designed to:
- Ingest ultrasonic fill-level telemetry from 10,000 smart trash bins across the city.
- Plan dynamic collection routes including **only bins over 80% full**.
- Achieve recalculation for **50 garbage trucks across 10,000 bins in under 45 seconds**.
- Track citizen complaints for missed waste pickups.
- **Actors**: Sanitation Supervisor (Fleet Operations), Truck Driver (In-Cab Navigation), Citizen (Public User), Smart Trash Bins (Ultrasonic Sensors).

---

## Component Architecture Highlights

- **Web Portal / API Gateway (`<<component>>`)**: Central entry point handling TLS termination, JWT authentication, RBAC, and rate limiting.
- **Sensor Data Ingestion Service (`<<component>>`)**: Decoupled ingestion worker handling high-frequency telemetry via MQTT / NB-IoT.
- **Driver Manifest Service (`<<component>>`)**: Dispatches shift manifests and streams turn-by-turn routes via WebSocket.
- **Route Optimization Service (`<<component>>`)**: Compute-optimized heuristics engine exposing the required **`Route Request`** interface (`gRPC / Protobuf`) to meet the strict 45-second recalculation deadline.
- **Complaint Management Service (`<<component>>`)**: Processes and tracks citizen missed-pickup reports.
- **Bin & Route Database (`<<component>>`)**: Multi-model storage cluster (PostgreSQL/PostGIS spatial data, TimescaleDB telemetry, and Redis cache).
