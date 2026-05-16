# Investment and Portfolio Theory

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/1.1.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/1.2.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/1.3.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/1.4.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/2.1.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/2.2.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/2.3.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/2.4.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.2.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.3.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.4.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.5.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/4.1.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/4.2.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Portfolio Selection and Risk Management/1.1.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Portfolio Selection and Risk Management/1.2.pdf]

Coursera "Investment and Portfolio Management" specialization (Rice University) — financial asset taxonomy, time value of money, bond valuation, return measurement, and risk measurement.

---

## Time Value of Money

### Core Principle

- A dollar today is worth more than a dollar tomorrow — money has time value because it can be invested at an opportunity cost rate `r`
- **Future value (FV):** `FV = PV × (1 + r)^n` — compounding grows exponentially; $100 at 5% becomes $16,783 after 15 years
- **Present value (PV):** `PV = FV / (1 + r)^n` — discounting reverses compounding; discount rate = interest rate = opportunity cost of capital
- Three synonyms for the same concept: discount rate, interest rate, opportunity cost of capital

### Cash Flow Streams

- **Uneven stream:** compound or discount each cash flow separately, then sum
- **Annuity:** series of equal fixed payments for n periods at constant rate r
  - Future value of annuity: `FV = C × ACF(r,n)` where ACF sums compounding factors
  - Present value of annuity: `PV = C × ADF(r,n)` where ADF is the annuity discount factor
- **Sinking fund problem:** solve for C given a target FV (e.g., what annual payment to accumulate $1M in 35 years at 6%?)
- **Loan problem:** solve for C given a loan amount as PV (e.g., monthly car payment on $37,150 at 4%/yr compounded monthly over 60 months)
- **Compounding periods:** "4% per year, compounded monthly" → periodic rate = 4%/12 = 0.333% per month; use monthly periods throughout

---

## Financial Asset Taxonomy

### Financial vs. Real Assets

- **Financial assets** — claims to future cash flows (bonds, stocks, mortgages, derivatives)
- **Real assets** — produce goods/services in the economy (land, buildings, machinery)
- Financial assets redistribute risk and cash flows; they do not directly generate economic output

### Asset Class Hierarchy

```
Financial Assets
├── Fixed amount claim (Debt instruments)
│   ├── Money market: maturity ≤ 1 year, high liquidity, low risk
│   └── Capital market (Bond market): maturity > 1 year, less liquid
└── Residual/equity claim
    ├── Preferred stock
    └── Common stock (Equity market)
```

### Three Broad Asset Classes

- **Fixed income / debt:** promise predetermined future cash flows; range from T-bills (risk-free) to junk bonds (high default risk); includes government bonds, corporate bonds, mortgage loans, municipal bonds
- **Equity instruments:** residual claim — equity holders receive what remains after debt holders are paid; represent ownership; no promised cash flow
- **Derivative securities:** contracts whose value derives from underlying financial assets (stocks, bonds, currencies, commodities); used for hedging and speculation

### Traditional vs. Alternative Asset Classes

- **Traditional:** public equities, investment-grade bonds, cash
- **Alternative:** private equity, hedge funds, real estate, commodities, infrastructure; typically lower liquidity, higher fees, often less correlated with traditional assets

---

## Bond Valuation

### Key Bond Features

| Feature | Description |
|---|---|
| **Face value (par value)** | Principal returned at maturity; typically $1,000 for corporate bonds |
| **Coupon rate** | Annual interest as % of face value; C = coupon rate × F |
| **Coupon payment** | Periodic cash flow; U.S. bonds typically semi-annual |
| **Maturity** | Date principal is repaid |

### Zero-Coupon Bond

- Single cash flow at maturity equal to face value F
- Price = `F / (1 + r)^T` where r = discount rate, T = years to maturity
- Example: 1-year zero-coupon, F = $10,000, r = 5.35% → Price = $10,000 / 1.0535 = $9,492

### Coupon Bond

- Cash flows = annuity of coupons C + face value F at maturity
- Price = `PV(annuity of C, r, T) + F / (1 + r)^T`
- If coupon rate > YTM: bond trades at premium (above par)
- If coupon rate < YTM: bond trades at discount (below par)
- If coupon rate = YTM: bond trades at par

