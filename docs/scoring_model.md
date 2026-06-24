# Scoring Model

The v2.2 and v3 scripts expose three scoring modes.

## Balanced

Default swing-trading mode.

| Component | Weight |
|---|---:|
| Trend | 25% |
| Momentum | 25% |
| Setup Quality | 20% |
| Risk Control | 10% |
| Market Regime | 8% |
| Relative Strength | 8% |
| HTF Confirmation | 4% |

Default minimum reward/risk: `1.8R`.

## Conservative

Use for larger positions, weak markets, ETFs, and slower large-cap swing trades.

| Component | Weight |
|---|---:|
| Trend | 25% |
| Momentum | 20% |
| Setup Quality | 15% |
| Risk Control | 15% |
| Market Regime | 10% |
| Relative Strength | 10% |
| HTF Confirmation | 5% |

Default minimum reward/risk: `2.0R`.

Conservative mode forces relative strength and HTF quality to matter more.

## Early Rocket

Use for high-momentum growth names and fresh breakout candidates.

| Component | Weight |
|---|---:|
| Trend | 20% |
| Momentum | 30% |
| Setup Quality | 20% |
| Risk Control | 10% |
| Market Regime | 5% |
| Relative Strength | 10% |
| HTF Confirmation | 5% |

Default minimum reward/risk: `1.5R`.

Early Rocket mode emphasizes momentum and relative strength but avoids hard-blocking early entries on HTF alone.

