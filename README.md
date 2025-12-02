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


✅ Key Features

Fetches monthly adjusted prices (total-return proxy) for SPY and BND from Alpha Vantage.
Compares four allocation strategies with dynamic triggers.
Outputs:

comparison_summary.csv — mean, median, std, p5/p25/p75/p95 for each strategy
pairwise_comparison.csv — probability one strategy beats another + average/median outperformance
terminal_wealth_hist_4strategies.png — histogram overlay of terminal wealth distributions




✅ Requirements
Create a requirements.txt:
numpy
pandas
matplotlib
requests

Install:
Shellpip install -r requirements.txtShow more lines

✅ How to Run

Get a free Alpha Vantage API key:
https://www.alphavantage.co/support/#api-key
Paste your key into the script:
PythonAPI_KEY = "YOUR_ALPHA_VANTAGE_KEY"Show more lines

Run:
Shellpython monte_carlo_dynamic.pyShow more lines



✅ SSL Bypass (Corporate Networks)
If your environment uses SSL inspection and blocks HTTPS:

The script includes a temporary SSL bypass so data can be fetched.
Remove the bypass and set VERIFY_SSL = True once your corporate root CA is installed in Python’s trust store.


✅ Outputs

comparison_summary_spy_bnd_alpha_norebalance.csv
pairwise_comparison_spy_bnd_alpha_norebalance.csv
terminal_wealth_hist_spy_bnd_alpha_norebalance_4strategies.png


✅ Example Results
=== Static 40/60 ===
mean:   2,139,177
median: 1,817,367
p5:       703,588
p95:    4,747,019

=== Dynamic A ===
mean:   2,194,635
median: 1,894,936
p5:       769,769
p95:    4,727,443

prob_dynamic_outperforms: 0.6654
avg_outperformance: $55,457


✅ How It Works (Step-by-Step)

Download Data
Fetch monthly adjusted closes for SPY and BND (dividends reinvested).
Compute Returns
Convert prices to monthly returns and align calendars.
Block Bootstrap
Sample contiguous blocks to preserve realistic patterns.
Simulate Strategies
Apply allocation rules to new contributions only:

Add $1,000 at start of each month.
Apply weights based on baseline or dynamic triggers.
Compound returns monthly.


Summarize & Compare
Compute distribution stats and pairwise comparisons.
Visualize
Plot overlapping histograms for all strategies.


✅ Extensions

Sensitivity Analysis: Vary tilt levels and block sizes.
Exact Historical Path: Simulate contributions on real SPY/BND timeline.
Inflation & Fees: Adjust returns for real purchasing power and costs.


📜 License
MIT License — free to use and modify.
