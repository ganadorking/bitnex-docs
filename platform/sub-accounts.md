# Sub-Accounts

Sub-accounts let you split your capital into isolated compartments under one master account — one per strategy, each with its own positions, margin and liquidations. They live on Hyperliquid under your master account: same non-custodial custody, and they show up identically on any Hyperliquid frontend.

## What you can do on Dasus

* **Create** a sub-account (just a name — your agent signs, no popup).
* **Rename** it at any time (pencil icon next to the name).
* **Transfer** perps USDC between master and sub, both directions.
* **Trade as** any sub-account: hit **Trade** on its row (or pick it from the wallet menu in the navbar). Orders, positions, balances, TP/SL and cancels all belong to that account until you switch back. The navbar shows `Sub: name` while a sub is active.

## Things to know

* **Isolated capital.** A sub-account's positions and liquidations never touch the master or the other subs.
* **Fees are family-wide.** Hyperliquid adds up master + subs volume for its VIP fee tiers — splitting capital never costs you a tier.

{% hint style="warning" %}
**Careful when copying a sub-account address.** These addresses are generated on the Hyperliquid L1. **Do not send funds directly to them — the funds will be lost.** Always use the **Transfer** button to move USDC between master and sub.
{% endhint %}

## Related pages

- [Portfolio](portfolio.md) — your main account's equity and tables (the page tells you when you're trading as a sub-account)
- [Fees](fees.md) — how volume tiers are counted across the account family
- [Funding Your Account](funding-account.md) — deposits, withdrawals and account types
