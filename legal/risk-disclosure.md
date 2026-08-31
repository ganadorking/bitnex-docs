# Risk Disclosure Statement

**Last updated:** August 31, 2026

This Risk Disclosure Statement describes the principal risks of using the Dasus interface ("Dasus") to trade on the underlying decentralized exchange protocol (the "Protocol"). It is part of, and should be read together with, the [Terms of Service](../terms.md). It does not describe every possible risk — markets can produce losses in ways nobody anticipated.

{% hint style="danger" %}
**Trading crypto assets — and especially trading them with leverage — can result in the loss of ALL the funds you deposit.** Only trade with money you can afford to lose completely.
{% endhint %}

## 1. Market risk

- Crypto asset prices are extremely volatile. Prices can move sharply, gap through levels, and remain irrational for longer than your margin lasts.
- Liquidity can evaporate: order books can thin out in seconds, spreads can widen dramatically, and market orders can fill far from the last printed price (slippage).
- Events outside crypto — macroeconomic news, regulation, exchange failures — can move prices at any hour. Perpetual markets never close.

## 2. Leverage and liquidation risk

- Leverage multiplies both gains and **losses**. At 10× leverage, a 10% adverse move can eliminate your margin; at higher leverage, even routine volatility can.
- If your margin falls below the Protocol's maintenance requirements, your position is **liquidated automatically**. Liquidation is executed by the Protocol, not by Dasus, and cannot be reversed.
- Liquidation can occur at a worse price than the reference liquidation price shown in the interface, and in extreme conditions your account can lose more than the margin assigned to a single position (cross-margin).

## 3. Funding and fee risk

- Perpetual contracts charge **funding** between longs and shorts on a recurring schedule. Holding a position over time can cost materially more than the entry and exit fees.
- Trading fees (the Protocol's and Dasus's builder fee) reduce your returns and are shown before you confirm each order.

## 4. Derivative pricing risk

- Perpetual contract prices can deviate from spot ("basis"). Mark price — used for margining and liquidation — can differ from the last traded price.
- Stop and take-profit triggers reference oracle/mark prices and execute as market orders once triggered: the fill price is **not guaranteed**.

## 5. Third-party market listings (HIP-3 and similar)

Some markets available through the interface are deployed **permissionlessly by third parties** on the Protocol's infrastructure. Dasus does not create, review, or approve these markets. They may involve elevated risk: low liquidity, unusual contract specifications, higher fee multipliers, sudden delisting, and incomplete documentation. Assess each market before trading it.

## 6. Copy trading risk

Copy trading places **real orders in your account**. In addition to all the market risks above:

- You can lose part or **all** of the capital you allocate to a copy.
- Copies execute **after** the trader's own orders, at possibly worse prices (latency and deviation risk).
- A trader's past performance — including every statistic shown on Dasus — guarantees nothing about future results.
- Stopping a copy **does not close** positions that are already open; managing them becomes your responsibility.

See the [Copy Trading Terms](copy-trading-terms.md) for the full terms.

## 7. Automated features risk

Features that act on your account automatically — copy trading, grid bots, TWAP execution, scale orders, take-profit/stop-loss — run on a **best-effort** basis. They can be delayed, interrupted, or fail because of network congestion, rate limits, API failures, server incidents, or bugs. An automation that fails to act (or acts late) can result in losses that manual trading would have avoided — and vice versa.

## 8. Guardian Mode is not a guarantee

Guardian Mode blocks new orders **signed through the Dasus interface** when your self-imposed limits are exceeded. It is a discipline tool, not a protective guarantee:

- It is **best-effort software** and can fail, lag, or miscompute.
- It cannot block orders you place through other interfaces, bots, or APIs against the same account.
- It never blocks closing positions — but closing at a loss is still a loss.

See the [Guardian Mode Terms](guardian-terms.md).

## 9. Vaults, staking and yield risk

- Depositing into vaults means the vault operator's strategy trades with your funds; you can lose deposited capital. Lock-up periods can prevent you from withdrawing during drawdowns.
- Staking involves protocol-level rules (unbonding periods, slashing where applicable) and price risk on the staked asset.
- Advertised yields are variable, not guaranteed, and can turn negative in real terms.

## 10. Technology and infrastructure risk

- **Smart contract / protocol risk:** the Protocol's on-chain system could contain bugs or be attacked. Funds live there, not on Dasus.
- **Bridge risk:** moving funds between chains (for deposits and withdrawals) relies on bridge infrastructure that has historically been a target of exploits.
- **Interface risk:** Dasus itself can suffer outages, bugs, or display errors. Data shown (prices, PnL, statistics) can be delayed or wrong; the Protocol's on-chain state is authoritative.
- **Wallet risk:** whoever controls your keys controls your funds. Phishing, malware, or losing your seed phrase can cost you everything, and nobody can reverse it.

## 11. Regulatory and jurisdictional risk

The legal treatment of crypto assets and derivatives varies by jurisdiction and changes quickly. Access to the interface, to specific features, or to the Protocol itself could become restricted or unlawful in your jurisdiction. You are solely responsible for complying with the laws that apply to you, including tax obligations.

## 12. No advice, no fiduciary duty

Nothing on Dasus — statistics, leaderboards, trader profiles, documentation, support answers — is investment advice or a recommendation. Dasus owes you no fiduciary duty. Every trading decision, including the decision to copy another trader, is exclusively yours.

---

If any part of this statement is unclear, do not trade until you understand it. You can reach us through the in-app support chat at [dasus.xyz](https://dasus.xyz).
