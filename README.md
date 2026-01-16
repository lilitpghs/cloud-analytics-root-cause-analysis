# cloud-analytics-root-cause-analysis
## Cloud Analytics & System Monitoring

### Explainable Root Cause Analysis for Modern Cloud Applications

## Overview

This project presents an applied root cause analysis (RCA) study for modern cloud-native applications using distributed tracing data and explainable machine learning. The goal is not merely to detect failures, but to identify which microservices and span-level attributes are responsible for failures, and why, in highly complex and sparse observability data. The analysis is implemented as a single end-to-end notebook, covering feature engineering, model training, and multiple explainability techniques. The work is grounded in realistic tracing data characteristics, including extreme sparsity (80–90% missing values), high dimensionality, and noisy signals.

## Problem Context

In microservices-based architectures, a single user request propagates across many independent services. Observability platforms collect massive volumes of trace and span data, yet root cause identification remains largely manual and time-consuming.

Traditional monitoring tools answer where an issue occurs, but not:

- which microservices truly drive failures

- which span attributes explain degraded behavior

- whether observed signals are causal or incidental

This project addresses that gap by combining high-performing ensemble models with explainable AI (XAI) techniques to support trustworthy and actionable RCA.

## Data & Observability Scope

The analysis is based on distributed tracing data with the following structure:

- Each trace represents a single request

- Each trace contains multiple spans (units of work)

- Spans include service names, tags, and error indicators

Traces are labeled as:

- Normal: no span reports an error

- Erroneous: at least one span reports an error

The resulting datasets are:

- high-dimensional (up to ~5,000 features)

- extremely sparse (80–90% missing values)

- derived from real observability data, not curated benchmarks

## Analytical Approach

#### Feature Engineering

Multiple feature representations were constructed to capture system behavior at increasing levels of detail:

1. Span presence (binary indicators of which microservices appear in a trace)

2. Span repetition counts (how often a span appears within a trace)

3. Span–tag combinations (service name + tag name + tag value)

4. Hybrid representations combining repetition counts and tags

These representations enabled systematic comparison of what level of detail actually improves explainability.

#### Predictive Modeling

Tree-based ensemble models (XGBoost, HistGradientBoosting) were used because they:

- handle missing values natively

- scale to thousands of sparse features

- achieve near-perfect classification accuracy

Across all feature setups, models achieved precision, recall, and F1-scores close to 1.0 on held-out test data. This confirmed that prediction is easy in this setting — the challenge lies in explanation.

## Explainability & Root Cause Analysis

To move beyond prediction, the project applied and compared:

- built-in tree-based feature importance

- permutation-based importance (model-agnostic)

- SHAP (local and global explanations)

- RIPPER rule induction (when accuracy allowed)

These methods were used in parallel to validate whether explanations were stable and consistent.

Special care was taken to address:

- extreme sparsity

- dominance of duration-related features

- agreement across multiple explanation techniques

## Key Results & Findings

This project produced several clear empirical findings:

1. Root causes are sparse and stable

Across all feature representations, a small subset of microservices repeatedly emerged as dominant contributors to failures, despite thousands of available features and extreme sparsity.

Certain services consistently explained the majority of erroneous traces, indicating non-random, stable root causes rather than diffuse system-wide issues.

2. Repetition patterns reveal failure behavior

When span repetition counts were included, failures were strongly associated with repeated database-related spans, suggesting retry loops or cascading failures rather than isolated errors.

These repetition-based signals were independently confirmed by:

- RIPPER rules (when accuracy was acceptable)

- permutation importance

- SHAP explanations

3. Contextual span attributes outperform raw durations

Duration-based features frequently appeared important, but removing all duration-related attributes did not eliminate explanatory power.

After removing durations:

- the same microservices and span-tag combinations remained dominant

- explainability methods continued to converge on the same root causes

This demonstrates that contextual attributes (service identity, tags, values) provide deeper insight than raw latency metrics alone.

4. Explainability methods converge on the same causes

SHAP, permutation importance, and rule-based methods repeatedly highlighted the same microservices and span attributes, even across different feature representations.

This convergence significantly increases confidence in the explanations and reduces the risk of spurious insights.

5. Interpretability changes operational usefulness

While near-perfect classifiers can be trained easily, their outputs are operationally useless without explanations.

By identifying:

- which services matter

- which attributes are associated with failures

- and how these signals behave

the analysis transforms raw observability data into actionable diagnostic insight.

## Practical Impact

This approach enables:

- faster identification of problematic microservices

- reduced investigation of low-impact components

- explainable, trust-building diagnostics for engineers

- decision support for reliability and operations teams

The work demonstrates a concrete foundation for explainable AIOps and RCA systems that scale to real-world observability data.

## Key Takeaway

High-performing models alone do not solve root cause analysis.
**Explanation is the product.**

This project shows that even in extremely sparse, high-dimensional tracing data, robust ML models combined with XAI can reliably surface true failure drivers — and do so in a way that engineers can trust and act upon.

## Repository Structure

```text
├── README.md             # Project documentation
├── capstone.ipynb        # Main analysis notebook (static, non-executable)
```
> **Note:**  
> The notebook is provided as-is for transparency and review.  
> Datasets and execution artifacts are not included.

## Keywords

Cloud Analytics · System Monitoring · Distributed Tracing · Explainable AI · Root Cause Analysis · AIOps · Decision Support · Observability · SHAP · Feature Importance · Microservices

## Author

**Lilit Poghosyan** — Background in Industrial Engineering, Business Intelligence, and Data Analytics, with a focus on improving decision quality in complex operational systems.
