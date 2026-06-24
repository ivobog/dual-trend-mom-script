# dual-trend-mom-script

TradingView Pine v6 scripts for the Dual Trend + Momentum Swing Score workflow.

The repository contains an indicator for live chart review and a matching strategy tester for backtesting the same signal engine.

Current v3 files live in `src/`. Older root-level scripts are kept as stable baselines and migration history.

## Files

- `src/dual_trend_momentum_indicator_v3.pine`
  Current v3.2 indicator for chart review, dashboards, labels, plots, and alerts.

- `src/dual_trend_momentum_strategy_v3.pine`
  Current v3.2 strategy tester with setup toggles, exits, scoring modes, stop/target modes, and market-regime split filters.

- `src/dual_trend_momentum_engine.pine`
  Pine library source for the next published engine version. Future script import path after publishing: `import ivobog/DualTrendMomentumEngine/3 as engine`.

- `CHANGELOG.md`
  Version history and release notes.

- `docs/architecture.md`
  v3 architecture notes and engine extraction plan.

- `docs/engine_contract.md`
  Shared-engine boundary and drift-control rules for the library-backed scoring/classification modules.

- `docs/usage_workflow.md`
  Practical chart-review and strategy-testing workflow.

- `docs/release_checklist.md`
  Compile, visual, strategy, alert, and documentation checks before a version is considered stable.

- `docs/scoring_model.md`
  Scoring mode weights and defaults.

- `docs/setup_classifications.md`
  Classification definitions and intended actions.

- `dual_trend_momentum_indicator_v2_2.pine`
  Stable v2.2 indicator baseline.

- `dual_trend_momentum_strategy_v2_2.pine`
  Stable v2.2 strategy baseline.

- `dual_trend_momentum_strategy_v2_3.pine`
  Phase 3 strategy tester with market-regime split filters for backtest isolation.

- `dual_trend_momentum_indicator_v2_1.pine`
  Stable v2.1 correctness baseline.

- `dual_trend_momentum_strategy_v2_1.pine`
  Stable v2.1 strategy correctness baseline.

- `Dual Trend + Momentum Swing Score v2.0`
  Original v2.0 indicator.

- `Dual Trend Momentum Strategy Tester v2.0`
  Original v2.0 strategy tester.

- `design.txt`
  Design notes and implementation roadmap.

- `docs/backtest_methodology.md`
  Phase 3 testing procedure for setup isolation, scoring mode comparison, market regime splits, and pass/fail criteria.

- `docs/backtest_results_v2_3.md`
  Phase 3 results log template.

- `docs/backtest_run_log_template.csv`
  Spreadsheet-friendly run log template.

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

- ATR
- SMA50
- Structure
- Structure + ATR

Target modes:

- R Multiple
- Prior High
- Measured Move
- ATR Target

The scripts estimate:

- Suggested stop
- Target
- Entry risk %
- Resistance distance
- Reward/risk to target
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

Use `src/dual_trend_momentum_strategy_v3.pine` in TradingView Strategy Tester for current testing. Use `dual_trend_momentum_strategy_v2_3.pine` as the stable Phase 3 baseline.

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
2. Paste or import `src/dual_trend_momentum_indicator_v3.pine`.
3. Review the score table and last-bar label.
4. Use `src/dual_trend_momentum_strategy_v3.pine` separately to compare entry and exit rules.
5. Compile both scripts after changes; Pine warnings often point to history-dependent calculations that need to be assigned before use.

For the full workflow, see `docs/usage_workflow.md`.

## Backtesting Workflow

Use `docs/backtest_methodology.md` for Phase 3 tests. Record results in `docs/backtest_results_v2_3.md` or `docs/backtest_run_log_template.csv`.

## Notes

The strategy tester is for comparing rule behavior, not for automatic trading advice. Signals still need chart context, liquidity review, and position sizing discipline.
