# dual-trend-mom-script

TradingView Pine v6 scripts for the Dual Trend + Momentum Swing Score workflow.

## Files

- `Dual Trend + Momentum Swing Score v2.0`
  Indicator version for chart reading, score dashboard, labels, background signals, and alerts.

- `Dual Trend Momentum Strategy Tester v2.0`
  Strategy/backtest companion that reuses the indicator signal engine and places test trades.

## Strategy tester usage

Use the strategy file when you want to compare entries and exits in TradingView Strategy Tester.

Key controls:

- Enable or disable setup families: Prime Clean Pullback, Clean Bull Pullback, Fresh Breakout, Momentum Continuation.
- Choose stop mode from recent swing low, SMA 50 minus ATR buffer, or ATR multiple.
- Set target R multiple and minimum reward/risk.
- Optional exits: danger signal, close below SMA 50, max bars in trade, breakeven, ATR trailing stop.
- Optional date filter for controlled backtest windows.

The strategy dashboard shows current trade state, active stop/target, bars in trade, and summary stats such as closed trades, win rate, net profit, profit factor, and max drawdown.
