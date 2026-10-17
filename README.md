# 🌾 Agricultural Problem Analysis and Advisory System

A web-based, rule-driven system that helps farmers identify crop problems and get clear treatment and prevention advice. The farmer selects a crop and the symptoms they see. The system matches them against expert-defined rules and returns the probable problem with advice.

> **Course project:** [Course name] | **Team:** [Your name / team members] | **Instructor:** [Instructor name]
> **Status:** 🚧 In development

---

## 📌 Table of Contents

1. [Problem](#-problem)
2. [Features](#-features)
3. [How It Works](#-how-it-works)
4. [Technology Stack](#-technology-stack)
5. [Project Structure](#-project-structure)
6. [Getting Started](#-getting-started)
7. [User Roles](#-user-roles)
8. [API Overview](#-api-overview)
9. [Documentation](#-documentation)
10. [Development Process](#-development-process)
11. [Testing](#-testing)
12. [Limitations and Future Work](#-limitations-and-future-work)
13. [Team](#-team)

---

## ❓ Problem

Farmers often cannot identify what is wrong with their crops. Many diseases, pests, and nutrient problems look alike, and expert help is slow to reach them. This leads to wrong treatment, delays, and lost harvests. This system gives quick, consistent, expert-based advice at any time. See `01-analysis/problem-statement.md` for details.

## ✨ Features

**For farmers**
- Register and log in
- Choose a crop and the symptoms observed
- Get the probable problem, ranked by match level
- Read treatment and prevention advice
- View past analyses

**For experts**
- Manage crops, symptoms, problems, and advice
- Create and edit the rules that link symptoms to problems

**For administrators**
- Manage user accounts and roles
- Monitor analyses and view basic statistics

## ⚙️ How It Works

```
Farmer selects crop + symptoms
            │
            ▼
   Frontend sends request (REST / JSON)
            │
            ▼
   Backend rule engine compares symptoms with stored rules
            │
            ▼
   Matching problems ranked by match level
            │
            ▼
   Problem + treatment + prevention advice shown, and saved to history
```

The system is **rule-based**. It does not use AI or machine learning, so its results are transparent and easy for experts to verify and update.

## 🛠 Technology Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript (optionally React) |
| Backend | Java, REST API |
| Database | Relational SQL database (e.g., MySQL or PostgreSQL) |
| Build tool | Maven |
| Modeling | UML (use case, class, sequence, activity) and ER diagram |
| Version control | Git |

## 📁 Project Structure

```
agri-advisory-system/
├── 01-analysis/        Problem statement, requirements, stakeholders, feasibility, SDLC choice
├── 02-design/          UML diagrams, rule base, wireframes, architecture
├── 03-database/        schema.sql, seed-data.sql, queries.sql
├── 04-backend/         Java REST backend (controller, service, model, repository)
├── 05-frontend/        Web user interface
├── 06-testing/         Test plan, test cases, test results
├── 07-documentation/   Final report, presentation, user manual, screenshots
└── 08-progress/        Daily plan and daily log
```

## 🚀 Getting Started

### Prerequisites

Install the following before you start:

- **Java JDK** [version, e.g., 17 or higher]
- **Maven**
- **Database server** [MySQL / PostgreSQL]
- **A modern web browser** (Chrome, Firefox, or Edge)
- **Git**

### 1. Get the code

```bash
git clone [repository-url]
cd agri-advisory-system
```

### 2. Set up the database

1. Create an empty database:
   ```sql
   CREATE DATABASE agri_advisory;
   ```
2. Load the tables and sample data:
   ```bash
   # Replace the command with your database client
   mysql -u [username] -p agri_advisory < 03-database/schema.sql
   mysql -u [username] -p agri_advisory < 03-database/seed-data.sql
   ```

### 3. Configure the backend

Open `04-backend/src/main/resources/application.properties` and set your database details:

```properties
# Example. Adjust the keys to match the framework you use.
db.url=jdbc:mysql://localhost:3306/agri_advisory
db.username=[your-username]
db.password=[your-password]
server.port=8080
```

> ⚠️ Never commit real passwords to Git. Keep your local credentials out of the repository (see `.gitignore`).

### 4. Run the backend

```bash
cd 04-backend
mvn clean install
mvn exec:java        # or: mvn spring-boot:run (if you use Spring Boot)
```

The API should now be available at `http://localhost:8080`.

### 5. Run the frontend

Open `05-frontend/index.html` in your browser, or serve the folder with a simple local server:

```bash
cd 05-frontend
python -m http.server 3000
```

Then visit `http://localhost:3000`.

*(If you use React: run `npm install` then `npm start` inside `05-frontend` instead.)*

### Default test accounts

| Role | Username | Password |
|---|---|---|
| Administrator | [admin] | [set in seed-data.sql] |
| Expert | [expert] | [set in seed-data.sql] |
| Farmer | [farmer] | [set in seed-data.sql] |

> Use these only for testing and demonstration. Remove or change them before any real deployment.

## 👥 User Roles

| Function | Farmer | Expert | Administrator |
|---|:---:|:---:|:---:|
| Run crop analysis | ✔ | ✔ | ✔ |
| View own history | ✔ | ✔ | ✔ |
| Manage crops, symptoms, problems | ✘ | ✔ | ✔ |
| Manage rules and advice | ✘ | ✔ | ✔ |
| Manage users and roles | ✘ | ✘ | ✔ |
| View system statistics | ✘ | ✘ | ✔ |

## 🔌 API Overview

> Planned endpoints. The final list is in `02-design/architecture.md`.

| Method | Endpoint | Purpose | Access |
|---|---|---|---|
| POST | `/api/auth/register` | Register a farmer | Public |
| POST | `/api/auth/login` | Log in | Public |
| GET | `/api/crops` | List crops | Logged-in users |
| GET | `/api/crops/{id}/symptoms` | List symptoms for a crop | Logged-in users |
| POST | `/api/analysis` | Submit crop and symptoms, get result | Logged-in users |
| GET | `/api/analysis/history` | View own analysis history | Logged-in users |
| POST/PUT/DELETE | `/api/crops`, `/api/symptoms`, `/api/problems`, `/api/rules` | Manage knowledge base | Expert, Admin |
| GET/POST/PUT/DELETE | `/api/users` | Manage users | Admin |

## 📚 Documentation

| Document | Location |
|---|---|
| Problem statement | `01-analysis/problem-statement.md` |
| Requirements | `01-analysis/requirements.md` |
| Stakeholders and users | `01-analysis/stakeholders-and-users.md` |
| Feasibility study | `01-analysis/feasibility-study.md` |
| SDLC choice | `01-analysis/sdlc-choice.md` |
| UML and ER diagrams | `02-design/uml/` |
| Rule base | `02-design/rules/rule-base.md` |
| Architecture | `02-design/architecture.md` |
| Test plan and cases | `06-testing/` |
| Final report and user manual | `07-documentation/` |

## 🔄 Development Process

The project follows an **Agile-style iterative approach** with a documented analysis and design phase up front. Work is delivered in short iterations, and each one ends with a tested, working feature. Progress is tracked in `08-progress/`. See `01-analysis/sdlc-choice.md`.

## 🧪 Testing

Test cases are written from the requirements and recorded in `06-testing/`.

```bash
cd 04-backend
mvn test
```

## ⚠️ Limitations and Future Work

**Current limitations**
- Covers only a limited set of crops and common problems
- Rule-based only, so it cannot diagnose from photos or unknown symptoms
- Advice is a guide and does not replace an agricultural expert for serious cases

**Possible future work**
- More crops, problems, and rules
- Additional interface languages
- Image-based diagnosis
- Weather and season-aware advice
- Mobile app

## 👨‍💻 Team

| Name | Role | Contact |
|---|---|---|
| [Name] | [e.g., Backend] | [email] |
| [Name] | [e.g., Frontend] | [email] |
| [Name] | [e.g., Database and documentation] | [email] |

## 🙏 Acknowledgements

- [Instructor name] for guidance
- [Agricultural experts or sources used for the rule base]

## 📄 License

This project was created for educational purposes as part of [Course name]. [Add a license if you plan to share the code publicly.]
