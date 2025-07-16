## 📊 Score Distribution Overview

The histogram below represents the number of wallets in each score range bucket (0–1000):

![Wallet Score Distribution](assets/score_distribution.png)

As seen:
- Most wallets fall in the **200–600** range
- Few wallets score below **100** (likely bots/liquidation-prone)
- Top-scoring wallets (800+) show strong reliability

### 🔝 High-Scoring Wallets (800–1000)
- Consistently repay borrowed assets
- Minimal to no liquidation events
- Long active history (many days between first and last transaction)
- High borrow and repay volumes
- Actively deposit and redeem assets

### ⚠️ Low-Scoring Wallets (0–200)
- Frequently liquidated
- High borrow amount with little or no repay
- Minimal activity span (few days or single action)
- Possibly bot-like or risky exploit behavior

---

## 🧠 Observations

- Mid-range scores (400–700) include many passive users (only deposit/redeem)
- Reliable wallets tend to interact with multiple Aave functions and maintain healthy ratios
- Liquidation is the biggest red flag driving scores down
