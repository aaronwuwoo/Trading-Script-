# NQ Context — Trading Indicator Suite

A pair of Pine Script indicators I built for trading NQ futures on funded prop firm capital. They give me the context I need to act fast at the cash open.

🔗 **Project writeup:** [aaronwuwoo.github.io/nq-context.html](https://aaronwuwoo.github.io/nq-context.html)

---

## 📊 What's in here

### `nq-context.pine` — main indicator

Overlays everything I want to see on one chart:

- **Gamma levels** — 0DTE, weekly, and monthly call walls, put walls, gamma flip lines. Each has its own styling and a staleness tracker so I know when the data is too old to trust.
- **Confluence zones** — auto-detects price areas where prior-day POC/VAH/VAL stack with round 100s/50s and QQQ-equivalent levels (via live NQ/QQQ ratio).
- **Session volume profile** — POC/VAH/VAL live, with a side histogram of where volume actually transacted.
- **Day-type detection** — measures Initial Balance vs. daily ATR to classify the day (Trend Day, Balanced, Wide IB, Coiling, Double Distribution, etc.).
- **Sweep tracking** — flags when price wicks through VAH/VAL/PDH/PDL/IBH/IBL and watches for reclaims back inside the level.
- **Six trigger patterns** — Sweep + Reclaim, Rejection Wick at Level, Trend Pullback to VWAP, Failed Breakout, Volume Climax Reversal, Compression Break.
- **Setup scoring** — stacks every context layer into a 0–10 confidence score. Triggers only fire when the score crosses my threshold so I don't take forced trades.

### `cvd-divergence.pine` — companion indicator

Tracks **cumulative volume delta** (aggressive buying vs. aggressive selling on every bar) and watches for divergences against price pivots.

When NQ pushes to a new high but CVD doesn't follow, the rally is happening on weakening order flow. New price low with CVD holding above its prior low = exhaustion from sellers. These divergences are my early signal for the cleanest reversals — moves where the crowd is positioned wrong and getting trapped.

I use it as a **second filter** on top of the NQ Context setup score. A long at a put wall with bullish CVD divergence is exactly the kind of high-conviction reversal trade I want. Short at a call wall with bearish divergence = the inverse.

---

## 🌅 My morning workflow

1. **Read flow** — check QQQ options flow on InsiderFinance (net GEX, call GEX, put GEX, dark pool prints) to set bias for the day.
2. **Pull levels** — grab fresh gamma levels from SpotGamma and plug them into `nq-context.pine`.
3. **Watch the score** — NQ Context draws every level, tracks the developing session profile, flags sweeps and reclaims, and scores setups in real time. Phone alert fires when score crosses threshold.
4. **Filter with CVD** — `cvd-divergence.pine` runs in a pane below. When it flags a divergence at a key level, the score gets a lot more meaningful.
5. **Take the trade** — or stay out. Forced trades stay quiet at 3–5/10 scores.

---

## 🛠️ How to use these scripts

1. Open [TradingView](https://www.tradingview.com)
2. Open the Pine editor
3. Paste in the script you want (`nq-context.pine` or `cvd-divergence.pine`)
4. Click **Save** → **Add to chart**
5. For `nq-context.pine`, plug in your daily gamma levels in the indicator settings — I pull mine from SpotGamma each morning.
6. Set up alerts if you want pings on your phone when high-conviction triggers fire.

---

## ⚙️ Built with

- **Pine Script v6**
- **TradingView** (charting)
- **Bookmap** (order flow context)
- **InsiderFinance** (options flow / GEX for bias)
- **SpotGamma** (daily gamma level data)
- A lot of mornings staring at NQ candles

---

## ⚠️ Disclaimer

This is a personal project. Not financial advice. I'm not responsible for trades you take with it. Use it as a learning tool, paper-trade it, and verify everything for yourself before risking real money. Markets are hard. Indicators are tools, not magic.

---

Built by [Aaron Wu](https://aaronwuwoo.github.io). UCI '30 · Business Administration · Trading NQ daily. Still iterating.
