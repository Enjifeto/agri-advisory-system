# Software Requirements Specification

**Project:** Agricultural Problem Analysis and Advisory System
**Course:** [Course name]
**Prepared by:** [Your name / team members]
**Date:** [Date]
**Version:** 1.0

---

## 1. Introduction

### 1.1 Purpose
This document lists the functional and non-functional requirements of the Agricultural Problem Analysis and Advisory System. It is the reference for design, implementation, and testing.

### 1.2 Scope
The system is a web-based, rule-driven application. Farmers select a crop and observed symptoms, and the system returns the probable problem with treatment and prevention advice. Experts and administrators manage the knowledge base. The system uses expert-defined rules only (no AI/ML). See `problem-statement.md` for full scope.

### 1.3 Definitions

| Term | Meaning |
|---|---|
| Farmer | Primary user who requests analysis of a crop problem |
| Expert | User who creates and maintains rules and advice |
| Administrator | User who manages accounts and system data |
| Symptom | An observable sign on a crop (e.g., yellow leaves) |
| Problem | A disease, pest, deficiency, or other cause of crop damage |
| Rule | A mapping: crop + set of symptoms → probable problem |
| Advice | Recommended treatment and prevention for a problem |
| Analysis | One request in which a user submits symptoms and gets a result |

### 1.4 Priority Levels
- **High:** the system cannot work without it.
- **Medium:** important, should be delivered.
- **Low:** desirable, delivered if time allows.

---

## 2. Overall Description

### 2.1 System Perspective
A client-server web application: browser frontend (HTML/CSS/JavaScript, optionally React), Java REST backend, and a relational SQL database.

### 2.2 User Classes

| User | Description | Technical skill |
|---|---|---|
| Farmer | Requests analysis, reads advice, views own history | Low |
| Expert | Manages symptoms, problems, rules, advice | Medium |
| Administrator | Manages users and oversees all data | High |

### 2.3 Operating Environment
- Client: any modern web browser on desktop or mobile.
- Server: Java runtime with a REST framework.
- Database: relational SQL database.

### 2.4 Assumptions and Dependencies
- Users have a device with a browser and an internet connection.
- Expert knowledge is available to define accurate rules.
- Symptoms are chosen from a predefined list, not typed freely.

---

## 3. Functional Requirements

### 3.1 User Account and Access

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | The system shall allow a farmer to register with name, username/email, and password. | High |
| FR-02 | The system shall allow registered users to log in and log out. | High |
| FR-03 | The system shall assign each user one role: Farmer, Expert, or Administrator. | High |
| FR-04 | The system shall restrict each function to the roles allowed to use it. | High |
| FR-05 | The system shall allow users to view and update their own profile. | Medium |
| FR-06 | The system shall allow users to change their password. | Medium |

### 3.2 Crop Problem Analysis

| ID | Requirement | Priority |
|---|---|---|
| FR-07 | The system shall display the list of supported crops. | High |
| FR-08 | The system shall display the symptoms relevant to the selected crop. | High |
| FR-09 | The system shall allow a farmer to select one or more symptoms. | High |
| FR-10 | The system shall match the crop and selected symptoms against the stored rules. | High |
| FR-11 | The system shall return the probable problem(s), ordered by how well they match. | High |
| FR-12 | The system shall display the cause, treatment, and prevention advice for each result. | High |
| FR-13 | The system shall show a clear message when no rule matches, suggesting contact with an expert. | High |
| FR-14 | The system shall show how many selected symptoms matched each result (match level). | Medium |
| FR-15 | The system shall require at least one symptom before an analysis can be submitted. | High |

### 3.3 History

| ID | Requirement | Priority |
|---|---|---|
| FR-16 | The system shall save each analysis (user, crop, symptoms, result, date/time). | High |
| FR-17 | The system shall allow a farmer to view their own analysis history. | High |
| FR-18 | The system shall allow a farmer to open a past analysis and see its full result. | Medium |
| FR-19 | The system shall allow a farmer to delete items from their own history. | Low |

### 3.4 Knowledge Base Management (Expert / Administrator)

| ID | Requirement | Priority |
|---|---|---|
| FR-20 | The system shall allow experts to add, edit, and delete crops. | High |
| FR-21 | The system shall allow experts to add, edit, and delete symptoms. | High |
| FR-22 | The system shall allow experts to add, edit, and delete problems (disease, pest, deficiency). | High |
| FR-23 | The system shall allow experts to add, edit, and delete advice linked to a problem. | High |
| FR-24 | The system shall allow experts to create and edit rules linking a crop and symptoms to a problem. | High |
| FR-25 | The system shall prevent deletion of an item that is used by existing rules, or warn before cascading. | Medium |
| FR-26 | The system shall validate that a rule contains a crop, at least one symptom, and a problem. | High |
| FR-27 | The system shall allow experts to search and filter knowledge base items. | Low |

### 3.5 Administration

