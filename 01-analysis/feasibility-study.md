# Feasibility Study

**Project:** Agricultural Problem Analysis and Advisory System
**Course:** [Course name]
**Prepared by:** [Your name / team members]
**Date:** [Date]
**Version:** 1.0

---

## 1. Purpose

This study checks whether the proposed system can be successfully built and used. It examines six aspects of feasibility (technical, economic, operational, schedule, legal and ethical, and social), compares alternatives, and ends with a recommendation. The goal is to decide whether the project should proceed before design and development begin.

---

## 2. Project Summary

The system is a web-based, rule-driven application. A farmer selects a crop and the symptoms observed. The system matches them against expert-defined rules and returns the probable problem with treatment and prevention advice. Experts and administrators maintain the knowledge base. The system uses a Java REST backend, an HTML/CSS/JavaScript (optionally React) frontend, and a relational SQL database.

---

## 3. Technical Feasibility

**Question:** Do we have the technology and skills to build it?

### 3.1 Technology Assessment

| Component | Choice | Available? | Notes |
|---|---|---|---|
| Backend | Java (REST) | Yes | Mature language, free tools, large community. Course-aligned. |
| Frontend | HTML, CSS, JavaScript (optionally React) | Yes | Runs in any browser, no installation for users. |
| Database | Relational SQL (e.g., MySQL, PostgreSQL) | Yes | Free, suited to structured crop, symptom, and rule data. |
| Logic | Rule-based matching | Yes | Simple to implement with database queries and service code. No AI/ML needed. |
| Modeling | UML tools (e.g., draw.io, StarUML) | Yes | Free options exist. |
| Version control | Git | Yes | Free. |

### 3.2 Skills Assessment

| Skill needed | Level in team | Gap and plan |
|---|---|---|
| Java and REST | [Rate yourself] | Learn through course material and tutorials. |
| SQL and database design | [Rate yourself] | Apply course database knowledge. |
| HTML/CSS/JavaScript | [Rate yourself] | Start plain, add React only if time allows. |
| UML and systems analysis | [Rate yourself] | Taught in course. |

### 3.3 Technical Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Rule engine becomes complex | Medium | Medium | Keep matching simple: count matched symptoms per rule. |
| Frontend-backend integration errors | Medium | Medium | Define REST endpoints early in `architecture.md`. |
| Learning curve for new tools | Medium | Medium | Use familiar tools, build in small steps. |
| Lack of reliable agricultural data | Medium | High | Use trusted sources and ask an expert to verify the rule base. |

**Conclusion:** Technically feasible. All tools are free, proven, and match the course.

---

## 4. Economic Feasibility

**Question:** Do the benefits justify the costs?

### 4.1 Estimated Costs

| Item | Cost | Notes |
|---|---|---|
| Software (Java JDK, IDE, database, Git, UML tool) | Free | Open-source or free tiers. |
| Hardware | Existing computers | No purchase needed. |
| Hosting (development) | Free | Runs on local machine. |
| Hosting (real deployment, optional) | Low | Small server or free-tier cloud service. |
| Internet | Existing | Needed for research and testing. |
| Development effort | Team time | Main real cost. |
| Domain knowledge | Expert time | Needed for rule verification, often free from instructors or extension staff. |

**Total cash cost for the course project: close to zero.**

### 4.2 Benefits

**Tangible**
- Less crop loss through faster, correct diagnosis.
- Less money wasted on wrong treatments.
- Less routine workload for extension officers.

**Intangible**
- Easier access to expert knowledge.
- More consistent advice.
- A preserved and reusable knowledge base.
- Records that reveal recurring local problems.
- Team gains practical experience in the full development cycle.

### 4.3 Cost-Benefit Summary

The cash cost is almost zero and the benefits are large for farmers and advisers, so the project is economically feasible. For a real deployment, ongoing costs (hosting, expert time to update rules) are small compared with the value of preventing crop loss.

**Conclusion:** Economically feasible.

---

## 5. Operational Feasibility

**Question:** Will the system work in practice and will people use it?

| Factor | Assessment |
|---|---|
| Fits user needs | Directly addresses misdiagnosis and delayed advice (see `problem-statement.md`). |
| Ease of use | Selection lists, short flow, and plain language suit low-skill users. |
| Device access | Mobile-friendly design suits smartphone use. |
| Connectivity | Lightweight pages reduce problems on slow connections. |
| Maintenance | Experts update rules through the interface, with no code changes. |
| Training needed | Minimal for farmers, short for experts and administrators. |
| Acceptance | Likely good if advice is accurate and the interface is simple. |