### Yield to Maturity (YTM)

- YTM = single discount rate that equates bond price to PV of all promised cash flows = IRR of the bond
- Inverse of price: when market rates rise, bond prices fall; when rates fall, prices rise
- Example: 20-year zero-coupon, F = $1,000,000 selling at $455,500 → YTM = ($1,000,000 / $455,500)^(1/20) - 1 ≈ 4.0%

---

## Measuring Returns

### Holding Period Return (HPR)

- `HPR = (Price_end - Price_begin + Cash dividends) / Price_begin`
- Example: Buy at $100, sell at $110, receive $5 dividend → HPR = (110 - 100 + 5) / 100 = 15%
- Applies to any asset; cash dividends for stocks, coupon payments for bonds

### Multi-Period Return Aggregation

- **Gross return:** `(1 + r)` — the growth factor per period
- **Cumulative value:** product of all gross returns; $1 × (1+r₁) × (1+r₂) × ... × (1+rₙ)
- **Geometric mean (realized return):** `[(1+r₁)(1+r₂)...(1+rₙ)]^(1/n) - 1` — correct measure of how much wealth grew per year; accounts for compounding
- **Arithmetic mean:** simple average of annual returns — unbiased estimate of the future expected return; does NOT reflect actual wealth accumulation when returns vary year to year
- Rule: use geometric mean to describe the past; use arithmetic mean to forecast the future

### Expected Return (Forward-Looking)

- If scenarios with probabilities are available: `E[r] = Σ p_s × r_s` (probability-weighted average)
- Example scenarios: Excellent (p=0.25, r=31%), Good (p=0.45, r=14%), Poor (p=0.25, r=-6.75%), Crash (p=0.05, r=-52%) → E[r] = 7.45%

---

## Measuring Risk

### Variance and Standard Deviation

- **Variance (σ²):** expected value of squared deviations from the mean — `σ² = Σ p_s × (r_s - E[r])²`
- **Standard deviation (σ):** square root of variance — common unit for risk; intuitive as "typical deviation from expected return"
- Higher volatility = higher variance = higher standard deviation
- Risk interpretation: the wider the dispersion of outcomes around the mean, the greater the uncertainty

### Limitations of Variance as a Risk Measure

Standard deviation assumes returns are normally distributed. Real asset returns deviate from normal in two important ways:

#### Skewness

- Measures asymmetry of the return distribution
- Normal distribution: skewness = 0
- **Negative skew (left skew):** extreme negative values dominate; distribution has a long left tail
- **Positive skew (right skew):** extreme positive values dominate; right tail is long
- Critical insight: when distribution is left-skewed, standard deviation **underestimates risk** — it misses the probability of large losses
- S&P 500 skewness ≈ -0.6 (mildly left-skewed); equity returns are not perfectly symmetric

#### Kurtosis

- Measures degree of "fat tails" — probability mass in extreme events
- Normal distribution: kurtosis = 0 (or 3 depending on convention)
- **High kurtosis ("leptokurtic"):** fat tails; extreme events more likely than normal distribution predicts
- Standard deviation underestimates likelihood of extreme events when kurtosis is elevated
- S&P 500 kurtosis ≈ 4.0 (slightly fat tails)

### Volatility Strategy Illustration (from Ang 2014)

Comparison of volatility-selling strategy vs. S&P 500 (1989–2012):

| Metric | Volatility Strategy | S&P 500 |
|---|---|---|
| Mean return | 9.9% | 9.7% |
| Standard deviation | 15.2% | 15.1% |
| Skewness | -8.3 | -0.6 |
| Kurtosis | 104.4 | 4.0 |

- Both strategies look identical on mean and std dev alone — but the volatility strategy has extreme negative skewness (-8.3) and catastrophic kurtosis (104.4): it collects a steady premium during calm markets but suffers catastrophic losses during crises
- This is the canonical example that **variance alone is insufficient as a risk measure** — skewness and kurtosis reveal hidden tail risk

### Key Takeaway on Risk Measurement

---

## Portfolio Construction Principles

[Source: WORK/KNOWLEDGE/Business/Financial Management/Financial Investment I/Financial Investment I.pdf]

