# Stakeholders and Users

**Project:** Agricultural Problem Analysis and Advisory System
**Course:** [Course name]
**Prepared by:** [Your name / team members]
**Date:** [Date]
**Version:** 1.0

---

## 1. Purpose

This document identifies everyone who is affected by, or has an interest in, the Agricultural Problem Analysis and Advisory System. It separates **users** (people who operate the system) from other **stakeholders** (people who are affected by it or influence it), and it describes what each group needs. These needs feed directly into `requirements.md` and the use case diagram.

---

## 2. Stakeholder Overview

| # | Stakeholder | Type | Influence | Interest |
|---|---|---|---|---|
| 1 | Farmers | Primary user | Medium | High |
| 2 | Agricultural experts | Primary user | High | High |
| 3 | System administrator | Primary user | High | High |
| 4 | Agricultural extension offices | Indirect | Medium | Medium |
| 5 | Agricultural institutions / government bodies | Indirect | Medium | Low |
| 6 | Project team (developers) | Internal | High | High |
| 7 | Course instructor | Evaluator | High | High |
| 8 | Consumers and local community | Indirect | Low | Low |

**Types:** *Primary user* = uses the system directly. *Indirect* = affected by the results. *Internal* = builds the system. *Evaluator* = judges the project.

---

## 3. User Profiles

### 3.1 Farmer

| Item | Description |
|---|---|
| **Who** | Smallholder or commercial farmers and their family members or assistants who grow crops. |
| **Goal** | Quickly find out what is wrong with a crop and what to do about it. |
| **Technical skill** | Low. May use a phone more than a computer. |
| **Education level** | Varies. Some users read with difficulty. |
| **Frequency of use** | Occasional, mostly during the growing season or when a problem appears. |
| **Device** | Mainly smartphone; sometimes shared computer. |
| **Connectivity** | Possibly slow or unstable internet. |

**Main tasks**
- Register and log in
- Choose a crop and symptoms
- Read the diagnosis and advice
- View past analyses

**Needs**
- Simple screens with few steps
- Plain language, no technical jargon
- Fast results
- Clear advice they can act on

**Pain points**
- Cannot name the disease or pest
- Waits too long for an expert
- Unsure which treatment to buy or apply

**Related requirements:** FR-01 to FR-19, NFR-01, NFR-11 to NFR-14

---

### 3.2 Agricultural Expert

| Item | Description |
|---|---|
| **Who** | Agronomists, plant pathologists, extension officers, or other people with crop protection knowledge. |
| **Goal** | Keep the knowledge base accurate and complete so farmers get correct advice. |
| **Technical skill** | Medium. Comfortable with forms and web tools. |
| **Frequency of use** | Regular, when adding or reviewing knowledge. |
| **Device** | Desktop or laptop. |

**Main tasks**
- Add, edit, and delete crops, symptoms, problems, and advice
- Create and update rules linking symptoms to problems
- Review how the rules perform

**Needs**
- Easy forms for managing knowledge, without touching code
- Validation that prevents incomplete or conflicting rules
- Ability to search and filter existing entries

**Pain points**
- Knowledge is scattered and not recorded in one place
- Hard to keep advice consistent across many farmers

**Related requirements:** FR-20 to FR-27, BR-01, BR-03, BR-04, NFR-19

---

### 3.3 System Administrator

| Item | Description |
|---|---|
| **Who** | The person responsible for running and maintaining the system. |
| **Goal** | Keep the system secure, available, and correctly configured. |
| **Technical skill** | High. |
| **Frequency of use** | Regular, for account and data oversight. |
| **Device** | Desktop or laptop. |

**Main tasks**
- Create, deactivate, and delete user accounts
- Assign and change roles
- Monitor analyses and system data
- View basic statistics
- Back up and maintain the database

**Needs**
- Full control of accounts and roles
- Overview of system activity
- Reliable backup and recovery

**Pain points**
- Unauthorized access risk
- Data loss or corruption

**Related requirements:** FR-28 to FR-32, NFR-04 to NFR-10, NFR-16, NFR-17

---

## 4. Other Stakeholders

| Stakeholder | What they want from the system | How they affect the project |
|---|---|---|
| **Extension offices** | Less repeated routine work, consistent advice across farmers. | Can supply expert knowledge and field feedback. |
| **Institutions / government bodies** | Better crop protection and food security; data on common problems. | May provide agricultural guidelines and approved treatments. |
| **Project team** | A working, well-documented system delivered on time. | Designs, builds, and tests the system. |
| **Course instructor** | Correct use of analysis, design, and development methods. | Sets requirements and grades the project. |
| **Consumers / community** | Stable, safe food supply. | Benefit from reduced crop losses; no direct control. |

---

## 5. Stakeholder Needs Summary

| Stakeholder | Key need | How the system responds |
|---|---|---|
| Farmer | Fast, understandable diagnosis | Symptom selection and rule-based result with advice |
| Expert | Easy knowledge management | Management screens for crops, symptoms, problems, rules, advice |
| Administrator | Control and security | User and role management, monitoring, secure authentication |
| Extension office | Consistent advice | Shared knowledge base used by all farmers |
| Instructor | Complete, well-modeled project | Full documentation set and UML models |

---

## 6. Role and Permission Matrix

| Function | Farmer | Expert | Administrator |
|---|:---:|:---:|:---:|
| Register / log in | ✔ | ✔ | ✔ |
| Update own profile | ✔ | ✔ | ✔ |
| Run crop analysis | ✔ | ✔ | ✔ |
| View own history | ✔ | ✔ | ✔ |
| View other users' history | ✘ | ✘ | ✔ |
| Manage crops, symptoms, problems | ✘ | ✔ | ✔ |
| Manage rules and advice | ✘ | ✔ | ✔ |
| Manage user accounts and roles | ✘ | ✘ | ✔ |
| View system statistics | ✘ | ✘ | ✔ |

---

## 7. Design Implications

These user characteristics lead to the following design decisions:

1. **Mobile-first, responsive interface**, because most farmers use phones.
2. **Selection lists instead of typing**, because symptom names are hard to spell and describe freely.
3. **Short flow:** crop → symptoms → result, in as few screens as possible.
4. **Plain, short language** in results and error messages.
5. **Lightweight pages** that load quickly on slow connections.
6. **Role-based access control on the server**, because three user types see different functions.
7. **Management screens for experts** so knowledge changes never require code changes.
8. **Optional second language** if the target farmers use a local language.

---

## 8. Communication and Feedback Plan

| Group | Method | When |
|---|---|---|
| Farmers (sample) | Short interview or survey on needs; trial of the prototype | Analysis phase and before final delivery |
| Experts | Interview to confirm rules and advice accuracy | During rule base creation and testing |
| Instructor | Progress review and feedback | At each phase milestone |
| Project team | Daily log and short progress check | Daily (see `08-progress/`) |

---

## 9. Risks Related to Users

| Risk | Impact | Mitigation |
|---|---|---|
| Farmers find the system too complex | Low adoption | Simple UI, test with real users, short flow |
| Farmers select wrong symptoms | Wrong diagnosis | Clear symptom names, ranked results with match level, show alternatives |
| Experts provide incomplete knowledge | Poor advice | Validation rules, expert review before release |
| Advice is trusted blindly | Wrong treatment in edge cases | Show a note advising consultation with an extension officer for serious cases |
| Weak internet for farmers | System seems slow or fails | Lightweight pages, clear error messages |
