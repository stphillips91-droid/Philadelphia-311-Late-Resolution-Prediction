# Philadelphia 311 Late Resolution Prediction

> Analyzing Philadelphia 311 service requests and estimating which new requests are at risk of late resolution.

---

## Overview

This project analyzes Philadelphia 311 service requests from 2023–2025 and builds classification models to estimate the risk that a request will be resolved after its expected completion date. It combines exploratory analysis with a year-based evaluation to examine both the usefulness and the limitations of the predictions.

---

## Business Problem

City service teams need to understand which types of requests are most likely to be completed late and where earlier attention may help. Identifying higher-risk requests at intake could support prioritization and workload planning.

A model would need to perform reliably on future requests before being used to guide those decisions. This project therefore evaluates performance on a later year of data rather than relying only on a random split of historical records.

---

## Objectives

- Explore late resolution patterns across request types and years
- Prepare and validate features available when a request is submitted
- Compare a no-skill baseline, logistic regression, and gradient boosting
- Evaluate how well the models perform on later-year requests
- Identify practical uses and limitations of the results

---

## Technologies Used

| Category | Technologies |
|---|---|
| Language | Python |
| Data analysis | pandas |
| Machine learning | scikit-learn |
| Development | Jupyter Notebook |
| Version control | Git, GitHub |

---

## Data

The analysis uses the City of Philadelphia's 311 Service and Information Requests data for 2023, 2024, and 2025.

**Source:** https://opendataphilly.org/datasets/311-service-and-information-requests/

The yearly files were combined and cleaned before analysis. Requests classified as “Information Only” and records without the dates required to determine late resolution were excluded. Model features were limited to information available at intake.

The raw data files are included in this repository.

---

## Repository Structure

```text
philadelphia-311-late-resolution/
├── 311prediction.ipynb
├── written_report.pdf (coming soon)
├── README.md
└── public_cases_fc_2023.csv (coming soon)
└── public_cases_fc_2024.csv (coming soon)
└── public_cases_fc_2025.csv (coming soon)
```

## Methodology

Combine the 2023–2025 request files and check data quality.
Define late resolution using the request's expected and actual completion dates.
Explore late resolution rates across years, service types, and other intake characteristics.
Prepare intake-time features and build preprocessing and modeling pipelines.
Train on 2023 requests, validate on 2024 requests, and test on 2025 requests.
Compare a no-skill baseline, logistic regression, and gradient boosting using ROC-AUC and other classification metrics.
Review the results and their implications for operational use.

## Results

Gradient boosting performed slightly better than logistic regression during validation, reaching approximately 0.71 ROC-AUC on 2024 requests. On the 2025 test set, its ROC-AUC declined to approximately 0.61. Logistic regression also declined on the later-year data.

The models showed some ability to distinguish higher-risk requests, but the drop in test performance limits confidence in applying them to future requests without further investigation and monitoring. The decline is evidence that performance changed across the evaluated years; it does not, by itself, establish the cause.

## Key Features

Exploratory analysis of multi-year service request data
Features limited to information available at request intake
Chronological training, validation, and test sets
Comparison against a no-skill baseline
Evaluation of model performance on later-year data
Discussion of how model limitations affect business recommendations

## Lessons Learned

This project strengthened my understanding of:

Defining a prediction problem around a real operational decision
Checking data quality before interpreting patterns
Preventing future information from entering intake-time predictions
Evaluating models on data from later periods
Communicating model limitations alongside performance results
Future Improvements
Investigate why performance changed on 2025 requests
Evaluate additional years of data, if available
Examine performance by service type and other relevant groups
Test whether different features or retraining schedules improve later-year performance
Assess how a risk ranking could be incorporated into a real service workflow

## About Me

I hold an M.S. in Data Analytics with an emphasis in Data Science from Western Governors University. My interests include data science, business analytics, and turning analytical findings into practical recommendations.
