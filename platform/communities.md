# Communities

## What is Communities?

Communities is a **social layer on top of the exchange**: creators share their own real trading activity, and everything you see — positions, PnL, charts, stats — comes **live from Hyperliquid's public data**.

**Nothing is executed for you.** If you want to trade an idea, it only pre-fills your own terminal: you choose your capital, review every parameter and **sign your own order**. Creators never touch your funds.

{% hint style="warning" %}
This is **not copy trading** and it is **not financial advice**. Past performance does not guarantee future results.
{% endhint %}

## How it works

### Joining a community

Every community sets its own access policy. What you see on its card or profile tells you how to get in:

| Access policy | How you join |
| --- | --- |
| **Open** | Press **Join** — you're in immediately, and the trade feed is public. |
| **Invite code** | The community is private (not listed in Explore). Ask the creator for their `XXXX-XXXX` code and enter it in **Have a code?** or on the community page. |
| **My referrals only** | Only wallets referred by the creator can join. If you don't have a referrer yet, the creator's referral code is applied to you automatically when you join. If you already signed up under a different referrer, you can't join this community. |
| **Approval** | Press **Join** to send a request. The creator approves or rejects it; you'll get a notification when you're accepted. |

Each community also has a **member limit** set by its creator. When the community is full, no one else can join until a spot frees up. A wallet can be a member of up to 100 communities.

### Trading an idea

1. Members see the creator's trades **live**: market, side, leverage, entry, current PnL and Stop Loss / Take Profit levels — all sourced from Hyperliquid's public data.
2. **Trade this idea** opens a summary of the parameters. Continuing takes you to **your own terminal**, pre-filled with the idea's side, leverage and SL/TP.
3. There you choose **your own size**, can change any parameter, review the fees, and **sign the order with your own wallet** — exactly like any other trade on Bitnex. If you do nothing, nothing happens.

### Creating a community

1. Open **Communities** and press **Create** (you'll be asked to sign the [Community Terms](../legal/community-terms.md) as an operator — a free, off-chain signature).
2. Choose a name, photo and short description, pick an **access policy** (table above), and set your **member limit** (default 500, up to 100,000).
3. **One community per wallet.** You can delete it at any time and create a new one.
4. **Auto-share is always on**: everything you trade in the Bitnex terminal is posted to your community automatically — opens, adjustments (adds, moved SL/TP) and closes, with the final result. Your stats (ROI, PnL, win rate, drawdown) are computed from your real Hyperliquid history — nothing is self-reported.
5. Your wallet address is **hidden by default**; you can make it public from your community settings.

## What Communities is NOT

* ❌ It is **not copy trading**. No order is ever placed on your account automatically.
* ❌ It is **not financial advice**. Trades shared by creators are information about their own activity.
* ❌ Creators cannot charge for access on Bitnex, promise returns, or manage anyone's funds.

## Signed terms

The first time you act in Communities you'll be asked to accept the [Community Terms](../legal/community-terms.md) by **signing a message with your wallet**:

* **Members** sign once before using a trade as a template.
* **Creators** sign once before creating a community.

The signature is a free, off-chain `personal_sign` message (no gas, no transaction, it cannot move funds). Bitnex stores the signed acceptance as proof.

## Notifications

The bell icon in the navbar shows new trades, adjustments and closed trades from the communities you're a member of, plus join requests (for creators) and approvals. Notifications are in-app; push and Telegram alerts are planned.

## Fees

Orders placed from a community idea pay exactly the same fees as any other Bitnex order (Hyperliquid's base fee plus the platform fee, always visible before you sign). Creators earn through the standard [Referral Program](referrals.md) when their members join with their referral code.
