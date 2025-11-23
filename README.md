# Mira – MLOps Pipeline

**Mira** is the MLOps star of the Constellation System — a cyclic, self-renewing workflow inspired by the variability of the star Mira.  
It implements a lightweight, production-ready MLOps lifecycle on AWS with an emphasis on clarity, repeatability, and safe model promotion.

---

## Overview

Mira provides a minimal but extensible MLOps baseline designed around atomic, observable, and failure-resistant training workflows.

The system focuses on:

- **Data ingestion**
- **Training & evaluation**
- **Artifact storage**
- **Model promotion rules**
- **Optional inference service refresh**

It is designed to be reusable as a core module for future ML/AI projects within the Constellation architecture.

---

## Scope

### Core Pipeline
- Prefect Flow (data → train → evaluate → artifact upload)
- S3-based model and artifact storage
- Metrics comparison for model promotion
- Atomic updates (only promote on success)

### Data & Validation
- Optional Great Expectations schema validation
- Fail-fast behavior on invalid data or schema drift

### Drift Monitoring (optional)
- Evidently reports stored in S3
- Can be executed on a scheduled basis (Prefect or CloudWatch Events)

### Integration Targets
- Can trigger downstream refresh (e.g., inference deployment in Alphard)
- Can be extended to feature transformation or embedding generation

---

## Stack

**Language**
- Python (Prefect tasks, data processing, training)

**AWS Services**
- S3 (data + model artifact store)
- CloudWatch (logs, optional scheduler)
- ECS / Fargate (optional training container runtime)
- IAM (least-privilege roles)
- ECR (training image registry)

**Optional**
- Great Expectations
- Evidently AI

---

## Structure

(To be completed after v0.2)

Suggested layout:

```bash
mira-mlops/
  flows/
  tasks/
  models/
  artifacts/
  expectations/     # optional Great Expectations checks
  infra/            # optional Terraform for S3/IAM
  docs/
```

## Status

### 0.2 — Pipeline work in progress
- Repo renamed to Mira
- Preparing Prefect pipeline
- Defining S3 model registry structure

### 0.1 — Repository initialized
