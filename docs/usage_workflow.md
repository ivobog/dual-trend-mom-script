# Usage Workflow

Use the v3 scripts from `src/` for new chart review and strategy testing.

## Chart Review

1. Open the chart in TradingView.
2. Paste or import `src/dual_trend_momentum_indicator_v3.pine`.
3. Confirm the label or dashboard shows:

```text
Engine: 3.2.0
```

4. Start with these defaults:

```text
Scoring Mode: Balanced
Dashboard Mode: Compact
Stop Mode: Structure + ATR
Target Mode: R Multiple
Use Notional Liquidity Filter: true
```

5. Review:

```text
Classification
Action
Dual Score
Trend Score
Momentum Score
Setup Score
Risk Score
Market Regime
Relative Strength
Stop
Target
Reward/Risk
```

## Strategy Testing

1. Open TradingView Strategy Tester.
2. Paste or import `src/dual_trend_momentum_strategy_v3.pine`.
3. Confirm the dashboard shows:

```text
Engine: 3.2.0
```

4. Test one setup type at a time:

```text
Trade Prime Clean Pullback: on
Trade Clean Bull Pullback: off
Trade Fresh Breakout: off
Trade Momentum Continuation: off
```

Then repeat for each setup type.

5. Test market regimes one at a time:

```text
Trade in Risk-On Market: on
Trade in Neutral Market: off
Trade in Risk-Off Market: off
```

Then repeat for Neutral and Risk-Off.

6. Record results in:

```text
docs/backtest_results_v2_3.md
docs/backtest_run_log_template.csv
```

## Suggested Review Order

1. Balanced mode on Daily timeframe.
2. Prime Clean Pullback only.
3. Clean Bull Pullback only.
4. Fresh Breakout only.
5. Conservative mode for setups that pass Balanced.
6. Early Rocket mode for high-momentum names.
7. Weekly timeframe sanity pass.
8. Combined setup test after isolated setup evidence is documented.

## Decision Rule

Do not enable a setup by default only because it looks good on charts. Keep or enable a setup only after the Strategy Tester shows positive expectancy across multiple symbols and regimes.
