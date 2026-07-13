# Funding Rate

Perpetual futures never expire — there is no settlement date that forces the contract price back in line with the asset's real market price. The **funding rate** is the mechanism that does this job instead: a small, periodic payment exchanged between long and short position holders that keeps each perp's price anchored to its underlying index/oracle price.

Funding is paid **peer-to-peer** between traders through the underlying on-chain exchange protocol. **Bitnex does not receive any part of funding payments** — it is not a fee.

## Why perps need funding

A perpetual contract's price is set by supply and demand on the order book, so it can drift away from the spot price of the underlying asset:

- If the perp trades **above** the index price, the market is long-heavy. A **positive** funding rate makes longs pay shorts, which discourages new longs and pulls the perp price back down toward the index.
- If the perp trades **below** the index price, the market is short-heavy. A **negative** funding rate makes shorts pay longs, nudging the price back up.

This constant economic pressure is what allows a contract with no expiry to reliably track its underlying asset.

## How payments work

| Funding rate | Who pays | Who receives |
| --- | --- | --- |
| **Positive** | Longs | Shorts |
| **Negative** | Shorts | Longs |

Key points:

- Funding is exchanged **periodically** at set intervals determined by the underlying protocol. You only pay or receive funding if you hold an open position **at the moment funding is applied**.
- The amount is proportional to your **position size (notional value)**, not your margin. A highly leveraged position pays or receives funding on its full notional value.
- Payments settle directly between traders on-chain. Neither Bitnex nor the underlying protocol keeps the funding paid by the losing side of the rate.
- The rate is calculated per market by the underlying protocol, based on the gap between the perp's price and the index/oracle price.

{% hint style="info" %}
Funding can work **for** you. If you hold a position on the receiving side of the rate — for example, a short while funding is positive — you collect funding payments for as long as the conditions persist.
{% endhint %}

## Where to see funding on Bitnex

- **Market header** — the current funding rate for the selected market is displayed in the stats bar at the top of the [trading interface](interface.md), alongside mark price, oracle price, 24h volume and open interest.
- **Markets list** — compare funding rates across markets when choosing what to trade.
- **Funding History tab** — in Pro view, the Funding History tab in the bottom panel shows every funding payment your account has paid or received, per position and per interval.
- **Portfolio** — funding flows are reflected in your account's PnL; see [Portfolio](../platform/portfolio.md) for the account-level view.

## Impact on positions held over time

Funding is a real cost (or income) that compounds the longer you hold a position across funding intervals:

- **Short-term trades** that open and close between funding times pay no funding at all.
- **Positions held for days or weeks** can accumulate meaningful funding costs — especially in strongly trending markets where the rate stays elevated in one direction.
- Funding affects your effective PnL: a position can be flat on price but negative overall after sustained funding payments. See [Entry Price & PnL](entry-price-pnl.md) for how PnL is calculated.

{% hint style="warning" %}
Funding payments are drawn from your margin. On a highly leveraged position, sustained funding costs gradually erode your margin buffer and move your position closer to its liquidation price. Factor funding into your risk management — see [Liquidation](liquidation.md) and [Margining](margining.md).
{% endhint %}

## Quick example

Suppose the BTC perp is trading above the BTC index price and the funding rate for the current interval is positive:

1. You hold a **long** BTC position when funding is applied → you **pay** funding, proportional to your position's notional size.
2. A trader holding a **short** BTC position of equal size **receives** that payment.
3. If the rate flips negative in a later interval and you still hold the long, the flow reverses and you **receive** funding.

## Related pages

- [Trading Interface](interface.md) — where market stats, including funding, are displayed
- [Entry Price & PnL](entry-price-pnl.md) — how funding interacts with your profit and loss
- [Liquidation](liquidation.md) — why margin erosion from funding matters
- [Margining](margining.md) — cross vs. isolated margin and leverage
