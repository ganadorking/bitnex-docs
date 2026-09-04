# Lend & Borrow

The **Earn** page lists Hyperliquid's native lending markets. Supply a token you already hold and it earns interest paid by the traders who borrow it — no lock-up, no strategy risk, no leader trading your money. It is the most conservative of the three Earn options.

## How it works

Every market is a pool. Lenders supply an asset; borrowers take it out against collateral they've posted. The rate is set by **utilization** — how much of the pool is currently borrowed:

| Column | What it means |
| --- | --- |
| **Supply APY** | What you earn right now for supplying that asset. It moves with utilization. |
| **Borrow APY** | What borrowers pay. Always higher than the supply rate. |
| **Utilization** | Share of the pool currently lent out. Higher utilization means higher rates — and less idle liquidity to withdraw from. |
| **Total supplied** | Size of the pool. |
| **Your deposit / Your borrow** | Your own position in that market. |

Stablecoin markets (USDC and other dollar tokens) are where most of the supply yield is. Some assets are marked **Collateral** with an LTV percentage: the protocol accepts them as collateral for borrowing but does not pay yield on them, so there is no Deposit button on those rows.

## Supplying

1. Open **Earn** from the navigation.
2. Pick a market and click **Deposit**.
3. Enter an amount — **Max** fills in your available spot balance of that token.
4. Confirm. Your agent wallet signs it: no wallet popup, no gas.

Interest accrues continuously and is reflected in your deposit's value. **Withdraw** takes it back to your spot balance, subject to the pool having free liquidity.

{% hint style="info" %}
You need [trading enabled](../guides/enable-trading.md) to supply or withdraw — the same agent wallet that signs your orders signs these actions.
{% endhint %}

## Health factor

If you borrow, the **health factor** is the number to watch: your account value weighted by each asset's LTV, divided by what you have borrowed. Below 100% you cannot borrow more, and as it approaches the liquidation threshold your collateral can be liquidated to repay the debt.

{% hint style="warning" %}
Borrowing to increase trading size stacks two risks on the same capital: the borrow position and the trade. A move against you can liquidate both. See [Liquidation](../trading/liquidation.md) and [Risk Disclosure](../legal/risk-disclosure.md).
{% endhint %}

## Risks

Lending is lower risk than [vaults](vaults.md), not risk-free:

- **Utilization risk.** If the pool is fully borrowed, withdrawals wait until borrowers repay or new supply arrives.
- **Rates are variable.** Today's APY is not a promise; it moves with demand every block.
- **Smart-contract and protocol risk.** These are Hyperliquid's markets, operating on-chain. Dasus is the interface, not the counterparty, and cannot reverse an on-chain outcome.
- **Collateral risk.** Borrowers' collateral is liquidated automatically if it falls short. In extreme market moves, bad debt is possible in any lending market.

## The three ways to earn

| | [Lend](lend-borrow.md) | [Vaults](vaults.md) | [Staking](staking.md) |
| --- | --- | --- | --- |
| **You earn from** | Interest paid by borrowers | A trader's strategy PnL | Validator rewards |
| **Can you lose principal?** | Only in extreme protocol events | Yes — the strategy can lose | Slashing / market risk on the token |
| **Access to funds** | Withdraw when the pool has liquidity | Per-vault lock-up rules | Unstaking queue |
| **Returns** | Variable rate | Not fixed, can be negative | Variable rate |

## Related pages

- [Vaults](vaults.md) — deposit into a trader's strategy
- [Staking](staking.md) — delegate HYPE to validators
- [Portfolio](../platform/portfolio.md) — see your Earn balance alongside everything else
