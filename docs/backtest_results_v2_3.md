# Backtest Results v2.3

Status: pending TradingView runs

This file is the working results log for Phase 3. Fill it in as tests are run from `docs/backtest_methodology.md`.

Preferred strategy script for Phase 3:

```text
dual_trend_momentum_strategy_v2_3.pine
```

## Summary Decisions

| Setup Type | Default State | Evidence Level | Decision Notes |
|---|---:|---:|---|
| Prime Clean Pullback | Enabled | Pending | Not tested yet |
| Clean Bull Pullback | Enabled | Pending | Not tested yet |
| Fresh Breakout | Enabled | Pending | Not tested yet |
| Momentum Continuation | Disabled | Pending | Not tested yet |

## Recommended Test Order

1. Balanced mode, Daily timeframe, US large caps, each setup isolated.
2. Balanced mode, Daily timeframe, ETFs, each setup isolated.
3. Balanced mode, Daily timeframe, Swiss stocks, each setup isolated.
4. Conservative mode on setup types that pass the Balanced test.
5. Early Rocket mode on fresh breakout and momentum continuation candidates.
6. Weekly timeframe sanity pass.
7. Combined setup test only after individual setup results are known.

## Run Log

| Run ID | Date Tested | Symbol | Timeframe | Asset Group | Date Range | Setup Tested | Scoring Mode | Stop Mode | Target Mode | Trades | Net Profit | Profit Factor | Max Drawdown | Win Rate | Avg Trade | Avg R | Median R | Avg Bars | Decision | Notes |
|---|---|---|---|---|---|---|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|
| v2.3-us-large-cap-AAPL-D-prime-pullback-balanced-structure-atr-r-multiple |  | AAPL | D | US Large Cap | 2020-latest | Prime Clean Pullback | Balanced | Structure + ATR | R Multiple |  |  |  |  |  |  |  |  |  | Pending |  |

## Setup-Type Results

### Prime Clean Pullback

| Asset Group | Timeframe | Scoring Mode | Symbols Tested | Total Trades | Median Profit Factor | Worst Max Drawdown | Decision |
|---|---|---|---:|---:|---:|---:|---|
| US Large Caps | Daily | Balanced | 0 | 0 |  |  | Pending |
| US ETFs | Daily | Balanced | 0 | 0 |  |  | Pending |
| Swiss Stocks | Daily | Balanced | 0 | 0 |  |  | Pending |

Notes:

```text
Pending.
```

### Clean Bull Pullback

| Asset Group | Timeframe | Scoring Mode | Symbols Tested | Total Trades | Median Profit Factor | Worst Max Drawdown | Decision |
|---|---|---|---:|---:|---:|---:|---|
| US Large Caps | Daily | Balanced | 0 | 0 |  |  | Pending |
| US ETFs | Daily | Balanced | 0 | 0 |  |  | Pending |
| Swiss Stocks | Daily | Balanced | 0 | 0 |  |  | Pending |

Notes:

```text
Pending.
```

### Fresh Breakout

| Asset Group | Timeframe | Scoring Mode | Symbols Tested | Total Trades | Median Profit Factor | Worst Max Drawdown | Decision |
|---|---|---|---:|---:|---:|---:|---|
| US Large Caps | Daily | Balanced | 0 | 0 |  |  | Pending |
| US ETFs | Daily | Balanced | 0 | 0 |  |  | Pending |
| High Momentum | Daily | Early Rocket | 0 | 0 |  |  | Pending |

Notes:

```text
Pending.
```

### Momentum Continuation

| Asset Group | Timeframe | Scoring Mode | Symbols Tested | Total Trades | Median Profit Factor | Worst Max Drawdown | Decision |
|---|---|---|---:|---:|---:|---:|---|
| US Large Caps | Daily | Balanced | 0 | 0 |  |  | Pending |
| High Momentum | Daily | Early Rocket | 0 | 0 |  |  | Pending |

Notes:

```text
Momentum Continuation is disabled by default until test evidence supports enabling it.
```

## Market Regime Split

| Setup Type | Regime | Scoring Mode | Trades | Profit Factor | Max Drawdown | Decision | Notes |
|---|---|---|---:|---:|---:|---|---|
| Prime Clean Pullback | Risk-on | Balanced |  |  |  | Pending |  |
| Prime Clean Pullback | Neutral | Balanced |  |  |  | Pending |  |
| Prime Clean Pullback | Risk-off | Balanced |  |  |  | Pending |  |
| Fresh Breakout | Risk-on | Early Rocket |  |  |  | Pending |  |
| Fresh Breakout | Neutral | Early Rocket |  |  |  | Pending |  |
| Fresh Breakout | Risk-off | Early Rocket |  |  |  | Pending |  |

## Scoring Mode Comparison

| Setup Type | Asset Group | Timeframe | Conservative PF / DD | Balanced PF / DD | Early Rocket PF / DD | Preferred Mode | Notes |
|---|---|---|---|---|---|---|---|
| Prime Clean Pullback | US Large Caps | Daily |  |  |  | Pending |  |
| Clean Bull Pullback | US Large Caps | Daily |  |  |  | Pending |  |
| Fresh Breakout | High Momentum | Daily |  |  |  | Pending |  |

## Stop And Target Comparison

| Setup Type | Scoring Mode | Stop Mode | Target Mode | Trades | Profit Factor | Max Drawdown | Avg R | Decision |
|---|---|---|---|---:|---:|---:|---:|---|
| Prime Clean Pullback | Balanced | Structure + ATR | R Multiple |  |  |  |  | Pending |
| Prime Clean Pullback | Balanced | SMA50 | Prior High |  |  |  |  | Pending |
| Fresh Breakout | Early Rocket | ATR | Measured Move |  |  |  |  | Pending |
| Fresh Breakout | Early Rocket | Structure + ATR | ATR Target |  |  |  |  | Pending |

## Final v2.3 Defaults

Pending evidence.

Proposed default stance until tests are complete:

```text
Trade Prime Clean Pullback: enabled
Trade Clean Bull Pullback: enabled
Trade Fresh Breakout: enabled
Trade Momentum Continuation: disabled
Scoring Mode: Balanced
Stop Mode: Structure + ATR
Target Mode: R Multiple
Dashboard Mode: Compact
```
