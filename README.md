# Clean Energy Thematic Index Builder

A replication of MSCI-style thematic index construction methodology applied
to the Clean Energy sector.

## Methodology

**Universe:** 39 global equities across clean energy and non-clean energy sectors

**Relevance Scoring (NLP):** Companies scored by keyword frequency in business
descriptions against 23 clean energy keywords (solar, wind, renewable, battery,
hydrogen, EV, etc.) — analogous to MSCI ISE relevance scoring methodology

**Eligibility Threshold:** >10% relevance score (12 of 39 companies selected)

**Weighting:** Float-adjusted market cap weighting with 10% issuer-level
concentration cap — iterative redistribution of excess weight to remaining
constituents

**Benchmark:** iShares Global Clean Energy ETF (ICLN)

**Backtest Period:** January 2022 – December 2024

## Results

| Metric | Index | Benchmark (ICLN) |
|--------|-------|-----------------|
| Annualised Return | -22.01% | -17.82% |
| Cumulative Return | -52.33% | -44.28% |
| Tracking Error (ann.) | 18.72% | — |
| Sharpe Ratio | -0.71 | -0.80 |
| Active Return | -4.19% | — |

## Threshold Sensitivity Analysis

| Threshold | Constituents | Ann. Return | vs Benchmark | Tracking Error |
|-----------|-------------|-------------|--------------|----------------|
| 10% (V1) | 12 | -22.01% | -4.19% | 18.72% |
| 20% (V2) | 6 | -20.43% | -2.61% | 20.66% |

**Finding:** Stricter relevance filtering reduced underperformance by 158bps,
suggesting thematic purity improves index quality in sector downturns.

## Key Findings

- Index underperformed benchmark by 419bps annualised over the period
- Underperformance driven by high concentration in small-cap volatile names
(FCEL, PLUG, LCID) after the 10% cap redistributed weight away from
large-cap anchors TSLA and NEE
- Tracking error of 18.72% reflects meaningful active bets vs the ETF benchmark
- Rolling TE ranged 12-24%, peaking in early 2022 (rate hike cycle) and
late 2024

## Files

- `universe_builder.py` — pulls company data and calculates relevance scores
- `index_constructor.py` — applies eligibility threshold, weights, and issuer cap
- `performance_analysis.py` — calculates returns, TE, Sharpe, and generates charts
- `universe.csv` — raw universe data with relevance scores
- `clean_energy_index_performance.png` — cumulative return and rolling TE chart

## Tech Stack

Python, Pandas, NumPy, yfinance, Matplotlib

## Methodology Reference

Inspired by MSCI thematic index construction methodology including relevance
scoring, eligibility screening, and iterative issuer capping.
