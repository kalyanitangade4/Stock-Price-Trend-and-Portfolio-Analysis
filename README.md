📊 Stock Portfolio Analysis

A data analysis project that evaluates an 8-stock equal-weighted portfolio against a market benchmark to uncover diversification effects, risk-adjusted performance, and concentration risk that aren't visible from price charts alone.

📌 Problem Statement

Picking individual stocks is easy to judge in hindsight, but investors rarely ask the harder question: did combining these holdings into a portfolio actually reduce risk, or did one stock just carry the rest? This project uses structured risk and return analysis to answer a concrete question: how does this 8-stock portfolio perform against the market on a risk-adjusted basis, and which holdings are driving that outcome?

🗂️ Dataset

The analysis uses five years of daily price data (Feb 2013 – Feb 2018) across 8 stocks spanning six sectors, plus a market benchmark return series, containing fields such as:

CategoryExample FieldsIdentifiersName (ticker), SectorPrice DataOpen, High, Low, Close, VolumeTimeDateBenchmarkBenchmark daily returnTarget metrics (derived)Daily return, annualized return, volatility, Sharpe ratio

~10,072 records (8 tickers × 1,259 trading days each), with no missing values or duplicate rows.

🎯 Objectives


Quantify the portfolio's return and risk relative to the benchmark.
Identify which holdings are driving portfolio performance, and which are dragging on it.
Determine how much diversification benefit the portfolio actually gets from combining low-correlation holdings.
Evaluate risk-adjusted performance using Sharpe ratio, volatility, Value-at-Risk, and maximum drawdown.
Translate the quantitative metrics into plain-language portfolio recommendations.


🔍 Methodology


Collect the data – Gather daily OHLCV price data for all 8 tickers, plus sector labels and a market benchmark return series.
Clean the data – Verify no missing values, no duplicate rows, and equal trading-day coverage across all tickers.
Explore the data – Pivot into a wide price matrix, compute daily returns, and build an equal-weighted, daily-rebalanced portfolio return series.
Find patterns – Compare individual holdings on volatility, correlation, and moving-average trend signals (50-day/200-day, golden/death cross).
Compute risk metrics – Calculate annualized return, annualized volatility, Sharpe ratio, 95% historical Value-at-Risk, maximum drawdown, and beta for every holding, the portfolio, and the benchmark.
Summarize findings – Compare the portfolio against the benchmark on cumulative growth and risk-adjusted return, and identify which holdings explain the gap.


📊 Key Findings


The portfolio outperformed its benchmark by a wide margin. $1 invested grew to ~$2.60 over the period (~23% annualized return) versus ~$1.90 for the benchmark (~15% annualized) — the gap widens sharply from 2016 onward.
That outperformance is concentrated in one holding. NVDA alone returned ~90% annualized with a Sharpe ratio of ~2.5 — by far the strongest of any holding. $100 in NVDA alone grew to nearly $2,000.
One holding actively hurt the portfolio. XOM (Energy) posted a slightly negative annualized return and a negative Sharpe ratio (~‑0.15) — the only holding to destroy value on a risk-adjusted basis.
Diversification measurably worked. All pairwise return correlations stayed moderate-to-low (0.12–0.50, no pair above 0.5), which is why portfolio volatility (~13% annualized) came in lower than 6 of the 8 individual stocks.
Risk stayed controlled despite a high-volatility holding. Maximum portfolio drawdown was ‑14.72%, moderate given NVDA's standalone volatility of ~36% annualized.


Suggested next step: stress-test the portfolio's return with NVDA removed to see how much of the "outperformance" is genuine diversified stock-picking versus a single concentrated bet — then use that to decide whether to trim NVDA, replace XOM, or add uncorrelated names outside Technology and Energy.

📈 Visualizations Produced


Growth of $100 invested — individual stocks
AAPL price with 50-day/200-day moving averages and golden/death cross signals
Rolling 30-day annualized volatility by stock
Daily return correlation heatmap
Cumulative growth: portfolio vs. benchmark
Risk vs. return scatter (all holdings, portfolio, benchmark)
Sharpe ratio comparison bar chart
Portfolio drawdown over time


🛠️ Tools & Technologies


Language: Python 3.x
Data Handling: Pandas, NumPy
Visualization: Matplotlib
Environment: Jupyter Notebook


▶️ How to Run

bash# 1. Install dependencies
pip install -r requirements.txt

# 2. Launch the analysis notebook
jupyter notebook Stock_portfolio_analysis.ipynb

💡 Business Recommendations


Consider trimming the NVDA position to lock in gains and reduce concentration risk, since one holding is driving nearly all of the portfolio's outperformance.
Reassess or replace the XOM (Energy) allocation given its negative risk-adjusted return over the period.
Maintain exposure across low-correlation sectors (Technology, Healthcare, Financials, Consumer Staples), since this measurably reduced overall portfolio volatility.
Move from static equal-weighting toward periodic rebalancing, to systematically lock in gains from outperformers rather than letting concentration build passively.
Treat moving-average crossover signals (golden/death cross) as a supplementary timing indicator alongside fundamentals, not a standalone strategy.


✅ Conclusion

This analysis shows the portfolio's strong performance isn't evenly earned across its 8 holdings — it concentrates heavily in one high-conviction, high-volatility stock, partially offset by one consistent detractor, with diversification doing real work to keep overall risk in check. These are concrete, addressable levers for portfolio construction rather than abstract risk figures, which is what makes the findings useful for an allocation decision rather than just a descriptive report.

👨‍💻 Author

Kalyani Tangade
B.Tech IT Graduate | Aspiring Data Analyst
Mumbai, India
kalyanitangade4@gmail.com