Coursera iMBA "Investments" (University of Illinois, Prof. Scott Weisbenner) — pages 1–10 read; intro and module overview only; full transcript content not transcribed (see cant-move.md).

Module 1 lesson structure (topics covered in full course):
- Lesson 1-2: Investments toolkit
- Lesson 1-3: Historical returns in the U.S.
- Lesson 1-4: Return and risk — intro to portfolios
- Lesson 1-5: Portfolio choice in general settings
- Lesson 1-6: Portfolio choice when correlations change
- Lesson 1-7: Calculating efficient portfolios of risky assets
- Lesson 1-8: Calculating more efficient portfolios
- Lesson 1-9: Module 1 review

### Core Lesson from Intro (pages 1-10)

- **Correlation dominates individual returns in portfolio construction** — assembling assets with the highest individual expected returns is not optimal if they are highly correlated
- Analogy: 2003-04 LA Lakers (all-star individuals: Kobe, Shaq, Karl Malone, Gary Payton) lost to 2003-04 Detroit Pistons (role-specialized team with complementary skills) 4-1 in NBA Finals
- Portfolio lesson: "Don't just care about expected returns of assets. Care a lot about how the assets in the portfolio correlate with each other."
- **Past performance is not a guarantee of future performance** — the Lakers were odds-on favorites; individual asset track records do not predict portfolio outcomes
- U.S. stocks have historically returned ~12%/year; not a guarantee going forward

Four statistical moments needed to fully describe a return distribution:
1. **Mean** — expected return (central tendency)
2. **Variance/Std dev** — dispersion around the mean
3. **Skewness** — asymmetry; negative skew = hidden downside tail
4. **Kurtosis** — fat tails; high kurtosis = catastrophic event risk understated by std dev

---

## Interest Rate Conventions

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/1.3.pdf]

### APR vs. Effective Rate

- **APR (Annual Percentage Rate) / Stated rate:** the advertised rate; e.g., "4% per year, compounded monthly" — this is NOT the actual annual growth rate
- **Effective annual rate (EAR):** what $1 actually grows to in one year: `EAR = (1 + APR/m)^m - 1` where m = compounding periods per year
- Example: APR = 4%/yr compounded monthly → EAR = (1 + 0.04/12)^12 − 1 = 4.074%
- T-bill yields and credit card APRs are stated rates; mortgage payments use the stated/12 periodic rate directly

### Effective Rate Conversions

- From periodic rate to any horizon t (in periods): `(1 + r_period)^t - 1`
  - Effective 2-month rate from monthly r: `(1+r)^2 - 1`
  - Effective 18-month rate: `(1+r)^18 - 1`
  - Effective annual rate from semiannual (m=2): `(1 + APR/2)^2 - 1`
- Rule: convert APR → periodic rate first, then compound over target horizon

### Continuous Compounding

- Limit as m → ∞: `FV = PV × e^(r×t)` where r is the continuously compounded rate
- Effective annual rate from continuously compounded r: `EAR = e^r - 1`
- Continuously compounded rate equivalent to EAR: `r_cc = ln(1 + EAR)`
- Used extensively in derivatives pricing (Black-Scholes), fixed income analytics, and quant finance

---

## Perpetuities and Growing Cash Flow Streams

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/1.4.pdf]

### Perpetuity

- Infinite series of equal fixed payments C per period
- `PV = C / r`
- Example: $1,000/year forever at r=10% → PV = $1,000 / 0.10 = $10,000
- The payment is received starting one period from now (ordinary perpetuity)

### Growing Perpetuity

- Payments grow at constant rate g per period forever
- `PV = C / (r − g)` — requires r > g (otherwise PV is infinite)
- Gordon Growth Model for stock valuation: `P = D₁ / (r − g)` where D₁ = next dividend, g = sustainable growth rate

### Growing Annuity

- Fixed n payments growing at rate g per period
- `PV = C/(r−g) × [1 − ((1+g)/(1+r))^n]`
- Example: Salary starting at $90K, growing 5%/yr for 5 years, r=8%: PV = (90K / 0.03) × [1 − (1.05/1.08)^5]
- As n → ∞ and g < r, growing annuity formula converges to growing perpetuity

---

## Money Market Instruments

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/2.3.pdf]

