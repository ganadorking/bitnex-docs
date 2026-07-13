# Liquidation

Liquidation is the forced closure of a leveraged position when its margin can no longer support it. On Bitnex, liquidations are executed entirely by the underlying on-chain exchange protocol — the same on-chain system that handles order matching and settlement. Bitnex never holds your funds and never triggers liquidations itself.

Understanding how liquidation works — and how to keep a healthy distance from it — is the single most important part of trading perpetual futures with leverage.

{% hint style="danger" %}
Leveraged trading is high risk. If your position is liquidated, you can lose the **entire margin** allocated to it. Never trade with funds you cannot afford to lose.
{% endhint %}

## What is liquidation?

When you open a leveraged position, you post **margin** (collateral) that backs the position. As the mark price moves against you, your unrealized losses eat into that margin.

Every position has a **maintenance margin** requirement — the minimum amount of margin that must remain to keep the position open. If your margin falls below this threshold, the underlying protocol liquidates the position: it is closed at the prevailing market conditions, and the margin backing it is used to cover the loss.

In short:

1. You open a position with margin behind it.
2. Price moves against you → unrealized PnL turns negative → available margin shrinks.
3. Margin drops below the maintenance requirement → the protocol liquidates the position.

## Maintenance margin

- **Initial margin** is what you post to open a position (determined by your position size and leverage).
- **Maintenance margin** is the smaller amount you must keep to hold the position open.

The buffer between the two is your safety zone. Higher leverage means a thinner buffer — the price has to move less against you before the maintenance threshold is breached.

Maintenance requirements are set by the underlying protocol per market. Markets with higher maximum leverage generally have tighter maintenance requirements. See [Margining](margining.md) for how cross and isolated margin apply these requirements differently.

## Your estimated liquidation price — always visible

Bitnex shows the **estimated liquidation price**:

- **Before you trade** — in the Order Details of every order form, alongside cost and fees, so you can see your risk before you commit.
- **On every open position** — in the positions table (Lite and Pro), updated as market conditions and your account state change.

{% hint style="info" %}
The liquidation price is an **estimate**. It shifts as your account changes — funding payments, other positions (in cross margin), added or removed margin, and partial fills all move it. Check it regularly rather than treating it as fixed.
{% endhint %}

## What affects your liquidation price

| Factor | Effect |
| --- | --- |
| **Leverage** | Higher leverage → liquidation price closer to your entry. Lower leverage → more room. |
| **Position size** | Larger positions consume more margin and are more sensitive to price moves. |
| **Margin mode** | In **cross margin**, your whole account balance backs the position — losses elsewhere pull your liquidation price closer. In **isolated margin**, only the margin assigned to that position is at risk. |
| **Unrealized PnL** | Losses on open positions reduce available margin; in cross mode, one losing position affects the others. |
| **Funding payments** | Periodic [funding](funding-rate.md) payments add to or subtract from your margin over time. |

## How to avoid liquidation

There is no way to make leverage safe — only ways to manage it:

- **Use lower leverage.** The most direct lever. Halving your leverage roughly doubles the distance to liquidation.
- **Size positions conservatively.** Risk a small fraction of your account per trade so a single loss never threatens the whole balance.
- **Add margin.** On isolated positions, you can add margin to push the liquidation price further away. In cross mode, keeping unused balance in the account serves the same purpose.
- **Set stop losses.** A [stop loss](tp-sl.md) closes your position at a level you choose, before liquidation is ever in play. Exiting at your stop is almost always better than being liquidated.
- **Watch the liquidation price.** It is displayed on every open position — if the mark price is approaching it, act early: reduce size, add margin, or close.

{% hint style="warning" %}
In fast-moving markets, price can gap through levels quickly. Do not rely on being able to react in time — set your protective orders in advance.
{% endhint %}

## What happens when a position is liquidated

- The underlying protocol closes the position; the margin backing it absorbs the loss.
- In **isolated margin**, losses are capped at the margin assigned to that position.
- In **cross margin**, the position draws on your shared account balance before liquidation occurs — so a liquidation event can consume more of your account.
- The liquidation is booked as realized PnL and appears in your trade history. See [Entry Price & PnL](entry-price-pnl.md) for how realized losses are recorded.

## Related pages

- [Margining](margining.md) — cross vs. isolated margin and leverage settings
- [Take Profit & Stop Loss](tp-sl.md) — protect positions before liquidation is a risk
- [Funding Rate](funding-rate.md) — periodic payments that affect your margin over time
- [Order Types](order-types.md) — stop market and stop limit orders for risk management
