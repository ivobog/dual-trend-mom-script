# Changelog

## v3.2.0

- Prepared the next engine library version for `ivobog/DualTrendMomentumEngine/3`.
- Moved larger pure score/classification modules into exported engine functions:
  - Relative strength scoring
  - HTF scoring
  - Local/blended trend scoring
  - Momentum, setup, risk, and dual scoring
  - Blowoff/distribution danger helpers
  - Setup classification
  - Pullback health, filter problem text, and action bias
- Updated v3 indicator and strategy to call the future `/3` engine API.
- Kept `request.security`, visual/dashboard/alert rendering, and strategy order execution local.

## v3.1.0

- Switched v3 indicator and strategy to `ivobog/DualTrendMomentumEngine/2`.
- Removed duplicated local pure helper functions from v3 scripts.
- Imported remaining status/classification constants from the engine library.
- Replaced local helper calls with engine library calls:
  - `rocPct`
  - `slopePct`
  - `slopeAtr`
  - `pctDistance`
  - `rollingSum`
  - `distributionBar`

## v3.0.0

- Added clean `src/` structure for v3 scripts.
- Added `src/dual_trend_momentum_engine.pine` as the Pine library anchor for future shared-engine extraction.
- Added setup classification, scoring model, and backtest methodology docs.
- Added usage workflow, release checklist, shared-engine contract, and screenshot placeholder docs.
- Added examples folder for screenshots.
- Imported published Pine library `ivobog/DualTrendMomentumEngine/1` for engine version, primary classification constants, and score clamping.
- Prepared local engine source for library version 2 with pure helper exports and remaining status/classification constants.
- Kept the larger signal calculation block local until the published library exports the full computation surface.

## v2.3.0

- Added market-regime split filters to the strategy tester:
  - Risk-on
  - Neutral
  - Risk-off
- Added Phase 3 backtest methodology and results templates.

## v2.2.0

- Added Conservative, Balanced, and Early Rocket scoring modes.
- Added dashboard modes:
  - Off
  - Compact
  - Full
  - Debug
- Added stop modes:
  - ATR
  - SMA50
  - Structure
  - Structure + ATR
- Added target modes:
  - R Multiple
  - Prior High
  - Measured Move
  - ATR Target
- Added optional dynamic JSON alerts.
- Updated reward/risk logic to evaluate the selected target.

## v2.1.0

- Fixed pullback chronology so the pullback low must occur after the prior high.
- Replaced weak higher-low checks with pivot-based swing structure.
- Anchored failed breakout detection to a stored breakout level.
- Added notional liquidity filtering.
- Updated strategy stop/target initialization to use actual strategy fill price.
- Added engine version display.

## v2.0.0

- Added Pine v6 indicator and strategy tester with trend, momentum, setup, risk, market regime, relative strength, HTF confirmation, dashboard, labels, and alerts.
