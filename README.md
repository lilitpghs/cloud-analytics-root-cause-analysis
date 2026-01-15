# cloud-analytics-root-cause-analysis
## Cloud Analytics & System Monitoring

### Explainable Root Cause Analysis for Modern Cloud Applications

#### Overview

This repository presents an applied analytics project focused on root cause analysis (RCA) in modern cloud-native applications using distributed tracing data and explainable machine learning. The work explores how high-volume observability data (application traces and spans) can be transformed into actionable insights that help engineers understand which microservices contribute to failures or performance degradation, and why. The implementation is provided as a single, end-to-end notebook reflecting the full analytical workflow, from feature construction to explainability-driven insights.

#### Problem Context

Modern cloud applications rely on microservices architectures, where individual user requests propagate across many independent services. While monitoring systems capture large volumes of

- application traces

- span-level metadata

- error indicators

identifying **the true root cause** of failures remains difficult.

Traditional monitoring highlights where issues appear, but often fails to explain:

- which components are responsible

- which attributes drive failures

- how issues propagate across services

This project addresses that gap by combining **high-performing machine learning models** with **explainable AI (XAI)** techniques to support clearer and faster diagnosis.

#### Data & Observability Scope

The analysis is based on **distributed tracing data**, where:

- Each trace represents a single request

- Each trace consists of multiple spans (units of work)

- Spans include service names, tags, and error indicators

Traces are labeled as:

- **normal**, if all spans are healthy

- **erroneous**, if at least one span reports an error

The resulting datasets are:

- high-dimensional

- sparse

- dominated by missing values

reflecting real-world observability challenges rather than curated datasets.

#### Analytical Approach

The notebook implements the following workflow:

#### Feature Engineering

Multiple feature representations were constructed to capture system behavior at different levels, including:

- span presence

- span repetition counts

- span–tag combinations

- selected duration-related attributes

#### Predictive Modeling

Tree-based ensemble models were applied due to their ability to:

- handle large amounts of missing data

- scale to high-dimensional inputs

- provide strong classification performance

Models achieved near-perfect accuracy in distinguishing normal and erroneous traces.

#### Explainability & Root Cause Analysis

To move beyond prediction, the project applies explainable AI methods, including:

- Tree-based ensemble models with strong predictive performance

- SHAP (SHapley Additive Explanations)

- permutation-based feature importance

- rule-based methods for validation

These techniques reveal:

- which microservices contribute most to failures

- which attributes and tag values are associated with degraded behavior

- how different explanations align across methods

Special attention is given to:

- Handling extremely sparse data (80–90% missing values)

- Balancing predictive power vs interpretability

- Validating explanations across multiple methods

#### Key Results

This work demonstrates that:

- High-performing ensemble models can be combined with XAI techniques to provide clear, actionable explanations

- Specific microservices and span-level attributes consistently emerge as drivers of failures

- Explainability methods converge on similar root causes across different feature representations

- Duration-based signals alone are insufficient — contextual span attributes provide deeper insight

- Interpretable outputs significantly improve the usefulness of analytics for operational teams

#### Practical Impact

The approach enables:

- Faster identification of problematic microservices

- Reduced time spent investigating low-impact components

- Clear explanations that support operational trust

- Decision support for system operators and reliability engineers

- A foundation for explainable AIOps and observability platforms

This type of analysis is especially relevant in high-volume, high-complexity environments where manual root cause investigation does not scale.

## Repository Structure

```text
├── capstone.ipynb        # Main analysis notebook (static, non-executable)
├── README.md             # Project documentation
```
> **Note:**  
> The notebook is provided as-is for transparency and review.  
> Datasets and execution artifacts are not included.

#### Keywords

Cloud Analytics · System Monitoring · Distributed Tracing · Explainable AI · Root Cause Analysis · AIOps · Decision Support · Observability · SHAP · Feature Importance · Microservices

#### Author

Lilit Poghosyan

Background in Industrial Engineering, Business Intelligence and Data Analytics

Focus on analytics that improve decision quality in complex operational systems
