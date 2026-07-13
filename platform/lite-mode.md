# Lite Mode

Lite Mode is Bitnex's simplified trading view — a clean, fast interface built around one question: **buy or sell?** It strips the terminal down to a price chart, a Buy/Sell panel, and your positions, so you can open and manage trades in seconds without navigating an order book or a multi-widget layout.

Lite is ideal if you:

- Are new to perpetual futures or on-chain trading
- Want a quick, mobile-friendly way to open and close positions
- Prefer a Robinhood-style experience over a full trading terminal

If you want depth charts, the live order book, advanced order types, and a full workspace, switch to the [Pro terminal](web-terminal.md) — your account and funds are identical in both views.

{% hint style="info" %}
Lite and Pro are two views of the **same non-custodial account**. Your balances, positions, and orders are shared — switching views never moves funds or closes trades.
{% endhint %}

## The price chart

The chart is the centerpiece of Lite Mode:

- **Line or candlestick** display — toggle between a clean price line and candles.
- **Timeframes** — switch between intervals to zoom from short-term moves to the bigger picture.
- Live **mark price** and 24h change for the selected market.

Pick any market from the selector at the top — Lite supports the same perp and spot markets as Pro.

## The Buy / Sell flow

Placing a trade in Lite takes a few taps:

1. **Choose a side** — tap **Buy** (long) or **Sell** (short).
2. **Enter an amount** — in **USDC** or in the **coin** itself; Lite converts between the two automatically.
3. **Set leverage** — tap the **leverage button** to adjust it for the market, up to that market's maximum. Lite trades use [cross margin](../trading/margining.md).
4. **Optionally attach TP/SL** — set a take-profit and/or stop-loss before you enter (see below).
5. **Review Order Details** — the estimated cost, fees, and estimated liquidation price are shown **before** you confirm. See [Fees](fees.md) for how pricing works.
6. **Confirm** — with trading enabled, the order is signed automatically, with no wallet popup. See [Enable Trading](../guides/enable-trading.md).

### Market or Limit

By default, Lite places **market orders** for instant execution. In the order settings you can switch to a **limit order** and set the exact price you want to be filled at. For the full range of order types — stop orders, scale orders, TWAP, and more — use the [Pro terminal](../trading/order-types.md).

## Take Profit & Stop Loss

Lite supports TP/SL both on new orders and on open positions:

- **On entry** — attach a take-profit and/or stop-loss when placing the order.
- **On a position** — open any position and add or edit TP/SL at any time.
- Set targets by **price** or by **gain/loss %**, and edit or cancel them whenever you like.

Read the full guide in [Take Profit & Stop Loss](../trading/tp-sl.md).

{% hint style="warning" %}
Leverage amplifies both gains and losses. Always check the estimated liquidation price shown in Order Details, and consider using a stop loss. See [Liquidation](../trading/liquidation.md).
{% endhint %}

## Your Positions, Orders, and History

Below the chart, three tabs keep track of your activity:

| Tab | What it shows |
| --- | --- |
| **Your Positions** | Open positions with size, entry price, unrealized PnL, and quick actions to close or edit TP/SL |
| **Your Orders** | Resting orders (e.g. limit orders and TP/SL triggers) with the option to cancel |
| **History** | Your past trades and closed positions |

For a deeper breakdown of how entry price, PnL, and ROE are calculated, see [Entry Price & PnL](../trading/entry-price-pnl.md).

## Switching between Lite and Pro

You can switch views **anytime** from the interface toggle — instantly and as often as you like:

- **Same account, same funds** — nothing to transfer or reconfigure.
- Positions opened in Lite appear in Pro (and vice versa), with the full management tools of whichever view you're in.
- A common pattern: open simple trades in Lite, then jump into [Pro](web-terminal.md) when you want the order book, advanced order types, or detailed history tabs.

## Next steps

- [Getting Started](../getting-started.md) — connect a wallet and fund your account
- [Funding Your Account](funding-account.md) — deposits and withdrawals via Arbitrum (USDC)
- [Enable Trading](../guides/enable-trading.md) — one-time setup for gasless, popup-free trading
- [The Pro Web Terminal](web-terminal.md) — the full trading workspace
