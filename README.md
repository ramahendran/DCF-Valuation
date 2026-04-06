# Automated DCF Valuation Engine

A fully automated Discounted Cash Flow valuation model built in Python. Enter any publicly traded ticker and the notebook fetches live financial data, builds a two-stage DCF, calculates WACC from first principles, and produces investment-banking-style outputs including a sensitivity heatmap, Monte Carlo simulation, and football field chart.

---

## Features

- **Live data ingestion** — pulls income statement, balance sheet, and cash flow statements via `yfinance`
- **Free Cash Flow computation** — calculates historical FCF and key financial ratios from raw financials
- **Two-stage growth model** — Stage 1 (high growth) and Stage 2 (transition) before terminal value
- **WACC from first principles** — cost of equity via CAPM, cost of debt from financials, blended by capital structure
- **Intrinsic value per share** — discounts projected FCFs and terminal value to present, adjusts for net debt and shares outstanding
- **Sensitivity heatmap** — 2D grid showing implied fair value across a range of WACC and terminal growth rate combinations
- **Monte Carlo simulation** — 10,000 runs sampling growth and discount assumptions to produce a probability distribution of fair value
- **Comparable multiples** — EV/EBITDA, P/E, and EV/Revenue implied values benchmarked against the DCF output
- **Football field chart** — consolidated valuation summary across all methods, styled to match IB pitch book conventions
- **Final scorecard** — buy/sell rating based on consensus implied value vs. current market price

---

## Installation

```bash
pip install yfinance numpy pandas scipy matplotlib seaborn plotly
```

---

## Usage

Open the notebook and edit the configuration cell at the top:

```python
TICKER          = 'AAPL'     # Any valid Yahoo Finance ticker

STAGE1_YEARS    = 5
STAGE1_GROWTH   = 0.08       # 8% growth in Stage 1
STAGE2_YEARS    = 5
STAGE2_GROWTH   = 0.05       # 5% growth in Stage 2
TERMINAL_GROWTH = 0.025      # 2.5% perpetuity growth rate

RISK_FREE_RATE   = 0.045     # 10-year Treasury yield
EQUITY_RISK_PREM = 0.055     # Equity risk premium
BETA_OVERRIDE    = None      # Set to a float to override fetched beta
TAX_RATE         = 0.21
```

Then run all cells. All outputs render inline.

---

## Outputs

| Output | Description |
|---|---|
| FCF History Table | Historical free cash flow and margin trends |
| WACC Summary | Cost of equity, cost of debt, and blended WACC |
| DCF Bridge | Year-by-year projected FCFs, PV factors, and terminal value |
| Sensitivity Heatmap | Fair value grid across WACC × terminal growth rate |
| Monte Carlo Distribution | Histogram of 10,000 simulated fair values with percentile bands |
| Comparable Multiples | EV/EBITDA, P/E, and EV/Revenue implied values vs. peers |
| Football Field Chart | Side-by-side valuation ranges across all methods |
| Final Scorecard | Consensus value, upside/downside vs. market price, and rating |

---

## Dependencies

| Package | Purpose |
|---|---|
| `yfinance` | Financial data fetching |
| `numpy` | Numerical computation |
| `pandas` | Data manipulation and styled table output |
| `scipy` | Statistical distributions for Monte Carlo |
| `matplotlib` | Static charts and football field |
| `seaborn` | Sensitivity heatmap styling |
| `plotly` | Interactive Monte Carlo visualization |

---

