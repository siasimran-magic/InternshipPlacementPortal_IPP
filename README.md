# Online Internship & Placement Preparation Portal (IPP)

[![Software Engineering](https://img.shields.io/badge/Course-Software%20Engineering%20(UE24CS351AA2)-0052CC.svg?style=for-the-badge&logo=codeforces&logoColor=white)](https://pes.edu)
[![Institution](https://img.shields.io/badge/Institution-PES%20University-E21A22.svg?style=for-the-badge&logo=academia&logoColor=white)](https://pes.edu)
[![Student SRN](https://img.shields.io/badge/SRN-PES1UG24CS453-orange.svg?style=for-the-badge&logo=target)](https://github.com/siasimran-magic)
[![Repository](https://img.shields.io/badge/GitHub-InternshipPlacementPortal__IPP-181717.svg?style=for-the-badge&logo=github)](https://github.com/siasimran-magic/InternshipPlacementPortal_IPP)
[![Build & Test](https://img.shields.io/badge/CI%2FCD-Passing-brightgreen.svg?style=for-the-badge&logo=github-actions)](https://github.com/siasimran-magic/InternshipPlacementPortal_IPP)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

---

## 📌 Executive Summary & Problem Statement

### 1. Problem Statement
> **Students often search for internship and placement opportunities across multiple platforms while separately preparing for aptitude tests and tracking applications and preparation progress. This fragmentation makes it difficult to organize opportunities, applications, test performance and preparation analytics in one place. The proposed Online Internship & Placement Preparation Portal provides a centralized system for opportunity discovery, applications, aptitude tests, progress tracking and analytics.**

### 2. Proposed Solution
The **Online Internship & Placement Preparation Portal (IPP)** is an integrated, unified software ecosystem engineered to eliminate fragmentation across campus recruitment workflows. It addresses the complete student lifecycle:

```
[ Opportunity Discovery ] ──▶ [ Application Tracker ] ──▶ [ Aptitude & Coding Engine ] ──▶ [ Analytics Dashboard ]
         ▲                                                                                          │
         └────────────────────── Automated Feedback & Readiness Metric ─────────────────────────────┘
```

* **Centralized Job & Internship Board**: Aggregate placement drives, off-campus opportunities, eligibility criteria, and deadlines in one real-time dashboard.
* **Kanban Application Lifecycle Tracking**: Visual stage tracking (`Applied` $\rightarrow$ `Shortlisted` $\rightarrow$ `OA Round` $\rightarrow$ `Interview` $\rightarrow$ `Offer` / `Rejected`).
* **Interactive Aptitude & Technical Test Simulator**: Timed adaptive assessments covering Quantitative Aptitude, Logical Reasoning, Verbal Ability, and Core CS Fundamentals (OS, DBMS, CN, DSA).
* **AI-Powered Readiness Analytics**: Individual readiness score, performance radar charts, domain-specific strengths/weaknesses, and percentile benchmarking against the batch.
* **TPO (Training & Placement Officer) Administration**: Drive scheduling, eligibility verification, student resume screening, and automated aggregate reporting.

---

## 📂 Repository Structure (SE Subject Anchor Deliverables)

This repository is strictly organized in accordance with the **Software Engineering (SE) Subject Anchor Guidelines**:

```
InternshipPlacementPortal_IPP/
│
├── 📁 1-SRS-and-WBS/         # a) Software Requirements Specification & Work Breakdown Structure
├── 📁 2-Test-Planning/        # b) Software Test Plan (IEEE 829), Strategy, Test Cases & Matrices
├── 📁 3-RE/                   # c) Requirements Engineering (FR, NFR & Bidirectional RTM Table)
├── 📁 4-Design/               # d) Architecture, Design Patterns, UML (Use Case, Component, Sequence), REST APIs
├── 📁 5-Project-Creation/     # e) GitHub Repo Configuration, Branching, Jira Agile/Scrum/Sprint Setup
├── 📁 6-GitHub-Copilot/       # f) AI Pair Programming, Copilot Code Gen Screenshots & Prompt Logs
├── 📁 7-Software-Testing/     # g) Software Testing Tools, AI Vibe Coding Bug Fixing & Retest Logs
├── 📁 8-Deployment/           # h) Deployment Guides, Docker, CI/CD Pipelines, Infrastructure & Environment
├── 📁 9-Demo/                 # i) Project Demo Walkthrough, Prototype Screencasts & Artifacts
└── 📄 README.md               # Master Repository Documentation
```

---

## 📑 Deliverables Index & Direct Navigation

| # | Anchor Folder | Key Contents & Artifacts | Primary Stakeholders | Status |
|:---:|:---|:---|:---|:---:|
| **a** | [**`1-SRS-and-WBS`**](./1-SRS-and-WBS/) | IEEE 830-1998 SRS document, WBS Work Packages (WP 1.0–6.0), Milestone Dictionary | TPO, Dev Team, PM | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **b** | [**`2-Test-Planning`**](./2-Test-Planning/) | IEEE 829 Test Strategy, Unit/Integration/System Scope, Pass/Fail Entry-Exit Criteria | QA Engineers, SDET | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **c** | [**`3-RE`**](./3-RE/) | Functional Requirements (FR-01 to FR-10), NFRs (Performance, Security), RTM Table | System Analysts, Dev | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **d** | [**`4-Design`**](./4-Design/) | Layered Architecture, UML Use Case, Component Diagram, Sequence Flow, REST API Specs | Architects, Engineers | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **e** | [**`5-Project-Creation`**](./5-Project-Creation/) | GitHub Repo Setup, Issue Templates, Jira Backlog, Sprint 1 & 2 Boards, Burndown Charts | Scrum Master, Team | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **f** | [**`6-GitHub-Copilot`**](./6-GitHub-Copilot/) | AI Prompt Engineering, Copilot Code Syntheses, Verification Screenshots, Repo Link | Dev Team | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **g** | [**`7-Software-Testing`**](./7-Software-Testing/) | Pytest / Jest test suites, AI Vibe Coding bug patches, Failure-to-Pass verification | QA & Dev | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **h** | [**`8-Deployment`**](./8-Deployment/) | Dockerfile, Docker Compose, GitHub Actions CI/CD workflow, Environment configuration | DevOps, Cloud Eng | ![Completed](https://img.shields.io/badge/Status-Documented-success) |
| **i** | [**`9-Demo`**](./9-Demo/) | Interactive Walkthrough, Feature Demonstrations, Video Links, Screenshots | Evaluators, Users | ![Completed](https://img.shields.io/badge/Status-Documented-success) |

---

## 🏛️ System Architecture & UML Modeling Preview

### 1. High-Level 3-Tier Layered Architecture Pattern
The system is implemented using a decoupled **Client-Server 3-Tier Layered Architecture** with RESTful communication:

```mermaid
graph TD
    subgraph Presentation_Layer["1. Presentation Tier (Client)"]
        UI_Web["Single Page Application (React / Next.js)"]
        UI_Mobile["Responsive PWA (Tailwind / Modern CSS)"]
        UI_State["Client State & Auth Store (JWT / Context API)"]
    end

    subgraph Application_Layer["2. Application Tier (API Services)"]
        Gateway["API Gateway / Reverse Proxy (Nginx)"]
        AuthSvc["Authentication & RBAC Service (OAuth2 / JWT)"]
        JobSvc["Opportunity Discovery & Filter Engine"]
        TrackerSvc["Application Tracker & Kanban Pipeline"]
        ExamSvc["Aptitude & Quiz Engine (Timed Sandbox)"]
        AnalyticsSvc["Readiness & Performance Analytics Aggregator"]
    end

    subgraph Data_Layer["3. Persistence Tier (Data Store)"]
        DB_Relational[(PostgreSQL / Supabase - Relational DB)]
        DB_Cache[(Redis - Session Cache & Quiz Timer)]
        FileStore[(Cloudinary / S3 - Student Resumes & Assets)]
    end

    Presentation_Layer --> Gateway
    Gateway --> AuthSvc
    Gateway --> JobSvc
    Gateway --> TrackerSvc
    Gateway --> ExamSvc
    Gateway --> AnalyticsSvc
    
    AuthSvc --> DB_Relational
    JobSvc --> DB_Relational
    TrackerSvc --> DB_Relational
    ExamSvc --> DB_Relational
    ExamSvc --> DB_Cache
    AnalyticsSvc --> DB_Relational
    TrackerSvc --> FileStore
```

### 2. UML Use Case Interaction Flow
```mermaid
flowchart LR
    Student((Student))
    TPO((Placement Officer))
    Admin((System Admin))

    subgraph Portal_Boundary["Online Internship & Placement Preparation Portal (IPP)"]
        UC1([Discover Opportunities & Apply])
        UC2([Track Application Status Kanban])
        UC3([Attempt Timed Aptitude & Coding Tests])
        UC4([View Readiness Analytics & Performance Score])
        UC5([Post Placement Drives & Verify Eligibility])
        UC6([Shortlist Applicants & Export Roster])
        UC7([Manage Question Bank & Test Schedules])
        UC8([User & Role-Based Access Control])
    end

    Student --> UC1
    Student --> UC2
    Student --> UC3
    Student --> UC4

    TPO --> UC5
    TPO --> UC6
    TPO --> UC7

    Admin --> UC8
    Admin --> UC7
```

### 3. Sequence Flow: Student Attempting Aptitude Test & Syncing Analytics
```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant WebUI as Frontend (SPA)
    participant ExamAPI as Exam Service
    participant Redis as Redis Cache
    participant DB as Relational Database
    participant Analytics as Analytics Engine

    Student->>WebUI: Selects Aptitude Mock Test & clicks "Start"
    WebUI->>ExamAPI: POST /api/tests/start (test_id, student_id)
    ExamAPI->>DB: Fetch test questions & shuffle sequence
    ExamAPI->>Redis: Set test session timer (TTL = 60 mins)
    ExamAPI-->>WebUI: 200 OK (Questions JSON, Session Token)
    
    loop Every Answer Selection
        Student->>WebUI: Selects Option / Types Response
        WebUI->>Redis: PUT /api/tests/sync (temp response auto-save)
    end

    Student->>WebUI: Clicks "Submit Test"
    WebUI->>ExamAPI: POST /api/tests/submit (final answers)
    ExamAPI->>Redis: Invalidate session timer
    ExamAPI->>DB: Compute score, mark correct/incorrect, store result
    ExamAPI->>Analytics: Trigger asynchronous analytics update (student_id)
    Analytics->>DB: Recompute domain percentile, accuracy, readiness index
    Analytics-->>ExamAPI: Readiness score updated (+4.2%)
    ExamAPI-->>WebUI: 200 OK (Score Report, Answer Keys, Analytics Delta)
    WebUI-->>Student: Renders Performance Radar Chart & Answer Breakdown
```

---

## 📋 Comprehensive Requirements & Traceability Overview (RE & RTM)

### Functional Requirements (FR)
* **FR-01 (Authentication & RBAC)**: Secure multi-role authentication (Student, Recruiter, TPO, Admin) via JWT tokens with encrypted credentials and password reset flows.
* **FR-02 (Opportunity Aggregator)**: Comprehensive searchable and filterable database of internships and full-time placement openings categorized by role, CTC, eligibility criteria, and deadline.
* **FR-03 (One-Click Application & Tracker)**: Students submit applications directly; state tracked via customizable stages (`Applied`, `Under Review`, `Shortlisted`, `Technical Assessment`, `HR Interview`, `Accepted`, `Rejected`).
* **FR-04 (Timed Aptitude Assessment Engine)**: Online testing environment with countdown timers, anti-cheat detection (tab-switch tracking), randomized question pools, and automated evaluation.
* **FR-05 (Question Bank Management)**: Curated repository of quantitative, verbal, reasoning, and technical MCQ questions with difficulty tags, company-wise past papers, and detailed explanations.
* **FR-06 (Readiness Analytics & Radar Charts)**: Visual diagnostic feedback on student performance, calculating percentile rankings, topic-level weaknesses, and overall employability score.
* **FR-07 (Resume Repository & Verification)**: PDF resume upload, validation, parsing, and attachment to company applications.
* **FR-08 (TPO Drive Management & Broadcast)**: TPO portal to publish company drives, set minimum CGPA / backlog criteria, and broadcast notifications.
* **FR-09 (Automated Notification Engine)**: Real-time alerts for impending application deadlines, scheduled assessments, and shortlist announcements via email and in-portal alerts.
* **FR-10 (Audit Logs & Export)**: Placement reports, student participation statistics, and test score exports in CSV/Excel formats for administrative reporting.

### Non-Functional Requirements (NFR)
* **NFR-01 (Performance)**: Page load time $< 1.8\text{ seconds}$ on standard broadband; API responses served within $200\text{ ms}$ at 95th percentile under normal loads.
* **NFR-02 (Security)**: Industry-standard TLS 1.3 encryption in transit, bcrypt hashed passwords with salt factor 12, strict CORS, and protection against OWASP Top 10 vulnerabilities (SQLi, XSS, CSRF).
* **NFR-03 (Scalability)**: Stateless backend API capable of horizontal scaling to support over $5,000$ concurrent student test submissions during live placement aptitude windows.
* **NFR-04 (Reliability & Availability)**: Minimum system uptime of $99.9\%$ during campus placement drives with automated database backups every 24 hours.
* **NFR-05 (Usability & Accessibility)**: Intuitive UI complying with WCAG 2.1 Level AA standards, responsive across mobile, tablet, and desktop viewports.
* **NFR-06 (Maintainability)**: Modular directory architecture adhering to Clean Architecture principles with over $80\%$ automated unit test code coverage.

### Requirements Traceability Matrix (RTM) Summary
| Req ID | Requirement Description | Architecture Module | Implementation Component | Test Case ID | Verification Status |
|:---:|:---|:---|:---|:---:|:---:|
| **FR-01** | Student & Admin Authentication | Auth Microservice | `AuthController.js` / JWT Provider | `TC_AUTH_01` | **Passed** ✅ |
| **FR-02** | Opportunity Discovery & Filters | Opportunity Service | `JobBoardView.jsx` / `JobRoute.js` | `TC_JOB_01` | **Passed** ✅ |
| **FR-03** | Kanban Application Tracker | Tracker Service | `ApplicationTracker.jsx` | `TC_TRK_01` | **Passed** ✅ |
| **FR-04** | Timed Aptitude Exam Simulator | Assessment Service | `TestRunner.jsx` / `ExamEngine.js` | `TC_EXM_01` | **Passed** ✅ |
| **FR-05** | Question Bank Management | Content Management | `QuestionBankService.js` | `TC_QBK_01` | **Passed** ✅ |
| **FR-06** | Student Readiness Analytics | Analytics Service | `AnalyticsDashboard.jsx` | `TC_ANL_01` | **Passed** ✅ |
| **FR-07** | Resume Storage & Verification | Storage Service | `ResumeUploadModal.jsx` / S3 API | `TC_RES_01` | **Passed** ✅ |
| **FR-08** | TPO Drive Scheduling & Criteria | Placement Admin | `TpoDriveManager.jsx` | `TC_TPO_01` | **Passed** ✅ |
| **FR-09** | Real-time Deadline Notifications | Messaging Service | `NotificationHub.jsx` / Webhook | `TC_NOTIF_01` | **Passed** ✅ |
| **FR-10** | Roster Export (Excel/CSV) | Reporting Service | `ExportService.js` | `TC_RPT_01` | **Passed** ✅ |

---

## 🛠️ Technology Stack

| Layer | Technologies Used |
|:---|:---|
| **Frontend UI/UX** | React.js / Vite, Vanilla CSS3 (Custom Design System, Dark Mode, Glassmorphism), Lucide Icons, Chart.js |
| **Backend & APIs** | Node.js (Express.js) / Python (FastAPI), RESTful API design, JWT Authorization |
| **Database & Caching** | PostgreSQL (Relational schema for students, jobs, tests), Redis (Session storage & timed quiz locks) |
| **Testing & Quality** | Jest, Supertest, Pytest, Playwright, Coverage reports |
| **AI & Vibe Coding** | GitHub Copilot, Gemini Code Assist, Automated failure-to-patch workflows |
| **DevOps & Cloud** | Docker, Docker Compose, GitHub Actions CI/CD, Nginx reverse proxy, Render / Vercel cloud hosting |
| **Project Management** | Jira Software (Agile Scrum/Kanban boards, Sprint burn-down), GitHub Projects |

---

## 🚀 Quick Start & Local Setup

### Prerequisites
* **Node.js**: v18.0.0 or higher
* **Python**: v3.10+ (if running backend microservices)
* **Docker & Docker Compose**: Recommended for containerized setup
* **Git**: Installed and configured

### 1. Clone the Repository
```bash
git clone https://github.com/siasimran-magic/InternshipPlacementPortal_IPP.git
cd InternshipPlacementPortal_IPP
```

### 2. Environment Setup
Create a `.env` file in the root directory (refer to [`.env.example`](./8-Deployment/)):
```env
PORT=5000
NODE_ENV=development
DATABASE_URL=postgresql://ipp_user:ipp_password@localhost:5432/ipp_db
JWT_SECRET=super_secret_jwt_key_placement_portal_2026
REDIS_URL=redis://localhost:6379
```

### 3. Run with Docker Compose
```bash
docker-compose up --build
```
The application will be accessible at:
* **Web Portal (Frontend)**: `http://localhost:3000`
* **API Documentation (Swagger/OpenAPI)**: `http://localhost:5000/api/docs`
* **PostgreSQL Database**: `localhost:5432`


