# dual-trend-mom-script

TradingView Pine v6 scripts for the Dual Trend + Momentum Swing Score workflow.

The repository contains an indicator for live chart review and a matching strategy tester for backtesting the same signal engine.

## Files

- `Dual Trend + Momentum Swing Score v2.0`
  Indicator version for chart reading, score dashboard, labels, background signals, plots, and alerts.

- `Dual Trend Momentum Strategy Tester v2.0`
  Strategy/backtest companion that reuses the indicator signal engine and places test trades.

- `design.txt`
  Design notes and implementation roadmap.

## Indicator

Use the indicator when reviewing charts manually.

It displays:

- Dual Score
- Trend Score
- Momentum Score
- Setup Score
- Risk Score
- Market Score
- Relative Strength Score
- HTF trend status
- Market regime
- Sector RS, when enabled
- Suggested stop, target, entry risk, resistance distance, and reward/risk

## Main Modules

- Trend: EMA/SMA stack, normalized MA slope, ADX/DMI, 52-week position, higher high / higher low structure, HTF confirmation.
- Momentum: benchmark RS, optional sector RS, ROC 21/63/126, RSI behavior, OBV, green/red volume, breakout pressure.
- Setup: pullback depth, MA support, reclaim behavior, breakout trigger, volume dry-up, reward/risk.
- Risk: extension, RSI overheat, resistance, heavy red volume, distribution days, failed breakout, market risk-off, sector weakness, gap exhaustion, liquidity warning.
- Market regime: benchmark trend, market ROC, market distribution count, risk-off penalty.
- Relative strength: stock vs benchmark, optional stock vs sector, combined RS score.

## Classifications

- Prime clean pullback
- Clean bull pullback
- Fresh breakout
- Momentum continuation
- Extended momentum
- Overheated momentum
- Filtered pullback
- Filtered momentum
- Trend repair
- Distribution risk
- Blowoff top
- Failed breakout
- No trade

## Risk And Trade Helpers

Stop modes:

- Recent swing low
- SMA 50 minus ATR buffer
- ATR multiple

The scripts estimate:

- Suggested stop
- Target R multiple
- Entry risk %
- Resistance distance
- Reward/risk to resistance
- Gap exhaustion
- Liquidity warning

## Market And RS Filters

Default market and benchmark symbols are `AMEX:SPY`.

Optional sector benchmark support is available. When enabled, the combined RS score blends:

- 70% benchmark RS
- 30% sector RS

Market risk-off uses:

- Market distribution count
- Market close vs SMA 50 / SMA 200
- Market short ROC
- Configurable risk-off score penalty

## Strategy Tester

Use `Dual Trend Momentum Strategy Tester v2.0` in TradingView Strategy Tester.

Entry toggles:

- Prime Clean Pullback
- Clean Bull Pullback
- Fresh Breakout
- Momentum Continuation

Exit controls:

- Stop / target
- Danger signal
- Market risk-off
- Gap exhaustion
- Close below SMA 50
- Max bars in trade
- Move stop to breakeven
- ATR trailing stop
- Date filter

The strategy dashboard shows:

- Current position
- Entry reason
- Average entry
- Active stop and target
- Bars in trade
- Open P/L
- Closed trades
- Win rate
- Net profit
- Profit factor
- Max drawdown
- Market risk-off status
- Benchmark RS, sector RS, and combined RS

## Alerts

Both scripts expose alert conditions for:

- Prime clean pullback
- Clean bull pullback
- Fresh breakout
- Momentum continuation
- Extended momentum
- Overheated momentum
- Filtered pullback
- Filtered momentum
- Trend repair
- Distribution risk
- Gap exhaustion
- Liquidity warning
- Market risk-off
- Sector RS failed
- Failed breakout
- Blowoff top

## TradingView Workflow

1. Open a chart.
2. Paste or import the indicator script.
3. Review the score table and last-bar label.
4. Use the strategy tester script separately to compare entry and exit rules.
5. Compile both scripts after changes; Pine warnings often point to history-dependent calculations that need to be assigned before use.

## Notes

The strategy tester is for comparing rule behavior, not for automatic trading advice. Signals still need chart context, liquidity review, and position sizing discipline.
