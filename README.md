# DRW Crypto Market Prediction

> Develop a model capable of predicting crypto future price movements using anonymized microstructure features.

**Competition:** [DRW - Crypto Market Prediction](https://www.kaggle.com/competitions/drw-crypto-market-prediction) hosted on Kaggle by [DRW](https://drw.com)

---

## Repository Contents

| Notebook | Author | Description |
|---|---|---|
| `drw-24th-place-in-the-private-lb.ipynb` | ELOIARMYOUNES | 24th place solution on private leaderboard |
| `drw-2nd-place-in-the-private-lb.ipynb` | ELOIARMYOUNES | 2nd place solution on private leaderboard |
| `drw-gasman-rnd-v1.ipynb` | gastondana627 | GasMan R&D fork – EDA, Plotly viz, microstructure analysis |

---

## GasMan R&D Notebook (`drw-gasman-rnd-v1.ipynb`)

A research extension built on top of the original 2nd place solution by [@ELOIARMYOUNES](https://github.com/ELOIARMYOUNES).

### What was added

**Pipeline restructure:**
- Split the original single-cell script into clearly labeled cells (Cell 1–7)
- `main()` now returns all key variables (`train_df`, `train_clean`, `test_df`, `model`, `X_train`, `y_train`, `X_test`) for downstream analysis

**Additional microstructure features:**
- `kyle_lambda` – order flow normalized by volume (market impact proxy)
- `flow_toxicity` – absolute order flow imbalance scaled by volume
- `market_stress` – volume/depth ratio weighted by imbalance magnitude
- `signed_volume` – directional volume (sign of net order flow × volume)
- `directional_volume` – net order flow × log volume
- `adverse_selection_proxy` – price impact scaled by volume
- `market_efficiency` – volume normalized by bid-ask spread

**Interactive visualizations (Plotly):**
- Label distribution histogram with mean and ±1σ lines
- Label box plot, CDF, and stats table (4-panel dashboard)
- Top 30 feature correlations with label (horizontal bar chart)
- Residual distribution + residuals vs predicted scatter
- Log volume vs label colored by order flow imbalance

**Documentation:**
- Markdown cells after each visualization explaining observations and implications for model R&D
- Attribution header citing original author and competition

### Baseline Results

| Model | Train MSE |
|---|---|
| LinearRegression (baseline) | 0.005608 |
| RandomForest (300 trees, depth 12) | TBD |
| XGBoost (500 trees, depth 8) | TBD |

---

## Setup

This repo is designed to run on **Kaggle** with the competition dataset attached as input.

**Required datasets:**
- `drw-crypto-market-prediction` (competition data)
- `best-time-training-unique-model-01` (time filter dataset by original author)

**Dependencies:**
```bash
numpy
pandas
scikit-learn
xgboost
plotly
matplotlib
```

---

## Credits

- **Original solution:** [ELOIARMYOUNES](https://www.kaggle.com/eloiarmyounes) — 2nd place on private leaderboard
- **Original Kaggle notebook:** [DRW: 2nd Place in the Private LB](https://www.kaggle.com/code/eloiarmyounes/drw-2nd-place-in-the-private-lb)
- **R&D fork:** [gastondana627](https://github.com/gastondana627)
- **Competition host:** [DRW](https://drw.com) via Kaggle

---

## PR

Open PR from this fork: [#1 – feat: add GasMan R&D notebook](https://github.com/ELOIARMYOUNES/Kaggle---DRW---Crypto-Market-Prediction/pull/1)