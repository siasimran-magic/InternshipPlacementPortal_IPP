# 2. Test Planning & Quality Assurance

[![Software Engineering](https://img.shields.io/badge/Course-Software%20Engineering%20(UE24CS351AA2)-0052CC.svg)](https://pes.edu)
[![Student SRN](https://img.shields.io/badge/SRN-PES1UG24CS453-orange.svg)](https://github.com/siasimran-magic)
[![Standard](https://img.shields.io/badge/Standard-IEEE%20829-blue.svg)](https://standards.ieee.org)

**Project**: Online Internship & Placement Preparation Portal (IPP)  
**Institution**: PES University | Department of Computer Science & Engineering  
**Student SRN**: PES1UG24CS453  

---

## 🎯 1. Test Strategy & Objectives (IEEE 829)
The objective of the Test Plan for the **Online Internship & Placement Preparation Portal (IPP)** is to establish a rigorous quality assurance framework to ensure:
* Zero data loss or state desynchronization during high-concurrency aptitude exams.
* Precise role-based access control (RBAC) isolating Student, Recruiter, TPO, and Admin actions.
* Smooth end-to-end user workflows from internship discovery to application tracking and readiness score calculation.
* Sub-2-second latency during test submission and real-time analytics aggregation.

---

## 🔬 2. Scope of Testing

### In-Scope
1. **Unit Testing**:
   - Verification of utility functions (score calculator, percentile ranker, deadline formatters).
   - Controller logic (JWT token generation, payload validation, password hashing).
2. **Integration Testing**:
   - API endpoints interaction with PostgreSQL database transactions.
   - Redis timer lock integration for aptitude test sessions.
   - Resume upload pipeline interacting with storage buckets.
3. **System & Functional Testing**:
   - Complete application tracking lifecycle: Applied $\rightarrow$ Shortlisted $\rightarrow$ Test Scheduled $\rightarrow$ Result.
   - Live mock aptitude assessment with automatic countdown and submission on timer expiry.
4. **Security & Vulnerability Testing**:
   - Prevention of SQL Injection, Cross-Site Scripting (XSS), and Cross-Site Request Forgery (CSRF).
   - Tamper-proofing of quiz submission payloads and student role elevation attempts.
5. **Performance & Stress Testing**:
   - Load testing simulating 1,000 to 5,000 concurrent students submitting tests simultaneously.

### Out-of-Scope
- Direct hardware failure testing of 3rd-party cloud providers (AWS/Vercel datacenters).
- In-person proctoring webcam video stream bandwidth testing.

---

## 🧪 3. Test Cases Specification

| Test ID | Module | Test Scenario | Preconditions | Input Data / Steps | Expected Result | Status |
|:---:|:---|:---|:---|:---|:---|:---:|
| `TC_AUTH_01` | Auth | Valid Student Login | Registered account in DB | Valid SRN/email & correct password | 200 OK, JWT returned, redirects to Student Dashboard | **Pass** ✅ |
| `TC_AUTH_02` | Auth | Invalid Password Attempt | Registered account in DB | Valid SRN with incorrect password | 401 Unauthorized, error toast displayed, no token issued | **Pass** ✅ |
| `TC_AUTH_03` | Auth | Role-Based Authorization | Logged in as Student | Access `/api/admin/tpo-drives` directly | 403 Forbidden response, access denied | **Pass** ✅ |
| `TC_JOB_01` | Jobs | Filter by Eligibility | Active drives in DB | Select CGPA $\ge 8.0$, Branch: CSE | Display only matching placement opportunities | **Pass** ✅ |
| `TC_JOB_02` | Jobs | Apply with Resume | Student logged in, profile complete | Click "Apply", attach standard resume | Application registered, status becomes "Applied" | **Pass** ✅ |
| `TC_TRK_01` | Tracker | Kanban Status Transition | Existing application in "Applied" | Recruiter moves card to "Shortlisted" | DB status updates, student receives notification | **Pass** ✅ |
| `TC_EXM_01` | Exam Engine | Start Timed Aptitude Exam | Eligible student, active test | Click "Start Exam" | Timer begins at 60:00, randomized questions loaded | **Pass** ✅ |
| `TC_EXM_02` | Exam Engine | Auto-Submit on Timeout | Ongoing test session | Allow timer to count down to 00:00 | Answers auto-submitted, session locked, score computed | **Pass** ✅ |
| `TC_EXM_03` | Exam Engine | Anti-Cheat Tab Switch Warning | Live test session active | Switch browser tab 3 times | Alert dialog triggered, 3rd switch triggers auto-lock | **Pass** ✅ |
| `TC_ANL_01` | Analytics | Readiness Score Calculation | Submitted $\ge 1$ practice test | Navigate to Analytics tab | Radar chart renders with quant, verbal, and technical scores | **Pass** ✅ |
| `TC_PERF_01`| Performance | High Concurrency Load | 2,000 simulated virtual users | Concurrent `POST /api/tests/submit` | 95th percentile response time $< 800\text{ ms}$, 0% error rate | **Pass** ✅ |

---

## 🚦 4. Entry and Exit Criteria

### Entry Criteria
* Code complete for the target sprint with clean compilation.
* All unit tests passing in the local development environment.
* Staging database seeded with test accounts, question banks, and dummy placement drives.
* CI/CD pipeline green on GitHub Actions.

### Exit Criteria
* $\ge 90\%$ test case pass rate across all functional modules.
* Zero Critical (Severity 1) or High (Severity 2) defects open.
* Test execution summary signed off by QA lead and TPO representative.
* RTM fully updated with verified test case executions.

---

## 📊 5. Defect Severity Classification Matrix

| Severity Level | Definition | Target Resolution Time | Example |
|:---|:---|:---:|:---|
| **S1 - Critical** | System crash, data corruption, security breach | $< 4\text{ hours}$ | Exam answers lost during submission; unauthorized admin elevation |
| **S2 - High** | Major feature broken with no workaround | $< 24\text{ hours}$ | Unable to upload resume PDF; application status fails to update |
| **S3 - Medium** | Feature malfunctioning with viable workaround | $< 48\text{ hours}$ | Filter dropdown sorting incorrectly; minor calculation lag in analytics |
| **S4 - Low** | Cosmetic flaw or minor UI alignment issue | Next Sprint | Badge color mismatch; typo in question explanation text |
