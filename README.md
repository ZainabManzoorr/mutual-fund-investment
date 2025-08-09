# Mutual Fund Comparison – Synthetic Data Analysis

## Overview
This project compares three synthetic mutual funds (NAVfund1, NAVfund2, NAVfund3) to demonstrate how to evaluate investment performance using key risk and return metrics.  
Although the data is synthetic, it is modeled to mimic realistic Net Asset Value (NAV) behavior — including market drift, volatility, and drawdowns.  
The analysis shows how to calculate and interpret investment metrics, compare funds, and make portfolio recommendations.

---

## Data
**Source:** Synthetic (simulated) NAV time series, created to resemble real-world fund performance.  
**Structure:**  
- `Date` (YYYY-MM-DD)  
- `NAVfund1`, `NAVfund2`, `NAVfund3` (numeric NAV values)  

*Note: This data is for educational purposes only and not investment advice.*

---

## Methods

### Metrics and Formulas
Let `r_t` = periodic returns, `N` = number of periods per year (e.g., 12 for monthly data).

1. **Periodic Return**  
   \[
   r_t = \frac{\text{NAV}_t}{\text{NAV}_{t-1}} - 1
   \]

2. **Cumulative Return**  
   \[
   R_{\text{total}} = \prod_{t}(1 + r_t) - 1
   \]

3. **Annualized (CAGR) Return**  
   If \( T \) = total years:  
   \[
   \text{CAGR} = \left(\frac{\text{NAV}_{\text{end}}}{\text{NAV}_{\text{start}}}\right)^{1/T} - 1
   \]

4. **Annualized Volatility**  
   \[
   \sigma_{\text{ann}} = \text{std}(r_t) \times \sqrt{N}
   \]

5. **Sharpe Ratio**  
   \[
   \text{Sharpe} = \frac{\text{CAGR} - r_f}{\sigma_{\text{ann}}}
   \]
   where \( r_f \) = risk-free rate (assumed 0% here).

6. **Maximum Drawdown**  
   \[
   \text{Drawdown}_t = \frac{\text{NAV}_t - \max_{s \le t} \text{NAV}_s}{\max_{s \le t} \text{NAV}_s}
   \]  
   \[
   \text{Max DD} = \min_t \text{Drawdown}_t
   \]

---

## Results

**Performance Summary:**
- **NAVfund1** — Return: **6.92%**, Volatility: **3.02%**, Sharpe: **2.29**, Max DD: **−2.70%**  
  *Most efficient performer; low volatility and shallow drawdowns.*
  
- **NAVfund2** — Return: **2.88%**, Volatility: **5.94%**, Sharpe: **0.48**, Max DD: **−9.86%**  
  *Underperforms on both return and risk-adjusted basis.*
  
- **NAVfund3** — Return: **8.28%**, Volatility: **5.22%**, Sharpe: **1.59**, Max DD: **−4.31%**  
  *Highest return, moderate volatility; good for return-seeking investors.*

---

## Recommendation

- **Risk-averse investor:** NAVfund1 offers the best risk-adjusted performance.
- **Return-seeking investor:** Blend NAVfund1 and NAVfund3 for balance.
- **NAVfund2:** Avoid unless it provides diversification benefits.

*This analysis is illustrative. Real investment decisions should use actual data, include fees, and assess correlations between assets.*

---

## How to Run

**Python Version:** 3.9+ (tested on 3.10)  

**Requirements:**
```bash
pandas
numpy
matplotlib

