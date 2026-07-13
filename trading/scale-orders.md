# Scale Orders

Scale orders let you split one large order into multiple limit orders spread across a price range — in a single step. Instead of placing one big limit order at a single price (and hoping the market reaches it), a scale order ladders your entry or exit across several price levels, so you build or unwind a position gradually as price moves through your range.

Scale orders are available in [Pro mode](../platform/web-terminal.md) from the order form, alongside the other advanced [order types](order-types.md).

## Why use scale orders

- **Better average price.** By laddering orders across a range, you avoid committing your full size at a single price point. If the market dips into your range, your fills average out across the levels you set.
- **Less market impact.** Several smaller limit orders resting at different levels absorb into the book more gently than one large order at one price.
- **No manual laddering.** Placing ten limit orders by hand is slow and error-prone. A scale order builds the whole ladder from a few parameters and submits it at once.
- **Discipline.** You define your range and sizing logic up front, instead of reacting order-by-order as price moves.

{% hint style="info" %}
Scale orders are made of **limit orders**, so they only fill at your chosen prices or better. They may fill partially, fully, or not at all — if price never enters your range, nothing executes. If you need time-based execution instead of price-based, see [TWAP](twap.md).
{% endhint %}

## Parameters

When you place a scale order, you configure:

| Parameter | What it does |
| --- | --- |
| **Side** | Buy or Sell — the ladder works for both entries and exits. |
| **Range start / end** | The upper and lower price bounds. Sub-orders are distributed between these two prices. |
| **Number of orders** | How many limit orders the total size is split into. More orders means a finer ladder with smaller individual fills. |
| **Total size** | The combined size across all sub-orders. |
| **Size skew** | Optional weighting of size toward one end of the range. A flat ladder splits size evenly; a skewed ladder places more size at the far end of the range (e.g. more size at lower prices when buying). |

{% hint style="warning" %}
Each sub-order must meet the **minimum order size** enforced by the underlying protocol. If you split a small total size across too many levels, some sub-orders may fall below the minimum and the order won't be accepted — reduce the number of orders or increase the total size.
{% endhint %}

## Example: buying a dip

Suppose BTC is trading at $65,000 and you want to accumulate a long position if price pulls back — but you don't know exactly where the dip will bottom out.

Instead of guessing one price, you place a **buy scale order**:

- **Range:** $64,000 (start) down to $61,000 (end)
- **Number of orders:** 6
- **Total size:** 0.6 BTC
- **Size skew:** weighted toward the lower end of the range

This creates six limit buy orders spaced between $64,000 and $61,000. Because of the skew, the orders near $61,000 are larger than the ones near $64,000 — you buy a little on a shallow dip and a lot more if the market drops deeper into your range.

Possible outcomes:

- **Price dips to $63,000 and bounces.** Only the top few orders fill. You hold a partial position with a good entry, and the unfilled orders remain resting in the book.
- **Price sweeps the whole range.** All six orders fill. Your average [entry price](entry-price-pnl.md) sits below the midpoint of the range, because the skew put more size at the cheaper levels.
- **Price never enters the range.** Nothing fills. You can cancel the ladder at any time at no cost beyond normal order placement (placing and cancelling unfilled limit orders is free — fees apply only to fills; see [Fees](../platform/fees.md)).

## Monitoring and cancelling

Once submitted, each sub-order appears as an individual limit order in the **Open Orders** tab of the [trading interface](interface.md). From there you can:

- Track which levels have filled and which are still resting.
- Cancel individual sub-orders if you want to trim the ladder.
- Cancel all remaining sub-orders to abandon the strategy.

Filled sub-orders behave like any other fill: they update your position, average entry price, and [PnL](entry-price-pnl.md), and appear in your Trade History.

{% hint style="info" %}
Sub-orders remain active until they fill or you cancel them. If you're using scale orders to build a leveraged position, remember that fills increase your exposure as price moves against the direction of your ladder — keep an eye on your margin usage and [liquidation price](liquidation.md), and consider attaching a [stop loss](tp-sl.md) to the resulting position.
{% endhint %}

## Tips

- **Match the ladder to your thesis.** A wide range with many orders suits gradual accumulation; a tight range with few orders behaves closer to a single limit order.
- **Use skew deliberately.** Skewing size toward the far end of the range means better average pricing if the full range fills — but smaller fills if price only grazes the near end.
- **Check the minimums.** Before increasing the number of orders, confirm each sub-order still clears the protocol's minimum order size — the order form will flag this before you submit.
- **Review Order Details.** As with every order on Bitnex, the exact costs and parameters are shown in Order Details before you confirm.
