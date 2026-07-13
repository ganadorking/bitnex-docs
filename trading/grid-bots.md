# Grid Bots

Grid bots are automated trading strategies that buy low and sell high for you, over and over, inside a price range you define. Instead of watching the chart and placing dozens of orders by hand, you configure a bot once and it places a ladder of orders across the range — buying when price dips to a lower level and selling when it climbs back up — capturing profit from each swing.

Grid bots run from inside the app and place real orders on the underlying on-chain exchange protocol, so every fill settles on-chain just like a manual trade.

## How grid trading works

A grid bot divides a price range into evenly spaced levels. At each level it maintains an order:

- **Below the current price** — buy orders. When price falls to a level, the bot buys.
- **Above the current price** — sell orders. When price rises to a level, the bot sells.

Each time a buy fills, the bot places a corresponding sell one level higher (and vice versa). Every completed buy-then-sell round trip books a small profit — the spacing between the two levels, minus [fees](../platform/fees.md). The more times price oscillates through the grid, the more round trips the bot completes.

{% hint style="info" %}
Grid orders are regular orders on the protocol's order book. They remain active until they are filled or cancelled — stopping the bot is what cancels its outstanding orders.
{% endhint %}

## Configuring a grid bot

When creating a bot you set:

| Parameter | What it controls |
| --- | --- |
| **Market** | The market the bot trades. |
| **Range low / high** | The price boundaries the grid operates within. Orders are only placed inside this range. |
| **Number of levels** | How many grid lines the range is divided into. More levels = tighter spacing, more frequent but smaller profits per round trip. Fewer levels = wider spacing, larger but less frequent profits. |
| **Investment** | The capital the bot allocates across its orders. |
| **Leverage** (where applicable) | On perp markets, the leverage applied to the bot's position. Higher leverage amplifies both returns and liquidation risk. |

A few practical notes:

- Set the range around where you actually expect price to trade. A range that is too wide leaves capital idle at levels that never fill; a range that is too narrow gets exited quickly.
- Each sub-order in the grid must meet the protocol's minimum order size. If your investment is small and your level count is high, individual orders may fall below the minimum — reduce the number of levels or increase the investment.
- The estimated cost and details are shown before you confirm, as with any order on Bitnex.

## Monitoring a running bot

Once running, the bot's page shows its live state: current position, open grid orders, filled orders, and realized profit from completed round trips. You can also see the bot's orders alongside your other activity in the Pro terminal's order tabs — see [The Interface](interface.md).

## Stopping a bot

You can stop a grid bot at any time from the app. Stopping the bot cancels its remaining open orders. Depending on the market and your preference, you can then close any position the bot was holding, or keep it and manage it manually like any other position — including attaching a [TP/SL](tp-sl.md).

## When grids do well — and when they don't

**Grids perform best in ranging (sideways) markets.** When price oscillates within your range, the bot repeatedly buys dips and sells rallies, accumulating profit from each swing.

**Grids perform poorly in strong trends.** If price breaks decisively out of the range:

- **Above the range** — all sell levels have filled and the bot has no more inventory to sell; it simply stops earning while price runs.
- **Below the range** — all buy levels have filled and the bot is holding its maximum position while price keeps falling, sitting on unrealized losses.

{% hint style="danger" %}
**Leverage + a price that leaves your range can lead to liquidation.** On a leveraged grid, if price trends beyond the range the bot can be left holding a full-size leveraged position against the trend. If margin falls below the maintenance requirement, the position is liquidated by the underlying protocol. Use conservative leverage, size grids so you can tolerate a full range breakout, and understand the mechanics in [Liquidation](liquidation.md) before running leveraged grids.
{% endhint %}

## Risk checklist

- Grid trading involves risk, including loss of your investment. It is not passive "guaranteed yield".
- Choose your range based on realistic expectations of where the market will trade, not just recent highs and lows.
- On perp grids, keep an eye on the [funding rate](funding-rate.md) — a persistently one-sided rate affects the carry cost of the position the bot holds.
- Start with a small investment and low (or no) leverage until you understand how the bot behaves in live conditions.

## Related pages

- [Order Types](order-types.md) — the order types available for manual trading
- [Margining](margining.md) — cross vs isolated margin and leverage
- [Liquidation](liquidation.md) — how and when positions are liquidated
- [Fees](../platform/fees.md) — how trading fees apply to every grid order
