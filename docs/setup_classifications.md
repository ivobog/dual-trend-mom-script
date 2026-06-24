# Setup Classifications

## Prime Clean Pullback

Highest-quality pullback setup.

Expected traits:

- Strong trend score.
- Strong momentum score.
- Healthy pullback depth.
- Price holds or reclaims key moving averages.
- RSI is constructive but not overheated.
- No distribution risk.
- No failed breakout.
- Reward/risk passes the active mode threshold.

## Clean Bull Pullback

Tradable pullback that is slightly less strict than Prime.

Expected traits:

- Trend remains intact.
- Pullback is not too deep.
- Price is above or reclaiming the mid trend.
- Volume behavior is not destructive.
- Reward/risk is acceptable.

## Fresh Breakout

Breakout through resistance with volume support.

Expected traits:

- Price clears prior resistance.
- Volume expands.
- Candle closes strongly.
- Price is not deeply overheated.
- Market and relative strength filters are acceptable.

## Momentum Continuation

Strong trend and momentum, but entry quality is less clean than a pullback or fresh breakout.

Default stance:

```text
Disabled in strategy tests until backtest evidence supports enabling it.
```

## Extended Momentum

Trend and momentum are strong, but entry is late.

Default action:

```text
Do not chase. Wait for consolidation or a pullback.
```

## Overheated Momentum

Momentum risk is elevated.

Common causes:

- RSI too high.
- Price too extended.
- Gap exhaustion.
- Wide stop distance.

Default action:

```text
Avoid new long entries. Existing holders may trail stops.
```

## Distribution Risk

Avoid or exit-risk condition.

Common causes:

- Heavy red volume.
- Distribution cluster.
- Close below SMA50 on elevated volume.
- Failed breakout.
- Gap exhaustion.

## Failed Breakout

Breakout failure anchored to a stored breakout level.

Expected sequence:

1. Price breaks above resistance.
2. Breakout level is stored.
3. Price closes back below that level within the failure window.
4. Failure occurs on elevated volume.

## Trend Repair

Chart is improving but not ready.

Default action:

```text
Watchlist only.
```