The money market consists of very short-term (≤1 year) debt instruments characterized by high liquidity and low credit risk. Central banks use it as the primary channel for monetary policy transmission.

### Federal Funds Market

- **Federal funds:** reserve balances that banks are required to hold at the Federal Reserve
- Institutions with excess reserves lend overnight to institutions short on reserves
- Rate = **federal funds rate** — unsecured overnight interbank rate; key monetary policy instrument
- Fed targets this rate via open market operations; historically ranged from near-zero (2009–2015) to ~20% (1980 Volcker)

### LIBOR (London Interbank Offered Rate)

- Daily survey-based rate at which large banks report they can borrow unsecured in the London interbank market
- Reference rate embedded in trillions of derivative contracts, mortgages, and commercial loans
- **LIBOR rigging scandal:** banks manipulated survey submissions to profit on derivative positions; resulted in large fines and settlements; LIBOR was phased out (replaced by SOFR in the U.S.)

### U.S. Treasury Bills (T-Bills)

- Zero-coupon securities issued by the U.S. Treasury; maturities of 4, 13, 26, and 52 weeks
- Backed by full faith and credit of U.S. government → effectively zero default risk; used to develop risk-free benchmark rates
- Highly liquid; traded OTC at very low transaction cost
- **Quoted as discount from face value on a 360-day basis:**
  `Price = F × (1 − discount_rate × days_to_maturity / 360)`
  Example: 86-day T-bill, bid discount 0.358 on $100,000 face → Price = $100,000 × (1 − 0.00358 × 86/360) = $99,914.46
- Ask yield (bond-equivalent yield) normalizes to a 365-day actual basis for comparison with coupon bonds

### Certificates of Deposit (CDs)

- Time deposit with a bank: fixed term, fixed interest; principal + interest returned at maturity
- Negotiable CDs (large denomination, ≥$100K) are tradeable in secondary market

### Commercial Paper (CP)

- Short-term unsecured promissory notes issued by corporations (1–270 days)
- Alternative to bank borrowing for investment-grade issuers; lower cost than revolving credit
- Typical use: bridge finance, working capital, M&A bridging
- Example: Verizon issued CP to bridge the $4.4B AOL acquisition (2015)

### Repurchase Agreements (Repo)

- **Repo:** sale of a security with commitment to repurchase at a specified price on a specified date — effectively a collateralized loan (seller borrows cash, pledges securities as collateral)
- **Reverse repo:** opposite side of the transaction (lender of cash, receives securities as collateral)
- Repo rate = implicit interest cost; overnight repos are most common
- Critically important in fixed income trading: used by dealers to finance bond inventories on a fully collateralized basis

---

## Bond Market Instruments

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/2.4.pdf]

### U.S. Treasury Notes and Bonds

- **Notes:** maturities 2–10 years; **Bonds:** maturities 10–30 years
- Both are coupon securities: semi-annual coupon payments + face value at maturity
- **On-the-run:** most recently auctioned issue for a given maturity — most liquid benchmark
- **Off-the-run:** prior issues; slightly less liquid; typically trade at a yield premium
- Quoted as price (per $100 face) plus accrued interest; prices above par when coupon > YTM

### TIPS (Treasury Inflation-Protected Securities)

- Principal adjusted proportionally to Consumer Price Index (CPI) changes
- Coupon payments applied to inflation-adjusted principal → both coupon and principal grow with inflation
- TIPS yield = real (inflation-adjusted) interest rate; nominal T-bond yield − TIPS yield = breakeven inflation expectation
- In 2012: 10-yr TIPS yield was near zero or negative — investors accepting real losses for inflation protection

### Corporate Bonds

- Firms borrow publicly via corporate bonds; pay semi-annual coupons + face value at maturity
- Governed by bond indenture (covenant document)
- Subject to **default risk**; rated by Moody's, S&P, Fitch
- **Investment grade:** Baa/BBB or above; **High-yield / junk:** Ba/BB or below
- Structural variants:
  - **Floating rate bond:** coupon resets periodically (e.g., LIBOR + spread) — minimal interest rate duration risk
  - **Secured bond:** backed by specific collateral; senior in liquidation
  - **Debenture:** unsecured; subordinated debentures are junior to regular debentures
  - **Callable bond:** issuer has right to redeem early at a preset call price — issuer benefits when rates fall
  - **Convertible bond:** holder can convert to equity at a preset conversion ratio — valuable when stock appreciates

