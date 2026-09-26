# Financial Transaction Intelligence Platform

An end-to-end financial transaction intelligence and fraud investigation platform combining **behavioral machine learning, graph-based risk analysis, alert prioritization, and evidence-grounded investigation workflows**.

The project investigates a central question: **can transaction-network structure identify coordinated fraud that conventional behavioral features cannot see?**

![Investigation Dashboard](screenshots/dashboard.png)

---

## Overview

Traditional fraud models evaluate transactions largely as independent events. Coordinated fraud can evade this approach when individual transactions appear ordinary but multiple customers are connected through shared devices, merchants, or other entities.

This platform adds an **entity graph layer** to conventional transaction-level fraud detection, allowing the system to capture structural relationships between:

- Customers
- Devices
- Merchants
- Transactions

The resulting system combines **fraud prediction, network intelligence, ring detection, alert scoring, case consolidation, and analyst-oriented investigation**.

---

## Key Results

| Metric | Result |
|---|---:|
| Transactions processed | **31,449** |
| Graph nodes | **972** |
| Graph edges | **17,765** |
| Fraud alerts | **944** |
| Investigation cases | **34** |
| Seeded fraud rings recovered | **12 / 12** |
| Alert precision | **64.8%** |
| Graph-enhanced ROC-AUC | **0.8618** |
| Graph-enhanced PR-AUC | **0.5512** |
| Ring Recall @ Top 10% | **0.9093** |

The graph-enhanced model improved:

- ROC-AUC from **0.8010 → 0.8618**
- PR-AUC from **0.4369 → 0.5512**
- Recall@10% from **0.3206 → 0.4429**
- Ring Recall@10% from **0.2808 → 0.9093**

The same model, temporal split, and training rows were used for the baseline and graph-enhanced experiments; the primary change was the feature set.

## Architecture

```text
Transactions ─▶ Behavioural Features ─┐
      │                                │
      ▼                                ├─▶ Fraud Model ─▶ ML Risk ─┐
Entity Graph ─▶ Graph Features ────────┘                           │
      │                                                            │
      ├──────────────────────▶ Network Risk ──────────────────────┤
      │                                                            ▼
      │                                                   Alert Scoring
      │                                                            │
      └──────────────────────▶ Ring Detection              Alert Prioritisation
                                                                    │
                                                                    ▼
                                                             Case Management
                                                                    │
                                                         Evidence Pack
                                                          (deterministic)
                                                                    │
                                                             LLM Narration
                                                                    │
                                                                    ▼
                                                                 Analyst
