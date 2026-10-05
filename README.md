# 🤖 Agentic AI for E-commerce KPI Anomaly Detection & Root-Cause Analysis

An **Agentic AI-powered Business Intelligence system** that automatically detects unusual movements in key e-commerce KPIs and investigates their possible business drivers using **LLMs, LangGraph, SQL, structured outputs, and data-driven KPI relationships**.

The project uses the **Brazilian Olist e-commerce dataset** to transform raw transactional data into daily business KPIs and then uses an agentic workflow to identify significant anomalies and generate business-oriented explanations.

---

## 📌 Project Overview

In a typical e-commerce business, metrics such as revenue, customer count, active sellers, and average customer spending continuously fluctuate.

The challenging part is not simply identifying that a KPI changed.

The real business question is:

> **"Why did this KPI change?"**

This project addresses that problem by building an AI-driven investigation pipeline that:

1. Processes raw Olist transactional data.
2. Creates daily business KPIs.
3. Detects significant KPI anomalies.
4. Groups consecutive abnormal observations into meaningful anomaly periods.
5. Identifies relevant driver KPIs for each anomaly.
6. Dynamically generates SQL queries to retrieve the required data.
7. Uses an SQL tool to safely retrieve KPI evidence.
8. Validates potential drivers against the observed anomaly.
9. Generates a concise business hypothesis.
10. Flags the explanation as ambiguous when the evidence is insufficient.

The goal is to move from:

**"The KPI changed."**

to:

**"The KPI changed, and here is the most evidence-supported explanation."**

---

# 🎯 Business Problem

Business teams frequently monitor dashboards containing hundreds of metrics.

When an important KPI suddenly increases or decreases, analysts usually have to:

- Identify the anomaly.
- Find the affected time period.
- Check related KPIs.
- Query historical data.
- Compare the anomaly period with the baseline.
- Investigate possible drivers.
- Determine whether the evidence supports a particular explanation.

This manual process can be slow and inconsistent.

This project automates a significant part of this investigation using an **agentic AI workflow**.

---

# 🧠 Key Idea

The system follows a two-stage investigation process.

### Stage 1 — Detect the anomaly

An LLM analyzes chronological KPI time-series data and identifies the strongest meaningful anomaly for each KPI.

The system avoids reporting every small fluctuation.

Instead, consecutive abnormal observations are grouped into a single anomaly period.

### Stage 2 — Investigate the anomaly

Once an anomaly is identified, specialized investigation nodes determine which underlying KPIs could explain the movement.

The system then:

```text
Anomaly
   ↓
Relevant KPI Drivers
   ↓
SQL Query Generation
   ↓
Database Tool
   ↓
Historical KPI Evidence
   ↓
Driver Validation
   ↓
Business Hypothesis
