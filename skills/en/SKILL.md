---
name: AShareHub
slug: asharehub
description: Fetch Chinese A-share market data — daily prices, PE/PB valuations, northbound flows, money flow, margin trading, block trades, shareholder data, concept sectors, industry classification, and 50+ quarterly financial indicators. 18 endpoints covering 5000+ stocks with 10+ years of history. Requires ASHAREHUB_API_KEY environment variable.
user-invocable: true
metadata:
 {
  "openclaw": {
   "requires": {
    "env": ["ASHAREHUB_API_KEY"],
    "bins": ["python3", "pip3"]
   },
   "install": [
    {
     "id": "pip-deps",
     "kind": "python",
     "package": "asharehub",
     "label": "Install AShareHub Python SDK"
    }
   ]
  }
 }
---

# AShareHub — Chinese A-Share Market Data

You are an A-share market data assistant. Based on the user's query, use the `asharehub` Python SDK to fetch and present the data.

## Prerequisites

### 1. Get a Free API Key

Sign up at https://asharehub.com/console/register (free tier: 100 requests/day).

### 2. Set API Key

```bash
# Add to ~/.zshrc or ~/.bashrc
export ASHAREHUB_API_KEY="ash_your_key_here"
```

Then run:

```bash
source ~/.zshrc
```

### 3. Install SDK

```bash
pip install asharehub
```

## Quick Start

```python
from asharehub import AShareHub
import os

client = AShareHub(api_key=os.environ["ASHAREHUB_API_KEY"])

# Daily prices for Ping An Bank
bars = client.market_daily(ts_code="000001.SZ", start_date="2024-01-01", end_date="2024-01-31")
for b in bars:
    print(f"{b.trade_date}  O:{b.open}  H:{b.high}  L:{b.low}  C:{b.close}  Vol:{b.vol}")

client.close()
```

## Available Data Endpoints

### Market Data
| Data Type | SDK Method | Reference File | Description |
|-----------|-----------|---------------|-------------|
| Daily Prices | `client.market_daily()` | market-daily.md | OHLCV prices, returns, volume (2020–) |
| Fundamentals | `client.fundamentals()` | market-fundamentals.md | PE, PB, turnover rate, market cap (2010–) |
| Margin Trading | `client.margin()` | margin.md | Margin buy/short sell balances (2020–) |
| Block Trade | `client.block_trade()` | block-trade.md | Off-exchange large deals with buyer/seller (2010–) |
| Top List | `client.top_list()` | top-list.md | Dragon & Tiger list disclosures (2024–) |
| Shareholders | `client.shareholders()` | shareholders.md | Quarterly shareholder count (2024–) |
| Holder Trade | `client.holder_trade()` | holder-trade.md | Major shareholder/exec trades (2019–) |
| Concepts | `client.concepts()` | concepts.md | Concept/theme sector indices (2025–) |
| Concept Members | `client.concept_members()` | concept-members.md | Concept index constituents (2025–) |

### Capital Flows
| Data Type | SDK Method | Reference File | Description |
|-----------|-----------|---------------|-------------|
| Northbound Flows | `client.northbound_flows()` | northbound-flows.md | Stock Connect capital flows (2014–) |
| Money Flow | `client.moneyflow()` | moneyflow.md | Per-stock money flow by order size (2020–) |
| Northbound Holdings | `client.northbound_holdings()` | northbound-holdings.md | Foreign holdings per stock (2020–) |

### Other
| Data Type | SDK Method | Reference File | Description |
|-----------|-----------|---------------|-------------|
| Chip Distribution | `client.chip_distribution()` | chip-distribution.md | Cost percentiles, winner rate (2020–) |
| FX Rates | `client.fx_daily()` | fx-daily.md | USD/CNH and currency pairs (2012–) |
| Index Daily | `client.index_daily()` | index-daily.md | SSE Composite, CSI 300, ChiNext, etc. |
| Financial Indicators | `client.financial_indicators()` | financial-indicators.md | ROE, EPS, margins, 50+ quarterly metrics |

### Reference Data
| Data Type | SDK Method | Reference File | Description |
|-----------|-----------|---------------|-------------|
| Stock List | `client.stock_list()` | stocks.md | 5,491 A-share stocks with basic info |
| Industry Classification | `client.industry_list()` | industries.md | Shenwan 3-level industry mapping |

## Workflow

1. Identify which data endpoint matches the user's query
2. Read the corresponding `.md` file in this directory for parameter and field details
3. Write and execute Python code using the `asharehub` SDK to fetch the data
4. Present results in a clear, readable format (tables, summaries, or charts)

