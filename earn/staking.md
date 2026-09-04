# Staking

Stake the underlying protocol's native token to network validators directly from Dasus — no separate wallet setup, no external staking dashboard. Staking supports the security of the underlying on-chain exchange protocol, earns you rewards that accrue automatically, and can reduce your trading fees through fee-discount tiers.

![Staking](../.gitbook/assets/staking.png)

{% hint style="info" %}
Staking is fully on-chain and non-custodial. Your staked tokens are delegated to validators through the underlying protocol — Dasus never holds them.
{% endhint %}

## How staking works

When you stake, you delegate the protocol's native token to a validator of your choice. Validators help secure the underlying protocol's network, and stakers share in the rewards generated for doing so.

- **Delegate from the app** — pick a validator, enter an amount, and confirm. The full flow happens inside Dasus.
- **Rewards accrue automatically** — no claiming schedule to manage; your rewards compound into your staked balance over time.
- **Stay in control** — you can add to your stake, switch validators, or begin unstaking whenever you choose, subject to the protocol's timing rules (see below).

## Why stake

| Benefit | What it means |
| --- | --- |
| **Staking rewards** | Earn rewards on your staked tokens, accrued automatically by the protocol. |
| **Trading fee discounts** | Staking qualifies you for fee-discount tiers from 5% to 40% off the base trading fee — Wood, Bronze, Silver, Gold, Platinum, Diamond. Your current tier is shown in the app — see [Fees](../platform/fees.md). |
| **Network participation** | Your stake contributes to the security and decentralization of the underlying protocol. |

## Getting started

1. **Connect** your wallet or sign in — see [Getting Started](../getting-started.md) if you're new.
2. **Acquire the protocol's native token** — you can obtain it on Dasus's spot markets or via [Swap](../platform/swap.md).
3. **Open Staking** under the Earn section of the app.
4. **Choose a validator** and review its details.
5. **Enter the amount** to stake and confirm.

Your staked balance, accrued rewards, and validator delegation are all visible in the Staking view and reflected in your [Portfolio](../platform/portfolio.md).

## Unstaking

Unstaking is initiated from the same Staking view, and it involves **two separate timers** set by the protocol:

| Step | Timing |
| --- | --- |
| **Undelegate** from a validator | A delegation is locked for 1 day; after that, undelegating is immediate |
| **Move HYPE back to your spot balance** | A **7-day queue**, always — this is the one that matters for liquidity |

The app shows the countdown for any pending withdrawal.

{% hint style="warning" %}
**Staked tokens are not liquid.** Getting HYPE back into your tradable balance takes 7 days, no matter how urgently you need it. Never stake capital you may want to trade or withdraw at short notice.
{% endhint %}

## Things to keep in mind

- **Rewards vary.** The staking reward rate is set by the protocol and falls as more tokens are staked network-wide; it is not fixed or guaranteed by Dasus. Rewards accrue continuously and are auto-compounded into your delegation.
- **Validator choice matters.** Review a validator's details before delegating.
- **Token price risk.** Staking rewards are paid in the protocol's native token, whose market price can go up or down. Staking does not protect you from price movements.
- **Fee tiers are dynamic.** Your fee-discount tier updates based on your staked amount — check the [Fees](../platform/fees.md) page in the app for your current rate.

## Related pages

- [Vaults](vaults.md) — earn by depositing into strategy vaults
- [Lend & Borrow](lend-borrow.md) — supply assets to the lending markets and earn interest
- [Fees](../platform/fees.md) — fee schedule, tiers, and discounts
- [Portfolio](../platform/portfolio.md) — track balances across trading, vaults, and staking