### Operational Risks

| Risk | Mitigation |
|---|---|
| Farmers choose wrong symptoms | Clear symptom names, ranked results showing match level. |
| Users distrust software advice | Use expert-verified rules and show a note to consult an extension officer for serious cases. |
| Poor connectivity | Lightweight pages and clear error messages. |
| Knowledge becomes outdated | Provide expert management screens and review rules regularly. |

**Conclusion:** Operationally feasible.

---

## 6. Schedule Feasibility

**Question:** Can it be completed in the available time?

| Phase | Folder | Estimated effort |
|---|---|---|
| Analysis | `01-analysis` | [X days] |
| Design (UML, rules, wireframes, architecture) | `02-design` | [X days] |
| Database | `03-database` | [X days] |
| Backend | `04-backend` | [X days] |
| Frontend | `05-frontend` | [X days] |
| Testing | `06-testing` | [X days] |
| Documentation and presentation | `07-documentation` | [X days] |
| **Total** | | **[Total days] of [Available days]** |

Fill in the days based on your deadline. The detailed plan is in `08-progress/daily-plan.md`.

### Schedule Risks and Controls

| Risk | Mitigation |
|---|---|
| Scope grows too large | Fix scope early, build High-priority requirements first, treat Low-priority and optional items as extras. |
| Underestimated coding time | Start the backend and database early, build in small tested steps. |
| Last-minute documentation | Write documents during each phase and keep a daily log. |
| Small team size | Limit crops and rules to a manageable set (for example, 3 to 5 crops). |

**Conclusion:** Feasible if the scope is controlled and the High-priority requirements come first.

---

## 7. Legal and Ethical Feasibility

| Area | Assessment |
|---|---|
| Software licensing | All chosen tools are free or open-source for educational use. |
| Data protection | Store only needed personal data. Hash passwords. Restrict access by role. |
| Agricultural content | Use rules from trusted, citable sources. Avoid recommending restricted or unsafe chemicals. |
| Accuracy and liability | Show that advice is a guide and that serious cases need an expert. |
| Intellectual property | Credit all sources and use no copied proprietary material. |

**Conclusion:** No legal or ethical barrier, provided sources are credited and a clear advice disclaimer is shown.

---

## 8. Social and Environmental Feasibility

- **Positive impact:** helps farmers protect income and food supply.
- **Inclusion:** simple language and mobile access widen reach. A local language option would help more.
- **Environmental:** correct diagnosis reduces unnecessary pesticide and fertilizer use, which reduces harm to soil and water.
- **Risk:** the digital divide may limit users without phones or internet. Extension officers can act as intermediaries.

**Conclusion:** Socially and environmentally beneficial.

---

## 9. Alternatives Considered

| Option | Advantages | Disadvantages | Decision |
|---|---|---|---|
| **A. Keep the manual process** (visits, neighbors) | No development cost. | Slow, inconsistent, limited reach, no records. | Rejected |
| **B. Printed guide or static website** | Cheap and simple. | Hard to search by symptom, no history, no management, cannot give ranked results. | Rejected |
| **C. Rule-based web system (proposed)** | Fast, transparent, expert-maintainable, stores history, fits course scope. | Needs development effort and expert input; limited to known rules. | **Selected** |
| **D. AI/ML image-based diagnosis** | Powerful, can use photos. | Needs large datasets, heavy skills and computing, out of course scope. | Rejected for now (possible future work) |

---

## 10. Risk Summary

| Risk | Area | Level | Response |
|---|---|---|---|
| Incorrect or incomplete rules | Technical / Operational | High | Verify with an expert, cite sources, add disclaimer. |
| Scope creep | Schedule | High | Prioritize requirements, freeze scope early. |
| Skill gaps | Technical | Medium | Learn incrementally, use simple tools first. |
| Integration problems | Technical | Medium | Define REST endpoints early, test often. |
| Low user adoption | Operational | Medium | Simple, mobile-friendly design and user testing. |
| Poor internet access | Operational | Medium | Lightweight pages, clear errors. |

---

## 11. Overall Conclusion and Recommendation

| Feasibility area | Result |
|---|---|
| Technical | Feasible |
| Economic | Feasible |
| Operational | Feasible |
| Schedule | Feasible with controlled scope |
| Legal and ethical | Feasible |
| Social and environmental | Beneficial |

**Recommendation:** Proceed with the project using the proposed rule-based web system (Option C). The main risks are rule accuracy and scope growth. Verify the rule base with an expert, build the High-priority requirements first, and keep the number of crops and rules manageable.
