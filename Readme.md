# Insurance Churn, Retention ROI & 3-Year CLV Strategy

## Author’s Note
This repository documents an end-to-end insurance analytics and financial strategy initiative.  
The work is structured to mirror how senior analytics, finance, and strategy teams present insights to executive leadership.

The analysis moves deliberately from **data → insight → financial impact → executive action**.

---

## 1. Business Context & Objective

Insurance profitability is increasingly challenged by:
- Rising customer acquisition costs
- High churn in early and mid-tenure cohorts
- Retention programs driven by churn signals rather than financial value

The core executive question addressed in this work is:

> **Where should retention capital be deployed to maximise long-term value while avoiding value-destructive incentives?**

---

## 2. Datasets Used (Full Transparency)

The analysis integrates multiple operational datasets commonly found in large insurance organisations.

### Customer & Demographics
- **customer.csv**  
  Core policyholder identifiers, tenure, premium amounts
- **demographic.csv**  
  Age, income, household attributes, credit indicators
- **address.csv**  
  Geographic attributes for stability and risk proxies

### Churn & Policy Lifecycle
- **termination.csv**  
  Policy termination and churn indicator
- **autoinsurance_churn.csv**  
  Churn-labelled insurance dataset used for modelling validation

### Claims & Risk Attributes
- **Insurance claims data.csv**  
  Vehicle characteristics, safety features, claim status
- **tic_2000_train / eval / target datasets**  
  Benchmark datasets for classification structure and validation

> **Note:** Raw customer data is intentionally excluded from this repository for confidentiality.  
> Only derived features and models are shared.

---

## 3. Analytical Phases & What Was Created

---

### Phase 2 — Customer Feature Engineering  
**Notebook:** `phase_2_customer_features.ipynb`

**What was done**
- Unified customer, demographic, and address data
- Created business-relevant features:
  - Tenure (years)
  - Tenure bands: New / Early / Mid / Loyal
  - Age bands
  - Income bands
  - Premium bands
  - Credit risk indicators
  - Family and home ownership stability flags

**Outcome**
- A clean, analytics-ready customer base (>2M records)
- Features aligned with how insurers think about risk and value

---

### Phase 3 — Claims & Risk Feature Engineering  
**Notebook:** `phase_3_claims_risk_features.ipynb`

**What was done**
- Processed vehicle and claims datasets
- Created:
  - Safety score (airbags, ESC, TPMS, braking assist, etc.)
  - Vehicle age bands
  - Regional risk density bands
  - Claim occurrence flags

**Outcome**
- Risk-adjusted customer profiles
- Separation of behavioural churn drivers from underwriting risk

---

### Phase 4 — Churn Analysis & Feature Consolidation  
**Notebook:** `phase_4_churn_analysis.ipynb`

**What was done**
- Integrated customer, risk, and claims features
- Prepared final churn modelling dataset
- Addressed class imbalance explicitly

**Outcome**
- Modelling dataset suitable for interpretable churn prediction

---

### Phase 5 — Churn Modelling (Python)  
**Notebook:** `phase_5_models.ipynb`

**Model**
- Logistic Regression (chosen for interpretability over black-box accuracy)

**Key Results**
- Recall on churners ≈ **67%**
- Model intentionally optimised for **business explainability**
- Produced **individual churn probabilities** (not just labels)

**Key Insight**
> Tenure and pricing position are stronger churn drivers than income alone.

---

### Phase 6 — Retention ROI & Financial Modelling (Excel)  
**File:** `phase_6_retention_clv_model.xlsx`

This phase translates analytics into **financial decisions**.

#### What was calculated
- Expected Revenue at Risk  
  *(Annual Premium × Churn Probability)*
- Retention Cost (10% incentive assumption)
- Net Retention ROI
- Retention Priority (High / Medium / Low)

#### Aggregate Financial Findings (Annual)
- **Total Revenue at Risk:** €21.7M
- **Estimated Retention Cost:** €4.68M
- **Net Retention ROI:** €17.0M

> Retention is economically justified, but **not uniformly across segments**.

---

### Phase 7 — 3-Year Customer Lifetime Value (CLV)

A forward-looking value model was introduced to avoid short-term bias.

#### CLV Model
- 3-year horizon
- Probability-adjusted revenues
- Retention costs included
- **10% discount rate (NPV-based)**

#### Key CLV Findings
- **Total 3-Year NPV CLV:** ~€23.5M
- Loyal customers generate **6–7×** the CLV of new customers
- New customers show highest churn (~67%) but lowest lifetime value

---

## 4. Quantified Strategic Findings (CEO-Level)

### 1. Value Concentration Is Extreme
- Loyal segment contributes **~60%+ of total CLV**
- New segment contributes <10% of total CLV despite high churn

### 2. Churn ≠ Investment Priority
- High churn does not automatically justify spend
- CLV-adjusted ROI materially changes priorities

### 3. Tenure Is the Primary Value Multiplier
- Each additional year of tenure dramatically improves lifetime value
- Tenure protection is more effective than reactive discounting

### 4. Pricing Tier Matters More Than Income
- Medium and high premium customers consistently outperform low premium segments in CLV
- Income alone is a poor proxy for retention value

---

## 5. Executive Recommendations

### Immediate (0–6 Months)
- Prioritise retention for **Loyal & Mid-tenure customers with medium/high premiums**
- Eliminate blanket discounts for New and low-value segments
- Embed churn probability + CLV into CRM decisioning

### Medium Term (6–18 Months)
- Develop tenure-acceleration programs
- Align underwriting, pricing, and retention strategies
- Monitor CLV by cohort quarterly

### Long Term (18+ Months)
- Institutionalise NPV-based CLV in financial planning
- Use predictive CLV to guide acquisition strategy
- Shift retention budgeting from cost-based to value-based governance

---

## 6. Executive Conclusion

This analysis reframes churn from a behavioural problem into a **capital allocation problem**.

The data demonstrates that:
- Retention investments must be prioritised, not universal
- Long-term value (CLV) is a more reliable guide than churn alone
- Financial discipline materially improves retention ROI

> **Sustainable profitability comes from retaining the right customers, not the most vocal ones.**

---

## 7. Tools & Technologies
- Python (Pandas, Scikit-learn)
- Microsoft Excel (Financial & CLV modelling)
- Power BI (Executive dashboards)
- GitHub (Documentation & governance)

---

## 8. Intended Audience
- Executive Leadership
- Strategy & Finance Teams
- Senior Business & Data Analysts
