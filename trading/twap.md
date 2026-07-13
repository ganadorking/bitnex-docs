# TWAP Orders

A **TWAP (Time-Weighted Average Price)** order splits a large order into smaller pieces and executes them at regular intervals over a period of time you choose. Instead of hitting the market with your full size at once, a TWAP works your order gradually — aiming for an average execution price close to the market's time-weighted average over that window.

On Bitnex, TWAP execution is handled **natively by the underlying on-chain exchange protocol**: once you submit a TWAP, the protocol slices and executes the sub-orders on-chain over the duration. You don't need to keep the app open for the order to keep running.

## Why use a TWAP?

Placing a single large market order can move the price against you — you "walk the book" and each successive fill gets worse. A TWAP spreads that impact out over time.

Use a TWAP when:

- **Your size is large relative to the market's liquidity** — entering or exiting a big position without pushing the price.
- **You want to reduce market impact** — smaller slices are absorbed by the order book more easily than one large sweep.
- **You want an average price, not a single print** — useful for building or unwinding a position without trying to time one perfect entry.
- **You want passive, hands-off execution** — set the size and duration, and let the protocol work the order.

{% hint style="info" %}
If you want to spread an order across a **price range** rather than across **time**, use a [Scale order](scale-orders.md) instead. TWAP distributes execution over time at prevailing prices; Scale distributes limit orders across price levels.
{% endhint %}

## Placing a TWAP on Pro

TWAP orders are available in the [Pro terminal](../platform/web-terminal.md):

1. Open the market you want to trade and select the **TWAP** order type in the order form.
2. Choose your side — **Buy/Long** or **Sell/Short**.
3. Enter the **total size** you want executed.
4. Set the **duration** — the total time window over which the order should run. The protocol divides your total size into sub-orders executed at intervals across this window.
5. Review the **Order Details**, including the estimated cost and fees, then confirm.

Because trading on Bitnex is gasless once [trading is enabled](../guides/enable-trading.md), each sub-order executes automatically — no wallet popups, no per-fill signatures.

{% hint style="warning" %}
Each executed slice is a fill and incurs trading fees like any other order. See [Fees](../platform/fees.md) for how maker/taker rates and your volume tier apply.
{% endhint %}

## Monitoring a running TWAP

Active TWAP orders appear in the **TWAP tab** of the bottom panel in the Pro terminal. From there you can track:

- **Progress** — how much of the total size has been executed so far.
- **Average fill price** — the running average across executed slices.
- **Time remaining** — how much of the duration is left.

You can **cancel a running TWAP at any time**. Already-executed slices remain filled (they are part of your position); only the unexecuted remainder is cancelled. Completed fills also show up in your **Trade History** tab like any other execution.

## TWAP vs. other order types

| | TWAP | Market | Scale |
| --- | --- | --- | --- |
| **Execution** | Sliced over time at intervals | Immediately, full size | Multiple limit orders across a price range |
| **Price** | Average of prevailing prices during the window | Best available prices right now | Only fills at your chosen levels or better |
| **Best for** | Large size, minimizing market impact | Speed and certainty of fill | Accumulating/distributing at specific prices |
| **Fill guarantee** | Fills at market as slices execute | Fills immediately | May not fill if price never reaches your range |

For the full comparison of everything available in the order form, see [Order Types](order-types.md).

## Caveats and risk notes

- **No price guarantee.** A TWAP executes at whatever prices prevail when each slice runs. In a trending market, your average price can end up meaningfully better — or worse — than the price when you submitted the order.
- **Time exposure.** While the TWAP runs, the market can move. A large adverse move mid-execution affects both your filled portion (as an open position) and the price of remaining slices.
- **Slices execute like market activity.** Each sub-order interacts with live liquidity; in thin markets, even slices can have some impact.
- **Positions opened by a TWAP behave normally.** Filled size counts toward your position, margin, and [liquidation](liquidation.md) calculations immediately — don't wait for the TWAP to complete before managing risk. You can attach a [TP/SL](tp-sl.md) to the resulting position at any time.

{% hint style="danger" %}
A TWAP reduces market impact — it does not remove market risk. Size your orders relative to your margin, monitor the TWAP tab while large orders are working, and use stop losses on the resulting position. See [Margining](margining.md) and [Liquidation](liquidation.md).
{% endhint %}
