# 5. Project Creation, GitHub Repository & Jira Agile Management

[![Software Engineering](https://img.shields.io/badge/Course-Software%20Engineering%20(UE24CS351AA2)-0052CC.svg)](https://pes.edu)
[![Student SRN](https://img.shields.io/badge/SRN-PES1UG24CS453-orange.svg)](https://github.com/siasimran-magic)
[![Agile Framework](https://img.shields.io/badge/Methodology-Scrum%20%2F%20Kanban-blue.svg)](https://atlassian.com)

**Project**: Online Internship & Placement Preparation Portal (IPP)  
**Institution**: PES University | Department of Computer Science & Engineering  
**Student SRN**: PES1UG24CS453  
**Repository**: [https://github.com/siasimran-magic/InternshipPlacementPortal_IPP](https://github.com/siasimran-magic/InternshipPlacementPortal_IPP)

---

## 🐙 1. GitHub Project Creation & Repository Setup

### Repository Details
* **Repository Name**: `InternshipPlacementPortal_IPP`
* **Visibility**: Public
* **Primary Branch**: `main` (Protected)
* **Development Branch**: `develop`
* **Feature Branches**: `feature/<feature-name>` (e.g., `feature/kanban-tracker`, `feature/aptitude-timer`)
* **Bugfix Branches**: `bugfix/<issue-id>` (e.g., `bugfix/timer-desync`)

### Branch Protection Rules
1. Require a pull request before merging into `main`.
2. Require at least 1 approving code review.
3. Require status checks to pass before merging (`CI / Build and Unit Tests`).
4. Enforce strict linear history and squash merges.

### Screenshots Placeholder & Directory Map
Place the captured screenshots in this directory with the following filenames:
* `screenshots/github_repo_creation.png`: Screenshot of initial repository setup, license, and `.gitignore`.
* `screenshots/github_branch_rules.png`: Screenshot of branch protection configuration for `main`.
* `screenshots/github_pr_workflow.png`: Screenshot of a completed pull request with peer code review and CI checks passing.

---

## 📊 2. Jira Software Scrum & Sprint Management

### Project Profile in Jira
* **Project Name**: Online Internship & Placement Preparation Portal
* **Project Key**: `IPP`
* **Project Type**: Scrum Software Development
* **Scrum Master / Lead**: PES1UG24CS453

### Epics Structure
| Epic Key | Epic Name | Description | Story Points |
|:---:|:---|:---|:---:|
| **IPP-EP-1** | Core Authentication & RBAC | Secure multi-role sign-in, JWT session management, student & TPO access control | 13 |
| **IPP-EP-2** | Opportunity Discovery & Job Board | Company placement drives listing, filters (CGPA/Branch), deadline trackers | 21 |
| **IPP-EP-3** | Application Tracking Lifecycle | Visual Kanban stage board, status transitions, notifications | 21 |
| **IPP-EP-4** | Aptitude & Assessment Simulator | Timed mock test runner, anti-cheat detection, instant evaluation | 34 |
| **IPP-EP-5** | Readiness Analytics Engine | Student performance radar chart, percentile calculation, weakness diagnosis | 21 |

### Sprint 1 Breakdown (Sprint Duration: 2 Weeks)
* **Sprint Goal**: Implement foundation services: Authentication, Database Schema, and Opportunity Listing Board.
* **Committed Story Points**: 34 SP
* **User Stories**:
  * `IPP-101`: As a student, I want to register and log in using my university SRN so that my profile is authenticated (5 SP).
  * `IPP-102`: As an admin/TPO, I want to authenticate with elevated privileges to manage placement records (5 SP).
  * `IPP-103`: As a student, I want to view active placement drives with eligibility filters (8 SP).
  * `IPP-104`: As a student, I want to upload my PDF resume to be attached with job applications (8 SP).
  * `IPP-105`: As a developer, I want to set up Docker Compose and CI/CD pipelines on GitHub Actions (8 SP).

### Sprint 2 Breakdown (Sprint Duration: 2 Weeks)
* **Sprint Goal**: Build the Timed Aptitude Exam Simulator and Application Tracking Kanban Board.
* **Committed Story Points**: 42 SP
* **User Stories**:
  * `IPP-201`: As a student, I want to launch a 60-minute aptitude test with live countdown timer (13 SP).
  * `IPP-202`: As an assessment engine, I want to auto-save student answers and auto-submit on timeout (8 SP).
  * `IPP-203`: As a student, I want to drag and drop my job applications across Kanban stages (8 SP).
  * `IPP-204`: As a student, I want to view my readiness radar chart after completing tests (13 SP).

### Screenshots Placeholder & Directory Map
Place the captured Jira screenshots in this directory with the following filenames:
* `screenshots/jira_backlog_view.png`: Jira Backlog showing Epics, User Stories, and Story Point estimations.
* `screenshots/jira_active_sprint_board.png`: Jira Active Sprint board with `To Do`, `In Progress`, `Code Review`, and `Done` columns.
* `screenshots/jira_burndown_chart.png`: Jira Burndown Chart illustrating story point burn-rate versus ideal trend line.
* `screenshots/jira_roadmap_gantt.png`: Jira Product Roadmap showing timeline milestones across Epics.
