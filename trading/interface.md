# Trading Interface

This page walks through the anatomy of placing and managing a trade on Bitnex. The flow is the same in both views — [Lite](../platform/lite-mode.md) keeps it minimal, while [Pro](../platform/web-terminal.md) exposes the full terminal — so everything below applies to both, with extra depth where Pro adds more control.

{% hint style="info" %}
Before you can place your first order, make sure you have completed the one-time setup: connect, enable trading, and deposit USDC. See [Enable Trading](../guides/enable-trading.md) and [Funding Your Account](../platform/funding-account.md).
{% endhint %}

## Placing a trade, step by step

### 1. Pick a market

Use the market selector (or the watchlist/favorites bar in Pro) to choose what you want to trade. Bitnex lists dozens of perpetual markets — BTC, ETH, SOL and many more — plus spot markets. Each market shows its live stats: mark price, oracle price, 24h change and volume, open interest, and the current funding rate for perps.

### 2. Choose a side

- **Perps:** Long (you profit if price rises) or Short (you profit if price falls).
- **Spot:** Buy or Sell the asset outright.

In Pro, the Buy/Long and Sell/Short toggle sits at the top of the order form. In Lite, they are the two large buttons under the chart.

### 3. Set your size

Enter the amount you want to trade, in the asset or in USD terms. For perps, remember that leverage multiplies your exposure — a small margin amount can control a much larger position.

### 4. Set leverage (perps only)

Adjust leverage per market with the leverage slider, up to that market's maximum (limits vary per market and are always shown in the app). Higher leverage means less margin required but a liquidation price closer to your entry. See [Margining](margining.md) for how cross and isolated margin work.

### 5. Choose an order type

Lite offers **Market** and **Limit** orders, plus attached TP/SL. Pro adds the full set:

| Order type | What it does |
|---|---|
| **Market** | Executes immediately at the best available price |
| **Limit** | Executes at your price or better; supports time-in-force options (GTC, IOC, post-only) |
| **Stop Market / Stop Limit** | Trigger orders that activate when price reaches your stop level |
| **Take Profit** | Closes a position at a profit target |
| **Scale** | Splits one order into multiple limit orders across a price range |
| **TWAP** | Splits the order over time for a time-weighted average price |

Full details, including when to use each type, are on the [Order Types](order-types.md) page, with dedicated pages for [Scale Orders](scale-orders.md) and [TWAP](twap.md).

### 6. Attach TP/SL (optional)

You can attach a Take Profit and/or Stop Loss to the order before placing it, defined by price or by gain/loss percentage. You can also add or edit them later on any open position — including by dragging the lines directly on the Pro chart. See [Take Profit & Stop Loss](tp-sl.md).

### 7. Review Order Details

Before you confirm, the Order Details section shows exactly what you are about to do:

- **Fees** — the exact trading cost for this order, always displayed before you trade. See [Fees](../platform/fees.md).
- **Margin required** — how much of your balance the position will use.
- **Estimated liquidation price** — where the position would be liquidated at the chosen size and leverage. See [Liquidation](liquidation.md).

{% hint style="warning" %}
Always check the estimated liquidation price before placing a leveraged order. If it sits uncomfortably close to the current price, reduce your leverage or position size.
{% endhint %}

### 8. Place the order

Hit the button. Because trading runs through your agent wallet, there is no wallet popup and no gas — the order is signed and routed instantly. Market orders fill against the live on-chain order book; limit and trigger orders rest until their conditions are met.

## Managing your trades

Once you are in a trade, everything lives in the tabs below the chart (Pro) or in the Positions/Orders/History tabs (Lite).

### Positions

The positions table shows each open position with:

- **Size and side** — long or short, and how much.
- **Entry price** — your average fill price across all fills. See [Entry Price & PnL](entry-price-pnl.md).
- **Mark price** — the current fair price used for PnL and liquidation.
- **Unrealized PnL and ROE %** — profit or loss if you closed now, and its size relative to the margin used.
- **Liquidation price** — updated live as margin and mark price move.
- **TP/SL** — attached targets, editable or cancellable at any time (full or partial size).

From this table you can close a position (fully or partially), adjust margin, or set and modify TP/SL.

### Open orders

Every resting order — limit, stop, take profit, scale sub-orders — appears under Open Orders. From here you can **modify** the price or size, or **cancel** individual orders or all at once. Orders remain active until they fill or you cancel them.

### History and fills

- **Trade History** shows every fill: price, size, fee paid, and timestamp.
- **Order History** shows the lifecycle of past orders, including cancelled and expired ones.
- Pro adds **Funding History** (funding payments on your perp positions — see [Funding Rate](funding-rate.md)) and a **TWAP** tab for running TWAP orders.

{% hint style="success" %}
Everything settles on-chain through the underlying protocol, so your positions, orders, and history reflect the actual on-chain state of your account — not an internal ledger held by Bitnex.
{% endhint %}

## Related pages

- [Order Types](order-types.md) — every order type explained
- [Take Profit & Stop Loss](tp-sl.md) — protecting positions
- [Margining](margining.md) — cross vs. isolated, leverage
- [Liquidation](liquidation.md) — how liquidation works and how to avoid it
- [Entry Price & PnL](entry-price-pnl.md) — how your numbers are calculated
