# Aurora Finance — ML Capstone Project

## Project Context

This is an IIT Bombay Executive PG Diploma capstone project for "Aurora Finance",
a fictitious mid-size financial services firm. We are a team of 5 building an
integrated ML-driven decision support system across 4 business modules plus
a unified dashboard.

**Deadline: May 19, 2026.**

## Team & Ownership

- Jayshree: Module 1 (Banking — Credit Risk + Fraud) — DONE
- Nikhil: Module 2 (Corporate Finance) — status uncertain
- Kiran + Kartik (me): Module 3 (Financial Markets)
- Kartik (me): Module 4 (Derivatives) — to be built
- Khushee: Module 5 (Integrated Dashboard)
- Jayshree: Executive deck and report

## Folder Structure

- `data/` — raw CSVs from professor (read-only inputs)
- `notebooks/` — one notebook per module
- `outputs/` — generated CSVs that feed the dashboard
- `dashboard/` — Streamlit app (app.py)

## Module Output Contracts (CSVs feeding the dashboard)

Each module exports to `outputs/` with these schemas:

- `risk_scored_portfolio.csv`: Loan_ID, Customer_Type, Annual_Income, Loan_Amount, 
  Debt_to_Income, Past_Default, PD_engineered, PD_predicted, Credit_Score, 
  Credit_Grade, Decision
- `fraud_alerts.csv`: Transaction_ID, Customer_ID, Amount, Transaction_Type, 
  Timestamp, Fraud_Prob_RF, Anomaly_Score, Hybrid_Score, Alert_Priority, Fraud_Engineered
- `project_rankings.csv`: Project_ID, Department, Investment_Cost, Predicted_NPV, 
  Success_Prob, EV_Score, Risk_Rating, Recommendation, Rank
- `portfolio_weights.csv`: Company, Weight, Expected_Return, Volatility, Sharpe_Contribution
- `hedging_recommendations.csv`: Ticker, Option_Type, Strike, Expiry, BS_Price, 
  ML_Price, Delta, Hedge_Shares, VaR_95, Hedge_Action

## Critical Methodology Standards

This project will be evaluated by IIT Bombay faculty. Methodological rigor matters
more than ML accuracy (the data is intentionally thin).

- NO look-ahead bias. Use `merge_asof` with `direction="backward"` for time joins.
- Train/test splits MUST be temporal, not random, for time-series data.
- Backtests MUST include transaction costs (10 bps round-trip minimum).
- For walk-forward validation, retrain quarterly minimum.
- Document every methodological choice in markdown cells.
- Use SHAP for explainability (executive audience requirement).

## Python Environment

- Python 3.11 in `venv/`
- Activate: `source venv/bin/activate`
- Key packages: pandas, numpy, scikit-learn, xgboost, shap, plotly, streamlit, scipy

## Style for ML Notebooks

Follow Jayshree's pattern from `notebooks/module1_credit_risk.ipynb`:
- Markdown cells explaining WHY before each code section
- Imports in cell 1
- EDA before modeling
- Multiple models compared (RF, LR, XGBoost minimum)
- Cost-based decisions where applicable
- SHAP plots
- Final CSV export to `outputs/`
- Executive summary in final markdown cell