# PhonePe Pulse Analysis: Decoding India’s Digital Payment Shift (2018–2021)

I wanted to see what India's move to digital payments actually looks like in real data, so I picked the PhonePe Pulse dataset and worked through it in a Jupyter notebook. It covers 36 states and union territories across 742 districts, from 2018 Q1 to 2021 Q2.

The notebook goes from data validation and cleaning to core operational questions: which states drive the bulk of volume, how payment use-cases evolved, which handset brands dominate user sign-ups, and whether population size or urban density better explains adoption.

---

## What I Found

* **Growth was fast:** Quarterly transactions scaled from 134 million in 2018 Q1 to 3.94 billion in 2021 Q2 (~29x growth). There was one visible dip—a 10.75% fall in 2020 Q2—which lines up with the national lockdown period (the data alone describes the correlation, not direct causation).
* **Payment use-cases shifted:** Merchant payments rose from 4.0% to 38.0% of total transactions, while recharge and bill payments dropped from 54.0% to 17.4%. Peer-to-peer (P2P) remained the largest individual category in most quarters.
* **Volume is concentrated:** Karnataka, Maharashtra, and Telangana together account for about 39.7% of all transaction volume, and the top ten states account for 80.3%.
* **Big states have massive headroom:** Only 15 of 36 states/UTs sit at or above the national registered users-to-population benchmark of 24.7%. Major population centers like Uttar Pradesh (15.4%), Bihar (14.4%), and West Bengal (19.4%) would require roughly 34.6 million additional registered users collectively just to match the national average.
* **Handset ecosystem is heavily concentrated:** Xiaomi, Samsung, Vivo, Oppo, and Realme account for 82.8% of registered user devices in 2021 Q2, up from 73.1% in 2018 Q1.
* **Conversion from app opens rose:** The ratio of completed transactions to total app opens increased from 31.8% in 2019 Q3 to 40.9% in 2021 Q2.
* **Population matters far more than density:** At the district level, total population shows a strong Spearman rank correlation of **0.79** with transaction volume, whereas population density only reaches **0.42**. Addressable market size drives transactions significantly more than crowded urban density alone.

---

## Dataset Overview

The data comes from the PhonePe Pulse project, structured across five Excel sheets:

| Sheet Name | Content |
| :--- | :--- |
| `State_Txn and Users` | Transactions, amount, registered users, and app opens by state and quarter |
| `State_TxnSplit` | Transactions by category (P2P, Merchant, Recharge & Bills, Financial Services, Others) |
| `State_DeviceData` | Registered users by phone brand, state, and quarter |
| `District_Txn and Users` | Transaction count, volume, and registered users at district level |
| `District Demographics` | District population census metrics, area, and population density |

### Important Context on Metrics
1. **"Users" = Registered Users:** Figures reflect sign-ups, not monthly active users (MAU).
2. **PhonePe Scope:** The data reflects PhonePe platform volume specifically, not aggregate UPI network data.
3. **Census Normalization:** Population baselines use census figures, making per-capita metrics an analytical proxy rather than real-time census data.
4. **App Opens Telemetry:** App opens are recorded as 0 prior to 2019 Q3, so earlier quarters are excluded from engagement and conversion analysis.

---

## Data Cleaning & Validation

* **Recovering Missing Value:** The transaction amount for Andhra Pradesh in 2021 Q1 was missing in the state table. I recovered it by aggregating the same state and quarter across both the transaction-type sheet and the district sheet. Both independently matched to the exact rupee, confirming the imputed value.
* **Cross-Sheet Reconciliations:** Reconciled district-level transaction counts, rupee amounts, and user registrations against their parent state records across all state-quarters to verify integrity before analysis.

---

## Repository Structure

```text
├── phonepe_pulse_analysis.ipynb
├── phonepe-pulse_raw-data_q12018-to-q22021-v0-1-5-1720351752.xlsx
├── district_code_mapping.csv
└── README.md)
```
## Limitations

* **Correlation, not causation:** These findings highlight observed patterns. For example, merchant payments are higher in states with more registered users, but the data alone cannot prove whether merchant supply or consumer demand drove that growth.
* **Time frame:** The data ends at Q2 2021, so newer features like UPI Lite, RuPay on UPI, and post-2021 trends are not covered.

---

## About Me

I built this project to work through real-world payment data and build practical experience in Python, Pandas, and exploratory data analysis.

Feedback or suggestions are always welcome—feel free to open an issue or reach out on [LinkedIn](www.linkedin.com/in/mohommed-rasheed-analyst).

