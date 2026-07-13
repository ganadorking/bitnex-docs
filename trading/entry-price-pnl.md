# Entry Price & PnL

Understanding how your entry price is calculated and how profit and loss (PnL) is measured is essential for tracking performance and managing risk. This page explains how Bitnex displays entry price, mark price, unrealized and realized PnL, and ROE — and how partial closes affect each of them.

## Entry price: your average across fills

Your **entry price** is the volume-weighted average price of all the fills that built your current position — not the price of any single order.

Orders on the underlying on-chain exchange protocol are matched against a live order book, so a single order can execute in several partial fills at slightly different prices. If you then add to the position with more orders, the entry price updates to reflect the new average.

**Example (long position):**

| Fill | Size | Fill Price |
|---|---|---|
| Fill 1 | 1 ETH | $3,000 |
| Fill 2 | 1 ETH | $3,100 |
| **Position** | **2 ETH** | **Entry price: $3,050** |

Key behaviors:

- **Adding to a position** in the same direction re-averages the entry price across all fills.
- **Reducing a position** (a partial close) does **not** change the entry price of the remaining size — it stays at the same average. The closed portion realizes PnL instead (see below).
- **Flipping direction** (closing fully and opening the opposite side) starts a fresh position with a new entry price.

{% hint style="info" %}
Fees (including the platform fee) are charged on each fill and shown in [Order Details](../platform/fees.md) before you trade. They affect your net result but are accounted for separately from the entry price itself.
{% endhint %}

## Mark price vs. last price

You will see two prices for every market, and they serve different purposes:

| Price | What it is | Used for |
|---|---|---|
| **Last price** | The price of the most recent trade in the order book | Charting, recent trades feed |
| **Mark price** | A protocol-computed fair price anchored to the underlying index/oracle price | **Unrealized PnL and [liquidation](liquidation.md)** |

The mark price is designed to resist short-term manipulation and thin-book price wicks. This is why your unrealized PnL can differ slightly from what the last traded price alone would suggest — and why a brief spike on the chart does not necessarily trigger a liquidation.

{% hint style="warning" %}
Liquidations and unrealized PnL are always driven by the **mark price**, not the last traded price. Both are visible per market in the app.
{% endhint %}

## Unrealized vs. realized PnL

### Unrealized PnL

**Unrealized PnL** is the profit or loss on your open position, marked to the current mark price. It moves in real time and is not yet booked to your balance.

- **Long:** unrealized PnL = (mark price − entry price) × position size
- **Short:** unrealized PnL = (entry price − mark price) × position size

Unrealized PnL contributes to your account equity and margin calculations — a large unrealized loss reduces the margin backing your positions. See [Margining](margining.md) for how this interacts with cross and isolated margin.

### Realized PnL

**Realized PnL** is booked the moment you close some or all of a position (or when a [TP/SL](tp-sl.md), liquidation, or other closing fill executes). It is calculated from your average entry price to the actual exit fill price, and it settles into your balance.

For perps, periodic [funding payments](funding-rate.md) also affect your running result while the position is open.

## ROE %

**ROE (Return on Equity)** expresses your PnL relative to the **margin used** for the position, rather than the position's full notional value:

> ROE % = PnL ÷ margin used × 100

Because leverage reduces the margin required for a given position size, ROE amplifies with leverage. A small move in the underlying price can produce a large positive or negative ROE on a highly leveraged position — in both directions.

{% hint style="danger" %}
High ROE cuts both ways. The same leverage that magnifies gains magnifies losses, and can bring your position toward its [liquidation price](liquidation.md) quickly. Size positions carefully and consider protective [stop losses](tp-sl.md).
{% endhint %}

## How partial closes work

Suppose you are long 2 ETH with an entry price of $3,050, and the mark price is $3,200:

1. **You close 1 ETH at $3,200.** The PnL on that 1 ETH — ($3,200 − $3,050) × 1 = $150, minus fees — becomes **realized PnL** and settles to your balance.
2. **The remaining 1 ETH keeps its $3,050 entry price.** Its unrealized PnL continues to float with the mark price.
3. If you later **add** 1 ETH at a new price, the entry price re-averages across the remaining and newly added size.

This means partial closes let you lock in profit (or cut part of a loss) without resetting the cost basis of what you keep open. You can also attach TP/SL to a **partial** position size — see [Take Profit & Stop Loss](tp-sl.md).

## Where to find it in the app

- **Positions table** (Lite and Pro): each open position shows entry price, mark price, unrealized PnL, and ROE %, updating in real time.
- **Position details:** open any position for a fuller breakdown, including margin used, estimated liquidation price, and attached TP/SL orders.
- **Trade History / Order History** (Pro tabs): per-fill records showing realized PnL on closing fills.
- **Share card:** generate a shareable card from any position showing the market, side, leverage, entry price, and ROE % — useful for sharing a trade without exposing your account size.
- **[Portfolio](../platform/portfolio.md):** account-level view of your PnL over time, across perps, spot, vaults, and staking.

## Related pages

- [Margining](margining.md) — cross vs. isolated margin and leverage
- [Liquidation](liquidation.md) — maintenance margin and estimated liquidation price
- [Take Profit & Stop Loss](tp-sl.md) — automating exits
- [Funding Rate](funding-rate.md) — periodic payments on perp positions
- [Fees](../platform/fees.md) — how trading costs are displayed before every order
