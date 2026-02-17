# AdvaitsAlgos

Systematic intraday trading strategies and supporting analytics
infrastructure designed and implemented by Advait Chorghade.

This repository contains performance visualisations and high-level
architectural summaries of quantitative models developed in C++ and
Python. Core implementation details are intentionally abstracted.

------------------------------------------------------------------------

## Overview

The strategies operate on baskets of mid- to large-cap equities
(\~\$1bn--\$100bn market cap) and are designed for intraday execution
with controlled risk exposure.

The broader system includes:

-   Real-time data ingestion and preprocessing\
-   Execution logic using limit-order prioritisation\
-   Slippage and liquidity modelling\
-   Risk and performance evaluation (Sharpe, drawdown, turnover)\
-   Backtesting and deployment framework (C++ + Python)

All positions are intraday; no overnight exposure is taken.

------------------------------------------------------------------------

## Strategy 1 -- Intraday Mean-Reversion Framework

This strategy focuses on short-horizon inefficiencies within liquid
equities.

Key characteristics:

-   Intraday-only positioning\
-   Limit-order driven execution to reduce slippage\
-   Sensitivity to spread and liquidity conditions\
-   Performance evaluated under varying execution assumptions

### Considerations

-   Fill probability assumptions require stress testing\
-   Liquidity constraints impact scalability\
-   Sharpe ratios shown assume a 0% risk-free rate for benchmarking
    purposes

![Strategy 1 Output](images/twoinone_labelled.png)

------------------------------------------------------------------------

## Strategy 2 -- Liquidity-Sensitive Momentum Structure

Developed in October 2023.

This strategy exploits short-term structural price movements and
requires rapid position accumulation.

Key characteristics:

-   Intraday positioning\
-   Execution-sensitive performance\
-   Explicit modelling of spread and capital deployment impact

The image below illustrates the difference between idealised execution
and slippage-adjusted execution using extrapolated Level 1 spread data.

![Strategy 2 Output](images/csm3.png)

### Considerations

-   Performance is highly sensitive to liquidity\
-   Slippage materially impacts realised Sharpe\
-   Tail risk exposure requires active monitoring\
-   Benchmark Sharpe assumes 0% risk-free rate

------------------------------------------------------------------------

## Technical Stack

-   C++ for performance-critical components\
-   Python for orchestration, analysis, and diagnostics\
-   Historical and real-time market data integration\
-   Performance visualisation and evaluation tooling

------------------------------------------------------------------------

## Notes

This repository focuses on system structure and performance diagnostics
rather than full source implementation.
