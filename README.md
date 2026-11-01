# Bursa Malaysia Sectors vs Bank Negara OPR — Data Profiling (EDA)

TTTC3213 Data Engineering · Assignment 1 · Universiti Kebangsaan Malaysia

| Name | Matric No. |
|---|---|
| RAVINRAJ A/L VASU | A212782 |
| CHARAN BAHADUR NEWAR A/L KARNA BAHADUR NEWAR | A211997 |
| ADAM BUKHARY BIN MOHAMMAD SHAHRUL NIZAM | A213606 |
| MUHAMMAD SYAMIL BIN MOHD ZAIDI | A213608 |

## Scenario
An investment firm wants to track how stocks in different Bursa Malaysia sectors behave before and after Bank Negara Malaysia's OPR announcements, so it can identify rate-sensitive sectors and adjust client portfolios faster. This notebook profiles and cleans the data for that scenario: missing values, outliers, duplicates, wrong types, inconsistent sector labels, and PII/bias risks.

## Data sources
| Data | Source | How obtained |
|---|---|---|
| Daily prices, dividends, splits (20 stocks + FBM KLCI) | [Yahoo Finance](https://finance.yahoo.com/quote/1155.KL) | `yfinance` Python library |
| Yahoo sector labels | [Yahoo Finance profile](https://finance.yahoo.com/quote/1155.KL/profile) | `yfinance` `Ticker.info` |
| Official Bursa sector per stock | [Bursa Malaysia](https://www.bursamalaysia.com/market_information/equities_prices) | Entered manually |
| OPR decisions since 2018 | [Bank Negara Malaysia](https://www.bnm.gov.my/monetary-stability/opr-decisions) | Transcribed from Monetary Policy Statements |

## How to run
```bash
git clone <this-repo-url>
cd <repo-folder>
pip install -r requirements.txt
jupyter notebook data_profiling.ipynb
```
Then choose **Kernel → Restart & Run All**.

- The first run downloads data from Yahoo Finance (needs internet, about 1–2 minutes) and saves it to `data/raw/`.
- Later runs read from `data/raw/`, so the notebook gives the same results offline. Delete `data/raw/` to download fresh data.

## Repository structure
```
├── data_profiling.ipynb     # the report
├── requirements.txt
├── data/
│   ├── raw/                 # untouched downloads (created on first run)
│   └── processed/           # cleaned output for the capstone pipeline
└── figures/                 # saved diagnostic charts
```

## Notebook contents
1. Scenario
2. Data source
3. Profiling and issue handling — data types, duplicates, invalid values, missing values, outliers, inconsistent categories, OPR event alignment
4. Diagnostic charts — missing-value heatmap, return histogram with IQR fences, sector boxplots, sector-label crosstab, group balance
5. PII and bias risks
6. Conclusion
