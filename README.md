# NQ Context — Trading Indicator Suite

A pair of custom Pine Script indicators I built and trade live every morning on NQ futures.

🔗 **Project writeup:** [aaronwuwoo.github.io/nq-context.html](https://aaronwuwoo.github.io/nq-context.html)

---

## 📊 What's in here

### `nq-context.pine`
The main indicator. Overlays everything I want to see at a glance:

- **Gamma levels** — 0DTE, weekly, and monthly call walls, put walls, and gamma flip lines, with staleness tracking
- **Confluence zones** — auto-detected price areas where prior-day POC/VAH/VAL stack with round 100s/50s and QQQ-equivalent levels
- **Session volume profile** — live POC/VAH/VAL with a side histogram
- **Day type detection** — measures Initial Balance vs. daily ATR to classify the day (Trend Day, Balanced, Wide IB, Coiling, Double Distribution, etc.)
- **Sweep tracking** — flags when price wicks through VAH/VAL/PDH/PDL/IBH/IBL
- **Six trigger patterns** — Sweep + Reclaim, Rejection Wick, Trend Pullback to VWAP, Failed Breakout, Volume Climax Reversal, Compression Break
- **Setup scoring** — combines every layer into a 0–10 confidence score; triggers only fire when the score crosses a threshold

### `cvd-divergence.pine`
Companion script. Tracks cumulative volume delta and auto-marks bull/bear divergences against price pivots.

---

## 🛠️ How to use

1. Open [TradingView](https://www.tradingview.com)
2. Open the Pine editor
3. Paste in the script you want
4. Click **Save** → **Add to chart**
5. For `nq-context.pine`, plug in your daily gamma levels in the indicator settings (I get mine from SpotGamma)

Set up alerts on the indicator if you want pings on your phone when a high-conviction trigger fires.

---

## ⚙️ Built with

- **Pine Script v6**
- **TradingView**
- A lot of mornings staring at NQ candles

---

## ⚠️ Disclaimer

This is a personal project. It's not financial advice and I'm not responsible for trades you take with it. Use it as a learning tool, paper-trade it, and verify everything for yourself before risking real money.

---

Built by [Aaron Wu](https://aaronwuwoo.github.io). Still iterating.
