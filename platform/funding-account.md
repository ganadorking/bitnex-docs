# Funding Your Account

Bitnex is non-custodial: your funds are held by the underlying on-chain exchange protocol, never by Bitnex. Funding your account means moving USDC from the Arbitrum network into your trading account — all from inside the app, in a few clicks. Once funded, your balance is unified across perps and spot, and trading is gasless.

{% hint style="info" %}
You can deposit before or after [Enable Trading](../guides/enable-trading.md). If you enable trading on a brand-new, empty account, the app will simply ask you to make your first deposit and then finish the setup automatically.
{% endhint %}

## Deposit USDC

Deposits are made by bridging USDC from Arbitrum into your trading account:

1. Connect your wallet (or your embedded wallet if you signed in with email/Google).
2. Open the **Deposit** dialog from the top bar or your [Portfolio](portfolio.md).
3. Make sure your wallet is on the **Arbitrum** network — the app will prompt you to switch if needed.
4. Enter the amount of **USDC** to deposit and confirm the transaction in your wallet.
5. The bridge processes your deposit on-chain. Your balance appears in the app once the bridge completes — usually within a moment.

{% hint style="warning" %}
**Deposit USDC on Arbitrum only.** Sending other tokens, or sending USDC from a different network, is not supported by the deposit flow and may result in loss of funds. Always double-check the network and the asset before confirming.
{% endhint %}

### Unified balance

Your deposited USDC lands in a single account balance shared between **perps and spot**. There is no need to transfer funds between sub-accounts to switch markets — the same balance backs your perp margin and your spot purchases. You can see the full breakdown (perps, spot, vaults, staking) in your [Portfolio](portfolio.md).

## Withdraw

Withdrawals work in reverse — from your trading account back to your wallet on Arbitrum:

1. Open the **Withdraw** dialog from the top bar or your [Portfolio](portfolio.md).
2. Enter the amount of USDC to withdraw.
3. Confirm with your wallet signature.
4. The funds arrive as **USDC on Arbitrum** in your wallet address.

Because Bitnex is non-custodial, withdrawals are executed by the underlying protocol's on-chain system — there is no approval queue, no support ticket, and no one who can freeze your withdrawal on the Bitnex side.

{% hint style="danger" %}
Your agent (session) key can sign orders but **cannot withdraw funds**. Withdrawals always require a signature from your own wallet. See [Enable Trading](../guides/enable-trading.md) for how this works.
{% endhint %}

## Getting USDC on Arbitrum

If you don't hold USDC on Arbitrum yet, common ways to get it:

- **Withdraw from a centralized exchange.** Most major exchanges support USDC withdrawals directly to the Arbitrum network. Select **Arbitrum (Arbitrum One)** as the withdrawal network — not Ethereum mainnet or another chain.
- **Bridge from another chain.** If your USDC lives on Ethereum or another network, use a bridge to move it to Arbitrum.
- **Swap on Arbitrum.** If you already hold other assets on Arbitrum, swap them for USDC using any decentralized exchange on the network.

You will also need a small amount of **ETH on Arbitrum** to pay the gas for the deposit transaction itself. After that, trading on Bitnex is gasless.

## Gasless trading after setup

Deposits and withdrawals are on-chain Arbitrum transactions and require gas. Everything in between does not:

- Placing, modifying, and cancelling orders costs **no gas**.
- Orders are signed automatically by your agent wallet — no wallet popup, no gas prompt.
- The only costs while trading are trading fees, shown transparently before every order — see [Fees](fees.md).

## Troubleshooting

### My deposit isn't showing yet

Bridging from Arbitrum takes a moment to finalize. If your balance hasn't appeared:

- Confirm the transaction succeeded on Arbitrum (check it in your wallet or a block explorer).
- Wait a short while — the balance appears automatically once the bridge completes; no manual claim is needed.
- Refresh the app if the balance still doesn't display after the transaction is confirmed.

### I sent funds on the wrong network or in the wrong token

The deposit flow supports **USDC on Arbitrum** only. Transfers of other tokens or from other networks are outside the supported flow and may not be recoverable. If you're unsure, verify the network and asset in the deposit dialog before confirming — and start with a small test amount.

### My wallet won't confirm the deposit

Make sure your wallet is connected to the **Arbitrum** network and holds enough ETH on Arbitrum to cover the transaction's gas. The app will prompt a network switch if you're on the wrong chain.

{% hint style="success" %}
Funded and ready? Head to the [Web Terminal](web-terminal.md) or [Lite Mode](lite-mode.md) to place your first trade.
{% endhint %}
