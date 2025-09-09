# SaaS Subscription and Churn Analysis

Data-driven deep dive into a SaaS business: who churns, why they churn, what it costs, and where to intervene for retention and revenue.

## 🔍 What’s in this project

- **Notebook**: `notebooks/SaaS Subscription and Churn Analysis.ipynb`
- **Raw data** (CSV):
  - `ravenstack_accounts.csv`
  - `ravenstack_subscriptions.csv`
  - `ravenstack_churn_events.csv`
  - `ravenstack_feature_usage.csv`
  - `ravenstack_support_tickets.csv`
- **Processed data** (created by the notebook):
  - `merged_saas_dataset.csv`
  - `cleaned_saas_dataset.csv`
  - `enhanced_saas_dataset.csv`

## 🧠 Key questions answered

- How bad is churn and where is it worst?
- Which plan tiers, geographies, and industries are bleeding revenue?
- What usage, support, and lifecycle signals predict churn?
- Where should the product team and CX team focus first?

## 📈 Core metrics & visuals

- Churned vs Active Customers
- Top 10 Churn Reasons
- MRR Distribution by Plan Tier and Revenue at Risk from Churn
- Subscription Duration vs Churn
- Error Rate vs Churn Status (keep error rate < 1%)
- Churn Rate by Industry, by Plan Type, by High-Value Accounts
- Upgrade/Downgrade Trends and Trial Conversion Rate
- Geo Revenue (Top 10 Countries)

## 🧪 Feature engineering (highlights)

Derived columns used throughout the analysis, including:
- `is_churned`, `is_active`, `subscription_duration_days`
- `billing_frequency`, `revenue_per_seat`, `MRR`-related aggregations
- Trial/upgrade/downgrade flags: `preceding_upgrade_flag`, `preceding_downgrade_flag`, `is_reactivation`
- Support/quality signals: `error_count`, `error_rate`, `support_ticket_flag`, `first_response_time_minutes`, `resolution_time_hours`, `escalation_flag`, `satisfaction_score`
- Usage signals: `usage_count`, `avg_usage_per_day`, `is_beta_feature`

## 🧾 Takeaways

- **Churn is ~80%** of the customer base. Catastrophic.
- **Enterprise tier** drives most MRR and the biggest revenue loss when churned. Treat it like VIP.
- **EdTech** shows the **highest churn rate**; **HealthTech** is more stable.
- **Error rate > 1% → churn spikes.** Reliability is non-negotiable.
- **Premium/high-value accounts churn slightly more** (~+5%) — they need white-glove care.
- Trials, long-tenure cliffs (≈200 & 800+ days), and downgrades are **clear churn triggers**.

## 🗂️ Project structure

```
.
├─ data/
│  ├─ raw/               # put the 5 ravenstack_*.csv here
│  └─ processed/         # notebook writes merged/cleaned/enhanced here
├─ notebooks/
│  └─ SaaS Subscription and Churn Analysis.ipynb
├─ reports/
│  └─ figures/           # optional: save charts here
├─ src/                  # optional: helper scripts if modularized
├─ requirements.txt
└─ README.md
```

## ⚙️ Environment

- Python 3.12+
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `jupyter`

## ▶️ How to run

1. Clone the repo and `cd` into it.
2. Create a virtual env:
   ```bash
   python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
   ```
3. Install deps:
   ```bash
   pip install -r requirements.txt
   ```
4. Put the 5 raw CSVs into `data/raw/`.
5. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook
   ```
6. Run all cells. Outputs/processed CSVs will be created as coded in the notebook.

## 📌 Roadmap

- Convert heavy notebook steps into reusable functions in `src/`.
- Add unit tests for feature engineering.
- Export key charts to `reports/figures/` automatically.
- Optional: lightweight Streamlit dashboard for exec summaries.

## 📄 License

MIT
