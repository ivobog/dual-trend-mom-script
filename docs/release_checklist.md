# Release Checklist

Use this checklist before treating a version as stable.

## Source Checks

- `ENGINE_VERSION` matches between indicator and strategy.
- Indicator title matches the intended version.
- Strategy title matches the intended version.
- Shared signal changes are applied to both indicator and strategy.
- Strategy-only changes are limited to entries, exits, backtest filters, and strategy dashboard rows.
- Indicator-only changes are limited to chart display, labels, plots, and alert presentation.

## TradingView Compile Checks

Compile each script:

```text
src/dual_trend_momentum_indicator_v3.pine
src/dual_trend_momentum_strategy_v3.pine
src/dual_trend_momentum_engine.pine
```

When the library source changes, publish it as a new TradingView library version before changing indicator/strategy import paths.

Record compile status:

| Script | Compile Status | Notes |
|---|---|---|
| Indicator v3 | Pending |  |
| Strategy v3 | Pending |  |
| Engine library anchor | Pending |  |

## Library Import Checks

- Current script import path matches the published library version.
- Imported `engine.engineVersion()` displays the expected version.
- No script imports a library version that has not been published yet.
- Helper functions are removed from scripts only after the imported replacements compile.

## Visual Checks

- Compact dashboard fits on a normal chart.
- Full dashboard exposes the main trading diagnostics.
- Debug dashboard exposes internal diagnostics.
- Last-bar label shows engine version, classification, action, stop, target, and reward/risk.
- Stop and target plots update when stop/target modes change.

## Strategy Checks

- Setup toggles isolate one setup type at a time.
- Market-regime toggles block or allow entries as expected.
- Stops and targets initialize from actual strategy fill price.
- Breakeven and ATR trailing options still behave as expected.
- Date filter still works.

## Alert Checks

- Existing `alertcondition()` alerts still compile.
- JSON alerts are off by default.
- JSON alerts include:

```text
ticker
timeframe
engineVersion
classification
action
dualScore
trendScore
momentumScore
setupScore
riskScore
marketRegime
relativeStrength
entry
stop
target
rewardRisk
```

## Documentation Checks

- `README.md` points to the current files.
- `CHANGELOG.md` includes the release.
- `docs/architecture.md` explains engine/library status.
- `docs/scoring_model.md` matches script weights.
- `docs/setup_classifications.md` matches script classifications.
- `docs/backtest_methodology.md` is still accurate.

## Release Decision

Only mark a version stable when both v3 scripts compile in TradingView and at least a smoke-test chart confirms the dashboard, stop/target, and strategy entry behavior.
