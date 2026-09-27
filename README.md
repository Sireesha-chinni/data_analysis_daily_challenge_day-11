# Day 11 – Excel Data Analyst Challenge: Insurance Claim Incident Analysis — Power BI Report

A Power BI dashboard analyzing insurance policy and claim data to surface trends in claim frequency and value, customer/location risk segments, fraud patterns, and the relationship between policy terms and claims.

## Files

| File | Description |
|---|---|
| `day-11-challenge_power_bi.pbix` | Power BI report — data model, measures, and both report pages |
| `Insurance_and_Claim_Incident_Analysis.pdf` | Original challenge brief |

## Dataset

Single flat table (`insurance`) with fields covering:

- **Policy** — policy number, state, annual premium, deductible, umbrella limit, bind date
- **Insured** — age, zip, occupation, education level, hobbies, sex, relationship
- **Incident** — date, type, severity, state/location, hour of day, property damage, injuries
- **Claim** — total claim amount, broken down into injury / property / vehicle claims
- **Vehicle** — make, model, year
- **Fraud** — fraud reported flag (Y/N)

## Measures

| Measure | Definition |
|---|---|
| `Total policies` | Count of distinct policies in the dataset |
| `Fraud Rate` | Share of claims flagged as fraudulent |

> Add a `Loss Ratio` measure (`SUM(total_claim_amount) / SUM(policy_annual_premium)`) if you want to extend the premium-vs-claims analysis further.

## Report pages

### Page 1 — Claims Overview
- **Card** — Total policies
- **Bar chart** — Claim count by policy state
- **Bar chart** — Claim count by incident type / severity
- **Clustered column chart** — Total claim amount by fraud status, hobbies, and sex
- **Column chart** — Total claim amount by insured relationship
- **Slicers** — Policy state, incident state

### Page 2 — Fraud & Risk Analysis
- **Line chart** — Average claim amount vs. annual premium
- **Column chart** — Claim/injury counts by state and incident date (year/quarter/month/day)
- **Line chart** — Average capital-loss by fraud status
- **Clustered bar chart** — Age by education level and occupation
- **Filled map** — Claim value and fraud rate by incident state
- **Slicers** — Policy state, incident state

## Key business questions addressed

1. **Claim trends** — by state, incident type, and time (Claims Overview + date hierarchy on Page 2)
2. **Highest-risk segments/locations** — map by incident state, fraud rate by hobbies/sex/relationship
3. **Fraud distribution and common factors** — fraud-split charts by hobbies, sex, and capital-loss
4. **Policy terms vs. claims** — average claim amount vs. annual premium trend

## Findings & recommendations

> Fill this section in with the specific numbers your visuals surface — e.g., which states/incident types have the highest claim counts, which hobbies or demographics correlate most with fraud, and whether higher premiums track with higher or lower claim amounts. A few sentences per bullet is enough for a management-facing summary.

- **Claim trends:**
- **Highest-risk segments/locations:**
- **Fraud patterns:**
- **Premium/deductible relationship:**
- **Recommendations:**

## How to use

1. Open `day-11-challenge_power_bi.pbix` in Power BI Desktop.
2. Use the **Policy State** and **Incident State** slicers on either page to filter all visuals.
3. Hover the map on Page 2 for per-state claim value and fraud rate.
4. Refresh the data model (**Home → Refresh**) if the underlying CSV has changed.

## Known gaps / next steps

- No dedicated summary/insights page with narrative text for management — add one to fully satisfy the deliverable list.
- `deductible` and `umbrella_limit` aren't yet used in any visual — could support the policy-terms-vs-claims question further.
- No policy-type slicer (dataset doesn't include an explicit "policy type" column; consider using `policy_csl` or `auto_make`/`auto_model` as a proxy if useful).
