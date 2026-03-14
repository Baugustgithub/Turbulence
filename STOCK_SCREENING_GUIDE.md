# How to Use Turbulence for Investment Decisions

## What This Tool Does (Plain English)

Turbulence is a **market stress thermometer**. It doesn't pick individual stocks — instead, it tells you **how risky the overall market is right now** so you can decide whether to buy, hold, or get defensive.

Think of it like a weather report for the stock market:

| Regime   | Score  | What It Means                          | What You Might Do                        |
|----------|--------|----------------------------------------|------------------------------------------|
| GREEN    | < 1.0  | Calm markets, low stress               | Invest normally, buy growth stocks       |
| YELLOW   | 1.0–2.0| Some stress, stay alert                | Be selective, avoid overconcentration    |
| ORANGE   | 2.0–3.0| Significant stress/fragility           | Reduce risky positions, raise cash       |
| RED      | ≥ 3.0  | Major turbulence (like COVID crash)    | Go defensive, hold cash/bonds/gold      |

---

## Quick Start: Check the Market Right Now

### Option 1: Command Line (Fastest)

```bash
cd Turbulence
python -m turbulence.run_daily
```

This prints a snapshot like:

```
  Date      : 2026-03-14
  Composite : 0.85
  Regime    : GREEN

Sub-factor z-scores:
  Turbulence z          +0.42
  Credit stress         +0.31
  Financial rel         -0.15
  Software rel          +1.20  █
  BTC rel               +0.55

  5-day trend: -0.032/day  → flat
```

### Option 2: Visual Dashboard (Best for Exploring)

```bash
streamlit run turbulence/dashboard.py
```

Opens an interactive dashboard in your browser with charts, gauges, and heatmaps.

---

## How to Use This for Stock Screening & Investment Decisions

### Strategy 1: Risk On / Risk Off

The simplest approach — use the regime to decide your overall aggressiveness.

- **GREEN regime** → "Risk On"
  - Buy stocks, especially growth names (tech, small caps)
  - Use full position sizes
  - Comfortable holding concentrated positions

- **YELLOW regime** → "Cautious"
  - Still okay to buy, but be pickier
  - Favor quality over speculation
  - Maybe hold 10–20% cash

- **ORANGE regime** → "Defensive"
  - Stop buying speculative stocks
  - Trim your weakest positions
  - Hold 20–40% cash, add bonds (TLT) or gold (GLD)

- **RED regime** → "Protect Capital"
  - Avoid buying stocks entirely
  - Sell risky holdings (ARKK-type names, small caps)
  - Move to cash, treasury bonds, or gold
  - Watch for the regime to drop back to ORANGE/YELLOW to re-enter

### Strategy 2: Read the Sub-Factors

The composite score is made up of individual signals. Each one tells you something:

| Sub-Factor       | What It Watches               | What a High Score Means                    |
|------------------|-------------------------------|--------------------------------------------|
| Turbulence z     | Overall market return chaos   | Assets are moving in unusual, extreme ways |
| Credit stress    | Junk bonds vs safe bonds      | Investors are dumping risky debt — panic    |
| Financial rel    | Bank stocks vs S&P 500        | Banks are underperforming — systemic worry  |
| Software rel     | Software stocks vs S&P 500   | Tech/growth is falling apart               |
| BTC rel          | Bitcoin vs Nasdaq             | Crypto cracking — liquidity drying up      |
| Corr break       | Correlation between assets    | Normal relationships are breaking down     |

**How to use these:**

- **Credit stress rising but everything else calm?** → Avoid junk bonds and high-yield, but stocks may be okay for now
- **Software rel spiking?** → Tech/growth selloff underway — rotate to value stocks or defensives
- **Financial rel spiking?** → Banks in trouble — avoid financials, consider if it spreads
- **BTC rel spiking?** → Liquidity is tightening — speculative assets will suffer first
- **Everything spiking at once?** → Get defensive fast, this is systemic stress

### Strategy 3: Trend Watching

The 5-day trend tells you if things are getting better or worse:

- **Rising trend + YELLOW** → Market deteriorating, might hit ORANGE soon — start getting cautious
- **Falling trend + ORANGE** → Storm may be passing — start watching for buying opportunities
- **Flat + GREEN** → Smooth sailing, stay the course

### Strategy 4: Use It as a Buy Signal

Some of the best buying opportunities come when the regime shifts **from RED/ORANGE back to YELLOW/GREEN**. This means the crisis is ending and stocks are likely still cheap.

**Watch for:**
1. Regime hits RED (crisis)
2. Score starts falling (trend turns negative)
3. Regime drops to ORANGE, then YELLOW
4. **This is your buy signal** — markets are recovering, prices are discounted

---

## What This Tool Does NOT Do

Be clear about what Turbulence is **not**:

- It does **not** pick individual stocks (it watches market-wide stress)
- It does **not** tell you exactly when to buy or sell
- It is **not** a guarantee — past patterns may not repeat
- It should be **one input** in your decision-making, not the only one

Think of it as answering: **"Is now a good time to be aggressive or defensive?"**

---

## Assets Being Monitored

The tool tracks these 18 assets to build its stress reading:

**Stock Market Indices:**
- SPY (S&P 500) — the broad U.S. stock market
- QQQ (Nasdaq 100) — big tech stocks
- IWM (Russell 2000) — small company stocks

**Bonds:**
- TLT (20+ Year Treasuries) — safe government bonds
- HYG (High Yield / Junk Bonds) — risky corporate bonds
- LQD (Investment Grade Bonds) — safer corporate bonds

**Commodities & Currency:**
- GLD (Gold) — traditional safe haven
- USO (Oil) — energy/economy gauge
- UUP (US Dollar) — currency strength

**Sector Indicators:**
- XLF (Financials) — bank health
- KRE (Regional Banks) — banking system stress
- IGV (Software) — tech/growth sentiment
- ARKK (Innovation ETF) — speculative appetite

**Alternative Asset Managers:**
- BX, KKR, APO, ARES — private equity firms (canary in the coal mine for financial stress)

**Crypto:**
- BTC-USD (Bitcoin) — risk appetite / liquidity gauge

---

## Example: Putting It All Together

Say you run the tool and see:

```
  Composite : 1.85
  Regime    : YELLOW
  Credit stress    +2.10  ██
  Software rel     +1.50  █
  5-day trend: +0.120/day  ↑ rising
```

**Translation:** The market is in caution territory and getting worse (rising trend). Credit markets are stressed (junk bonds selling off) and tech is underperforming.

**Action you might take:**
- Don't buy speculative tech stocks right now
- If you hold junk bond funds, consider trimming
- Keep some cash ready — if it hits ORANGE, you'll want dry powder
- Watch daily — if the trend reverses, the stress may blow over

---

## Disclaimer

This tool is for **educational and informational purposes only**. It is not financial advice. Always do your own research and consider consulting a financial advisor before making investment decisions. Past market patterns do not guarantee future results.
