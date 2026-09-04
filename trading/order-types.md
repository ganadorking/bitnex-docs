# Order Types

Dasus Pro supports a full range of order types, from simple market orders to advanced execution algorithms. Every order is matched on the underlying on-chain exchange protocol's central limit order book, and the estimated cost — including fees — is always shown in Order Details before you confirm.

| Order type | What it does | When to use it |
| --- | --- | --- |
| **Market** | Executes immediately at the best available price | You want in or out *now* and accept the current price |
| **Limit** | Executes only at your specified price or better | You want price control and are willing to wait for a fill |
| **Stop Market** | Triggers a market order when price reaches your stop price | Cutting losses or entering on a breakout, prioritising execution |
| **Stop Limit** | Triggers a limit order when price reaches your stop price | Same as Stop Market, but with price control on the fill |
| **Take Market / Take Limit** | Triggers an order when price reaches your profit target | Locking in gains automatically without watching the chart |
| **Scale** | Splits one order into multiple limit orders across a price range | Building or exiting a position gradually across a zone |
| **TWAP** | Splits one order into slices executed over time, natively on the protocol | Large orders you want to execute with reduced market impact |
| **Chase** | A post-only order that automatically re-prices to stay at the front of the book | Getting a maker fill on a moving market without re-quoting by hand |

{% hint style="info" %}
**Lite mode** offers Market and Limit orders, plus attachable Take Profit / Stop Loss. Switch to **Pro** anytime for the full set — see [The Trading Interface](interface.md). All of these work on [spot](spot.md) markets too, not just perps.
{% endhint %}

### Market

A market order executes immediately against the best prices resting on the order book. You specify the size; the protocol fills you at the best available levels until the order is complete.

- **Pros:** guaranteed execution (as long as there is liquidity), instant.
- **Cons:** the fill price can differ from the last price you saw — especially for larger sizes in thinner books (slippage).

**Example:** BTC is trading around $65,000 and you want long exposure immediately. You place a market buy for 0.1 BTC and are filled at the best asks on the book. Your average fill becomes your [entry price](entry-price-pnl.md).

### Limit

A limit order rests on the order book at your chosen price and only fills at that price or better. Buy limits fill at your price or lower; sell limits fill at your price or higher.

**Time-in-force (TIF)** controls how long the order stays active:

| TIF | Behaviour |
| --- | --- |
| **GTC** (Good-Til-Cancelled) | Rests on the book until fully filled or you cancel it |
| **IOC** (Immediate-Or-Cancel) | Fills whatever is possible instantly; the unfilled remainder is cancelled |
| **Post-only** | Only enters the book as a maker order; cancelled if it would execute immediately as a taker |

{% hint style="info" %}
Post-only is useful if you specifically want maker execution. Maker and taker orders are charged at different rates — see [Fees](../platform/fees.md).
{% endhint %}

**Example:** ETH trades at $3,450 and you want to buy a dip. You place a GTC limit buy at $3,380. The order rests on the book and fills only if the price trades down to your level.

### Stop Market

A stop market order stays inactive until the market reaches your **trigger price**, then executes as a market order.

- As a **stop loss:** you're long BTC from $65,000 and set a stop market sell triggered at $63,500. If price falls to $63,500, your position is closed at market — no manual action needed.
- As a **breakout entry:** you set a stop market buy above resistance to enter only if the market breaks out.

Stop markets prioritise *getting filled* over the exact fill price. In fast markets, the fill can be some distance from the trigger.

### Stop Limit

A stop limit works like a stop market, but places a **limit order** at your chosen limit price when triggered, instead of a market order.

**Example:** You're long and set a stop with trigger $63,500 and limit price $63,300. If price hits $63,500, a sell limit at $63,300 is placed. You won't be filled below $63,300 — but if the market gaps through your limit, the order may not fill at all, leaving the position open.

{% hint style="warning" %}
A stop limit protects you from a bad fill price but does **not** guarantee execution. For a stop loss you rely on to prevent [liquidation](liquidation.md), a stop market is generally the safer choice.
{% endhint %}

### Take Profit (Take Market / Take Limit)

A take profit order triggers when the market reaches your profit target and closes some or all of your position. **Take Market** fills at market when triggered; **Take Limit** places a limit order at your chosen price instead — the same trade-off as Stop Market vs. Stop Limit. On Dasus you can:

- Attach a TP to a new order at placement time.
- Add or edit a TP on an existing position — full or partial size, defined by price or by gain %.
- Drag the TP line directly on the Pro chart.

**Example:** You're long SOL from $140 and set a take profit at $155 for 50% of the position. If price reaches $155, half the position closes automatically and the realized PnL is booked.

For the full workflow, see [Take Profit & Stop Loss](tp-sl.md).

### Scale

A scale order splits a single order into multiple limit orders (2 to 20) distributed across a price range you define — a start price, an end price, and the number of sub-orders. You can also apply a **size skew** to weight more size toward one end of the range. Each sub-order must meet the protocol's minimum order size.

**Example:** Instead of one limit buy at $3,380, you scale-buy ETH from $3,400 down to $3,300 across 10 orders, skewed so larger sizes sit at the lower prices. You accumulate progressively into weakness with a better blended entry.

Full details and configuration options: [Scale Orders](scale-orders.md).

### TWAP

A TWAP (time-weighted average price) order splits your total size into slices executed over a time window, natively by the underlying protocol. It's designed for larger orders where placing everything at once would move the market against you.

**Example:** You want to buy a position that is large relative to the book's current depth. Rather than sweeping the asks in one market order, you run a TWAP over 30 minutes and the order executes in evenly spaced slices, targeting the average price over that window.

Running TWAPs appear in the **TWAP** tab of the Pro terminal, where you can monitor progress or terminate them early. A TWAP requires a minimum of **$100** notional, runs for 5 minutes to 24 hours, and carries **no Dasus platform fee**. Full details: [TWAP Orders](twap.md).

### Chase

A chase order rests a **post-only limit** at the front of the book on your side and automatically **re-prices it** as the best bid/offer moves, so it keeps following the market without ever crossing the spread. Every fill it gets is a maker fill.

- **Offset** — how far behind the best bid/ask to rest. `0` keeps you at the front of the book; a larger offset trades fill probability for a better price.
- **Max chase distance** — how far the chase is allowed to follow the price away from where it started. Beyond that, it stops.
- **Re-pegs and filled size** are shown live in the **Chase** tab of the bottom panel, where you can stop it at any time.

{% hint style="warning" %}
**A chase runs in your browser tab.** Close the tab, switch markets or stop the chase and the re-pricing ends — but the order already resting on the book **stays open as a normal limit order**. Cancel it from Open Orders if you don't want it. The order form runs one chase at a time.
{% endhint %}

**Example:** you want to buy ETH as a maker while the price drifts up. Instead of cancelling and re-placing your limit every few seconds, you start a chase: it keeps your bid at the front of the book, filling at maker rates, until it's done or the price runs past your maximum distance.

---

{% hint style="success" %}
Whichever order type you use, the Order Details panel shows the estimated cost, fees and (for leveraged positions) the estimated liquidation price **before** you confirm. Review it every time — see [Fees](../platform/fees.md) and [Liquidation](liquidation.md).
{% endhint %}
