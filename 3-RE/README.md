# 3. Requirements Engineering (RE)

[![Software Engineering](https://img.shields.io/badge/Course-Software%20Engineering%20(UE24CS351AA2)-0052CC.svg)](https://pes.edu)
[![Student SRN](https://img.shields.io/badge/SRN-PES1UG24CS453-orange.svg)](https://github.com/siasimran-magic)
[![Standard](https://img.shields.io/badge/Standard-IEEE%20830-blue.svg)](https://standards.ieee.org)

**Project**: Online Internship & Placement Preparation Portal (IPP)  
**Institution**: PES University | Department of Computer Science & Engineering  
**Student SRN**: PES1UG24CS453  

---

## 📌 Problem Statement Reference
> "Students often search for internship and placement opportunities across multiple platforms while separately preparing for aptitude tests and tracking applications and preparation progress. This fragmentation makes it difficult to organize opportunities, applications, test performance and preparation analytics in one place. The proposed Online Internship & Placement Preparation Portal provides a centralized system for opportunity discovery, applications, aptitude tests, progress tracking and analytics."

---

## ⚙️ 1. Functional Requirements (FR)

| Req ID | Requirement Name | Description & Processing Flow | Input Parameters | Output / System Response | Priority |
|:---:|:---|:---|:---|:---|:---:|
| **FR-01** | **User Authentication & RBAC** | System validates credentials and issues JWT token containing role claims (`student`, `recruiter`, `tpo`, `admin`). | SRN/Email, Password, Role | Auth Token (JWT), Profile Data, Role View | **Must Have (P1)** |
| **FR-02** | **Centralized Opportunity Discovery** | Searchable repository of job/internship listings with filters for role type, minimum CGPA, branch, stipend/CTC, and deadline. | Search keywords, Filter tags | Filtered list of eligible drives with countdown timers | **Must Have (P1)** |
| **FR-03** | **Application Submission & Management** | Students apply with stored profile & verified resume; system enforces eligibility checks before allowing submission. | Student ID, Drive ID, Resume ID | Status: `Applied`, Confirmation ID generated | **Must Have (P1)** |
| **FR-04** | **Visual Application Tracker (Kanban)** | Interactive board displaying applications categorized into status columns (`Applied`, `Shortlisted`, `OA Round`, `Interview`, `Offer`, `Rejected`). | Application ID, Target Status | Instant visual drag-and-drop update & DB persistence | **Must Have (P1)** |
| **FR-05** | **Timed Aptitude Assessment Simulator** | Test-taking engine with randomized question sets, countdown timer, auto-save on selection, and auto-submit on timeout. | Test ID, Student Answers Array | Test Result, Score breakdown, Accuracy percentage | **Must Have (P1)** |
| **FR-06** | **Question Bank & Categorization** | Repository of MCQs categorized by topic (Quant, Verbal, Reasoning, Core CS) with difficulty levels and solution keys. | Question data, Topic, Difficulty | Stored questions accessible for mock and official tests | **Should Have (P2)** |
| **FR-07** | **Readiness Analytics & Radar Charts** | Analytical engine that aggregates mock scores, identifies weak domains, and computes an overall Employability Readiness Score. | Historical test scores, Timings | Interactive Radar Charts, Strength/Weakness Report | **Must Have (P1)** |
| **FR-08** | **Resume Upload & Parsing** | Validates PDF resumes, checks file size ($\le 5\text{MB}$), generates cloud storage URL, and extracts key skills. | PDF Resume Document | Secure Cloud URL, Extracted Skills List | **Should Have (P2)** |
| **FR-09** | **TPO Drive & Placement Scheduling** | TPOs can post company drives, configure cutoffs, review eligible student rosters, and broadcast announcements. | Drive title, Criteria, CTC, Dates | Published drive listing, Automated email triggers | **Must Have (P1)** |
| **FR-10** | **Automated Alerts & Notifications** | System sends in-portal alerts and emails for upcoming drive deadlines, test schedules, and shortlist announcements. | Event Trigger (Drive deadline, Result) | Push Notification, Email alert delivered | **Could Have (P3)** |

---

## 🛡️ 2. Non-Functional Requirements (NFR)

| Req ID | Category | Metric / Specification | Target Threshold | Verification Method |
|:---:|:---|:---|:---|:---|
| **NFR-01** | **Performance & Latency** | Page initial load time; API response latency under 95th percentile. | Initial load $< 1.8\text{s}$, API latency $< 200\text{ms}$ | Google Lighthouse & Apache JMeter benchmark |
| **NFR-02** | **Security & Privacy** | Password hashing with bcrypt, TLS 1.3 in transit, strict RBAC authorization, protection against SQLi and XSS. | Zero high-risk OWASP Top 10 vulnerabilities; 100% encrypted tokens | OWASP ZAP Automated Security Scan |
| **NFR-03** | **Scalability & Concurrency** | Ability to handle peak simultaneous traffic during scheduled campus aptitude tests. | $\ge 5,000$ concurrent student test sessions without session drops | Locust / k6 distributed stress testing |
| **NFR-04** | **Reliability & Availability** | System operational availability during active campus placement season. | $\ge 99.9\%$ uptime with automated failover and daily DB snapshots | CloudWatch / Prometheus uptime monitoring |
| **NFR-05** | **Usability & Accessibility** | Responsive layout across mobile, tablet, and desktop viewports; color contrast compliance. | WCAG 2.1 Level AA compliance; System Usability Scale (SUS) $> 80$ | Axe DevTools accessibility audit |
| **NFR-06** | **Maintainability & Portability** | Decoupled modular design with containerized deployment. | Docker container build time $< 3\text{ mins}$, Test coverage $> 80\%$ | Jest / Pytest automated coverage report |

---

## 🗺️ 3. Bidirectional Requirements Traceability Matrix (RTM)

The Requirements Traceability Matrix guarantees that every user requirement stated in the problem statement maps directly to functional specifications, architectural components, implementation modules, and verified test cases:

| Need ID | Problem Statement Need | Requirement ID | Functional Requirement | Architecture Component | Source File / Implementation | Test Case ID | Verification Status |
|:---:|:---|:---:|:---|:---|:---|:---:|:---:|
| **N-01** | Centralized discovery of opportunities | **FR-02** | Centralized Opportunity Discovery | Opportunity Service | `JobController.js`, `JobBoard.jsx` | `TC_JOB_01` | **Verified ✅** |
| **N-02** | Simplified application workflow | **FR-03** | Application Submission | Application Service | `ApplicationController.js` | `TC_JOB_02` | **Verified ✅** |
| **N-03** | Unified tracking of applications | **FR-04** | Visual Application Tracker | Tracker Service | `TrackerBoard.jsx`, `KanbanView.js` | `TC_TRK_01` | **Verified ✅** |
| **N-04** | Separate & structured aptitude prep | **FR-05** | Timed Aptitude Exam Simulator | Assessment Service | `ExamEngine.js`, `QuizRunner.jsx` | `TC_EXM_01` | **Verified ✅** |
| **N-05** | Rich question bank & explanations | **FR-06** | Question Bank Management | Content Service | `QuestionBank.js`, `QuestionModel.js`| `TC_QBK_01` | **Verified ✅** |
| **N-06** | Actionable preparation analytics | **FR-07** | Readiness Analytics & Radar | Analytics Service | `AnalyticsEngine.py`, `RadarChart.jsx`| `TC_ANL_01` | **Verified ✅** |
| **N-07** | Centralized verified student resume | **FR-08** | Resume Upload & Parsing | Storage Service | `ResumeHandler.js`, `S3Uploader.js` | `TC_RES_01` | **Verified ✅** |
| **N-08** | TPO oversight & placement management | **FR-09** | TPO Drive & Scheduling | Placement Management | `TpoController.js`, `DriveManager.jsx`| `TC_TPO_01` | **Verified ✅** |
| **N-09** | System security & student identity | **FR-01** | User Authentication & RBAC | Security & Auth Service| `AuthMiddleware.js`, `JwtService.js` | `TC_AUTH_01` | **Verified ✅** |
| **N-10** | High availability during placement drives | **NFR-03**| High Concurrency & Scalability | Redis + Load Balancer | `nginx.conf`, `redis_session.py` | `TC_PERF_01` | **Verified ✅** |
