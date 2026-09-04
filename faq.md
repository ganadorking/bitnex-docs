# Frequently Asked Questions

Quick answers to the most common questions about Dasus. If you can't find what you're looking for here, check the rest of the docs or reach out through our [official channels](others/official-links.md).

## General

### What is Dasus?

Dasus is a non-custodial trading platform for perpetual futures and spot markets. It is a front-end interface built on top of a high-performance decentralized on-chain exchange protocol, which provides the liquidity, order matching (a full on-chain central limit order book), custody, and settlement. Dasus gives you a fast, polished interface to trade on that infrastructure — in [Lite](platform/lite-mode.md) or [Pro](platform/web-terminal.md) mode.

### Is Dasus custodial? Who holds my funds?

No. Dasus never holds your funds. Your assets are held by the underlying protocol's on-chain system and remain under your control at all times. Dasus is an interface: it helps you view markets, build orders, and sign transactions — it cannot access or move your money.

### Do I need to sign up or complete KYC?

No traditional sign-up and no KYC on Dasus. You connect a wallet (or create an embedded self-custodial wallet with your email or Google account) and start trading. See [Getting Started](getting-started.md).

### Is Dasus available in my country?

{% hint style="warning" %}
Dasus is **not available to U.S. persons** or to residents of restricted or sanctioned jurisdictions. On first connect you sign a message accepting the [Terms of Service](terms.md) and confirming you are not a U.S. person.
{% endhint %}

## Getting started

### How do I connect?

Two ways:

- **Crypto wallet** — MetaMask, Coinbase Wallet, or Rainbow.
- **Email or Google** — creates an embedded self-custodial wallet via Privy, so you can trade without installing a wallet extension.

Either way, the wallet is yours and self-custodial. Full walkthrough in [Getting Started](getting-started.md).

### What is "Enable Trading"?

A one-time setup step. You sign a small set of approvals on the Arbitrum network that create an **agent wallet** (a session key). From then on, the agent wallet signs your orders automatically — no wallet popup for every trade, and no gas per trade.

{% hint style="info" %}
The agent key **cannot withdraw funds**. It can only sign trading actions, and you can revoke it at any time from the app. See [Enable Trading](guides/enable-trading.md).
{% endhint %}

### How do I deposit and withdraw?

Deposits are made by bridging **USDC from Arbitrum** into your trading account, directly from inside the app. Withdrawals go back to Arbitrum as USDC. Your balance is unified across perps and spot. Details in [Funding Your Account](platform/funding-account.md).

### Does trading cost gas?

Once you've enabled trading, order placement is **gasless** — orders are signed by your agent wallet and executed by the underlying protocol without per-trade gas fees. You only interact with Arbitrum for deposits, withdrawals, and the initial approvals.

## Trading

### What markets can I trade?

Hundreds of them, in four families:

