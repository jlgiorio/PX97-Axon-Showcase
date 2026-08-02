# OPERATIONAL PERFORMANCE & FEASIBILITY REPORT | PX97-AXON

**Quantitative Trading System Operational Performance Audit**  
**Target Asset:** Mini-Índice Bovespa (WIN) — Brazilian Futures Market  

---

## 1. Executive Summary

This document presents the technical audit of operational feasibility and performance for the **PX97-Axon** quantitative trading ecosystem operating on the B3 Mini-Índice (WIN). The analysis covers 11 operational months (**August 8, 2025 to July 10, 2026**, excluding March 2026 dedicated to parameter calibration and manual testing). 

The audit evaluates algorithm efficiency under a recommended initial margin allocation of **R$ 500.00 per contract**, comparing real dynamic position management (1 to 3 contracts) against a static 5-contract leverage simulation.

---

## 2. Technical System & Architecture Overview

PX97-Axon is an autonomous trading ecosystem built on a **decoupled asynchronous microservices architecture**. 
* **Predictive Layer:** Combines Deep Long Short-Term Memory (LSTM) Recurrent Neural Networks with a Large Language Model (LLM) macro news semantic sentiment classifier.
* **Meta-Labeling Audit:** A secondary Random Forest Machine Learning model operates in *Shadow Mode* for real-time cross-validation.
* **Risk Management:** Fully dynamic, applying volatility-adjusted stops/takes (ATR), maximum holding time liquidation (106-minute Timedrop), minimum balance protection, and daily loss limits.

---

## 3. Audited Performance Metrics Comparison Table

| Metric | Dynamic Real Contracts (1-3 Lotes) | Static 5-Contract Simulation |
| :--- | :---: | :---: |
| **Total Evaluated Trades** | **318 trades** | **318 trades** |
| **Net Accumulated Profit** | **R$ 10.090,60** | **R$ 34.383,21** |
| **Financial Win Rate** | **60.1%** | **61.3%** |
| **Profit Factor (Fator de Lucro)** | **2.11** | **2.14** |
| **Max Static Drawdown** | **R$ -90,40** | **R$ -342,00** |
| **Max Trailing Drawdown** | R$ 591,58 | R$ 1.498,38 |
| **Average Profit per Trade** | R$ 31,73 | R$ 108,12 |
| **Recommended Margin (R$ 500/lote)** | R$ 500,00 to R$ 1.500,00 | R$ 2.500,00 |
| **Return on Minimum Margin** | **2,018.1%** | **1,375.3%** |

---

## 4. Detailed Scenario Analysis

### Scenario A: Dynamic Real Lote Management (1 to 3 Contracts)
Under real log execution, the system generated **R$ 10.090,60 in net profit** with a maximum static drawdown of **only R$ -90,40**. Operating with a R$ 500.00 safety margin, the account was never exposed to margin call risk. The worst consecutive loss sequence in historical logs was only 4 stops (totaling R$ -195,72), which was easily absorbed by accumulated profits.

### Scenario B: Static 5-Contract Leverage Simulation
When simulating a constant position size of 5 contracts, the system extracted **R$ 34.383,21 from the market**. The maximum static drawdown was **R$ -342,00** (occurring in the first month). The largest consecutive loss sequence (4 consecutive stops totaling R$ -1.368,15) occurred when the account had already accumulated over R$ 12,461.67 in net profits, absorbing the drawdown without operational risk.

---

## 5. Proprietary Trading Firm (Prop Firm) Compliance

Unlike Trailing Drawdown, leading Brazilian prop firms (such as Axia Investing) utilize **Static Drawdown** rules (fixed loss limit relative to initial balance). Under these rules:
* PX97-Axon easily satisfies operational limits of **R$ 1.250,00** and **R$ 2.350,00** in both scenarios.
* **Dynamic Real Contracts:** Account balance never dropped below R$ -90,40.
* **Static 5 Contracts:** Minimum absolute balance was R$ -342,00 (over 70% safety buffer).

**Conclusion:** The ecosystem is fully compliant and institutional-grade ready for capital allocation and proprietary firm management.

---

*Quantitative Software Engineering & Compliance — Confidential Portfolio Report*
