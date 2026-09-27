# Analytics Intern Assignment

## Overview

Analytical take-home assignment for a live-service mobile game.

The analysis focuses on four areas:

1. Game health, retention, monetization, and rewarded ads
2. Promotion/sales incrementality
3. Acquisition channel quality
4. 14-day player churn prediction

The analysis uses SQL and Python and emphasizes reproducible analysis, statistical reasoning, data-quality validation, and business interpretation.

---

## Project Structure

```text
analysis/       Exploratory analysis, profiling, and analytical decision log
deliverables/   Final reproducible Python analyses for Deliverables 1–4
sql/            Production SQL and investigation queries
outputs/        Tables, charts, and model evaluation outputs
models/         Trained model artifacts
```

## Key Findings

1. Game Health
Top 1% of paying players generated approximately 9.44% of observed revenue.
Top 10% generated approximately 48.08%.
Top 50% generated approximately 90.23%.
Retention metrics were calculated using right-censored cohort denominators.
Rewarded-ad cap attainment was evaluated using observed cap state.


3. Promotions

Promotion periods showed substantially higher observed ARPDAU and purchaser conversion.

However, the analysis is observational and therefore cannot establish causal incremental revenue.

A post-promotion analysis did not show an aggregate deficit consistent with a simple one-for-one timing-shift explanation.

The recommended next step is a randomized eligible-player holdout experiment.


3. Acquisition Channels

Raw D7 revenue differed across acquisition channels, but channel populations had materially different country-tier, platform, and install-month compositions.

After standardizing to a common observed mix, the revenue differences between channels were not statistically distinguishable from zero.


4. Churn Prediction

A logistic regression model was evaluated using a chronological holdout.

ROC-AUC: 0.752
PR-AUC: 0.343
Test churn prevalence: approximately 14.5%
Top 10% risk decile: approximately 41.0% observed churn
Top 20% risk: approximately 49.1% cumulative churn capture

The model is therefore used as a targeting/ranking tool rather than as a causal intervention model.


## Reproducibility

The raw CSV data is not included in this repository.

To reproduce the analysis:

Place the provided CSV files in csv/.
Install dependencies:
pip install -r requirements.txt
Build the DuckDB analytical database:
python analysis/setup_database.py
Run the relevant deliverable scripts under deliverables/.

See the individual scripts and SQL files for details.
