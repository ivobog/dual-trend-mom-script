# Backtest Methodology

Version target: v2.3

This document defines how to test the Dual Trend + Momentum strategy tester so results are comparable across setup types, symbols, market regimes, and scoring modes.

## Purpose

The goal is not to prove that every signal works. The goal is to identify which setup types have positive expectancy, which market regimes they survive, and which defaults should remain enabled.

## Test Scripts

Use the latest compiling strategy script. Prefer v2.3 for market-regime split tests:

```text
dual_trend_momentum_strategy_v2_3.pine
```

Use the indicator only for visual confirmation:

```text
dual_trend_momentum_indicator_v2_2.pine
```

Record the displayed engine version with every test run.

## TradingView Strategy Settings

Use consistent settings unless a test explicitly says otherwise:

```text
Initial capital: 100,000
Order size: 10% of equity
Commission: 0.05%
Slippage: 1 tick
Pyramiding: 0
Order timing: default TradingView strategy fill behavior
```

If the strategy script settings change, document the change in the run notes.

## Primary Timeframes

Test these first:

```text
Daily
Weekly
```

Optional follow-up timeframes:

```text
4H
1H
```

Daily and weekly remain the primary intended swing-trading use case.

## Date Ranges

Use at least one broad multi-cycle range and one recent range.

Recommended:

```text
2018-01-01 to latest available bar
2020-01-01 to latest available bar
2022-01-01 to latest available bar
```

For younger symbols, use the longest available clean history and mark it as limited history.

## Symbol Groups

### US Large Caps

```text
AAPL
MSFT
NVDA
AMZN
META
GOOGL
JPM
COST
AVGO
```

### US ETFs

```text
SPY
QQQ
IWM
XLK
XLF
XLE
SMH
```

### Swiss Stocks

```text
NESN
NOVN
ROG
UBSG
ZURN
SIKA
GEBN
SFSN
ACLN
```

Use TradingView's exact exchange prefixes when running tests.

### High Momentum / Early Rocket Names

Use current screener outputs. Record the source and date of the screener list.

## Setup-Type Isolation

Do not judge the combined strategy first. Test setup types separately.

For each isolated test, enable exactly one entry toggle:

```text
Trade Prime Clean Pullback
Trade Clean Bull Pullback
Trade Fresh Breakout
Trade Momentum Continuation
```

Then run a combined test only after individual setup results are documented.

## Scoring Mode Tests

Run each isolated setup under:

```text
Conservative
Balanced
Early Rocket
```

Recommended expectations:

```text
Conservative: fewer trades, lower drawdown, stronger filters.
Balanced: primary production candidate.
Early Rocket: more momentum sensitivity, higher selectivity needed around liquidity and gap exhaustion.
```

## Stop And Target Tests

Start with the v2.2 default:

```text
Stop Mode: Structure + ATR
Target Mode: R Multiple
```

Then compare:

```text
Stop Mode: ATR
Stop Mode: SMA50
Stop Mode: Structure
Target Mode: Prior High
Target Mode: Measured Move
Target Mode: ATR Target
```

Change one dimension at a time. Do not change scoring mode, setup toggles, stop mode, and target mode in the same comparison run.

## Market Regime Split

For each promising setup, run three filters:

```text
Risk-on only
Neutral only
Risk-off allowed
```

Use the v2.3 strategy inputs:

```text
Trade in Risk-On Market
Trade in Neutral Market
Trade in Risk-Off Market
```

For isolated regime tests, enable only one of those inputs at a time.

## Required Metrics

Record these metrics from TradingView Strategy Tester:

```text
Net profit
Profit factor
Max drawdown
Win rate
Average trade
Number of trades
Largest win
Largest loss
Average bars in trade
```

Also record manually when available:

```text
Average R
Median R
Consecutive losses
Exposure percentage
Notes about outlier trades
```

## Pass Criteria

A setup type is tradable only if it satisfies all of these:

```text
Enough trades for the symbol group and date range
Profit factor above 1.3
Average R positive
Max drawdown acceptable for the use case
No dependence on one giant trade
Stable behavior across several symbols
Stable behavior outside ideal bull-market conditions
```

Preferred stricter targets:

```text
Profit factor above 1.5
Max drawdown below 20%
Average R positive
Expectancy positive even if win rate is moderate
```

## Failure Criteria

Disable or downgrade a setup type if it shows:

```text
Profit factor below 1.0 over broad tests
Large losses clustered in weak markets
Results dominated by one symbol or one trade
Very few trades despite broad symbol coverage
Poor behavior after realistic slippage and commission
Unstable results between scoring modes
```

## Run Naming Convention

Use this format in notes and screenshots:

```text
v2.3-[asset_group]-[symbol]-[timeframe]-[setup]-[mode]-[stop]-[target]-[date_range]
```

Example:

```text
v2.3-us-large-cap-AAPL-D-prime-pullback-balanced-structure-atr-r-multiple-2020-latest
```

## Evidence To Save

For every important run, save:

```text
Strategy Tester summary screenshot
List of key settings
Symbol and timeframe
Date range
Setup toggles
Scoring mode
Stop mode
Target mode
Notes on outlier trades
Final decision: keep, disable, or retest
```
