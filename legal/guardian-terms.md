# Guardian Mode Terms

**Version:** v1 · **Last updated:** August 14, 2026

These Guardian Mode Terms govern the Guardian Mode feature of the Bitnex interface. They supplement the [Terms of Service](../terms.md) and the [Risk Disclosure Statement](risk-disclosure.md). Activating Guardian Mode requires **signing a message with your wallet** that records the limits you chose; nothing activates without that signature.

## 1. What Guardian Mode is

1. Guardian Mode is a **self-discipline tool**: you define risk limits (maximum leverage, maximum risk per trade, daily and weekly loss limits, maximum drawdown, trades per day, pause after a loss, losing streak, volatility filter), and the Bitnex interface **refuses to sign new orders** that would violate them.
2. Guardian Mode is enforced **by the Bitnex interface only**, at the moment an order is signed. It does not — and cannot — control orders you place through other interfaces, bots, APIs, or wallets against the same account.
3. Guardian Mode is **not custody**. Your funds stay on the Protocol; Bitnex never holds or controls them. You can always trade the same account from any other client, with or without Guardian.

## 2. Closing is always allowed

Guardian Mode **never blocks closing a position**, reducing exposure, or placing a stop. When a limit is exceeded, only **new** risk-increasing orders are blocked.

## 3. The unlock delay

1. **Tightening a limit applies instantly. Loosening a limit — or turning Guardian off — waits** for the delay you chose at activation (from 1 day up to 365 days).
2. The delay is the point of the tool: it prevents you from removing your own protections in the middle of a losing streak. You can cancel a **pending** loosening at any time (which keeps the stricter configuration).
3. During the delay, the previously effective (stricter) configuration keeps being enforced.

## 4. Best-effort mechanism

Guardian Mode is software, and you accept that it works on a **best-effort** basis:

- Its measurements (daily loss, drawdown, streak, equity) derive from public account data that can be delayed or incomplete.
- It can fail to block an order it should have blocked, or block one it should not have. It is not a guarantee against losses of any kind.
- Configuration is stored per wallet in your browser; clearing browser data can remove your configuration (the signed activation record remains).

## 5. No liability

To the maximum extent permitted by law, Bitnex is not liable for losses that occur with Guardian Mode active (limits that did not trigger, mismeasurement, delays) nor for opportunities missed because an order was blocked. Guardian Mode does not create any duty of care, suitability obligation, or fiduciary relationship.

## 6. Changes

We may update these terms and the feature itself (available limits, evaluation logic, delay presets) by publishing a new version. Material changes are shown in the app; continued use of Guardian Mode after they take effect means you accept them.
