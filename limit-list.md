# Limit List — Daily Limit-Up/Limit-Down Stocks

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
