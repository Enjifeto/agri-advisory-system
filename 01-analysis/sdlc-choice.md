# SDLC Model Choice

**Project:** Agricultural Problem Analysis and Advisory System
**Course:** [Course name]
**Prepared by:** [Your name / team members]
**Date:** [Date]
**Version:** 1.0

---

## 1. Purpose

This document explains which Software Development Life Cycle (SDLC) model the project follows and why. It compares the main models against the needs of this project, states the decision, and shows how the chosen model maps onto the project folders and schedule.

---

## 2. Project Characteristics That Affect the Choice

| Characteristic | Description | Effect on model choice |
|---|---|---|
| Requirements | Mostly clear from the start (crop, symptoms, rules, advice, three user roles), but details may change after expert or user feedback. | Needs some flexibility. |
| Size | Small to medium, with a small team. | Heavy process is unnecessary. |
| Time | Fixed course deadline. | Needs early, working results. |
| Technology | Known stack: Java, SQL, HTML/CSS/JavaScript. | Low technical uncertainty. |
| Users | Farmers, experts, administrators. | Feedback is valuable. |
| Documentation | Course requires analysis and design documents and UML. | Needs a documented process. |
| Risk | Main risk is rule accuracy and scope growth. | Needs frequent checking and control of scope. |

---

## 3. Models Considered

### 3.1 Waterfall
Phases run in strict order: requirements → design → implementation → testing → deployment. Each phase finishes before the next begins.

| Strengths | Weaknesses |
|---|---|
| Simple and easy to manage | Changes are hard and costly late in the project |
| Strong documentation | Working software appears only at the end |
| Clear milestones | Problems found late in testing |

### 3.2 Agile (Scrum / iterative)
Work is split into short iterations. Each iteration delivers a small working part and gets feedback.

| Strengths | Weaknesses |
|---|---|
| Handles changing requirements | Needs discipline and regular review |
| Working software early and often | Can produce thin documentation if not controlled |
| Risks found early | Scope can grow without limits |

### 3.3 RAD (Rapid Application Development)
Uses fast prototyping and user feedback, with reusable components, to build quickly.

| Strengths | Weaknesses |
|---|---|
| Very fast delivery | Needs constant user involvement |
| Prototypes confirm needs early | Less suitable when design must be rigorous |
| Good for UI-heavy systems | Quality can suffer under speed pressure |

### 3.4 Spiral
Repeats cycles of planning, risk analysis, building, and evaluation.

| Strengths | Weaknesses |
|---|---|
| Strong risk management | Complex and expensive to run |
| Suits large, high-risk projects | Too heavy for a small course project |

---

## 4. Comparison

Scores: 1 = poor fit, 5 = excellent fit.

| Criterion | Waterfall | Agile | RAD | Spiral |
|---|:---:|:---:|:---:|:---:|
| Handles requirement changes | 1 | 5 | 4 | 4 |
| Early working software | 1 | 5 | 5 | 3 |
| Fit for small team | 4 | 5 | 4 | 2 |
| Fixed deadline | 3 | 4 | 5 | 2 |
| Supports required documentation | 5 | 3 | 2 | 4 |
| Risk management | 2 | 4 | 3 | 5 |
| Simplicity | 5 | 4 | 4 | 2 |
| **Total (out of 35)** | **21** | **30** | **27** | **22** |

The scores are the team's judgment based on the project characteristics in section 2.

---

## 5. Decision

**Chosen model: Agile-style iterative development, with a short Waterfall-style start for analysis and design.**

In practice this is a hybrid:

1. **Phases 1 and 2 (Analysis and Design) are done up front, in order,** like Waterfall. The course requires documents and UML, and a clear design avoids rework.
2. **Phases 3 to 5 (Database, Backend, Frontend) are built in short iterations,** like Agile. Each iteration delivers one small working feature.
3. **Testing runs inside every iteration,** with a final full test at the end.
4. **A simple prototype of the main screens is shown early for feedback,** borrowing from RAD.

