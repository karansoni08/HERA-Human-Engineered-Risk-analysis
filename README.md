# 🧠 HERA — Human Engineered Risk Analysis

> **AI-driven Human-Centric Threat Modeling Framework**  
> Integrating human behavior analytics, social engineering intelligence, and large language models (LLMs) to identify and mitigate human-engineered cybersecurity risks.

---

## 🌍 Overview

Traditional cybersecurity models often focus on **technical vulnerabilities** — firewalls, patches, and malware signatures — while overlooking the **human layer**, where the majority of breaches originate.

**HERA (Human Engineered Risk Analysis)** bridges this gap.

It is a next-generation **AI-powered threat modeling system** that fuses:
- **Behavioral analysis**
- **Social engineering detection**
- **Large Language Model (LLM) reasoning**
- **Standardized frameworks** (MITRE ATT&CK, STRIDE, NIST CSF 2.0)

The goal: to **understand and predict human-driven attack vectors** such as phishing, insider manipulation, and behavioral anomalies — then translate them into structured, actionable intelligence.

---

## 🧩 Core Concept

HERA models each threat as a triad of:

| **Dimension** | **Description** |
|----------------|----------------|
| 🎭 **Actor** | The human or entity initiating the threat (e.g., insider, external attacker, social engineer). |
| 🧬 **Vector** | The behavioral or social pathway exploited (e.g., email phishing, privilege misuse, cognitive bias). |
| 💥 **Impact** | The operational, reputational, or data-level consequence of the exploit. |

This **Actor–Vector–Impact (AVI)** structure is powered by **LLM reasoning**, which interprets raw unstructured data (incident reports, chat logs, phishing datasets) and transforms it into **machine-readable threat models**.

---

## 🏗️ System Architecture

           ┌────────────────────────────┐
           │  Input Sources             │
           │  (Incident reports, logs,  │
           │   phishing data, insider   │
           │   activity, text corpus)   │
           └────────────┬───────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │  Preprocessing Layer       │
           │  • Text extraction (PyPDF2)│
           │  • PII redaction (Presidio)│
           │  • Language detection       │
           └────────────┬───────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │  LLM Reasoning Engine      │
           │  (Ollama + LLaMA / Mistral)│
           │  • Actor-Vector-Impact     │
           │  • Risk Categorization     │
           │  • Framework Mapping       │
           └────────────┬───────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │  Threat Output Generator   │
           │  • JSON & Markdown reports │
           │  • MITRE/STRIDE mappings   │
           │  • Confidence scores       │
           └────────────┬───────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │  Integration Layer         │
           │  • Databricks / SIEM / GRC │
           │  • Visualization Dashboards│
           └────────────────────────────┘




---

## ⚙️ Features

- 🧠 **AI-Powered Contextual Understanding** — Leverages LLaMA 3, DeepSeek, or Mistral LLMs for deep contextual reasoning.  
- 🔐 **Privacy-Preserving Processing** — Fully **air-gapped**, ensuring sensitive data never leaves the local environment.  
- 🧩 **Multi-Framework Support** — Aligns results with **MITRE ATT&CK**, **STRIDE**, and **NIST CSF 2.0** categories.  
- ⚡ **Automated Risk Summarization** — Generates ranked threat summaries and heatmaps for quick decision support.  
- 🧱 **Extensible Design** — Plug-and-play architecture for integrating new datasets, model types, or output pipelines.

---

## 🧪 Example Use Cases

| **Use Case** | **Description** |
|---------------|----------------|
| 🎯 **Social Engineering Risk Detection** | HERA analyzes phishing datasets or chat logs to detect manipulation patterns and map them to behavioral attack vectors. |
| 🧍‍♂️ **Insider Threat Modeling** | Detects anomalous employee activities or policy deviations, and classifies intent or risk severity using AVI analysis. |
| 🧾 **Incident Report Enrichment** | Converts unstructured security reports into structured JSON objects for SIEM/GRC ingestion. |
| 🧬 **Cognitive Bias Mapping** | Uses LLM reasoning to link social engineering attacks to cognitive biases (authority, scarcity, trust) for training simulations. |
| 🧰 **Enterprise Risk Visualization** | Outputs feed into Databricks dashboards or Power BI for visual heatmaps and trend analytics. |

---

## 🧱 Project Components

| **Directory** | **Description** |
|----------------|----------------|
| `/src` | Core threat modeling scripts and LLM orchestration logic. |
| `/models` | Model prompt templates, system configurations, and LLaMA runtime definitions. |
| `/data` | Input datasets (phishing reports, insider threat logs, etc.). |
| `/outputs` | Generated threat models, JSON risk reports, and visualization files. |
| `/docs` | Architecture diagrams, research papers, and framework mappings. |
| `/tests` | Unit and integration testing scripts. |

---

## 🧰 Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/HERA.git
cd HERA

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

