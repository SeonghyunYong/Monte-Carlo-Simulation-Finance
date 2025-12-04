Monte Carlo Portfolio Simulation (Dynamic Allocation, No Rebalancing)



✅ Overview
This project simulates long-term portfolio growth using block-bootstrap Monte Carlo with dynamic allocation rules applied only to new contributions (no rebalancing of existing holdings). It compares four strategies over a 30-year horizon with monthly contributions of $1,000:

Strategy A) All-Equity:
100% SPY

Strategy B) Static 40/60:
40% SPY / 60% BND

Strategy C) Dynamic Conservative:
Baseline: 60% SPY / 40% BND
When market >20% below previous bull peak → 80/20
When market >100% above previous bear trough → 40/60

Strategy D) Dynamic Growth:
Baseline: 80% SPY / 20% BND
When >10% below previous bull peak → 100/0
When >200% above previous bear trough → 60/40



✅ Why Block Bootstrap?
Unlike random sampling, block bootstrap preserves:

Serial correlation (momentum/mean reversion patterns)
Cross-asset co-movement (equity/bond correlation)
This makes simulations more realistic than naive Monte Carlo.


✅ How to Run

Get a free Alpha Vantage API key:
https://www.alphavantage.co/support/#api-key
Paste your key into the script:
API_KEY = "YOUR_ALPHA_VANTAGE_KEY"



✅ How It Works (Step-by-Step)

Download Data
Fetch monthly adjusted closes for SPY and BND (dividends reinvested).

Compute Returns
Convert prices to monthly returns and align calendars.

Block Bootstrap
Sample contiguous blocks to preserve realistic patterns.

Summarize & Compare
Compute distribution stats and pairwise comparisons.

Visualize
Plot overlapping histograms for all strategies.
