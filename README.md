# Aave V2 Credit Scoring Challenge

## Overview

This project aims to build a credit scoring model that assigns a score between **0 and 1000** to each wallet based on its historical interaction with the Aave V2 protocol. The model is trained using transaction-level data, identifying trustworthy vs. risky wallet behavior based on features such as borrow patterns, repayment behavior, and liquidation calls.

## Objective

* Load raw JSON transaction data.
* Engineer features per wallet based on transaction patterns.
* Train a machine learning model to generate scores.
* Normalize scores into a 0–1000 range.
* Save final scores as a CSV.

---

## Folder Structure

```
aave-credit-scoring/
├── data/
│   ├── user-wallet-transactions.json     # Raw input JSON (renamed or alias OK)
│   ├── wallet_scores.csv                 # Output CSV from scoring
├── src/
│   └── score_generator.py                # Scoring script
├── assets/
│   └── score_distribution.png            # Score distribution chart
├── score_distribution_plot.py            # Plotting script
├── requirements.txt                      # Python dependencies
├── readme.md                             # Challenge overview + instructions
├── analysis.md                           # Deep-dive behavior + insights

```

---

## How to Run

### 1. Install Python dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the scoring script

```bash
python src/score_generator.py --input data/user_transactions.json --output data/wallet_scores.csv
```

### 3. Output

You will get a CSV file like this:

```csv
user,score
0xabc123..., 832
0xdef456..., 174
```

---

## Feature Engineering

We created behavioral features at the wallet level:

* **Transaction frequency:** total number of actions
* **Action breakdown:** deposit, borrow, repay, liquidationcall, redeemunderlying
* **Active duration:** days active on Aave
* **Borrow/Repay ratio:** incomplete or risky repayment
* **Average borrow size**
* **Liquidation count:** indicator of risky behavior

---

## Model Used

We used **RandomForestRegressor** from scikit-learn. It handles non-linear relationships and is interpretable.

* The raw output is normalized to a range of **0–1000** using `MinMaxScaler`.
* This final score represents the wallet’s trustworthiness.

---

## Scoring Philosophy

* **Higher scores (800–1000):** Consistent repayments, low liquidation, frequent deposits.
* **Lower scores (0–300):** Bot-like repetitive patterns, incomplete repayment, frequent liquidations.
* **Medium scores (400–700):** Mixed behavior, typically newer or mid-risk wallets.

---

## Limitations

* No supervision labels were available — model assumes typical DeFi best practices.
* Market conditions (e.g., price volatility) are not considered.

---

## Future Enhancements

* Add supervised learning with known ground-truth credit data.
* Use clustering to pre-label good vs. bad actors.
* Integrate additional DeFi protocols for holistic scoring.

---

## Author

Diksha Nagvekar
Email: [dikshanagvekar999@gamil.com]
