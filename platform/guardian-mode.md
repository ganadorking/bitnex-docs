# Guardian Mode

![Guardian Mode — your equity against your limits](../.gitbook/assets/guardian.png)

## What it is

Guardian Mode lets you set your own risk limits, and Dasus enforces them **before you sign an order**. You decide the rules once, when you're calm; they apply every time, including the times you'd rather they didn't.

{% hint style="warning" %}
**Guardian is a discipline tool, not account custody.** Your funds live on the underlying protocol and you can always trade them from another client. What Guardian guarantees is that **no order breaking your rules is placed from Dasus**. We will never tell you it makes losses impossible.
{% endhint %}

**Guardian never blocks you from closing a position or setting a stop.** Only orders that open or increase exposure are evaluated. A limit that traps you in a trade would be worse than no limit at all.

## Turning it on

Guardian Mode has its own page at **/guardian**. Activation is a short wizard — nothing turns on until the last step:

1. **Pick a risk profile** — Conservative, Balanced, or Aggressive. The profile fills in every limit; you can fine-tune them next.
2. **Adjust the key limits** — max leverage, risk per trade, daily loss, losing streak.
3. **Choose your unlock delay** — written **in days**, from 1 to 365. This is how long any future loosening will wait.
4. **Review the summary, accept the terms, and sign with your wallet.** The signature records the limits you chose; without it, nothing activates.

At that moment Guardian freezes your **starting capital** — the account value at activation — and measures your maximum drawdown against it, like a funding-firm account. The chart on the page draws your equity from that starting point against the exact lines where Guardian will block new orders, and the **Capital targets** section translates each percentage into dollars: the threshold where the block triggers and how much room you have left.

Configuration is **per wallet**: each account you connect has its own Guardian, its own limits, and its own signature.

After activation, the page shows your parameters as a plain list — rule and value, exactly as configured. Tap any number to change it (a value of 0 disables that rule). Tightening applies instantly; loosening waits for your unlock delay.

## The limits

| Limit | What it does | Measured from |
| --- | --- | --- |
| **Max leverage** | Blocks any order above this leverage | The order you're placing |
| **Max risk per trade** | Blocks the order if hitting your stop would cost more than this share of your account | Distance between entry and your stop, times leverage |
| **Daily loss** | Once you're down this much today, no new positions | Your equity curve since local midnight |
| **Weekly loss** | Same, over the week starting Monday | Your equity curve since Monday |
| **Max drawdown** | Blocks while your account sits this far below your starting capital | The capital frozen at activation (or your peak, for configs created before this existed) |
| **Trades per day** | Caps how many positions you open in a day. Closes never count | Your fills since local midnight |
| **Pause after a loss** | Forced wait after any losing close | Timestamp of your last losing fill |
| **Losing streak** | Stops you after N losses in a row | Consecutive losing closes, most recent first |
| **Extreme volatility** | Blocks markets that moved more than this in 24h | The market's 24h change |

### Notes on how these are measured

**Everything comes from your real on-chain account**, not from a counter stored in your browser. If it lived in local storage, clearing it would defeat the limit on exactly the day it matters most.

**Max risk per trade needs a stop.** Without one, the risk of a trade isn't a number anyone can compute. If you set a per-trade risk limit and place an order with no stop attached, Guardian shows a warning — you can continue, but it tells you that the limit can't protect you here.

**The losing streak resets each day.** It blocks only while your most recent loss is from today. Otherwise the block would be permanent: a streak only ends with a win, and you can't win if you can't trade. The rule means "stop for today and review", not "you're out for good".

## The unlock delay

This is the part that makes Guardian actually work.

- **Tightening a limit is immediate.** Lowering a cap or turning a rule back on applies the moment you save it.
- **Loosening a limit waits.** Raising a cap, removing a rule, or switching Guardian off does not take effect until your unlock delay has passed — the delay you wrote in days (1–365) when you activated, adjustable like any other rule.

Without this, the first time a limit gets in your way — down on the day, wanting to make it back — you'd switch it off in two clicks and the feature would be decoration.

While a change is waiting you'll see a banner with the countdown and a **Keep the strict limit** button, which cancels the pending change instantly. Going back to the stricter rule never waits.

Queueing a second loosening change restarts the clock, so the delay can't be walked around in small steps.

## When an order is blocked

You get a modal that names the rule, your limit, and the current value — for example *"Max leverage: your limit 10×, right now 25×"*. There is no "ignore and continue" button on a block. To change the limit you go to the Guardian page, and that change goes through your unlock delay.

Warnings are different: nothing is broken, but something is worth a second look. Those you can continue past with one deliberate click.

## What Guardian covers

Guardian checks every order that is signed in your browser before it is sent: the order form (market, limit, stop, scale, TWAP and chase), chart trading and dragged orders, TP/SL, edits to open orders, grid bots, Swap, the staking swap, prediction markets, Lite mode, and sub-accounts or vaults you trade from Dasus. Closing orders (reduce-only) always go through — Guardian never traps you in a position. The Guardian page shows this list so there is no doubt about what is and isn't under your rules.

## What Guardian does not do


- It does not stop you trading the same account from another client (the Hyperliquid app, other frontends, the API).
- It does not apply to copy trading: the copy engine runs on Dasus servers with its own key, outside your browser.
- It does not move, hold, or restrict your funds in any way.
- It does not close positions for you, add stops for you, or act on your account.

## Interaction with bots

Grid and DCA bots go through the same barrier. If you've hit your daily loss limit, your bots stop placing new orders too — which is the point. Cancelling existing bot orders always works.
