# Shared Engine Contract

The v3 indicator and strategy import:

```pine
import ivobog/DualTrendMomentumEngine/2 as engine
```

The v3.2 indicator and strategy are prepared to import the next engine library version after publishing:

```pine
import ivobog/DualTrendMomentumEngine/3 as engine
```

Version `/3` owns the larger pure scoring and classification modules. The scripts keep data collection, rendering, alerts, and strategy order execution local.

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
Relative strength data collection
HTF trend data collection
Trend geometry
Pullback geometry
Resistance and breakout geometry
Volume quality
Candle quality
Failed breakout detection
Risk/reward helper
Engine score/classification calls
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

## Library Extraction Boundary

Imported from library version 3:

```text
engineVersion()
classification constants for primary setup/risk states
remaining classification/status constants
clampScore()
rocPct()
slopePct()
slopeAtr()
pctDistance()
rollingSum()
distributionBar()
relativeStrengthScore()
combinedRelativeStrengthScore()
relativeStrengthStatus()
htfScore()
htfStatus()
localTrendScore()
blendedTrendScore()
Momentum score
momentumScore()
setupScore()
riskScore()
dualScore()
blowoffTop()
distributionRisk()
classifySetup()
pullbackHealthStatus()
filterProblemText()
actionBiasText()
```

Keep stateful strategy order handling outside the engine.
