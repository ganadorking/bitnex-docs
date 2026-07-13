# Margin & Leverage

Margin is the collateral that backs your leveraged positions. On Bitnex, margin is managed entirely by the underlying on-chain exchange protocol — your funds stay in your own on-chain trading account, and the protocol enforces margin requirements transparently. This page explains how margin modes work, how leverage affects your risk, and how to adjust both.

{% hint style="info" %}
New to leveraged trading? Start with small position sizes and low leverage, and always check your estimated liquidation price in Order Details before confirming a trade. See [Liquidation](liquidation.md) for how liquidations work.
{% endhint %}

## What is margin?

When you open a perpetual futures position, you don't pay the full notional value of the trade. Instead, you post **margin** — collateral (USDC) from your trading account — and the position size is amplified by your chosen leverage.

- **Notional value** = position size × price
- **Margin used** = notional value ÷ leverage
- **Available to trade** = your account balance minus margin already in use

Example: a position with $1,000 notional at 10x leverage requires $100 of margin. The remaining balance in your account stays available for other positions or orders.

Your margin usage and available balance are always visible in the order form and in your [Portfolio](../platform/portfolio.md).

## Cross vs. isolated margin

Bitnex supports two margin modes:

| | Cross margin | Isolated margin |
|---|---|---|
| **Default** | Yes | No — opt-in per market |
| **Availability** | Lite and Pro | Pro only, on supported markets |
| **Collateral** | Your entire account balance backs all cross positions | Only the margin you assign to that position |
| **Loss containment** | A losing position can draw on your full balance before liquidation | Losses are capped at the margin allocated to the position |
| **Liquidation behavior** | Liquidation is based on account-wide margin | Liquidation is based on that position's margin only |

### Cross margin (default)

With cross margin, all of your positions share your account balance as collateral. Unrealized profits on one position can offset losses on another, which makes liquidation less likely for any single position — but a large loss can consume your whole account balance.

Cross margin is the default mode everywhere on Bitnex, and the only mode in [Lite](../platform/lite-mode.md).

### Isolated margin (Pro)

With isolated margin, you dedicate a specific amount of collateral to a single position. If the position moves against you, only that allocated margin is at risk — the rest of your account is untouched. The trade-off: because the position has less collateral behind it, it reaches its liquidation price sooner.

Isolated margin is available in [Pro mode](../platform/web-terminal.md) on supported markets. Select the margin mode in the order form before opening the position.

{% hint style="success" %}
Rule of thumb: use **isolated** when you want a strict cap on how much a single trade can lose. Use **cross** when you want maximum distance to liquidation and are comfortable with your full balance backing the position.
{% endhint %}

## Leverage

Leverage multiplies your exposure relative to the margin you post. It is set **per market**, and each market has its own maximum — limits vary by market and are shown directly in the app next to the leverage selector.

Key effects of leverage:

- **Higher leverage → less margin required** for the same position size.
- **Higher leverage → smaller price move to liquidation.** At high leverage, even a small adverse move can wipe out the margin backing the position.
- **Leverage amplifies both directions.** Gains and losses are calculated on the full notional value, not just your margin. See [Entry Price & PnL](entry-price-pnl.md).

{% hint style="warning" %}
Leverage does not change how much the market moves — it changes how much each move affects *you*. A position at high leverage can be liquidated by routine volatility. Size positions so that a normal market swing does not threaten your margin, and consider protecting positions with a stop loss ([TP/SL](tp-sl.md)).
{% endhint %}

## Changing leverage

You can adjust leverage per market at any time using the leverage control in the order form:

- **Before opening a position** — set the leverage you want; the order form updates the required margin and estimated liquidation price in real time.
- **On an open position** — changing the market's leverage adjusts the margin requirements of your existing position. Lowering leverage allocates more margin to the position (moving the liquidation price further away); raising leverage frees margin but brings the liquidation price closer.

For isolated positions on Pro, you can also adjust the margin assigned to the position directly, which changes its liquidation price without altering the position size.

{% hint style="danger" %}
Increasing leverage on an open position reduces the margin buffer protecting it. Always re-check the updated liquidation price after any leverage change.
{% endhint %}

## Monitoring your margin

Keep an eye on these figures, shown in the order form, the positions tab, and your [Portfolio](../platform/portfolio.md):

- **Margin used** — collateral currently committed to open positions.
- **Available to trade** — balance free for new positions and orders.
- **Estimated liquidation price** — shown before you place an order and on every open position.
- **Unrealized PnL** — moves with the mark price and affects your cross-margin health.

Because Bitnex uses a unified balance for perps and spot (see [Funding Your Account](../platform/funding-account.md)), your full trading account is visible in one place.

## Related pages

- [Liquidation](liquidation.md) — what happens when margin falls below the maintenance requirement
- [Take Profit & Stop Loss](tp-sl.md) — automate your exits and cap downside
- [Funding Rate](funding-rate.md) — periodic payments that affect perp positions
- [Order Types](order-types.md) — market, limit, trigger orders and more
