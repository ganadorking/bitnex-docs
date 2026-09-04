# Prediction Markets (Outcomes)

Outcome markets let you trade the probability of an event — "BTC above 100,000 on Oct 1?", a central-bank rate decision, a price range — as **Yes / No shares** that settle at **1 USDC** if the outcome happens and **0** if it doesn't. On Dasus they live under **Trade → Outcomes** and always open in the Pro terminal.

{% hint style="warning" %}
**HIP-4 markets are deployed by third parties.** Outcome markets are created independently and permissionlessly on Hyperliquid (HIP-4). Dasus surfaces them from on-chain activity and does **not** review, verify or approve them. The first time you open one on a device, you'll be asked to read and confirm a deployer disclaimer before trading.
{% endhint %}

## How they work

* **Shares, not leverage.** A share's price moves between 0 and 1 USDC and reads as the market's implied probability. Buying *Yes* at 0.30 costs 0.30 USDC per share and pays 1 USDC per share if the market resolves *Yes* (0 if it resolves *No*). Selling works the other way around.
* **No leverage, no funding, no liquidation.** These are spot markets: the terminal hides leverage, margin, TP/SL and funding controls when you open one.
* **Multi-outcome questions** (for example a rate decision with several options) list one row per option; each option is its own Yes/No pair.
* **Resolution.** Every market has an expiry and a resolution source (an oracle or a documented criterion, shown under **Details**). Once resolved, the market leaves the live list; your shares settle and the position stays visible in **Portfolio → Outcomes** and in your fills history.

## Risks to understand before trading

Because these markets are permissionless, they may carry **elevated risk**: low liquidity, high volatility, incomplete documentation, imperfect settlement or resolution criteria, and outcome determination by a resolution source or oracle that may be delayed, disputed or incorrect. Read the market's **Details**, the deployer's documentation (where available) and the [Risk Disclosure](../legal/risk-disclosure.md) before proceeding.

## Fees on outcome markets

Outcome markets are charged differently from the rest of the platform:

- **Opening a position is free** — the protocol fee is charged only when you **close** or get liquidated.
- The fee scale is set by each market's deployer, and averages roughly **half** a regular market's rate.
- The Dasus platform fee applies per order as usual, and the order form shows the exact cost before you confirm.

See [Fees](../platform/fees.md) for the full picture.

## Where your positions show up

Open outcome positions appear in the **Outcomes** tab of the terminal's bottom panel and under **Portfolio → Outcomes**, with their fills in your trade history like any other market.

## Market links

Every market has a readable URL, for example:

```
https://dasus.xyz/trade/btc-touches-65000-by-oct-1-at-1200-am-utc-yes
```

The date and time in the URL are in **UTC** (the title on screen shows the same moment in your local time zone). Links in the Hyperliquid format (`/trade/out:…`) open the same market, and older Dasus links that used local time keep working.
