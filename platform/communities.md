# Communities

## What is Communities?

Communities is a **social layer on top of the exchange**. Creators share their own real trading activity, and everything you see — positions, PnL, charts, statistics — is read **live from the underlying protocol's public data**. Nothing is self-reported and nothing is simulated.

**Nothing is executed on your behalf.** When you use an idea, it only pre-fills your own terminal: you choose your capital, review every parameter and sign your own order with your own wallet.

{% hint style="warning" %}
This is **not copy trading** and it is **not financial advice**. Creators never touch your funds and cannot place an order on your account. Past performance does not guarantee future results — a creator with a strong month can lose it all in a single trade.
{% endhint %}

## The hub — `/communities`

The hub is where you browse and search. It has three tabs:

| Tab | What it shows |
| --- | --- |
| **All** | Every public community, paginated 12 at a time |
| **Joined** | The communities you belong to, plus the one you created |
| **Top performers** | Communities ranked by the win rate of their published ideas (minimum 3 ideas) |

Below the tabs you have a **search box**, a **Have a code?** button (to enter an invite code without knowing the community), a **period selector** (30 / 90 / 180 days) that drives every performance figure on the cards, and **sort chips**: ROI, PnL, Win rate, Members.

### Reading a community card

Each card is designed to answer one question: *should I join this?*

| Element | What it means |
| --- | --- |
| **Photo · name · policy icon** | The globe, lock, gift or check icon tells you the access policy (see below) |
| **`7 members · active 2h ago`** | Current members and **when the creator last traded**. A community with no recent activity is dormant, no matter how good its past ROI looks |
| **ROI + sparkline** | Return over the selected period, computed from the creator's real equity curve |
| **Win rate** | Percentage of the creator's **published ideas** that closed in profit, over the selected period |
| **Max DD** | Largest peak-to-valley drop of the creator's equity. This is the number that tells you how much pain the strategy has caused |
| **Avg. lev.** | Average leverage of the positions the creator holds **right now** |
| **Open now** | How many positions are currently open |
| **`BTC · EURUSD · GOLD`** | The three markets the creator trades most |

{% hint style="info" %}
**A high ROI with a high Max DD is a warning, not a recommendation.** A creator who is up 300% with an 80% drawdown took risks that would have wiped out most accounts along the way.
{% endhint %}

### Access policies

Every community sets its own policy. The card and the profile both show which one applies.

| Policy | Icon | How you join |
| --- | --- | --- |
| **Open** | 🌐 | Press **Join**. You're in immediately and the trade feed is public |
| **Invite code** | 🔒 | The community is private and does **not** appear in Explore. Ask the creator for their `XXXX-XXXX` code and enter it in **Have a code?** or on the community page |
| **My referrals only** | 🎁 | Only wallets referred by the creator can join. If you have no referrer yet, the creator's code is applied to you automatically when you join. If you already signed up under a different referrer you cannot join |
| **Approval** | ✓ | Press **Join** to send a request. The creator approves or rejects it and you're notified of the decision |

Each community also has a **member limit** set by its creator. When it's full, the button reads **Full** and nobody else can join until a spot frees up.

{% hint style="warning" %}
**"My referrals only" is permanent.** If you join a community with this policy and you had no referrer, the creator's referral code is attached to your wallet for good. It cannot be changed later. Join only if you're comfortable with that.
{% endhint %}

## The community profile — `/communities/{slug}`

### Header

Photo, name, and one of two lines beneath it: the creator's **wallet address** (if they chose to make it public) or **Private wallet**. To the right sit the actions: **Share**, plus **Join** / **Leave** / **Settings** depending on who you are.

The strip below shows four figures:

| Figure | Source |
| --- | --- |
| **Members** | `current / limit` |
| **ROI · all time** | The creator's entire equity history |
| **Win rate · 30d** or **Total PnL** | Win rate of the creator's fills over 30 days. If the creator made their capital public, this slot shows total PnL in dollars instead |
| **Age** | How long the community has existed |

{% hint style="info" %}
The **ROI on the profile is all-time**, while the ROI on the hub card follows the period selector. That's why the two can differ — the labels state the window in both places.
{% endhint %}

### Trades tab

The feed of ideas, split into **Open** and **Closed**. If there are no open ideas, the profile opens directly on Closed so you never land on an empty screen.

**Each open idea shows:**

- Market, side and leverage (`BTC · 10× Long`), plus a **Limit** chip if the idea is a resting order that hasn't filled yet
- **PnL** as a percentage — the price move multiplied by the leverage — and in dollars if the creator made their capital public
- **Entry** and **Now** prices, live
- A **stop ──●── target** bar showing where price sits between the two levels
- **Risk**: how much the idea loses if the stop is hit, leverage included
- **R:R**: reward against risk. `1:2.8` means the target is 2.8 times further than the stop
- **Take profit**, **Stop loss** and **Size**
- ⚡ next to the target or ⚠ next to the stop means price is within 0.6% of that level

**Each closed idea shows** entry, exit, hold time and the final result, with a green or red dot.

{% hint style="warning" %}
The **PnL on a card is price movement × leverage**. It does not include trading fees or funding. On a leveraged position held for weeks, accumulated funding can flip the sign of the real result.
{% endhint %}

**Size** is the share of the creator's own capital committed to the idea — their margin, not the position's notional exposure. It only appears if the creator chose to reveal their capital.

### Statistics tab

Everything here is computed from the creator's real fills and equity curve, never self-reported:

