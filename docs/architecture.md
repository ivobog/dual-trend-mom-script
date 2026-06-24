# Architecture

## Current Structure

```text
src/
  dual_trend_momentum_engine.pine
  dual_trend_momentum_indicator_v3.pine
  dual_trend_momentum_strategy_v3.pine
docs/
  architecture.md
  backtest_methodology.md
  backtest_results_v2_3.md
  engine_contract.md
  release_checklist.md
  scoring_model.md
  setup_classifications.md
  usage_workflow.md
examples/
  screenshots/
```

## Engine Strategy

The indicator and strategy import the published engine library:

```pine
import ivobog/DualTrendMomentumEngine/2 as engine
```

Library version 2 provides shared version/classification helpers, status constants, score clamping, and pure helper exports such as ROC, slope, rolling sum, percent distance, and distribution-bar helpers.

The next engine version is prepared in `src/dual_trend_momentum_engine.pine` and should be published as library version 3:

```pine
import ivobog/DualTrendMomentumEngine/3 as engine
```

Library version 3 adds exported scoring and classification modules for relative strength, HTF trend, local trend, momentum, setup, risk, dual score composition, setup classification, pullback health, filter problem text, and action bias.

The v3 architecture end state is now:

```text
Indicator imports engine library.
Strategy imports engine library.
Shared scoring/classification helpers live only in the engine.
Indicator owns visuals and alerts.
Strategy owns entries, exits, and backtest controls.
```

## Current Boundary

The engine owns pure scoring and classification decisions. The indicator and strategy still own data collection, especially `request.security` calls, plus chart rendering, alerts, strategy entries, exits, and dashboards.

## Migration Plan

1. Publish `src/dual_trend_momentum_engine.pine` as library version `/3`.
2. Compile the v3.2 indicator and strategy with `import ivobog/DualTrendMomentumEngine/3 as engine`.
3. Keep visual/dashboard code in the indicator.
4. Keep order/execution code in the strategy.

## Drift Control

When changing shared signal logic:

```text
Update indicator and strategy in the same commit.
Keep ENGINE_VERSION identical.
Run TradingView compile checks for both scripts.
Record behavior changes in CHANGELOG.md.
```

See `docs/engine_contract.md` for the shared-engine boundary and `docs/release_checklist.md` for release verification.
