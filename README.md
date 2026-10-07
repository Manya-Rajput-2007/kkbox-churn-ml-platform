# KKBox Churn ML Platform

Production-grade customer churn prediction platform with ML reliability monitoring, autonomous incident investigation, and controlled retraining.

## Project Goal

Build an end-to-end machine learning platform for customer churn prediction that demonstrates production-grade:

- temporal machine learning
- data and feature validation
- experiment tracking and model lineage
- model monitoring and drift detection
- incident investigation
- controlled retraining
- champion/candidate model management
- human approval workflows
- canary deployment and rollback
- ML reliability and agent evaluation

## Machine Learning Task

Binary classification:

> Predict the probability that a customer will churn.

The initial dataset is the **KKBox Churn Prediction** dataset.

## Architecture

```text
React + TypeScript
        |
     FastAPI
        |
  +-----+-----+----------------+
  |           |                |
Monitoring   ML Pipeline    Agent API
  |           |                |
Evidently   DVC / S3        LangGraph
Prometheus
Grafana
        |
      MLflow
        |
   PostgreSQL