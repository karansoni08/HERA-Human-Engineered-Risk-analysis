# 🧠 HERA: Human Engineered Risk analysis
### Quantifying Human Cyber Risk through Behavioral Analytics + AI-Driven Insight  

---

## 🔍 Overview  
Modern cybersecurity threats are increasingly **human-driven** — phishing, impersonation, data mishandling, and insider misuse remain key attack vectors.  
This project introduces an **LLM-powered, human-centric threat-modeling framework** that analyzes behavioral data, quantifies risk, and generates actionable insights through AI reasoning.

By combining deterministic analytics (for transparent scoring and detection) with **large-language-model intelligence** (for policy understanding, scenario generation, and mitigation guidance), this system transforms human behavior into measurable cybersecurity posture — without using any real personal data.

---

## 🧩 Key Features  
| Capability | Description |
|-------------|-------------|
| **OME² Threat Framework** | A four-pillar human threat model — *Origin, Method, Exposure, Outcome* — capturing both intent and consequence. |
| **Human Threat Index (HTI)** | 0–100 quantitative score per user or department based on likelihood, impact, and detectability. |
| **Policy Intelligence via LLM** | Translates plain-text corporate policies into enforceable JSON control rules. |
| **Attack Scenario Generator** | Crafts realistic breach narratives tailored to each department’s risk profile. |
| **Analyst Summarization Copilot** | Summarizes anomalies into SOC-style triage notes for faster investigation. |
| **Adaptive Mitigation Coach** | Produces personalized guidance and awareness text for managers and employees. |
| **Data Visualization Suite** | Heatmaps, time-series trends, privilege-risk plots for clear decision insight. |
| **Privacy by Design** | 100 % synthetic data generation — no real employee or sensitive data used. |

---

## ⚙️ Architecture  

```text
+--------------------------------------------------------------------------------+
|                      LLM-ASSISTED HUMAN THREAT MODEL (OME²)                    |
+--------------------------------------------------------------------------------+
| 1. Data Layer                                                                  |
|    ├─ Synthetic datasets: users, phishing, access logs, policy violations       |
|                                                                                |
| 2. Analytics & Scoring Layer                                                   |
|    ├─ Feature engineering (behavioral metrics)                                 |
|    ├─ Human Threat Index (HTI) computation                                     |
|    └─ Mapping to OME² pillars (Origin–Method–Exposure–Outcome)                 |
|                                                                                |
| 3. LLM Intelligence Layer                                                      |
|    ├─ Policy→Control Extraction  → policy_rules.json                           |
|    ├─ Attack Scenario Generation → scenarios/*.json                            |
|    ├─ Analyst Summaries        → triage/*.json                                 |
|    └─ Mitigation Coaching      → guidance/*.json                               |
|                                                                                |
| 4. Visualization & Reporting Layer                                             |
|    ├─ Heatmaps, charts, dashboards (matplotlib/Plotly)                         |
|    └─ Executive PDF/Markdown report (Jinja2 templates)                         |
+--------------------------------------------------------------------------------+