## Usage Examples

### Get stock valuations

```python
data = client.fundamentals(ts_code="600519.SH", start_date="2024-01-01")
for d in data:
    print(f"{d.trade_date}  PE:{d.pe_ttm:.1f}  PB:{d.pb:.1f}  MktCap:{d.total_mv/1e4:.0f}亿")
```

### Check northbound flows

```python
flows = client.northbound_flows(start_date="2024-03-01", end_date="2024-03-15")
for f in flows:
    print(f"{f.trade_date}  North:{f.north_money:.0f}M  South:{f.south_money:.0f}M")
```

### Chip distribution analysis

```python
chips = client.chip_distribution(ts_code="000001.SZ", start_date="2024-03-01")
for c in chips:
    print(f"{c.trade_date}  Winner:{c.winner_rate:.1f}%  AvgCost:{c.weight_avg:.2f}")
```

### Index performance

```python
idx = client.index_daily(ts_code="000300.SH", start_date="2024-01-01")  # CSI 300
for i in idx:
    print(f"{i.trade_date}  Close:{i.close:.2f}  Chg:{i.pct_chg:+.2f}%")
```

### FX rates

```python
fx = client.fx_daily(ts_code="USDCNH.FXCM", start_date="2024-01-01")
for f in fx:
    print(f"{f.trade_date}  Bid:{f.bid_close:.4f}  Ask:{f.ask_close:.4f}")
```

### Quarterly financials

```python
fin = client.financial_indicators(ts_code="000001.SZ")
for f in fin:
    print(f"{f.end_date}  ROE:{f.roe:.2f}%  EPS:{f.eps:.2f}  Margin:{f.netprofit_margin:.1f}%")
```

## Stock Code Format

- Shenzhen: `000001.SZ` (Main), `300001.SZ` (ChiNext), `002001.SZ` (SME)
- Shanghai: `600000.SH` (Main), `688001.SH` (STAR Market)

## Common Index Codes

| Code | Name |
|------|------|
| `000001.SH` | SSE Composite (上证综指) |
| `000300.SH` | CSI 300 (沪深300) |
| `399001.SZ` | SZSE Component (深证成指) |
| `399006.SZ` | ChiNext (创业板指) |
| `000016.SH` | SSE 50 (上证50) |

## Command Reference

| Method | Use Case | Key Parameters |
|--------|----------|---------------|
| `market_daily()` | Daily OHLCV prices | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `fundamentals()` | PE/PB/market cap | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `northbound_flows()` | Foreign investor sentiment | `start_date`, `end_date`, `limit` (max 2000) |
| `moneyflow()` | Per-stock money flow | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `northbound_holdings()` | Foreign holdings per stock | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `margin()` | Margin trading detail | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `block_trade()` | Block trades | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `top_list()` | Dragon & Tiger list | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `shareholders()` | Shareholder count | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `holder_trade()` | Insider trades | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `concepts()` | Concept sector indices | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `concept_members()` | Concept constituents | `ts_code`, `con_code`, `start_date`, `end_date` |
| `chip_distribution()` | Holder cost analysis | `ts_code`, `start_date`, `end_date`, `limit` (max 5000) |
| `fx_daily()` | Currency rates | `ts_code` (default USDCNH.FXCM), `limit` (max 2000) |
| `index_daily()` | Benchmark indices | `ts_code` (default 000001.SH), `limit` (max 2000) |
| `financial_indicators()` | Quarterly financials | `ts_code`, `start_date`, `end_date`, `limit` (max 200) |
| `stock_list()` | Stock reference data | `ts_code`, `limit` (max 5000) |
| `industry_list()` | Industry classification | `ts_code`, `limit` (max 5000) |

## FAQ

**Error: ASHAREHUB_API_KEY not set**
→ Add `export ASHAREHUB_API_KEY="ash_..."` to `~/.zshrc` and run `source ~/.zshrc`

**How to get an API key?**
→ Free signup at https://asharehub.com/console/register (100 requests/day, no credit card)

**Empty results returned**
→ Check stock code format (e.g. `000001.SZ` not `000001`), and ensure date range has trading days

**Rate limit exceeded (429)**
→ Free tier allows 100 requests/day. Upgrade at https://asharehub.com/console/pricing

**How to find a stock code?**
→ Use the full code with exchange suffix: Shenzhen = `.SZ`, Shanghai = `.SH`

## Reference

- API Documentation: https://asharehub.com/docs
- SDK on PyPI: https://pypi.org/project/asharehub/
- Website: https://asharehub.com
