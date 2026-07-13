# Web Terminal (Pro)

The Pro terminal is Bitnex's full-featured trading interface — a dense, multi-widget layout built for active traders. Everything you need to trade a market lives on a single screen: a TradingView-style chart, a live order book, a recent trades feed, an advanced order form, and a set of account tabs covering balances, positions, orders and history.

![The Pro terminal](../.gitbook/assets/trade-terminal.png)

You can switch between **Lite** and **Pro** at any time from the toggle in the top bar — your positions, orders and balances are the same in both views. If you prefer a simpler experience, see [Lite Mode](lite-mode.md).

{% hint style="info" %}
The Pro terminal streams data in real time directly from the underlying on-chain exchange protocol, so the prices, book depth and trades you see reflect the live on-chain order book.
{% endhint %}

## Market header

The bar at the top of the terminal shows the vital stats for the selected market:

- **Mark price** — the price used for margining, unrealized PnL and liquidation calculations.
- **Oracle price** — the underlying index price the perp is anchored to.
- **24h change & volume** — the market's price change and traded volume over the last 24 hours.
- **Open interest** — the total size of open positions in the market.
- **Funding** — the current funding rate and countdown to the next funding payment. See [Funding Rate](../trading/funding-rate.md) for how it works.

Click the market name to open the market selector and search across dozens of perp and spot markets.

## Chart

The chart is a TradingView-style candlestick chart with multiple timeframes, drawing tools and indicators.

A standout feature: you can **manage TP/SL directly on the chart**. When you have an open position, drag the take-profit and stop-loss lines to the price levels you want — the orders update as you drag. Entry price and estimated liquidation price are also plotted so you can see your risk at a glance. See [Take Profit & Stop Loss](../trading/tp-sl.md).

## Order book & recent trades

The **order book** shows live bids and asks with translucent depth bars so you can read liquidity at a glance:

- Asks (sell orders) on top, bids (buy orders) below, with the spread in the middle.
- A **grouping selector** lets you aggregate price levels for a wider or tighter view of depth.
- Click a price level to pre-fill it into the order form.

The **recent trades** feed streams every execution in the market in real time — price, size and time — colored by whether the buyer or seller was the aggressor.

## Order form

The order form is where you build and place trades:

- **Order types** — Market, Limit (with time-in-force options), Stop Market / Stop Limit, Take Profit, Scale and TWAP. See [Order Types](../trading/order-types.md) for a full comparison, plus dedicated pages for [Scale Orders](../trading/scale-orders.md) and [TWAP](../trading/twap.md).
- **Leverage** — adjustable per market up to that market's maximum, shown in the app.
- **Margin mode** — cross margin by default, with isolated margin available on supported markets. See [Margining](../trading/margining.md).
- **Reduce-only** — restrict an order so it can only decrease an existing position, never open or flip one.
- **TP/SL attach** — optionally attach take-profit and stop-loss triggers to the order before you place it.

{% hint style="success" %}
Before you confirm, **Order Details** shows the exact cost of your trade — including all fees — so there are never surprises. Your current fee tier is visible on the [Fees](fees.md) page and in the fee row of every order form.
{% endhint %}

{% hint style="warning" %}
Trading with leverage carries liquidation risk. The estimated liquidation price is shown before you place an order and on every open position — review it before confirming. See [Liquidation](../trading/liquidation.md).
{% endhint %}

## Bottom tabs

The panel below the chart keeps your full account context in view while you trade:

| Tab | What it shows |
| --- | --- |
| **Balances** | Your unified perps + spot balances and available margin |
| **Positions** | Open positions with entry price, mark price, unrealized PnL, ROE %, liquidation price and TP/SL controls |
| **Open Orders** | Resting orders, editable and cancellable individually or in bulk |
| **TWAP** | Active TWAP orders and their execution progress |
| **Trade History** | Your past fills with price, size and fees |
| **Funding History** | Funding payments paid or received on your perp positions |
| **Order History** | A complete log of placed, filled and cancelled orders |

For how entry price, PnL and ROE are calculated, see [Entry Price & PnL](../trading/entry-price-pnl.md).

## Watchlist & favorites

Star any market to pin it to the **favorites bar** at the top of the terminal. Your watchlist shows live prices and 24h change for each pinned market, so you can jump between your markets with one click.

## Next steps

- New to the terminal layout? Start with the [Trading Interface](../trading/interface.md) overview.
- Haven't enabled trading yet? Follow the [Enable Trading](../guides/enable-trading.md) guide — a one-time setup that makes all subsequent trading gasless and popup-free.
- Prefer something simpler? Switch to [Lite Mode](lite-mode.md) anytime from the top bar.
