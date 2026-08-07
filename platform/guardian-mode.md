# Guardian Mode

## What it is

Guardian Mode lets you set your own risk limits, and Bitnex enforces them **before you sign an order**. You decide the rules once, when you're calm; they apply every time, including the times you'd rather they didn't.

{% hint style="warning" %}
**Guardian is a discipline tool, not account custody.** Your funds live on the underlying protocol and you can always trade them from another client. What Guardian guarantees is that **no order breaking your rules is placed from Bitnex**. We will never tell you it makes losses impossible.
{% endhint %}

**Guardian never blocks you from closing a position or setting a stop.** Only orders that open or increase exposure are evaluated. A limit that traps you in a trade would be worse than no limit at all.

## Turning it on

Guardian Mode has its own page at **/guardian**. Open it and flip the switch in the header.

The first time you enable it, Bitnex fills in a conservative starting point: 10× max leverage, 2% risk per trade, 5% daily loss, 10% weekly loss, 20% max drawdown, 10 trades per day, 15-minute pause after a loss, and a 3-loss streak limit. Adjust any of them to your own style.

Each rule has its own switch, separate from its value: turning a rule off and setting its number are two different gestures, so you never have to type a zero into a risk field to disable it.

## The limits

| Limit | What it does | Measured from |
| --- | --- | --- |
| **Max leverage** | Blocks any order above this leverage | The order you're placing |
| **Max risk per trade** | Blocks the order if hitting your stop would cost more than this share of your account | Distance between entry and your stop, times leverage |
| **Daily loss** | Once you're down this much today, no new positions | Your equity curve since local midnight |
| **Weekly loss** | Same, over the week starting Monday | Your equity curve since Monday |
| **Max drawdown** | Blocks while your account sits this far below its all-time peak | Your full equity history |
| **Trades per day** | Caps how many positions you open in a day. Closes never count | Your fills since local midnight |
| **Pause after a loss** | Forced wait after any losing close | Timestamp of your last losing fill |
| **Losing streak** | Stops you after N losses in a row | Consecutive losing closes, most recent first |
| **Allowed hours** | Outside your window you can only close, not open | Your device's local clock |
| **Allowed days** | Same, by weekday | Your device's local clock |
| **Extreme volatility** | Blocks markets that moved more than this in 24h | The market's 24h change |

### Notes on how these are measured

**Everything comes from your real on-chain account**, not from a counter stored in your browser. If it lived in local storage, clearing it would defeat the limit on exactly the day it matters most.

**Max risk per trade needs a stop.** Without one, the risk of a trade isn't a number anyone can compute. If you set a per-trade risk limit and place an order with no stop attached, Guardian shows a warning — you can continue, but it tells you that the limit can't protect you here.

**The losing streak resets each day.** It blocks only while your most recent loss is from today. Otherwise the block would be permanent: a streak only ends with a win, and you can't win if you can't trade. The rule means "stop for today and review", not "you're out for good".

**Hours use your device's clock**, so they follow you across time zones. A window can cross midnight (22 → 06 works).

## The unlock delay

This is the part that makes Guardian actually work.

- **Tightening a limit is immediate.** Lowering a cap, shortening your hours, or turning a rule back on applies the moment you save it.
- **Loosening a limit waits.** Raising a cap, removing a rule, or switching Guardian off does not take effect until your unlock delay has passed (24 hours by default).

Without this, the first time a limit gets in your way — down on the day, wanting to make it back — you'd switch it off in two clicks and the feature would be decoration.

While a change is waiting you'll see a banner with the countdown and a **Keep the strict limit** button, which cancels the pending change instantly. Going back to the stricter rule never waits.

Queueing a second loosening change restarts the clock, so the delay can't be walked around in small steps.

## When an order is blocked

You get a modal that names the rule, your limit, and the current value — for example *"Max leverage: your limit 10×, right now 25×"*. There is no "ignore and continue" button on a block. To change the limit you go to the Guardian page, and that change goes through your unlock delay.

Warnings are different: nothing is broken, but something is worth a second look. Those you can continue past with one deliberate click.

## What Guardian does not do

- It does not stop you trading the same account from another client.
- It does not move, hold, or restrict your funds in any way.
- It does not close positions for you, add stops for you, or act on your account.

## Interaction with bots

Grid and DCA bots go through the same barrier. If you've hit your daily loss limit, your bots stop placing new orders too — which is the point. Cancelling existing bot orders always works.
