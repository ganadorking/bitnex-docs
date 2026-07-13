# Getting Started

Welcome to Bitnex. This guide walks you through everything you need to place your first trade — from connecting a wallet to managing your positions. The whole setup takes just a few minutes.

Bitnex is a non-custodial trading interface for perpetual futures and spot, built on top of Hyperliquid. That means Hyperliquid provides the liquidity, matching engine, and on-chain custody, while Bitnex gives you a fast, clean interface to trade. There's no traditional sign-up and no KYC on Bitnex itself.

{% hint style="info" %}
**Your funds stay yours.** Bitnex never holds your money. Deposits live in Hyperliquid's on-chain system, under your own control — not with Bitnex.
{% endhint %}

## Before you begin

Bitnex is **not available to U.S. persons** or to anyone located in a restricted or sanctioned jurisdiction. Access is geo-restricted, and during setup you'll be asked to confirm — by signing a message — that you are not a U.S. person.

## 1. Connect

Head to [bitnex.pro](https://bitnex.pro) and choose how you want to connect:

- **With a crypto wallet** — MetaMask, Coinbase Wallet, or Rainbow.
- **With email or Google** — this creates an embedded wallet for you automatically (via Privy), so you can get started without installing a wallet extension.

Either option gives you a wallet that Bitnex uses to interact with Hyperliquid on your behalf.

## 2. Accept the Terms

The first time you connect, you'll be asked to accept the Bitnex Terms of Service. You do this by **signing a message with your wallet** — this signature is recorded for compliance purposes.

- No gas fee is charged for signing.
- Signing the Terms also confirms that you are not a U.S. person.

{% hint style="info" %}
The current Terms of Service version is **1.0.0**. Signing is a one-time step unless the Terms are updated.
{% endhint %}

## 3. Enable Trading

Next, click **Enable Trading**. This is a one-time setup that lets you trade smoothly, without a wallet popup on every single order.

When you enable trading, you approve a set of one-time signatures that create an **agent wallet** — a session key that can place orders on your behalf. These approvals are signed on the **Arbitrum** network.

Why this matters:

- **Sign once, trade freely.** After this step, you place orders without a wallet popup each time. Trading is gasless once you're set up.
- **The agent key can't touch your funds.** It can place and manage orders, but it **cannot withdraw** anything.
- **You stay in control.** You can revoke the agent session at any time.

{% hint style="success" %}
This is the step that makes Bitnex feel fast. Approve once, then trade freely with no interruptions.
{% endhint %}

## 4. Deposit USDC

To trade, you'll need USDC in your Hyperliquid account. From inside the app, you can **bridge USDC from Arbitrum to Hyperliquid** in a few clicks.

- Deposits move from Arbitrum into Hyperliquid's on-chain system.
- Your balance appears in Bitnex once the bridge completes.
- When you want to take funds out, **withdrawals go back to Arbitrum**.

{% hint style="warning" %}
Make sure you're bridging **USDC on Arbitrum**. Double-check the network before you send.
{% endhint %}

## 5. Place your first trade

With funds deposited, you're ready to trade. Here's the flow:

1. **Pick a market.** Choose a perpetual futures market or a spot market.
2. **Choose a side.** Select **Buy** (long) or **Sell** (short).
3. **Set your size.** Enter how much you want to trade.
4. **Set leverage (perps only).** For perpetual futures, choose your leverage. Spot trades don't use leverage.
5. **Review the Order Details.** Before you confirm, Bitnex shows you the full order breakdown — including fees.
6. **Place the order.** Confirm to send it to Hyperliquid.

{% hint style="info" %}
**On fees:** Bitnex charges a small fee on top of Hyperliquid's standard trading fees. The exact amount is always shown in the **Order Details** before you place a trade — so there are never any surprises.
{% endhint %}

## 6. Manage your positions

Once you're trading, everything you need to stay on top of your activity is built in:

- **Positions** — see your open positions, size, entry price, and live P&L.
- **Open Orders** — view and cancel orders that haven't filled yet.
- **History** — review your past trades and fills.
- **Close / TP-SL** — close a position at any time, or set a **Take Profit** and **Stop Loss** to manage risk automatically.

## Lite vs Pro

Bitnex offers two ways to view the market, and you can switch between them anytime:

- **Lite** — a simple, streamlined view for placing trades quickly.
- **Pro** — the full trading terminal, with candlestick and line charts, the order book, positions, open orders, and history all in one place.

Beyond trading, you'll also find **Portfolio**, **Vaults/Earn**, **Staking**, **Referrals**, and **Swap** inside the app.

{% hint style="info" %}
**Remember:** at every step, your funds remain non-custodial. Bitnex is the interface; Hyperliquid holds custody on-chain, and only you can withdraw.
{% endhint %}

## Next steps

- Still have questions? Head over to the [FAQ](faq.md).