### Asset-Backed Securities (ABS) and Mortgage-Backed Securities (MBS)

- **Securitization:** pooling loans (mortgages, auto loans, student loans, credit card receivables) and issuing claims against the pool cash flows as tradeable securities
- **MBS:** most common; pass-through structure routes mortgage principal + interest payments to bondholders as they are received
- Historical note: David Bowie securitized future music royalties for $55M in bonds (1997) — early celebrity ABS

### Municipal Bonds

- Issued by state and local governments; typically fund public infrastructure
- **Interest income is federal tax-exempt** — primary advantage; often exempt from state tax in issuing state
- Tax-equivalent yield: `muni_yield / (1 − marginal_tax_rate)` for comparison to taxable bonds

### International Bonds

- **Eurobond market:** bonds issued in a currency other than the issuer's home currency (Eurodollar bonds, Euroyen bonds); issued offshore; lighter regulatory burden
- **Sovereign debt:** government-issued bonds denominated in foreign currency; emerging market debt carries significant default risk (e.g., Greek sovereign debt crisis 2010–2012)

---

## Equity Securities

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.2.pdf]

### Common Stock

- Issued to raise equity capital; represents ownership shares
- Confers voting rights at shareholders' meetings and claim on earnings (dividends)
- Shareholders are **residual claimants**: last in priority in liquidation; maximum loss = amount invested (**limited liability**)
- **Agency problem:** separation of ownership (shareholders) and management (executives) creates incentive misalignment
- No maturity

### Preferred Stock

- Hybrid: promises fixed dividends (bond-like) but no contractual obligation to pay (stock-like)
- No voting rights; unpaid dividends accumulate (cumulative preferred) and must be paid before common dividends
- No specified maturity

### Debt vs. Equity

- Debt claims senior to equity claims in all scenarios
- Interest on debt is **tax-deductible**; dividends are **not** — creates the "tax shield" advantage for debt financing

### Major Stock Indices

| Index | Region | Notes |
|---|---|---|
| DJIA | US | 30 large-cap, price-weighted |
| S&P 500 | US | 500 stocks, market-cap-weighted; benchmark |
| NASDAQ | US | Tech-heavy |
| Wilshire 5000 | US | Total market |
| Russell 2000 | US | Small-cap |
| Nikkei 225 | Japan | |
| FTSE 100 | UK | |
| STOXX 600 | Europe | |
| Hang Seng | Hong Kong | |
| MSCI World | Global | |

### Stock Return and Valuation

**Total return** = dividends + capital gains: `r = (D_{t+1} + P_{t+1} - P_t) / P_t`

**Dividend Discount Model (DDM):** value = PV of all future dividends
- Gordon growth model (constant dividend growth): `P_0 = D_1 / (r - g)`
- Sensitive to small changes in r and g — treat output as range, not point estimate

---

## Derivative Securities

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.3.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.4.pdf]
[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/3.5.pdf]

### Options

- **Option:** right (not obligation) to buy or sell the underlying at a fixed price on or before expiration
- **Premium:** the cost of acquiring an option (unlike forwards/futures, which cost nothing to enter)
- **Call:** right to **buy** at strike price X; exercised when S_T > X
- **Put:** right to **sell** at strike price X; exercised when S_T < X
- **American option:** exercisable any time before expiration; **European:** only at expiration

**Option payoffs and profits (X = strike, S_T = spot at expiration, P = premium):**

| Position | Payoff condition | Payoff | Profit |
|---|---|---|---|
| Long call | S_T > X | S_T − X | S_T − X − P |
| Long call | S_T ≤ X | 0 | −P |
| Short call | S_T > X | −(S_T − X) | P − (S_T − X) |
| Long put | S_T < X | X − S_T | X − S_T − P |
| Long put | S_T ≥ X | 0 | −P |
| Short put | S_T < X | −(X − S_T) | P − (X − S_T) |

### Forwards and Futures

