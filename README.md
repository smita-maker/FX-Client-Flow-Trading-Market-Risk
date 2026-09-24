# FX Client Flow Trading & Market Risk Simulator

A Python and Power BI simulation of an FX flow trading desk, modelling institutional client flow, dealer pricing, currency positioning, partial hedging, mark-to-market P&L and market risk across EUR/USD, GBP/USD and USD/JPY.

## Project Overview

The project simulates the workflow of an FX client-flow trading desk:

**Market data → Client flow → Pricing → Execution → Dealer positioning → Hedging → Residual exposure → P&L → VaR / Expected Shortfall → Stress testing**

The objective is to demonstrate practical understanding of FX trading, sales and market-risk concepts using a reproducible quantitative framework.

## Key Results

| Metric | Result |
|---|---:|
| Simulated client trades | 1,000 |
| Simulated client flow | $11.16B |
| Simulated spread revenue | $1.63M |
| Simulated MTM P&L | $8.95M |
| 95% Historical VaR | $313.86K |
| 95% Expected Shortfall | $500.13K |
| Maximum residual exposure | $88.39M |
| Adverse stress loss | $9.45M |

The adverse stress scenario exceeds the illustrative $5M stress limit, while the simulated residual-position, VaR and Expected Shortfall metrics remain within their respective illustrative limits.

## Market Data

Historical daily FX rates are sourced from the Federal Reserve Economic Data (FRED).

Pairs analysed:

- EUR/USD
- GBP/USD
- USD/JPY

Period:

**January 2021 – December 2024**

Daily returns are used to calculate descriptive statistics, correlations and the simulated trading-book risk measures.

## Client Flow Simulation

Because institutional client trading blotters are proprietary, client activity is synthetically generated.

Four client segments are modelled:

- Asset Managers
- Hedge Funds
- Corporates
- Banks

The simulation assigns client types, FX pairs, trade directions and trade notionals using predefined modelling assumptions.

The simulated client flow is then priced using pair-specific spreads and size-based spread adjustments.

## Dealer Positioning and Hedging

Client trades are translated into dealer currency positions.

The model assumes that the dealer hedges **80% of cumulative currency exposure**, leaving a **20% residual position** exposed to FX movements.

For EUR/USD and GBP/USD, positions are calculated in the relevant base currency. USD/JPY exposure is represented in USD.

This allows the model to capture the relationship between:

**Client flow → dealer inventory → hedging → residual market exposure**

## P&L

The model calculates simulated mark-to-market P&L using the opening residual FX position and subsequent FX price movements.

The resulting P&L is a simulated trading-book measure rather than realised trading profit.

The model does not incorporate:

- Transaction costs
- Slippage
- Funding costs
- Financing effects
- Full hedge execution costs

## Market Risk

Three complementary approaches are used:

### Historical VaR

A 95% one-period historical VaR is calculated from the simulated event-day portfolio P&L distribution.

**95% VaR: $313.86K**

### Expected Shortfall

Expected Shortfall measures the average loss within the worst 5% of the simulated P&L distribution.

**95% Expected Shortfall: $500.13K**

### Stress Testing

An adverse 5% FX scenario is constructed against the direction of each current residual position.

The resulting simulated adverse stress loss is:

**$9.45M**

This exceeds the illustrative $5M stress limit.

## Power BI Dashboard

The Power BI dashboard contains four views:

### 1. Trading Desk Overview

Provides a high-level view of:

- Client flow
- Simulated spread revenue
- Simulated MTM P&L
- Historical VaR
- Adverse stress loss
- Risk-limit utilisation

### 2. Client Flow

Analyses:

- Client flow by segment
- Spread revenue by client segment
- Trade frequency
- Average trade size

### 3. Trading Book & P&L

Analyses:

- Maximum residual exposure by FX pair
- Simulated MTM P&L by pair
- Cumulative P&L
- Final residual positions

### 4. Market Risk

Analyses:

- Adverse stress loss by FX pair
- Risk-limit utilisation
- VaR versus Expected Shortfall
- Maximum residual exposure

## Technology

- Python
- Pandas
- NumPy
- SciPy
- Matplotlib
- Excel
- Power BI

## Repository Structure

```text
FX-Client-Flow-Trading-Market-Risk/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── FX_Client_Flow_Market_Risk_Simulator.ipynb
│
├── powerbi/
│   ├── FX_Client_Flow_Market_Risk_Simulator.pbix
│   └── FX_Client_Flow_Market_Risk_Dashboard.pdf
│
└── data/
    └── FX_Client_Flow_PowerBI_Data.xlsx
```

## Important Modelling Disclaimer

Client trades, client-type probabilities, trade-size distributions, risk limits and stress scenarios are synthetic modelling assumptions created for this project.

The project does not use proprietary bank, client or trading-desk data.

Market prices are sourced from publicly available FRED data.

Risk metrics are calculated from the simulated trading-book P&L distribution and should not be interpreted as forecasts or actual institutional risk limits.

## Author

**Smita Bonal**

MSc Finance & Investment | University of Leeds

**Focus:** FX Trading, Market Risk, Asset Management and Quantitative Finance