| ID | Requirement | Priority |
|---|---|---|
| FR-28 | The system shall allow the administrator to view all users. | High |
| FR-29 | The system shall allow the administrator to create, deactivate, and delete user accounts. | High |
| FR-30 | The system shall allow the administrator to change a user's role. | Medium |
| FR-31 | The system shall allow the administrator to view all analyses for monitoring purposes. | Medium |
| FR-32 | The system shall provide basic statistics (e.g., most frequent problems, analyses per crop). | Low |

### 3.6 Optional Features (if time allows)

| ID | Requirement | Priority |
|---|---|---|
| FR-33 | The system may support a second interface language. | Low |
| FR-34 | The system may let farmers send feedback on whether the advice helped. | Low |
| FR-35 | The system may let users print or download an analysis result. | Low |

---

## 4. Non-Functional Requirements

### 4.1 Performance

| ID | Requirement |
|---|---|
| NFR-01 | An analysis result shall be displayed within 3 seconds under normal load. |
| NFR-02 | Pages shall load within 3 seconds on a standard broadband connection. |
| NFR-03 | The system shall support at least 50 concurrent users without failure. |

### 4.2 Security

| ID | Requirement |
|---|---|
| NFR-04 | Passwords shall be stored as salted hashes, never as plain text. |
| NFR-05 | All protected functions shall require authentication and role authorization on the server side. |
| NFR-06 | All user input shall be validated on both client and server. |
| NFR-07 | The system shall prevent SQL injection (use prepared statements/parameterized queries). |
| NFR-08 | The system shall prevent cross-site scripting by escaping output. |
| NFR-09 | The system should use HTTPS when deployed. |
| NFR-10 | Sessions or tokens shall expire after a period of inactivity. |

### 4.3 Usability

| ID | Requirement |
|---|---|
| NFR-11 | The interface shall be simple enough for a first-time farmer to complete an analysis without training. |
| NFR-12 | The system shall use clear language and avoid technical jargon in results and messages. |
| NFR-13 | The interface shall be responsive and usable on both phone and desktop screens. |
| NFR-14 | Error messages shall explain what went wrong and what the user can do next. |

### 4.4 Reliability and Availability

| ID | Requirement |
|---|---|
| NFR-15 | The system shall handle invalid input and errors without crashing. |
| NFR-16 | Database operations that change several tables shall use transactions to keep data consistent. |
| NFR-17 | The system shall be available at least 95% of the time during the demonstration period. |

### 4.5 Maintainability and Portability

| ID | Requirement |
|---|---|
| NFR-18 | The code shall follow a layered structure (controller, service, repository, model). |
| NFR-19 | Rules and advice shall be stored in the database so experts can change them without changing the code. |
| NFR-20 | The system shall run in any modern browser (Chrome, Firefox, Edge). |
| NFR-21 | Setup and run instructions shall be documented in the README. |

### 4.6 Data

| ID | Requirement |
|---|---|
| NFR-22 | The database shall enforce integrity through primary keys, foreign keys, and constraints. |
| NFR-23 | The system shall store personal data only as needed (name, contact, credentials). |

---

## 5. Business Rules

| ID | Rule |
|---|---|
| BR-01 | Only experts and administrators may change crops, symptoms, problems, rules, and advice. |
| BR-02 | A farmer may view only their own history. |
| BR-03 | Every rule must link one crop, one or more symptoms, and one problem. |
| BR-04 | Every problem must have at least one piece of advice before it can be used in a rule. |
| BR-05 | Match level is the share of a rule's symptoms that the user selected; results are ranked by it. |
| BR-06 | Deactivated users cannot log in, but their history is kept. |

---

## 6. External Interface Requirements

### 6.1 User Interface
- Pages: Home, Register, Login, Analysis, Result, History, Knowledge Base Management, User Management.
- Consistent navigation and layout across pages.

### 6.2 Software Interface
- Frontend communicates with the backend through REST endpoints using JSON over HTTP(S).
- Backend communicates with the database through JDBC or an ORM.

### 6.3 Hardware Interface
- No special hardware. Standard device with a browser.

---

## 7. Requirement Traceability (Summary)

| Objective | Requirements |
|---|---|
| Identify crop problems from symptoms | FR-07 to FR-15 |
| Provide treatment and prevention advice | FR-12, FR-13, FR-23 |
| Maintain the knowledge base | FR-20 to FR-27, NFR-19 |
| Record analysis history | FR-16 to FR-19 |
| Manage users and roles | FR-01 to FR-06, FR-28 to FR-31 |
| Secure and reliable operation | NFR-04 to NFR-10, NFR-15 to NFR-17 |

---

## 8. Acceptance Criteria (Summary)

1. A farmer can register, log in, select a crop and symptoms, and see a result with advice.
2. An expert can add a new rule and see it used in the next analysis without a code change.
3. An unauthorized user cannot open expert or administrator pages.
4. Invalid or empty input is rejected with a clear message.
5. Every High-priority requirement passes its test case in `06-testing/test-cases.md`.
