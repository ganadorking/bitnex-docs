# Enable Trading (Agent Wallet)

Before you place your first order on Bitnex, you'll complete a one-time setup step called **Enable Trading**. This creates an **agent wallet** — a dedicated session key that signs your orders automatically in the background, so you can trade without approving a wallet popup for every single action.

This page explains what the agent wallet is, exactly what it can and cannot do, and how to manage or revoke it.

## What is an agent wallet?

Trading on the underlying on-chain exchange protocol is fully non-custodial: every order, cancellation, and modification must be cryptographically signed. Signing each of those actions manually with your main wallet would mean a confirmation popup on every click — unusable for active trading.

The agent wallet solves this. When you click **Enable Trading**:

1. Bitnex generates a fresh keypair **locally in your browser**. The private key never leaves your device and is never sent to Bitnex servers.
2. You sign a **one-time approval** with your main wallet, registering the agent key with the underlying protocol as an authorized signer for your account.
3. From then on, the agent key signs your trading actions instantly and silently — no popups, no gas.

Think of it as a session key with a strictly limited job description: it can trade on your behalf, and nothing else.

{% hint style="success" %}
**Your funds stay safe.** The agent wallet has no ability to withdraw or transfer your funds — that permission is architecturally impossible for it to have on the underlying protocol. Even if the agent key were somehow exposed, an attacker could not move your assets out of your account. Withdrawals always require a signature from your main wallet. You can also revoke the agent at any time.
{% endhint %}

## The one-time approvals

Enabling trading involves signing a small number of approvals with your **main wallet** (or your embedded wallet, if you signed in with email or Google):

| Approval | What it does |
| --- | --- |
| **Agent approval** | Registers the agent wallet as an authorized session signer for your account on the underlying protocol. |
| **Platform fee approval** | Sets the maximum platform fee Bitnex may attach to your orders. Your actual costs are always shown in Order Details before you trade — see [Fees](../platform/fees.md). |

A few things to know:

- These approvals are **signed on the Arbitrum network**. If your wallet is on a different network, the app switches it to Arbitrum automatically — just accept the network-switch prompt if your wallet asks.
- They are **signatures, not transactions you fund** — enabling trading does not require you to pay gas out of pocket, and once set up, trading itself is gasless.
- You only do this **once per wallet** (or again after revoking or if the session expires).

## What the agent wallet CAN and CANNOT do

| ✅ Can | ❌ Cannot |
| --- | --- |
| Place orders (market, limit, stop, TP/SL, scale, TWAP) | Withdraw funds |
| Cancel and modify orders | Transfer assets to another address |
| Adjust leverage and margin mode | Approve other agents or change permissions |
| Manage positions (close, set TP/SL) | Access your main wallet's private key |

The separation is enforced by the underlying protocol itself, not by Bitnex — agent keys are simply not granted withdrawal or transfer rights at the protocol level.

## Revoking or rotating the session

You stay in control of the agent wallet at all times:

- **Revoke** — from the app's settings, you can revoke the current agent at any moment. The key is immediately deauthorized on-chain and can no longer sign anything for your account. Your funds and open positions are unaffected.
- **Rotate** — you can also generate a brand-new agent key and approve it, replacing the old one. Useful if you've cleared your browser data, switched devices, or simply want a fresh session.
- **Expiry** — agent approvals have a validity period on the underlying protocol. When a session expires, the app will prompt you to re-enable trading with a single signature.

{% hint style="info" %}
The agent key is stored in your browser on your device. If you switch browsers or devices, or clear your browser storage, you'll be asked to enable trading again — this is expected and takes just one signature.
{% endhint %}

## Troubleshooting

### "Signature verification failed" or the signing prompt errors out

- Check that your wallet is connected to the **Arbitrum network**. The app switches networks automatically, but some wallets require you to confirm the switch first.
- Reject any stale pending requests in your wallet, refresh the page, and retry **Enable Trading**.
- If you use multiple wallet extensions, make sure the correct one is active and connected.

### "Session expired" or orders suddenly ask for approval again

Your agent approval has reached the end of its validity period. Click **Enable Trading** again and sign once — your balances, positions, and orders are untouched.

### Enable Trading is unavailable or fails on an empty account

The underlying protocol requires a funded account before an agent can be activated. If your account is empty, the app automatically shows the deposit step — complete it (see [Funding Your Account](../platform/funding-account.md)) and the setup finishes on its own.

### I revoked my agent by mistake

No harm done. Click **Enable Trading**, sign the approval again, and you're back in business.

## Next steps

- New to Bitnex? Start with the full [Getting Started](../getting-started.md) walkthrough.
- Ready to trade? Explore the available [Order Types](../trading/order-types.md).
- Questions about costs? Review [Fees](../platform/fees.md) or check the [FAQ](../faq.md).
