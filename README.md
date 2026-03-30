# 📊 Portfolio Risk \& Return Analyzer — NSE Stocks

> A fully formula-driven Excel financial model for analysing risk, return, and portfolio performance of NSE-listed equities.

\---

## What the Model Does

This workbook analyses the historical daily price performance of four NSE-listed stocks — **TCS, Reliance Industries, Infosys, and HDFC Bank** — across approximately 100 trading days. It then computes key risk-return metrics for each stock individually, and aggregates them into a weighted portfolio view with summary statistics and charts.

The entire model is formula-driven: changing any price in the **Data** sheet cascades through all downstream calculations automatically.

The model also demonstrates how portfolio construction and asset allocation impact overall investment performance.

It reflects a simplified version of real-world portfolio analysis used in investment advisory and wealth management.

The model structure mirrors basic portfolio analysis frameworks used in entry-level roles in investment advisory and wealth management.

\---

## Sheet-by-Sheet Structure

|Sheet|Purpose|
|-|-|
|**Data**|101 rows of daily close prices (₹) for 4 NSE stocks|
|**Returns**|Daily returns computed via `(Pₜ − Pₜ₋₁) / Pₜ₋₁` for each stock|
|**Metrics**|Per-stock risk-return statistics (annualised)|
|**Portfolio**|Weighted portfolio aggregation, Sharpe Ratio, and charts|

\---

## How Portfolio Return is Calculated

Portfolio return uses a **weighted average** of individual annualised returns:

```
Portfolio Return = Σ (Wᵢ × Rᵢ)
```

Implemented in Excel as:

```excel
=SUMPRODUCT(B4:B7, C4:C7)
```

where `B4:B7` = stock weights and `C4:C7` = annualised returns linked from the Metrics sheet.

\---

## How Portfolio Risk is Calculated

A **simplified weighted variance** method is used (assuming zero correlation between assets for interpretability). In practice, incorporating covariance between assets would provide a more accurate portfolio risk estimate

```
Portfolio Risk = √ Σ (Wᵢ² × σᵢ²)
```

Implemented in Excel as:

```excel
=SQRT(SUMPRODUCT(B4:B7 \\\* B4:B7, D4:D7 \\\* D4:D7))
```

> ⚠️ \\\*\\\*Note for advanced users:\\\*\\\* This simplified approach ignores cross-stock correlations. A full covariance matrix approach (using `MMULT`) would produce a more precise portfolio risk figure. This simplified version is intentionally used here for clarity and interpretability at a student level.

\---

## Key Metrics Explained

|Metric|Formula|Interpretation|
|-|-|-|
|**Annualised Return**|`Avg Daily Return × 252`|Expected yearly return|
|**Annualised Std Dev**|`Daily StdDev × √252`|Annual volatility / risk|
|**Sharpe Ratio**|`(Ann. Return − RFR) / Ann. StdDev`|Return earned per unit of risk taken|
|**Risk-Free Rate**|Set to **6% p.a.** (Indian T-bill proxy)|Benchmark for Sharpe calculation|

A **Sharpe Ratio > 1.0** is generally considered good; above 2.0 is excellent.

\---

## Colour Coding Convention (Industry Standard)

|Colour|Meaning|
|-|-|
|🔵 **Blue text**|Hardcoded inputs — user-editable assumptions|
|⚫ **Black text**|Formula-calculated values — do not overwrite|
|🟢 **Green text**|Values linked from another sheet|
|🟡 **Yellow background**|Key assumptions requiring attention|

\---

## Insights a User Can Derive

1. **Which stock has the highest risk-adjusted return?** → Compare Sharpe Ratios on the Metrics sheet.
2. **Which stock is the most volatile?** → Look at Annualised Std Dev.
3. **Is the portfolio well-diversified by allocation?** → View the Pie Chart.
4. **How does the portfolio Sharpe compare to individual stocks?** → Diversification should ideally improve the ratio.
5. **What happens if I change the weights?** → Edit the blue cells in `Portfolio!B4:B7` — all metrics update instantly.
6. **Which stock had the worst single-day loss?** → Min Daily Return on the Metrics sheet.

\---



\## Key Findings



\- Certain stocks in the portfolio demonstrate superior Sharpe Ratios, indicating stronger risk-adjusted performance compared to others.

\- Portfolio diversification reduces overall volatility compared to individual stocks, improving stability and consistency of returns.

\- Higher absolute returns do not always translate to better investment choices, emphasizing the importance of risk-adjusted evaluation.

\- Portfolio performance is highly sensitive to asset allocation, highlighting the critical role of weight optimization in investment decision-making.

\---

\## 👤 Investor Suitability



This portfolio framework is suitable for investors seeking a balance between risk and return, particularly moderate-risk investors. By adjusting asset weights, the model can be adapted for conservative (low volatility, stable returns) or aggressive (higher return, higher risk) investment strategies based on individual financial goals and risk tolerance.

\---

\## Future Improvements



\- Incorporate covariance matrix-based portfolio risk calculation for more accurate risk estimation

\- Integrate automated data fetching using APIs or Power Query for real-time analysis

\- Extend the model to include efficient frontier and optimal portfolio allocation

\- Expand to multi-asset portfolios including debt and hybrid instruments

\---

## How to Customise

* **Change weights:** Edit cells `B4:B7` on the Portfolio sheet (must sum to 100%).
* **Change Risk-Free Rate:** Edit cell `B3` on the Metrics sheet.
* **Replace with real data:** Paste actual NSE closing prices into the Data sheet (`B3:E103`) — all formulas update automatically.
* **Add more stocks:** Extend the model by adding columns in Data and Returns, then adding rows in the Portfolio table.

\---

## Tools \& Skills Demonstrated

* Dynamic cross-sheet formula referencing
* Financial statistics: `AVERAGE`, `STDEV`, `SQRT`, `SUMPRODUCT`, `COUNTIF`, `MIN`, `MAX`
* Annualisation of daily returns and volatility
* Sharpe Ratio computation
* Weighted portfolio construction
* Professional financial model formatting (colour coding, freeze panes, aligned tables)
* Data visualisation: Line chart (price trends) + Pie chart (allocation)
* Portfolio construction and asset allocation analysis
* Application of financial theory (risk-return tradeoff, diversification, asset allocation) in practical modelling

\---

## Project Context

Built as a practical financial modelling project demonstrating portfolio construction, risk analysis, and investment decision-making using real market data.

\---

*Model built with Excel | Data: Historical price data sourced from NSE Website | Last updated: March 2026*

