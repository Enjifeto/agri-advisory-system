# Problem Statement

**Project:** Agricultural Problem Analysis and Advisory System
**Course:** [Course name]
**Prepared by:** [Your name / team members]
**Date:** [Date]
**Version:** 1.0

---

## 1. Background

Agriculture is the main source of food and income for millions of families, especially smallholder farmers. Crop production is constantly threatened by pests, plant diseases, nutrient deficiencies, and poor farming practices. When a problem appears in the field, the speed and quality of the response often decides whether the farmer saves the harvest or loses it.

In many farming communities, expert advice comes from agricultural extension officers, who serve large numbers of farmers over wide areas. A farmer often notices a problem long before an expert can visit.

## 2. Problem Description

Farmers face the following problems when their crops are affected:

1. **Difficulty identifying the problem.** Many diseases, pests, and deficiencies show similar symptoms (yellow leaves, spots, wilting), so farmers frequently misdiagnose them.
2. **Limited access to expert advice.** There are too few extension officers for the number of farmers. Visits are slow, infrequent, or unavailable.
3. **Delayed or wrong treatment.** Without a correct diagnosis, farmers apply the wrong remedy, apply it too late, or waste money on unnecessary inputs. This lowers yields and income.
4. **Scattered and unstructured knowledge.** Agricultural knowledge exists in manuals, training sessions, and experts' heads. It is not organized in one place where a farmer can quickly search it.
5. **No record of past problems.** Farmers and experts usually keep no history of crop problems, so recurring issues and local patterns go unnoticed.

## 3. Current System and Its Limitations

Currently, a farmer who notices a crop problem relies on personal experience, neighbors, or a visit from an extension officer. This manual process:

- is slow and depends on the expert's availability;
- gives inconsistent advice from person to person;
- cannot be accessed at any time or from any place;
- does not store data for later analysis.

## 4. Proposed Solution

This project proposes a **web-based, rule-driven Agricultural Problem Analysis and Advisory System**. The user selects a crop and the symptoms they observe. The system matches those inputs against a knowledge base of expert-defined rules (crop + symptoms → probable problem → recommended action) and returns the likely problem together with clear advice on treatment and prevention.

The system is **rule-based**. It does not use artificial intelligence or machine learning. Its logic is transparent and easy to verify, and agricultural experts can maintain it.

## 5. Objectives

### General Objective
To design and develop a web-based system that helps farmers identify crop problems and receive timely, reliable advice.

### Specific Objectives
- Collect and analyze the requirements of farmers, agricultural experts, and administrators.
- Design the system using UML models (use case, class, sequence, activity) and an ER diagram.
- Build a knowledge base of crops, symptoms, problems, and advice stored in a relational database.
- Implement a rule engine that maps selected symptoms to probable problems.
- Develop a Java REST backend and a web-based user interface.
- Allow experts or administrators to add, update, and delete rules and advice.
- Store each analysis request so farmers can review their history.
- Test the system for correctness, usability, and security.

## 6. Scope

### In Scope
- User registration and login with role-based access (Farmer, Expert, Administrator).
- Selecting a crop and symptoms for analysis.
- Rule-based identification of probable problems, with a ranked or matched result.
- Display of treatment and prevention advice.
- Management of crops, symptoms, problems, rules, and advice by experts/administrators.
- Viewing history of past analyses.
- Web access through a standard browser.

### Out of Scope
- Artificial intelligence, machine learning, or image-based diagnosis.
- Real-time sensor or IoT data integration.
- Weather forecasting and market price prediction.
- Online payment or marketplace functions.
- Native mobile applications.

## 7. Stakeholders and Users

| Stakeholder | Role / Interest |
|---|---|
| Farmers | Primary users. Need fast, understandable advice on crop problems. |
| Agricultural experts | Provide and maintain the knowledge (rules and advice). |
| System administrator | Manages users, data, and system settings. |
| Extension offices / institutions | Benefit from reduced workload and consistent advice. |
| Course instructor | Evaluates the analysis, design, and implementation. |

## 8. Constraints and Assumptions

**Constraints**
- The project must be completed within the course timeline.
- Technologies: Java (REST backend), HTML/CSS/JavaScript (optionally React), and a relational SQL database.
- The knowledge base is limited to a selected set of crops and common problems.

**Assumptions**
- Farmers or their assistants have access to a device with a browser and an internet connection.
- Agricultural expertise (sources or expert input) is available to define accurate rules.
- Users can describe symptoms by selecting from a predefined list.

## 9. Expected Benefits

- **Faster diagnosis**, available at any time without waiting for a visit.
- **Better decisions**, with correct treatment that reduces crop loss and wasted inputs.
- **Consistent advice** based on expert-defined rules.
- **Preserved knowledge** in a structured, reusable, and updatable form.
- **Useful records** that show recurring problems over time.

## 10. Success Criteria

The project will be considered successful if:

1. A user can select a crop and symptoms and receive a relevant diagnosis with advice in a few seconds.
2. Experts or administrators can manage the knowledge base without changing the code.
3. The system correctly returns the expected result for all prepared test cases.
4. Access is restricted properly by user role, and passwords and inputs are handled securely.
5. All required analysis, design, and testing documents are completed.

## 11. Problem Statement (Summary)

> Farmers lack quick and reliable access to expert knowledge when their crops are attacked by diseases, pests, or nutrient problems. This causes misdiagnosis, delayed treatment, reduced yields, and financial loss. There is a need for an accessible, web-based system that analyzes reported crop symptoms against expert-defined rules and provides clear, actionable advice, while keeping a structured and maintainable record of agricultural knowledge.
