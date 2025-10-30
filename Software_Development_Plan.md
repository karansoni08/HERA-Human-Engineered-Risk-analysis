# 🧠 HERA: Human Engineered Risk Analysis  
### Software Development Plan (8 Phases)

---

## **Overview**
HERA (Human Engineered Risk Analysis) is an **LLM-assisted human-centric threat modeling system** designed to detect and quantify social engineering and insider risks.  
The project follows an **8-phase structured software development lifecycle**, integrating both deterministic analytics and AI reasoning using the **OME² Framework (Origin • Method • Exposure • Outcome)**.

---

## 🗂️ **Phase 1 — Planning & Requirement Analysis**

### 🎯 Objective
Define the overall vision, scope, and purpose of HERA, and establish project goals, deliverables, and success metrics.

### 🧩 Key Tasks
- Define the purpose: Quantify human-driven cyber risks using behavioral and policy data.  
- Identify stakeholders: Cybersecurity analysts, compliance officers, researchers.  
- Document functional and non-functional requirements.  
- Determine tech stack: Python, Pandas, JSON, LLM (Ollama/Mistral), Matplotlib, ReportLab.  
- Establish evaluation metrics (HTI accuracy, LLM JSON validity, reporting quality).

### 📦 Deliverables
- Project Charter  
- Requirement Specification Document  
- Data Schema Design (CSV structures)  
- Defined OME² framework model

### 🛠️ Tools
Miro / Lucidchart (brainstorming), Markdown / Docs for documentation.

### ✅ Outcome
A clear, actionable project blueprint defining the “what,” “why,” and “how” of HERA.

---

## **Phase 2 — System Design & Architecture**

### 🎯 Objective
Develop the technical architecture, module hierarchy, and data flow for HERA.

### 🧩 Key Tasks
- Design the overall system architecture (Data → Analytics → LLM → Visualization).  
- Define module dependencies and interfaces.  
- Create the OME² data model (Origin, Method, Exposure, Outcome).  
- Establish project folder structure: `/data`, `/src`, `/outputs`, `/docs`.  
- Specify JSON schemas for LLM outputs (policy_rules, scenarios, triage, guidance).

### 📦 Deliverables
- `ARCHITECTURE.md` with diagrams  
- OME² data and class models  
- Defined JSON schemas and configuration templates

### 🛠️ Tools
Mermaid, Draw.io, Markdown, UML diagrams.

### ✅ Outcome
A scalable and modular blueprint ensuring system clarity and extensibility.

---

## **Phase 3 — Data Layer Development**

### 🎯 Objective
Build the synthetic data generation and ingestion pipeline for safe, realistic datasets.

### 🧩 Key Tasks
- Implement `generate_synthetic_data.py` using **Faker** and **Random**.  
- Create CSVs:
  - `user_directory.csv`
  - `phishing_simulation.csv`
  - `access_logs.csv`
  - `policy_violations.csv`  
- Validate schema using **Pydantic** or **Pandera**.  
- Generate 100–300 synthetic user profiles with varied behaviors.

### 📦 Deliverables
- `/data` directory with populated synthetic datasets  
- Schema validation scripts and logs  
- Data generation documentation

### 🛠️ Tools
Python, Pandas, Faker, Pandera.

### ✅ Outcome
A privacy-safe, fully synthetic dataset representing realistic enterprise activity.

---

## **Phase 4 — Analytics & Scoring Engine**

### 🎯 Objective
Develop the deterministic analytics engine that computes risk scores and maps threats using the OME² model.

### 🧩 Key Tasks
- Implement `feature_engineering.py` (behavioral metrics extraction).  
- Create `score_risk.py` to compute **Human Threat Index (HTI)**:  
  `HTI = Likelihood × Impact × (1 - Detectability)`  
- Map risk signals to OME² pillars with `map_ome2_vectors.py`.  
- Test and calibrate thresholds for role-based accuracy.

### 📦 Deliverables
- `risk_scores.csv` output  
- Analytics engine scripts  
- Unit tests for calculations

### 🛠️ Tools
Python, Pandas, Numpy, JSON.

### ✅ Outcome
An explainable scoring engine that quantifies human risk with precision and transparency.

---

## **Phase 5 — LLM Intelligence Layer**

### 🎯 Objective
Integrate large language models for policy understanding, scenario generation, triage summarization, and mitigation coaching.

### 🧩 Key Tasks
1. **Policy → Control Extraction (`llm_extract_policy_rules.py`)**  
   Converts unstructured policies into structured JSON control rules.  
2. **Attack Scenario Generator (`llm_generate_scenarios.py`)**  
   Creates realistic department-specific attack narratives.  
3. **Analyst Summarizer (`llm_summarize_triage.py`)**  
   Produces SOC-style summaries from raw activity logs.  