### Why this choice

- Requirements are mostly clear but may change after expert feedback on the rules. Iterations absorb those changes cheaply.
- Working software appears early, so problems are found while there is still time to fix them.
- Up-front analysis and design satisfy the course's documentation and modeling needs.
- The approach is light enough for a small team and a fixed deadline.
- Frequent small deliveries limit the main risks: wrong rules and scope growth.

### Why not the others

- **Waterfall alone:** too rigid, and working software would appear only at the end.
- **RAD alone:** needs constant user involvement and gives less attention to documentation.
- **Spiral:** too heavy for the size of this project.

---

## 6. How the Model Maps to the Project

| Phase | Folder | Approach |
|---|---|---|
| 1. Analysis | `01-analysis` | Up front, documented |
| 2. Design | `02-design` | Up front, documented (UML, rule base, wireframes, architecture) |
| 3. Database | `03-database` | Iteration 1 |
| 4. Backend | `04-backend` | Iterations 2 to 4 |
| 5. Frontend | `05-frontend` | Iterations 3 to 5, alongside the backend |
| 6. Testing | `06-testing` | Inside every iteration, plus final system test |
| 7. Documentation | `07-documentation` | Updated during each phase, finalized at the end |

---

## 7. Iteration Plan

Each iteration ends with a working, tested feature. Adjust the number of days to your deadline (see `08-progress/daily-plan.md`).

| Iteration | Goal | Main requirements | Done when |
|---|---|---|---|
| **1. Foundation** | Database schema and sample data (3 to 5 crops, symptoms, problems, advice, rules) | NFR-22, NFR-19 | Tables created and seed data loads |
| **2. Analysis core** | Rule engine and REST endpoints for crops, symptoms, and analysis | FR-07 to FR-15 | An analysis request returns a correct result via API |
| **3. Analysis UI** | Pages for choosing a crop and symptoms and showing the result | FR-07 to FR-14, NFR-11 to NFR-13 | A user completes an analysis in the browser |
| **4. Accounts and history** | Registration, login, roles, and history | FR-01 to FR-06, FR-16 to FR-18, NFR-04, NFR-05 | Users log in and see only their own history |
| **5. Knowledge management** | Expert and admin screens for crops, symptoms, problems, rules, advice, and users | FR-20 to FR-26, FR-28 to FR-30 | An expert adds a rule that works in the next analysis |
| **6. Polish and release** | Bug fixes, security checks, final testing, documentation, presentation | NFR-06 to NFR-10, all High requirements | All High-priority test cases pass |

### Rules for each iteration
1. Pick only the requirements listed for that iteration.
2. Build, then test before moving on.
3. Commit to Git when the feature works.
4. Record what was done in `08-progress/daily-log.md`.
5. If time runs short, drop Low-priority items first, never the High ones.

---

## 8. Controls for Scope and Quality

| Risk | Control |
|---|---|
| Scope grows | Keep requirements prioritized; Low-priority and optional items only after all High ones pass |
| Rules are wrong | Verify the rule base with an expert before and after Iteration 1 |
| Documentation falls behind | Update the related document at the end of each iteration |
| Late bugs | Test inside each iteration and keep test cases in `06-testing` |
| Lost work | Commit to Git after each working feature |

---

## 9. Review Points

| Point | Check |
|---|---|
| End of Phase 2 | Analysis and design documents complete and consistent |
| End of Iteration 3 | First end-to-end demo: crop → symptoms → result |
| End of Iteration 5 | All High-priority features present |
| End of Iteration 6 | All tests done, documents finalized, presentation ready |

---

## 10. Conclusion

An Agile-style iterative approach with a short, documented analysis and design phase fits this project best. It keeps the documentation and modeling the course expects, delivers working features early, absorbs changes to the rules, and keeps scope under control within a fixed deadline.
