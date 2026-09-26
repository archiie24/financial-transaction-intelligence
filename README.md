# Financial Transaction Intelligence Platform

An end-to-end fraud investigation platform combining **transaction-level machine learning with graph intelligence** to detect coordinated fraud, prioritize alerts, and support evidence-grounded investigations.

![Investigation Dashboard](docs/screenshots/dashboard.png)

## Overview

Traditional fraud models evaluate transactions individually. This platform adds a **customer–device–merchant graph layer** to capture relationships that transaction-level behavioral features may miss.

The system combines:

**ETL → Feature Engineering → Fraud Modeling → Graph Intelligence → Alert Scoring → Case Management → Evidence-Based Investigation**

## Results

| Metric | Result |
|---|---:|
| Transactions processed | **31,449** |
| Graph nodes / edges | **972 / 17,765** |
| Graph-enhanced ROC-AUC | **0.862** |
| Graph-enhanced PR-AUC | **0.551** |
| Ring Recall @ Top 10% | **0.909** |
| Fraud rings recovered | **12 / 12** |
| Alerts generated | **944** |
| Investigation cases | **34** |
| Alert precision | **64.8%** |

### Baseline vs Graph-Enhanced

The experiment uses the **same Random Forest model, temporal split, and training rows**; only the feature set changes.

![Model Comparison](docs/figures/model_comparison.png)

The graph-enhanced model improves ROC-AUC from **0.801 → 0.862** and Ring Recall@10% from **0.281 → 0.909**.

## Architecture

![Architecture](docs/figures/architecture.png)

Transactions are transformed into behavioral and graph-derived features. Model risk, behavioral risk, and network risk are combined for alert prioritization, followed by case consolidation and deterministic evidence retrieval. The LLM is used only to **narrate retrieved evidence**, not generate investigation facts.

## Graph Intelligence

![Graph Investigation](docs/figures/graph_visualization.png)

The entity graph connects **customers, devices, and merchants**, enabling features such as shared customers, customer degree, device historical fraud rate, and merchant-level fraud signals.

![Feature Importance](docs/figures/feature_importance.png)

Graph-derived features account for approximately **40% of model feature importance** in the graph-enhanced model.

## Investigation Workflow

![Interactive Investigation](docs/screenshots/graph_investigation.png)

Alerts are consolidated into investigation cases around shared entities. Each case provides network context, transaction evidence, risk signals, and financial exposure.

![Case Evidence](docs/screenshots/case_evidence.png)

Evidence is retrieved deterministically before generating the investigation brief, keeping the LLM constrained to known facts.

![Investigation Brief](docs/screenshots/llm_investigation_brief.png)

## Adversarial Robustness

The graph layer was evaluated against controlled perturbations designed to weaken behavioral and graph signals, including lower transaction amounts, slower activity, reduced customer sharing, merchant diversification, and device variation.

![Adversarial Robustness](docs/figures/adversarial_robustness.png)

## Technology

**Python · Pandas · NumPy · SQL · SQLite · scikit-learn · Random Forest · NetworkX · Gemini · Matplotlib · HTML/CSS/JavaScript**

## Repository

```text
notebooks/     # End-to-end transaction and graph investigation pipelines
data/          # Exported console data
docs/figures/  # Analytical figures
docs/screenshots/ # Interactive platform screenshots
index.html     # Self-contained investigation console
