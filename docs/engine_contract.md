# Shared Engine Contract

The v3 indicator and strategy import:

```pine
import ivobog/DualTrendMomentumEngine/2 as engine
```

Until the Pine library extraction is complete, the indicator and strategy still contain a local copy of the larger signal calculation engine.

## Shared Logic

These concepts must stay aligned between:

```text
src/dual_trend_momentum_indicator_v3.pine
src/dual_trend_momentum_strategy_v3.pine
```

Shared areas:

```text
Inputs for trend, momentum, pullback, risk, market/RS, HTF, scoring, display, and alerts
Constants
Helper functions
Core indicators
Market regime
Relative strength
HTF trend
Trend geometry
Pullback geometry
Resistance and breakout geometry
Volume quality
Candle quality
Failed breakout detection
Risk/reward helper
Trend score
Momentum score
Setup score
Risk score
Dual score
Danger conditions
Classification logic
Pullback health
Action bias
Colors
Plots
Background
Labels
Alerts
```

Strategy-only areas:

```text
Strategy declaration
Strategy tester inputs
Market-regime entry split filters
Entry order IDs and reasons
Trade stop/target initialization from actual fill
Exit rules
Strategy dashboard rows
Strategy performance metrics
```

Indicator-only areas:

```text
Indicator declaration
Chart-review-only display behavior
Indicator dashboard rows
```

## Required Version Rule

Whenever shared signal logic changes:

```text
Indicator ENGINE_VERSION == Strategy ENGINE_VERSION
Indicator and strategy are changed in the same commit
Both scripts compile in TradingView
CHANGELOG.md records the behavior change
```

## Library Extraction Target

Imported from library version 2:

```text
engineVersion()
classification constants for primary setup/risk states
clampScore()
rocPct()
slopePct()
slopeAtr()
pctDistance()
rollingSum()
distributionBar()
remaining classification/status constants
```

Move score modules once the helper function signatures are stable:

```text
Trend score
Momentum score
Setup score
Risk score
Dual score
Classification
Action bias
```

Keep stateful strategy order handling outside the engine.