4. **Mitigation Coach (`llm_generate_guidance.py`)**  
   Generates tailored awareness messages and control recommendations.  

### 📦 Deliverables
- `policy_rules.json`  
- `scenarios/*.json`, `triage/*.json`, `guidance/*.json`  
- Prompt templates and validation logs

### 🛠️ Tools
Ollama (LLaMA 3 / Mistral), Python (requests/jsonschema).

### ✅ Outcome
An AI-assisted reasoning layer that transforms data into contextual and actionable intelligence.

---

## **Phase 6 — Visualization & Reporting**

### 🎯 Objective
Visualize insights and generate professional-grade executive reports.

### 🧩 Key Tasks
- Build `visualize.py` for:
  - Risk heatmaps by department  
  - Top risky identities  
  - Phishing behavior trends  
- Create `report_builder.py` to compile:
  - Figures + JSON insights → PDF/Markdown  
  - Include LLM summaries and ethics appendix  

### 📦 Deliverables
- `charts/*.png`  
- `human_threat_model_report.pdf`  
- Report templates (Jinja2/ReportLab)

### 🛠️ Tools
Matplotlib, Plotly, ReportLab, Jinja2.

### ✅ Outcome
An interpretable, visual report translating analytics into executive-ready intelligence.

---

## **Phase 7 — Testing, Validation & Quality Assurance**

### 🎯 Objective
Verify system correctness, robustness, and ethical compliance.

### 🧩 Key Tasks
- Conduct **functional and unit testing** for each module.  
- Validate all LLM outputs against strict JSON schemas.  
- Measure model consistency (temperature = 0–0.2).  
- Conduct **ethics and fairness review** using simulated edge cases.  

### 📦 Deliverables
- `/tests` folder with automated scripts  
- QA report (accuracy, reproducibility, bias metrics)  
- Compliance and ethics statement  

### 🛠️ Tools
PyTest, JSONSchema, Flake8, Black.

### ✅ Outcome
A stable, reproducible, bias-free system ready for deployment and presentation.

---

## **Phase 8 — Deployment, Documentation & Maintenance**

### 🎯 Objective
Prepare HERA for deployment, public release, and long-term sustainability.

### 🧩 Key Tasks
- Finalize all documentation (`README.md`, `ARCHITECTURE.md`, `SOFTWARE_DEVELOPMENT_PLAN.md`).  
- Create `requirements.txt` and setup guide.  
- Package sample reports and datasets for demo.  
- Optional: containerize project using Docker.  
- Plan maintenance tasks (LLM retraining, dataset refresh).  

### 📦 Deliverables
- Complete GitHub repository  
- Final documentation set  
- Optional Docker container  
- Demo-ready environment  

### 🛠️ Tools
Git, GitHub Actions, Docker (optional), Markdown.

### ✅ Outcome
A production-ready, well-documented project repository suitable for academic submission or professional demonstration.

---

## 🗓️ **Timeline Overview (8 Weeks)**

| Phase | Duration | Deliverable |
|-------|-----------|-------------|
| **1. Planning** | Week 1 | Requirement & Scope Document |
| **2. System Design** | Week 2 | Architecture Blueprint |
| **3. Data Layer** | Week 3 | Synthetic Data Generator |
| **4. Analytics Engine** | Week 4 | HTI & OME² Mapping Engine |
| **5. LLM Layer** | Weeks 5–6 | AI-Driven Intelligence Modules |
| **6. Visualization** | Week 7 | Charts & Executive Report |
| **7. Testing/QA** | Week 7–8 | Validation Report |
| **8. Deployment** | Week 8 | Final Repository & Documentation |

---

## 🧾 **Final Deliverables Summary**

- ✅ **Executable Codebase:** `/src`, `/data`, `/outputs`, `/docs`  
- ✅ **LLM Modules:** Policy Extraction, Scenario, Triage, Guidance  
- ✅ **Analytics Engine:** HTI computation and OME² mapping  
- ✅ **Report Outputs:** Charts, dashboards, and executive PDF  
- ✅ **Documentation:** README, Architecture, SDP, Ethics report  
- ✅ **Testing Suite:** QA and JSON schema validation

---

## ⚖️ **Ethics & Compliance**
HERA is designed under a strict privacy-first principle:
- Uses **synthetic data only** — no personal or organizational identifiers.  
- Enforces **local/offline LLM inference** to prevent data exposure.  
- Includes bias-checking and fairness analysis in QA phase.  

---

## 🚀 **Outcome**
By the end of the development cycle, **HERA** will deliver:
- A functional AI-assisted platform that models human-centric risks.  
- A robust data analytics and visualization framework.  
- Executable LLM intelligence modules for automated policy reasoning and narrative reporting.  
- A reproducible and ethical research-grade cybersecurity tool.

---
