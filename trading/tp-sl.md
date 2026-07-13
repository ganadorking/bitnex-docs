# Take Profit / Stop Loss

Take Profit (TP) and Stop Loss (SL) orders let you automate your exits. Set a target where profits are locked in, a level where losses are cut, or both — and let the platform manage the trade for you, even while you're away.

TP/SL is available in both [Lite](../platform/lite-mode.md) and [Pro](interface.md) views.

## How TP/SL works

- A **Take Profit** triggers when the market moves in your favor and reaches your target price, closing (all or part of) the position to realize the gain.
- A **Stop Loss** triggers when the market moves against you and reaches your stop price, closing (all or part of) the position to limit the loss.
- Both are **trigger orders**: they rest off the book until the **mark price** reaches the trigger level, at which point a **market order** is executed to close the position.

{% hint style="info" %}
Triggers are evaluated against the **mark price**, not the last traded price. This protects you from being stopped out by a single outlier trade or a brief wick in a thin book.
{% endhint %}

## Two ways to set TP/SL

### 1. Attach on order placement

When placing a new order, expand the **TP/SL** section of the order form and set your targets before you enter the trade. Once the order fills, the TP and SL are active immediately — your exit plan is in place from the first second of the position.

### 2. Add to an existing position

Already in a trade? Open the **Positions** tab, select **TP/SL** on the position, and configure your exits there. You can add, edit, or remove TP/SL on any open position at any time.

## Configuration options

| Option | What it does |
| --- | --- |
| **Trigger price** | Set the exact price at which the TP or SL fires. |
| **Gain / loss %** | Set the trigger as a percentage gain or loss instead of a price — the platform calculates the corresponding trigger price for you. |
| **Full size** | The entire position is closed when the trigger fires. |
| **Partial size** | Only the amount you specify is closed — useful for scaling out of winners or reducing risk in stages. |

Estimated PnL at the trigger level is shown as you configure it, so you know what a fill at that price would mean before you confirm. See [Entry Price & PnL](entry-price-pnl.md) for how PnL is calculated.

## Managing TP/SL

- **Edit anytime** — change the trigger price, switch between price and % mode, or adjust the size of an existing TP/SL.
- **Cancel anytime** — remove a TP or SL without touching the position itself.
- **Drag on the chart (Pro)** — your active TP and SL appear as lines on the Pro chart. Drag a line to a new level and confirm to update the trigger instantly. This is often the fastest way to trail a stop as a trade moves in your favor.

{% hint style="warning" %}
**A stop loss is not a guarantee.** Two things every trader should understand:

- **Execution price can differ from the trigger price.** When your SL fires, it executes as a market order at the best available prices. In fast or gapping markets, the fill can be worse than the trigger — this is slippage, and it is inherent to stop orders on any venue.
- **An SL set too close to your liquidation price may not protect you.** If price gaps through both levels, or slippage carries the fill past your maintenance threshold, the position can be liquidated before or despite the stop. Keep a healthy buffer between your stop and your estimated liquidation price — see [Liquidation](liquidation.md).
{% endhint %}

## TP/SL in Lite vs. Pro

| | Lite | Pro |
| --- | --- | --- |
| Attach TP/SL to a new order | Yes | Yes |
| Set TP/SL on an open position | Yes | Yes |
| Price-based trigger | Yes | Yes |
| Gain/loss %-based trigger | Yes | Yes |
| Partial-size TP/SL | Yes | Yes |
| Drag TP/SL lines on the chart | — | Yes |

## Tips for using TP/SL well

- **Set the SL first.** Decide what you're willing to lose before thinking about what you hope to gain.
- **Mind the funding and volatility.** On volatile markets, very tight stops get triggered by normal noise. Give the trade room, and size the position down instead — see [Margining](margining.md).
- **Use partial TPs to de-risk.** Taking part of the position off at a first target lets the rest run with reduced exposure.
- **Combine with stop orders.** For more control over execution, Pro also offers standalone Stop Market and Stop Limit orders — see [Order Types](order-types.md).

{% hint style="success" %}
TP/SL orders are managed by the underlying on-chain exchange protocol, so they remain active even if you close the Bitnex tab or disconnect your wallet.
{% endhint %}
