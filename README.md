# Frankenstein Ultimate — Zero-Lag Live Scalper (Pine Script v5)

Frankenstein Ultimate is a high-performance TradingView indicator built for scalpers and intraday traders who need fast, reliable, and low-latency BUY / SELL signals. It combines predictive trend modeling with zero-lag momentum detection and multi-layer market filters to deliver high-probability entries on liquid instruments and lower timeframes.

- Deterministic, non-repainting signals
- Optimized for 1m–5m scalping and quick intraday moves
- Clear visual entry markers, dynamic Stop Loss (SL) and Take Profit (TP) display

---

## Quick demo
![Frankenstein Ultimate screenshot](https://github.com/user-attachments/assets/e6e7e74e-c2f3-4a22-a818-9a641953ee8f)

---

## Design goals
- Minimize indicator lag while preserving stability and signal quality  
- Avoid signals in range-bound, low-volatility markets  
- Require multi-layer confirmation before signaling an entry  
- Show immediate, visual risk boundaries (SL / TP) at time of signal

---

## How it works (overview)
Frankenstein Ultimate evaluates price in real-time using four independent components. A trade signal is emitted only when all components agree.

1. Momentum Detection — TEMA (Triple Exponential Moving Average)  
   - TEMA is the primary trigger. It reduces lag vs a standard EMA and reacts faster to momentum shifts. Crossovers of price vs TEMA trigger potential short-term directional changes.

2. Trend Validation — LSMA (Least Squares Moving Average)  
   - LSMA uses linear regression to estimate the trend slope and project the current trend. Signals are allowed only when price direction aligns with the projected trend.

3. Momentum Exhaustion Filter — Stochastic RSI  
   - Filters out entries when momentum is overextended. Longs avoid overbought, shorts avoid oversold to reduce late entries.

4. Volatility Filter — ATR-based threshold  
   - Blocks signals in low-range / sideways markets, preventing overtrading when price movement is insufficient for scalping.

At signal time, the indicator plots entry arrows/labels and automatically computes and draws Stop Loss (based on recent swing structure) and dynamic Take Profit (based on user Risk:Reward).

---

## Signal generation logic
A BUY or SELL signal is generated only when all of these are true:
- Momentum trigger is valid (price <> TEMA crossover)
- Trend direction is confirmed (price relative to LSMA projection)
- Momentum is not exhausted (Stoch RSI filter)
- Volatility exceeds the minimum threshold (ATR filter)

When a signal is produced the indicator plots:
- An entry label/triangle (green = BUY, red = SELL)
- SL line at the computed stop level
- TP marker(s) based on Risk:Reward

---

## Trade conditions

### Long (BUY)
- Price crosses above TEMA
- Price is above the LSMA trend line
- Stochastic RSI < 80 (not overbought)
- Volatility (ATR) confirmed above threshold

### Short (SELL)
- Price crosses below TEMA
- Price is below the LSMA trend line
- Stochastic RSI > 20 (not oversold)
- Volatility (ATR) confirmed above threshold

---

## Features
- Real-time BUY / SELL labels directly on candles
- Zero-lag, color-coded trend visualization
- Automatic Stop Loss based on recent swing structure
- Dynamic Take Profit computed from user Risk:Reward
- Visual TP / SL markers at entry
- No repainting behavior — historical signals remain fixed

---

## Configuration (defaults & description)

| Parameter | Default | Description |
| --- | ---: | --- |
| Reaction Speed | 10 | TEMA sensitivity (lower = faster reaction) |
| Global Trend | 80 | LSMA trend length (longer = smoother trend) |
| Volatility Filter | 20 | ATR activity threshold (percent or units depending on implementation) |
| Risk : Reward | 1.5 | Take Profit multiplier relative to Stop Loss |

> Tip: Start with defaults and adjust Reaction Speed and Global Trend to match the volatility of your chosen instrument/timeframe.

---

## Installation
1. Open TradingView  
2. Navigate to the Pine Editor  
3. Create a New Script  
4. Paste the Frankenstein Ultimate source code  
5. Click Save  
6. Select Add to Chart

No external libraries or data sources are required.

---

## Recommended markets & timeframes
- Best: highly liquid indices, futures, Forex majors, high-volume equities  
- Acceptable: crypto pairs with tight spreads (test first)  
- Timeframes: 1m to 5m (primary use-case). Can be used on higher timeframes with parameter tuning.

---

## Best practices
- Always backtest and paper-trade before using live capital.  
- Use instrument-specific Reaction Speed and Global Trend settings.  
- Prefer instruments and sessions with reliable liquidity (overnight / thin sessions can produce false signals).  
- Combine with sound position sizing and a written trading plan.

---

## Limitations
- The indicator does not predict future price — it identifies conditions that historically correlate with higher probability moves.  
- It cannot eliminate trading risk or guarantee profits.  
- Results vary across instruments and market regimes; parameter tuning and validation are required.

---

## Example workflow
1. Add Frankenstein Ultimate to chart with default settings.  
2. Observe signals for a single instrument for at least 1–2 trading sessions (paper trade).  
3. Tune Reaction Speed for the instrument/timeframe to reduce false signals.  
4. Validate overall expectancy (win rate × avg R) via backtest or manual journaling.  
5. Deploy with strict position sizing and SL management.

---

## FAQ
Q: Does the indicator repaint?  
A: No. Frankenstein Ultimate is deterministic and non-repainting; plotted historical signals remain fixed.

Q: Can I use it on higher timeframes?  
A: Yes, but results and optimal parameters differ. Test and tune the Global Trend and Reaction Speed.

Q: Is performance guaranteed?  
A: No. All trading contains risk. Use backtesting and paper trading.

---

## Changelog
- v1.0 — Initial release: TEMA trigger, LSMA trend validation, Stochastic RSI filter, ATR volatility filter, dynamic SL/TP plotting.

---

## License
MIT License — free to use, modify, and distribute with attribution. See LICENSE file for full text.

---

## Disclaimer
Trading involves significant financial risk. Past performance does not guarantee future results. This indicator is a decision-support tool only and does not replace disciplined risk management or independent analysis. Always validate strategies using paper trading or backtesting before deploying capital.
