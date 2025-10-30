# HERA: Human Engineered Risk Analysis
### All-in-one Architecture Diagram (OME²: Origin • Method • Exposure • Outcome)

> The diagram below captures **data sources, processing pipeline, LLM modules, OME² mapping, outputs, and artifacts** in one place.

```mermaid
flowchart LR
  %% =========================
  %% STYLE / LEGEND
  %% =========================
  classDef layer fill:#0b172a,stroke:#1e293b,stroke-width:1,color:#e5e7eb;
  classDef box fill:#0f213e,stroke:#334155,stroke-width:1,color:#e5e7eb;
  classDef file fill:#0f172a,stroke:#475569,color:#e5e7eb;
  classDef llm fill:#172554,stroke:#2563eb,color:#e5e7eb;
  classDef out fill:#111827,stroke:#6b7280,color:#e5e7eb;
  classDef note fill:#0f172a,stroke:#334155,color:#93c5fd,font-style:italic;

  %% =========================
  %% LAYER 0: LEGEND
  %% =========================
  subgraph LEGEND[Legend]
    direction LR
    L0a[Process / Module]:::box --> L0b[(Data File / Artifact)]:::file
    L0c{{LLM Module}}:::llm --> L0d[[Outputs / Reports]]:::out
    L0e[/Note/]:::note
  end
  class LEGEND layer

  %% =========================
  %% LAYER 1: DATA
  %% =========================
  subgraph L1[1) Data Layer (/data)]
    direction TB
    D1[(user_directory.csv\nroles, departments, privilege_level, critical_asset_access)]:::file
    D2[(phishing_simulation.csv\nopened, clicked, creds_submitted, reported, timestamp)]:::file
    D3[(access_logs.csv\naction, data_gb, after_hours, anomalous_geo, resource, timestamp)]:::file
    D4[(policy_violations.csv\nviolation_type, severity, repeat_count, timestamp)]:::file
    N1[/100% SYNTHETIC DATA — no real PII/]:::note
  end
  class L1 layer

  %% =========================
  %% LAYER 2: ANALYTICS & SCORING
  %% =========================
  subgraph L2[2) Analytics & Scoring Layer (/src)]
    direction TB
    A1[feature_engineering.py\n• phish_click_rate\n• large_after_hours_downloads\n• anomalous_geo_logins\n• privilege_escalations]:::box
    A2[score_risk.py\nHTI Engine = 100 × Likelihood × Impact × (1 - Detectability)\n(Weights & thresholds in config)]:::box
    A3[map_ome2_vectors.py\nOME² Mapping:\nOrigin • Method • Exposure • Outcome]:::box
    O1[(risk_scores.csv)]:::file
    N2[/Deterministic & explainable math; unit tested/]:::note
  end
  class L2 layer

  %% DATA -> ANALYTICS
  D1 --> A1
  D2 --> A1
  D3 --> A1
  D4 --> A1
  A1 --> A2 --> O1
  A2 --> A3

  %% =========================
  %% LAYER 3: LLM INTELLIGENCE
  %% =========================
  subgraph L3[3) LLM Intelligence Layer (/src)]
    direction TB
    LLM1{{llm_extract_policy_rules.py\n→ policy_rules.json\n"Policy → Control Extraction"}}:::llm
    LLM2{{llm_generate_scenarios.py\n→ scenarios/*.json\n"Attack Scenario Generator"}}:::llm
    LLM3{{llm_summarize_triage.py\n→ triage/*.json\n"Analyst Summarizer"}}:::llm
    LLM4{{llm_generate_guidance.py\n→ guidance/*.json\n"Mitigation Coach"}}:::llm
    P1[(policy_rules.json)]:::file
    S1[(scenarios/*.json)]:::file
    T1[(triage/*.json)]:::file
    G1[(guidance/*.json)]:::file
    N3[/Local/offline LLM preferred; strict JSON schema; temp ≤ 0.2/]:::note
  end
  class L3 layer

  %% ANALYTICS -> LLM
  A3 --> LLM2
  A2 --> LLM3
  LLM1 --> P1
  LLM2 --> S1
  LLM3 --> T1
  LLM4 --> G1

  %% =========================
  %% LAYER 4: VISUALIZATION & REPORTING
  %% =========================
  subgraph L4[4) Visualization & Reporting Layer (/src, /outputs, /docs)]
    direction TB
    V1[visualize.py\nHeatmaps, Top-N, Trends, Privilege-risk]:::box
    V2[report_builder.py\nExecutive PDF/Markdown via templates]:::box
    C1[(charts/*.png or .html)]:::file
    R1[[docs/human_threat_model_report.pdf\n— Executive Summary\n— Methodology (OME²)\n— Results (figures, tables)\n— LLM Advisory (policy rules, scenarios, triage, guidance)\n— Ethics & Limitations]]:::out
    N4[/Outputs stitched into a single executive deliverable/]:::note
  end
  class L4 layer

  %% FEEDS TO VIZ/REPORT
  O1 --> V1 --> C1 --> V2
  P1 --> V2
  S1 --> V2
  T1 --> V2
  G1 --> V2
  V2 --> R1

  %% =========================
  %% COMPLIANCE & ETHICS SIDE NOTES
  %% =========================
  subgraph SIDE[Compliance, Ethics & Controls]
    direction TB
    E1[/NIST SP 800-53 & ISO 27001 Annex A\nmapped in guidance/]:::note
    E2[/Ethics: fairness, bias, transparency\n(Synthetic-only; no real identities)/]:::note
  end

  %% VISUAL LINK (dotted)
  R1 -. references .-> E1
  R1 -. appendix .-> E2
