Summary

  This script performs a Monte Carlo simulation of portfolio growth using historical monthly returns for an equity ETF (e.g., VT or SPY) and a bond ETF (e.g., BNDW or BND). It uses a joint block bootstrap to preserve cross-asset correlation and models contributions, annual raises, bonuses, and optional rebalancing. Multiple strategies (static and dynamic allocations) are compared over a long horizon (default: 30 years).



What It Does

  Downloads historical monthly adjusted prices from https://www.alphavantage.co/support/#api-key.
  
  Converts prices to monthly returns.
  
  Generates a contribution schedule (base monthly, annual raises, bonuses).
  
  Runs Monte Carlo simulations with block bootstrap to model realistic return sequences.
  
  Supports:
  
    Static allocations (e.g., 60/40 equity/bond).
    Dynamic strategies (adjust weights based on drawdowns/recoveries).
    Optional rebalancing (monthly, quarterly, annual).
    
  Outputs:
  
    Summary CSV of terminal wealth statistics.
    Pairwise comparison CSV of strategy outperformance probabilities.
    Histogram plot of terminal wealth distributions.




How to Run

  1. Install dependencies:
    Shellpip install requests numpy pandas matplotlibShow more lines

  2. Get an Alpha Vantage API key and update CONFIG["data"]["api_key"].
     
  3. Edit CONFIG at the top of the script:
    Symbols (equity_symbol, bond_symbol).
    Simulation parameters (months, n_paths, block_size).
    Contribution details and strategies.

  4. Run the script:
     
  5. Outputs will be saved as:
    comparison_summary.csv
    pairwise_comparison.csv
    terminal_wealth_hist.png



How to Read the Outputs

  comparison_summary.csv:
    Columns: mean, median, std, p5, p25, p75, p95.
    These represent terminal wealth distribution metrics for each strategy.
  pairwise_comparison.csv:
    prob_B_outperforms_A: Probability that strategy B beats A.
    avg_B_minus_A: Average difference in terminal wealth.
  terminal_wealth_hist.png:
    Overlapping histograms of terminal wealth for all strategies.
