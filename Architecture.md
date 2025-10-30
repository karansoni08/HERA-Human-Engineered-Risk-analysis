                ┌────────────────────────────────────────┐
                │          1. DATA LAYER                 │
                │────────────────────────────────────────│
                │  • user_directory.csv                  │
                │  • phishing_simulation.csv             │
                │  • access_logs.csv                     │
                │  • policy_violations.csv               │
                │                                        │
                │  → 100% Synthetic, Privacy-Safe Data   │
                └────────────────────────────────────────┘
                                  │
                                  ▼
                ┌────────────────────────────────────────┐
                │     2. ANALYTICS & SCORING LAYER       │
                │────────────────────────────────────────│
                │  • Feature Engineering (behavior stats) │
                │  • Human Threat Index (HTI) calculation │
                │    = Likelihood × Impact × (1-Detect.) │
                │  • OME² Mapping                        │
                │     - Origin: Who initiates             │
                │     - Method: How attack occurs         │
                │     - Exposure: What asset is affected  │
                │     - Outcome: What impact results      │
                │  → Output: risk_scores.csv              │
                └────────────────────────────────────────┘
                                  │
                                  ▼
                ┌────────────────────────────────────────┐
                │       3. LLM INTELLIGENCE LAYER         │
                │────────────────────────────────────────│
                │  • Policy → Control Extraction          │
                │      → policy_rules.json                │
                │  • Attack Scenario Generator            │
                │      → scenarios/*.json                 │
                │  • Analyst Summarizer (SOC reports)     │
                │      → triage/*.json                    │
                │  • Mitigation Coach                     │
                │      → guidance/*.json                  │
                │  (Local/offline inference recommended)  │
                └────────────────────────────────────────┘
                                  │
                                  ▼
                ┌────────────────────────────────────────┐
                │   4. VISUALIZATION & REPORTING LAYER    │
                │────────────────────────────────────────│
                │  • Charts & Heatmaps (matplotlib)       │
                │  • Dashboards (optional)                │
                │  • Executive Report (PDF/Markdown)      │
                │    ├─ OME² threat summary               │
                │    ├─ Policy insights (LLM)             │
                │    ├─ Scenarios, Triage & Guidance      │
                │    └─ Ethics & Recommendations          │
                │  → Output: human_threat_model_report.pdf│
                └────────────────────────────────────────┘
