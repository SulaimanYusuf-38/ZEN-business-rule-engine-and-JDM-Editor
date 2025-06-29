# 🎓 Scholarship Eligibility Decision Model – GoRules Implementation

This project presents a scoring-based decision model to assess student eligibility for scholarship allocation using rule-based logic. Built with GoRules JDM, the system evaluates multiple factors to ensure fair, transparent, and consistent selection outcomes.

## 📌 Objective

To design an automated, rule-driven system that classifies students into scholarship categories based on their academic performance, financial background, institutional status, and extracurricular involvement.

## 🧠 Background

Traditional scholarship systems often rely heavily on GPA, which may introduce bias and overlook qualified candidates. This model overcomes that limitation by combining four weighted criteria:
- Academic GPA (max 40 pts)
- Annual Family Income (max 25 pts)
- Socioeconomic Tier (max 15 pts)
- Extracurricular Score (max 20 pts)

The total score determines the scholarship category:
- **≥ 85** → Full Scholarship  
- **70–84** → Partial Scholarship  
- **60–69** → Manual Review  
- **< 60** → Not Eligible

## 🔗 GoRules Flow Overview

The decision model is built using a GoRules graph with the following logical flow:

1. `Input Validator`: Checks completeness of all fields (GPA, income, socio status, EC score)  
2. `GPA Handler`: Rejects candidates with GPA < 3.0  
3. Decision Tables:
   - `Annual Income` → Income-based score  
   - `Socio Status` → Score by institution tier  
   - `Extracurricular Score` → Score from 0–10 EC rating  
4. `Aggregator`: Sums all scores and classifies final result  
5. `Result`: Outputs student ID, total score, and scholarship category

> If any required field is missing or GPA < 3.0, the system immediately returns `Not Eligible`.

## 📁 Required Input Schema

Each applicant must submit the following fields:

| Field                | Type     | Description                              |
|---------------------|----------|------------------------------------------|
| `studentID`         | String   | Unique student identifier                |
| `fullName`          | String   | Full name of applicant                   |
| `GPA`               | Float    | Grade Point Average (0.0–4.0)            |
| `AnnualIncome`      | Integer  | Total annual household income (AUD)      |
| `SocioStatus`       | String   | Tier 1, Tier 2, or Tier 3 institution     |
| `ExtracurricularScore` | Float | Score from 0 to 10                        |

## 🧪 Test Cases

| Scenario                      | Result                     |
|------------------------------|----------------------------|
| Missing Income               | Not Eligible               |
| GPA < 3.0                    | Not Eligible               |
| High GPA + Low Income        | Full Scholarship (score 85)|
| Mid GPA + Moderate Income    | Partial Scholarship (score 79) |
| GPA 3.2, EC 6.5, Tier 3      | Manual Review (score 67)   |

These test cases ensure the system behaves correctly across valid, invalid, and edge inputs.

## 🛠️ Tools & Platform

- **Platform**: [GoRules Decision Platform](https://www.gorules.io/)
- **Model Format**: JSON (.gorules decision graph)
- **Design Flow**: Visual graph with function nodes, decision tables, and condition routing

## 📷 Screenshots

Include these assets in your GitHub repo:
- `Screenshot JDM Graph.png` – visual flow of the decision model
- `PDFfile-47895810.pdf` – detailed report with test cases and academic references

## 👤 Author

**Sulaiman Yusuf Zakaria**  
Master of Business Analytics – Macquarie University  
Student ID: 47895810

---

This model was submitted for the **COMP8440 – Automated Decision Making in Business** course and demonstrates practical application of rule-based automation for ethical, transparent decision support systems.