- Both: agreement to buy/sell asset at a specified future date and price; no money exchanged at inception
- **Long position:** commits to buy; **Short position:** commits to deliver
- Unlike options: **both sides are obligated** — no choice at expiration
- **Forward contracts:** OTC, customized, bilateral counterparty risk; widely used for FX hedging
- **Futures contracts:** exchange-traded (CBOT, CME), standardized contracts, **clearinghouse eliminates counterparty risk**
- Futures cover commodities (corn, crude oil, live cattle) and financials (stock indices, currencies, T-bonds)

**Payoffs at maturity:**
- Long: `(P_T − F_0) × contract_size`
- Short: `(F_0 − P_T) × contract_size`

**FX forward example:** US investor hedging 1M Mexican pesos due in 6 months; agrees forward rate 20 MXN/USD. If spot rate at maturity is 25 MXN/USD: short (investor) payoff = (0.05 − 0.04) × 1M = +$10,000.

---

## Market Participants and Structure

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/4.1.pdf]

### Investors and Issuers

| Actor | Role |
|---|---|
| New households | Net dis-savers; borrow for capital goods |
| Established households | Net savers; accumulate multi-asset portfolios |
| Retired households | Net dis-savers; de-accumulate, shift to low-risk |
| Firms | Net demanders of capital; issue debt and equity |
| Governments | Net borrower or lender depending on fiscal balance; T-bills/notes/bonds as primary issuance vehicle |

### Financial Intermediaries

- **Role:** match capital suppliers (investors) with demanders (firms, government)
- Include: banks, investment companies, insurance companies, credit unions

### Investment Companies

- Pool investor funds to invest on their behalf
- **NAV = (assets − liabilities) / shares outstanding**
- **Closed-end fund:** fixed share count; shares trade on exchanges at premium/discount to NAV
- **Open-end (mutual) fund:** redeemable at NAV daily; types: money market, equity, sector, bond, international, balanced, index
- **ETF:** exchange-traded; priced throughout the day like stocks; examples: SPY (S&P 500), DIA (DJIA), QQQ (NASDAQ 100)
- **Private equity:** equity in non-public firms; exempt from SEC registration; funds startups, management buyouts, LBOs
- **Hedge funds:** unregistered, restricted to high-net-worth/institutional investors; standard fee = 2% AUM + 20% profits

### Primary vs. Secondary Markets

- **Primary market:** new securities issued; company raises funds
  - **IPO:** first public share offering; underwriter buys entire issue (**firm commitment**) or best-efforts
  - **SEO (Seasoned Equity Offering):** additional shares by already-public company
  - **Private placement:** direct sale to accredited investors; no SEC registration
  - IPO process: select bank → red herring (preliminary prospectus) → roadshow/bookbuilding → SEC approval → pricing
  - **IPO underpricing:** average first-day return historically 10–65%; systematic, especially in tech booms
- **Secondary market:** trades in existing securities; proceeds go to sellers, not company

### Trading Mechanics

[Source: WORK/KNOWLEDGE/Business/Investment and Portfolio Management/Global Financial Markets and Instruments/4.2.pdf]

- **Market order:** execute at best available price; guaranteed execution, uncertain price
- **Limit order:** buy at max / sell at min specified price; guarantees price, not execution; forms the **limit order book**
- **Stop order:** triggered when price crosses threshold
  - **Stop-loss:** sell when price drops below level (risk management)
  - **Stop-buy:** buy when price rises above level (used with short positions)
- **Buying on margin:** borrow from broker; securities as collateral; amplifies gains and losses
  - **Initial margin requirement:** minimum equity fraction at time of purchase (e.g., 50%)
  - **Maintenance margin:** minimum ongoing equity fraction (e.g., 30%); breaching triggers **margin call**
- **Short selling:** borrow security → sell → later buy back to "cover"; profits when price falls
  - Short-sellers must post margin; margin call if price rises beyond maintenance threshold
  - Role: price discovery, hedging; controversial (SEC banned short-selling on ~1000 firms in Sept 2008)
- **Algorithmic / HFT trading:** computer-driven; exploits micro-price discrepancies; co-location of servers at exchanges reduces latency
- **Flash crash (May 6, 2010):** $4B automated futures sell order → HFTs absorbed then rapidly offloaded → feedback loop → Dow fell ~1000 pts in minutes
