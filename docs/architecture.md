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

The v3 architecture adds `src/dual_trend_momentum_engine.pine` as a library anchor. The intended end state is:

```text
Indicator imports engine library.
Strategy imports engine library.
Shared scoring/classification helpers live only in the engine.
Indicator owns visuals and alerts.
Strategy owns entries, exits, and backtest controls.
```

## Why The Engine Is Not Fully Imported Yet

The published library currently does not export the full signal engine. Removing the remaining local calculation block before those exports exist would leave the indicator and strategy without the variables used by dashboards, alerts, plots, entries, exits, and classification logic.

## Migration Plan

1. Keep v3 scripts compiling with library `/2` plus the local calculation block.
2. Move score modules into exported library functions.
3. Publish another library version.
4. Remove local score/classification calculation only after imported replacements compile.
5. Keep visual/dashboard code in the indicator.
6. Keep order/execution code in the strategy.

## Drift Control Until Full Library Extraction

When changing shared signal logic before the full library import is complete:

```text
Update indicator and strategy in the same commit.
Keep ENGINE_VERSION identical.
Run TradingView compile checks for both scripts.
Record behavior changes in CHANGELOG.md.
```

See `docs/engine_contract.md` for the shared-engine boundary and `docs/release_checklist.md` for release verification.