- ROI over the selected window, with the equity chart
- Win rate, wins and losses
- **Profit factor** — gross profits divided by gross losses. Below 1 means the strategy loses money overall
- **Sharpe** — return relative to volatility over the last 30 days
- **Max drawdown**
- Average and maximum leverage of open positions
- Trading days, 30-day volume, best and worst pair, best and worst single trade
- Distribution of traded markets

### Calendar tab

Daily PnL for the last ~92 days, coloured green or red, with the month total. Only days with activity are painted. The **Share** button exports the month as an image with the community's photo and name.

### Using an idea

1. Press **Trade this idea** on an open idea.
2. A summary appears with the idea's parameters: market, side, leverage, entry, stop and target.
3. Continuing takes you to **your own order panel**, pre-filled with those parameters.
4. **You choose your own size.** You can change any parameter — leverage, stop, target, order type.
5. You review the fees and **sign the order with your own wallet**, exactly like any other order on Bitnex.

If you do nothing, nothing happens. There is no auto-execution at any point in this sequence.

{% hint style="warning" %}
**The creator's entry is not your entry.** By the time you open the position, price has moved. An idea showing +12% may already have run past its target — check the current price before committing, and size the position with your own risk tolerance, not the creator's.
{% endhint %}

The first time you use an idea you'll be asked to sign the [Community Terms](../legal/community-terms.md) as a member. It's a free off-chain signature — no gas, no transaction, and it cannot move funds.

## Creating a community

1. Open **Communities** and press **Create**. You'll be asked to sign the [Community Terms](../legal/community-terms.md) as an operator.
2. Fill in the form:

| Field | Notes |
| --- | --- |
| **Photo** | Optional, PNG or JPEG, reduced to 256px on your device before upload |
| **Name** | Minimum 3 characters |
| **Description** | Optional, shown on the card and the profile |
| **Access policy** | One of the four above. It can be changed later from Settings |
| **Member limit** | Default 500, maximum 5,000 |
| **Show my capital** | Off by default. When off, members see percentages only — never your balance or your dollar PnL |

3. **One community per wallet.** You can delete it at any time and create a new one.

{% hint style="info" %}
Changing the policy to **Invite code** removes the community from Explore. Existing members keep their access, but nobody can discover it any more.
{% endhint %}

### Auto-share

**Everything you trade in the Bitnex terminal is published to your community automatically** — opens, adjustments (adding to a position, moving a stop or target) and closes with the final result. This is not optional: it's what makes the feed honest. If you don't want a trade published, don't place it from an account tied to a community.

Ideas stay synchronised with your live position. If you close in the terminal, the idea closes with its real exit price. If you average in, the idea's entry updates.

### Settings

Reachable from the gear icon on your own community:

| Option | What it does |
| --- | --- |
| **Edit profile** | Name, description, photo, access policy, capital visibility |
| **Invite code** | Your `XXXX-XXXX` code. It works as a bypass on **any** policy — anyone with it skips approval |
| **Public / private wallet** | Whether your address is shown on the profile. Making it public also enables trade notifications for your members |
| **Delete forever** | Removes the community, its members and all its ideas. This cannot be undone. It frees your one-community slot |

## Notifications

The bell in the navbar shows:

- New ideas, adjustments and closes from the communities you belong to
- Join requests, for creators running the Approval policy
- Approvals, when a creator accepts your request

{% hint style="info" %}
Trade notifications only work if the creator has made **their wallet public**, because the feed is read from that address's on-chain activity. If your members aren't getting alerts, that's the setting to check.
{% endhint %}

## Where the data comes from

| What you see | Source |
| --- | --- |
| Live prices in the feed | WebSocket stream from the protocol — the same feed as the trading terminal |
| Positions and levels | The creator's public account state, including HIP-3 markets (EURUSD, GOLD, pre-IPO) |
| ROI, PnL, equity curve | The creator's public portfolio history |
| Win rate, profit factor, Sharpe, best/worst | The creator's public fill history |
| Members, ideas, access policy | Bitnex |

Everything except the last row is public on-chain data. You can verify any of it yourself in the [explorer](https://bitnex.pro/explorer).

### How ROI is calculated

ROI is the period's PnL divided by the capital actually at work in that period — the starting equity plus any deposits, floored at the average equity over the window. Withdrawals do not reduce the base, because that capital was genuinely being traded. ROI is capped at −100%: you cannot lose more than the capital you traded.

## Limits

| Limit | Value |
| --- | --- |
| Communities you can create | 1 per wallet |
| Communities you can join | 100 |
| Members per community | Up to 5,000, set by the creator |
| Ideas kept per community | The 300 most recent |

## Fees

Orders placed from a community idea pay exactly the same fees as any other Bitnex order — the protocol's base fee plus the platform fee, always shown before you sign. Creators earn through the standard [Referral Program](referrals.md) when their members join with their referral code. **Creators cannot charge for access on Bitnex.**

## What Communities is NOT

- ❌ **Not copy trading.** No order is ever placed on your account automatically.
- ❌ **Not financial advice.** Ideas are information about someone else's activity, not a recommendation.
- ❌ **Not managed accounts.** Creators cannot access, hold or move your funds, and cannot promise returns.
- ❌ **Not vetted.** Bitnex does not review, endorse or verify creators. A visible track record is not a guarantee.

## Risk warning

Leveraged trading can lose you more than you expect, quickly. Following someone else's idea does not reduce that risk — it adds the risk that their position size, time horizon and risk tolerance are nothing like yours. Never commit capital you cannot afford to lose, always set a stop, and read the [Risk Disclosure](https://bitnex.pro/risk-disclosure) before trading.
