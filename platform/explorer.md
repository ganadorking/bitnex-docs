# Explorer & Track

Two research tools built on public on-chain data: the **Explorer** looks up anything on Hyperliquid, and **Track** turns any wallet address into a readable trading profile. Both are read-only, work without connecting a wallet, and show data anyone can verify on-chain.

## Explorer

Paste an **address**, a **transaction hash**, a **block height** or a **token** into the search box and the Explorer resolves it:

| You look up | You get |
| --- | --- |
| **Address** | The account's activity on the L1 — actions, transfers and fills |
| **Transaction** | The action that was signed, its result, and the block it landed in |
| **Block** | Height, timestamp and the transactions it contains |
| **Token** | Price, market cap, circulating / total / max supply, deployer, deploy time, contract, and the genesis distribution (initial allocation, top 20 — not current holders) |

There's a shortcut to open your own wallet, and token pages are linked directly from the **Token details** panel on the [Markets](markets.md) page.

## Track any wallet

**Track** answers "what is this account actually doing?" for any address — yours or someone else's:

- **Account value**, split between perps and spot.
- **Unrealized PnL** and the number of open positions.
- **30-day volume** and 30-day activity: realized PnL, number of trades, win rate.
- **Long / short exposure** breakdown.
- **Open positions**, **open orders** and **recent fills**.

From a tracked wallet you can jump straight to **Copytrade** if that trader is available as a leader on Dasus.

{% hint style="info" %}
Everything here is public on-chain state. Tracking a wallet is not a connection to it: it gives you no permission over that account, and it gives that account nothing about you.
{% endhint %}

{% hint style="warning" %}
**Read a wallet's history the way you'd read a track record.** A single visible number — a big position, a good month — says very little on its own. Check the length of the record, the drawdowns, and the leverage before drawing conclusions, and never mirror a position you don't understand. See [Risk Disclosure](../legal/risk-disclosure.md).
{% endhint %}

## Related pages

- [Leaderboard](leaderboard.md) — the top accounts by PnL, ROI, equity and volume
- [Copy Trading](copy-trading.md) — follow a trader automatically, with your own limits
- [Markets](markets.md) — token details and live market data