- **Crypto perpetuals** — BTC, ETH, SOL and hundreds more, with leverage.
- **Spot** — buy and hold the token itself. See [Spot Trading](trading/spot.md).
- **Stocks, indices, commodities and FX** — TSLA, NVDA, SP500, GOLD, EURUSD and many others, traded as perpetual futures margined in USDC (you don't own the underlying share or metal).
- **Prediction markets** — Yes/No outcome shares. See [Outcomes](trading/outcomes.md).

Each market shows mark price, oracle price, 24h change and volume, open interest and funding rate. Browse everything on the [Markets](platform/markets.md) page, or see the day at a glance on the Heatmap.

### What order types are supported?

| Order type | Lite | Pro |
| --- | :---: | :---: |
| Market | ✅ | ✅ |
| Limit (GTC / IOC / post-only) | ✅ | ✅ |
| Stop Market / Stop Limit | — | ✅ |
| Take Market / Take Limit | — | ✅ |
| TP/SL (attached to orders and positions) | ✅ | ✅ |
| [Scale orders](trading/scale-orders.md) | — | ✅ |
| [TWAP](trading/twap.md) | — | ✅ |
| Chase (auto-repricing post-only) | — | ✅ |

See [Order Types](trading/order-types.md) for how each one works.

### What is cross vs isolated margin?

- **Cross margin** (the default, and the only mode in Lite): all positions share your account's available balance as collateral. Efficient, but a losing position draws on the whole account.
- **Isolated margin** (Pro, on supported markets): a position gets its own dedicated margin. Losses on that position are capped at the margin you assigned to it.

Leverage is adjustable per market up to that market's maximum, which is shown in the app. More in [Margining](trading/margining.md).

### What is the funding rate?

A periodic payment between longs and shorts that keeps the perp price anchored to the underlying index/oracle price. When the rate is **positive, longs pay shorts**; when **negative, shorts pay longs**. Funding is paid peer-to-peer between traders — Dasus does not receive any of it. The current rate is shown per market in the app. See [Funding Rate](trading/funding-rate.md).

### How does liquidation work?

If your account or position margin falls below the maintenance requirement, the position is liquidated by the underlying protocol. Your estimated liquidation price is shown **before** you place an order and on every open position.

{% hint style="danger" %}
Leverage amplifies both gains and losses. A leveraged position can be liquidated and lose its entire margin. Manage risk with sensible position sizing and stop losses. See [Liquidation](trading/liquidation.md).
{% endhint %}

### How is my PnL calculated?

Your **entry price** is the average price of your fills. **Unrealized PnL** moves with the mark price while the position is open; **realized PnL** is booked when you close. **ROE %** expresses PnL relative to the margin used. Full breakdown in [Entry Price & PnL](trading/entry-price-pnl.md).

### Can I set take profit and stop loss?

Yes. TP/SL can be attached to a new order or set on an existing position (for full or partial size), defined by price or by gain/loss percentage, and edited or cancelled at any time. On Pro you can also drag the TP/SL lines directly on the chart. See [TP/SL](trading/tp-sl.md).

### What are grid bots?

Automated grid trading strategies you configure and run from the app: set a price range, the number of grid levels, and your investment, and the bot places orders across the range. Grid trading involves risk — with leverage, if price moves outside your range the position can be liquidated. See [Grid Bots](trading/grid-bots.md).

## Fees

### What are the fees?

Dasus adds a small platform fee on top of the underlying protocol's base trading fees. Rates follow a **maker/taker** model with **volume-based tiers**. The full fee schedule and your current tier are shown in the app on the [Fees](platform/fees.md) page, and the exact cost of every trade is displayed in Order Details **before** you confirm.

### Can I reduce my fees?

Four ways, and they stack:

- **Trade more.** Both the base protocol fee (14-day volume) and the Dasus platform fee (30-day volume) step down with volume.
- **Be a maker.** Post Only orders pay 40% of the taker platform fee, and a lower base rate too.
- **[Stake HYPE](earn/staking.md).** Staking tiers cut the base fee by 5% to 40%.
- **Referral discount.** The protocol applies a referral discount to accounts registered under a referrer; the Fees page shows whether it is active for you.

**TWAP orders pay no platform fee at all.** Full detail on the [Fees](platform/fees.md) page.

## Earn

### What are Vaults?

On-chain vaults that follow trading strategies run by vault leaders — a copy-trading style product. You deposit, the leader trades, and depositors share the PnL. Performance and history are shown per vault. Vaults carry risk of loss, and withdrawals follow each vault's rules. See [Vaults](earn/vaults.md).

### Can I lend out idle assets?

Yes. The **Earn** page lists the protocol's native lending markets: supply an asset and earn interest paid by borrowers, withdraw when the pool has liquidity. Rates are variable and set by utilization. See [Lend & Borrow](earn/lend-borrow.md).

### What is Staking?

You can stake the protocol's native token to validators directly from the app. Rewards accrue automatically, and staking may reduce your trading fees through fee-discount tiers. See [Staking](earn/staking.md).

## Platform & access

### What languages does Dasus support?

The app is available in **English, Spanish, French, Korean and Chinese**. Switch from the settings menu; these docs are in English.

### Can I use Dasus on my phone?

Yes — the Dasus web app is fully responsive and works in your mobile browser, in both Lite and Pro modes. There is no native mobile app at this time.

### Is there an API or mobile app?

There is **no public API** for now, and no native mobile app — Dasus is web only. Everything runs in the browser on desktop and mobile.

### What's the difference between Lite and Pro?

- **Lite** — a simple, Robinhood-style experience: big price chart, Buy/Sell, amount, leverage, TP/SL, and tabs for positions, orders, and history. See [Lite Mode](platform/lite-mode.md).
- **Pro** — a full trading terminal: TradingView-style candlestick chart, live order book with depth, recent trades feed, advanced order types, and tabs for Balances, Positions, Open Orders, TWAP, Trade History, Funding History, and Order History. See [Web Terminal](platform/web-terminal.md).

You can switch between the two at any time — same account, same balances.

### Where can I see my overall account?

The [Portfolio](platform/portfolio.md) page shows total equity, the equity curve with PnL, volume and max drawdown for the period you pick, balances by account (perps, spot, vaults, outcomes, Earn, staking), your positions/orders/history, and a full deposits & withdrawals ledger. For the day-by-day view and your track record statistics, open the [PnL Calendar](platform/calendar.md).

### Can I research other traders?

Yes, all from public on-chain data: the [Leaderboard](platform/leaderboard.md) ranks the top accounts, [Track](platform/explorer.md#track-any-wallet) turns any address into a readable profile, and the [Explorer](platform/explorer.md) looks up addresses, transactions, blocks and tokens. If a trader is available as a leader, you can follow them with [Copy Trading](platform/copy-trading.md).

### How do referrals work?

Create a code instantly — no volume requirement — and share your link. You earn **20% to 60%** of the platform fee generated by the traders who join through you — the rate rises with their combined 30-day volume and never goes back down. Your invitees pay the same fee schedule as everyone else; your share comes out of the Dasus platform fee, not out of their pocket. Rewards are claimable in USDC from the app, and affiliates can pass part of their commission down to their own network, up to 3 levels. See [Referrals](platform/referrals.md).

### How do I know I'm on the real Dasus?

Always double-check the URL — **dasus.xyz** — and only trust links listed on our [Official Links](others/official-links.md) page. Dasus will never DM you first or ask for your seed phrase or private keys.
