# cloud-analytics-root-cause-analysis
# Cloud Analytics & System Monitoring

## Explainable Root Cause Analysis for Cloud Applications

### Overview
This project presents an applied root cause analysis (RCA) study for modern cloud-native applications using distributed tracing data and explainable machine learning. The goal is not only to detect failures, but to identify which microservices and trace attributes drive failures — and why — in highly sparse, high-dimensional observability data.

The analysis is implemented as a single end-to-end notebook covering feature engineering, predictive modeling, and multiple explainability techniques, using data characteristics representative of real production observability systems (80–90% sparsity, thousands of features).

### Problem Context
In microservices architectures, failures propagate across many services, making root cause identification largely manual and time-consuming. While modern monitoring tools indicate where issues occur, they rarely explain which components and which attributes actually drive failures.

This project addresses that gap by combining high-performing ensemble models with explainable AI (XAI) to support trustworthy and actionable RCA.

### Methodology

Feature engineering from distributed tracing data (service presence, repetition patterns, span–tag combinations)

Tree-based ensemble models (XGBoost, HistGradientBoosting) for scalable learning on sparse data

Multiple explainability techniques (SHAP, permutation importance, rule-based methods) used in parallel to validate explanation stability

### Key Findings

Root causes are sparse and stable despite extreme dimensionality and noise

Contextual service and span attributes provide more explanatory power than raw duration metrics

Independent explainability methods consistently converge on the same failure drivers

Explanation — not prediction — determines operational usefulness

### Impact
The project demonstrates how explainable ML can transform raw observability data into actionable diagnostic insight, supporting faster and more trustworthy decision-making in complex operational systems.

### Repository

```text
├── README.md                                     # Project documentation
├── cloud_analytics_root_cause_analysis.ipynb     # Main analysis notebook (static, non-executable)
├── Master Thesis IESM.pdf                        # Master’s thesis document
```

### Keywords
Explainable AI · Root Cause Analysis · Distributed Tracing · Cloud Analytics · AIOps · Decision Support · Microservices
