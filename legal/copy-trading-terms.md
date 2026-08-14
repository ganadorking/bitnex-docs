# Copy Trading Terms

**Version:** v1-2026-08 · **Last updated:** August 14, 2026

These Copy Trading Terms (the "Copy Terms") govern the copy trading feature of the Bitnex interface. They supplement the [Terms of Service](../terms.md) and the [Risk Disclosure Statement](risk-disclosure.md). Before your first copy, Bitnex asks you to accept these terms by **signing a message with your wallet**; the signed record (address, version, timestamp) is stored as cryptographic proof of acceptance, and the full canonical text is displayed by your wallet at the moment of signing.

{% hint style="danger" %}
Copy trading places **real orders in your account** and can generate losses, including the **partial or total loss** of the capital you allocate.
{% endhint %}

## 1. Nature of the service

1. Copy trading is an **automation tool**: the Bitnex engine observes the public on-chain activity of the trader you select and mirrors their **new** position changes into your account, proportionally to your allocation and within the risk limits you configure.
2. Bitnex is **not** a fund manager, portfolio manager, investment advisor, or fiduciary. The selection of a trader — and the decision to start, adjust, or stop a copy — is **exclusively yours**.
3. The traders you can copy are **not** employed, vetted, endorsed, or supervised by Bitnex. Statistics shown on their profiles are computed from public on-chain data and can be delayed, incomplete, or wrong.

## 2. The agent key

1. To execute copies, you approve an **agent key** ("session key") on the Protocol. This key can **only place and manage orders** in your account. It **cannot withdraw or transfer funds** — that restriction is enforced by the Protocol itself, not by Bitnex policy.
2. The agent key is stored **encrypted** (AES-256-GCM) on Bitnex servers and is used only by the copy engine.
3. You can **revoke** the agent key at any time on-chain from the interface. Revoking it stops all copying immediately.

## 3. Execution

1. Copies are executed on a **best-effort, always-after** basis: your order is placed after the copied trader's order is observed. Price differences ("deviation"), delays, partial fills, skipped orders (for example, below the Protocol's ~$10 per-order minimum), rate limits, and execution failures are **inherent** to the service and expected in normal operation.
2. Your configured risk limits (maximum leverage, maximum entry deviation, auto-stop on loss, asset filters) are applied by the engine **before** placing each copy. Copies that violate them are skipped.
3. If your account lacks margin, copies simply do not execute until margin is available. The engine does not borrow, deposit, or move funds for you — it cannot.
4. **Inverse mode** opens the opposite side of the copied trader's positions. All the same execution risks apply.
5. **Auto-stop on loss** (when enabled) closes only the positions the engine itself opened and stops the copy. It is a full stop, not a pause. Trigger evaluation is best-effort: in fast markets the realized loss can exceed the configured threshold.

## 4. Stopping and its consequences

1. You can stop a copy at any time. **Stopping does not close the positions that are already open** in your account: they remain yours to manage.
2. Bitnex may pause or terminate the copy engine — globally or for a specific account — for maintenance, security, legal, or operational reasons. Positions already open remain in your account and under your control via the Protocol.

## 5. Fees

Copied orders pay the same trading fees as your manual orders (the Protocol's fees plus the Bitnex builder fee shown in the app). Bitnex does not currently charge a separate copy-trading fee or profit share; if that changes, it will be shown in the app before you accept it.

## 6. No liability for results

To the maximum extent permitted by law, Bitnex is not liable for trading losses arising from copy trading, including losses caused by the copied trader's decisions, execution delays or deviations, skipped or failed orders, engine downtime, or your own configuration. **Past performance of any trader guarantees nothing.**

## 7. Your representations

By enabling copy trading you represent that:

- you understand leveraged derivatives and the mechanics described in the [Copy Trading documentation](../platform/copy-trading.md);
- you meet the eligibility requirements of the [Terms of Service](../terms.md);
- the funds you allocate are yours and you can afford their total loss; and
- you will not use copy trading to manipulate markets, evade sanctions, or violate any law.

## 8. Changes

We may update these Copy Terms by publishing a new version. Material changes require re-acceptance (a new signature) before new copies can be started. Copies already running continue under the version you signed until you next interact with the feature.
