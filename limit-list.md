# Limit List — Daily Limit-Up/Limit-Down Stocks

## Background — A China-Specific Mechanism

Unlike US/EU markets, **Chinese A-shares enforce daily price limits**: a stock cannot rise or fall by more than a fixed percentage from the previous close in one trading day.

| Board | Daily Limit | Note |
|-------|-------------|------|
| Main board (Shanghai/Shenzhen) | **±10%** | Most stocks |
| ChiNext (创业板, 300xxx) | **±20%** | Higher tech-growth board |
| STAR Market (科创板, 688xxx) | **±20%** | Sci-tech innovation board |
| ST stocks (Special Treatment) | **±5%** | Distressed companies under restructuring |
| New IPOs (first 5 days) | No limit | Then revert to board's normal limit |

### Why this matters for investors
- **`limit_type="U"` (涨停, "limit up")**: A stock hitting its upper bound is a strong bullish signal in China. Many retail-driven strategies focus on "first board" (首板) and "consecutive boards" (连板) — stocks hitting limit-up multiple days in a row.
- **`limit_type="D"` (跌停, "limit down")**: Stuck at lower bound, often signals panic selling or a known negative event.
- **`limit_type="Z"` (炸板, "broken limit")**: Stock hit limit-up intraday but failed to close at the limit — usually a bearish reversal signal.

### Key fields explained
- **`fd_amount` (封单, "seal order amount")**: The total bid value queued at the limit-up price. A large seal indicates strong buying pressure that exhausted available sellers.
- **`first_time` / `last_time`**: When the stock first/last hit the limit during the day. Earlier first-touch + sustained close = stronger signal.
- **`open_times`**: How many times the limit was broken intraday. 0 = clean limit, higher = weaker conviction.
- **`limit_times` (连板数)**: Consecutive days at limit. "3连板" = 3 days in a row at limit-up, a momentum-trader favorite.

### Caveats for foreign investors
- Daily limits **suppress true price discovery** during extreme events. A stock might "want" to fall 30% but takes 3+ days at -10% to find equilibrium.
- This creates **"locked stocks"** — you may be unable to exit a position for several days.
- Limit-up streaks are heavily watched by retail investors and often discussed on Chinese financial social media.

## SDK Method

```python
client.limit_list(ts_code=None, start_date=None, end_date=None, limit_type=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, ts_code, name, close, pct_chg, limit, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.limit_list(limit=3, limit_type="U")
print(df[["trade_date", "ts_code", "name", "pct_chg"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit_type` | str | None | `U`=limit-up, `D`=limit-down, `Z`=broken limit |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `ts_code` | Stock code |
| `name` | Stock name |
| `close` | Closing price (CNY) |
| `pct_chg` | Price change % |
| `amount` | Turnover (thousand CNY) |
| `limit_amount` | Turnover at limit price |
| `float_mv` / `total_mv` | Free-float / total market cap |
| `fd_amount` | Seal order amount |
| `first_time` / `last_time` | First/last limit hit time |
| `open_times` | Times limit was broken |
| `limit_times` | Consecutive limit days |
| `limit` | Type: U=up, D=down, Z=broken |

## Data Coverage

- From: 2020
- Excludes ST stocks
- API path: `GET /v1/market/limit-list`
